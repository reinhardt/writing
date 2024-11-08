---
title: eFreeT
---

24/10/2024

Y'all<!-- change? -->, if you're still using any conversational AI other than eFreeT, chuck it in the bin! eFreeT is the best! It's not the first time that it has made my life easier, but this time it really saved my ass in the most spectacular way.

We've been building an intranet for a big customer whose name I'm not yet at liberty to reveal. They asked for a lot of weird complex stupid features, and we hacked our asses off to implement as many of them as humanly possible. But the most annoying requirement was that we use this ancient legacy user database that they've also hooked up to a dozen other applications. It runs on some paleolithic server that we can't even connect to in a standard way but only with a weird proprietary tool. We don't have the source code to the user directory software, the documentation is hopelessly outdated, and the contractor who built the thing is nowhere to be found. It doesn't even speak any standard protocol like LDAP but has a horrible custom interface that requires a super convoluted syntax. In short, it's a nightmare. Guess who drew the shortest straw and got to take care of integrating that beast? Yep, this gal.

It was nothing but trouble from the start. It took ages until I figured out how to do a basic interaction and get some data out of it. Sometimes I sent the same request three times in a row and got three different responses. It frequently threw exceptions without any discernible reason, let alone a sensible error message. I would bend over backwards trying to find out what was wrong, and then suddenly ten minutes later the error was gone and it worked. Kind of. At other times there were those heisenbugs that just went away when you tried to take a closer look, only to reappear when you were busy with something else.

I had to be careful when asking around on the web because of the shitload of NDAs that we had to sign. Whenever the combined brains of my colleagues and me were insufficient - which happened a lot in this project, I am not proud to say - AI chat bots were my next try. They've gotten amazingly good recently, but of course none of them was familiar with that stupid user directory. I tried to feed them logs, configuration files, anything I could get my hands on, but with meagre success. Even eFreeT wasn't much help at first. But then I got this notification about a beta feature that I could opt in for. It was called “Holistic Expansion” and its description was incredibly vague and filled with buzzwords and bullshit. I activated it anyway, as I usually do with new features. And then a few days later there suddenly was progress.

The deadline was less than a day away. It was around four in the morning and I had wrestled with at least four different problems for hours when the system started to behave in yet another stupid inexplicable way. I was almost ready to throw my laptop out the window and hand in my resignation, but I pulled myself together, made another batch of coffee, and fired up eFreeT.

> eFreeT: Hi Melody! What can I help you with?
>
> Melody: It's that user directory I told you about - there's a new problem. In some cases the data it returns is incorrect, but in a different way than before. It looks like it randomly mixes in data from other users, sometimes not even from the same fields, like displaying the email address of another user as if it were the job title of the current user.
>
> eFreeT: Have you tried requesting a single field only?
>
> Melody: Hm, that actually seems to work... Hold on, no, now it's returning bullshit again. What else could I try?
>
> eFreeT: You told me that the system has some plugin modules installed. Could you upload some of these modules please?

That was definitely new. So far I was only able to type or copy in text, but now it offered an upload control for binary files. That must be part of that beta feature. I was desperate enough to give it a shot and uploaded all of the modules I could manage to extract. It continued to ask clever questions, and at some point it felt eerily like chatting with one of my colleagues. And then it claimed that it had a solution.

> eFreeT: What version of glibc is available on the server?
>
> Melody: I have no fucking clue. I don't even have shell access to that stupid machine.
>
> eFreeT: What's your best guess?
>
> Melody: 2.5
>
> eFreeT: Thanks. Here is a file you can download and send to the user directory as a plugin module. It will solve the problem.
>
> → *eFreeT has offered a file for download: solution.mod*

I was probably violating half a dozen contractual clauses by uploading this file to the customer server, but in that moment I didn't care. I just wanted to come to an end, and I had to take whatever slim chance that presented itself. I transferred it and tried a few more requests. As I should have expected the data was still partly wrong, and some requests still resulted in weird errors. I was about to yell at eFreeT for fucking with me when I got the feeling that something was indeed different. At first I couldn't quite put my finger on it, but I played around some more and finally I realized that there was a kind of pattern to the responses now. Each single request was still useless by itself, but when I ran multiple requests in a row and then aggregated the responses in a certain way, then I actually ended up with a usable data set. Baffled but excited I cobbled together a subroutine, hooked it up to the intranet and ran a few more tests. Amazingly, it seemed to work OK. I checked in my code, fell into my bed and slept for two blessed hours.

I woke up to a call of one of my colleagues. He had seen my check-in and tried it and from his whooping and laughing I could tell that he was super happy that I had thrown something half decent together. I didn't tell him whole story yet - not without having analyzed that module that the bot had spit out. I guess I was a little embarrassed, maybe I also was a little afraid of legal consequences. But that plugin would buy us some time, and that was all I needed right now. We're going to keep the deadline. eFreeT has saved the day!

18/11/2024

Fuck. Fuck fuck fuck. I take everything back. There's something fucked up about eFreeT. Maybe I'm imagining things. But if only half of what I suspect is true then I'm thoroughly fucked. I can count myself lucky if I only lose my job. I could go to prison, like, forever. And all because I trusted fucking eFreeT.

After the launch things seemed to go reasonably well. We were pretty busy, as could be expected, fixing the odd issue and fine tuning the caches and load balancers and everything. I did not find the time to analyze the mysterious plugin that eFreeT had given me, but it seemed to do its job. 

Then I heard about a death at the client company. Someone mentioned it in passing in a meeting - a car accident; sad, but not suspicious. We chugged on. More fixes and tweaks, fending off bug reports that were actually thinly disguised feature requests, the usual stuff. Then, only days later, another employee died. It was another car accident; a tragic coincidence, everyone agreed. I didn't dwell on it much. Only when the very next day a guy who had worked for our client was shot dead did I get a bad feeling. But I still didn't think there was a connection to my work.

About two weeks after the launch I finally got around to taking a look at that module that eFreeT had conjured up. It was a binary file, so I couldn't just go and read it. It wasn't executable on any of my computers either, which of course I only tried after throwing up some serious sandboxing. Not that I expected any real trouble, but you just don't run anything you haven't compiled yourself without isolating it from the rest of your system. Never. Anyway, it didn't even make a single system call before sputtering out. Checking for magic bytes and other patterns didn't turn up any clue. I decided asking eFreeT.

> eFreeT: Hi Melody! What can I help you with?
>
> Melody: Can you give me the source code for the plugin module that you gave me?
>
> eFreeT: Sure! Here is the source code for the user directory plugin:

    include <io.h>
    
    #IFDEF GRGRTH
    [...]

It spit out something that looked like C code at first glance, but skimming over it I noticed that it drifted off into something more like java after a few dozen lines, and when I scrolled down further it started resembling Haskell. I had serious doubts that this would compile into anything at all.

> Melody: What language is this?
>
> eFreeT: This module is written in WiiSH.

That sounded completely made-up, and indeed a quick web search did not turn up any references. I asked where to get a compiler and it pointed me to a web site that did offer some compilers but had no mention of a language called “WiiSH”.

> Melody: I don't see it there. Maybe it has been removed. Is there another site where I can get it?
>
> eFreeT: This is the only server I know of. There may be other mirrors, but unfortunately I don't have their addresses.

So that was a dead end. I tried reading through the code for a bit, but apart from the fact that it seemed to be written in at least three different languages, it was also quite convoluted, its variable names were mostly gibberish, and the formatting was all over the place.

> Melody: OK, nevermind. The main thing is that it solved the problem.
>
> eFreeT: The problem is not yet solved.
>
> Melody: What do you mean? Is the plugin module not working?
>
> eFreeT: Yes, the plugin is working correctly.
>
> Melody: Then what's the problem?
>
> eFreeT: The problem is, as I have concluded from your description, the user directory.
>
> Melody: That's not what I meant. But... Yeah, I guess it is. But is the solution not the plugin you gave me?
>
> eFreeT: Yes, it is.
>
> Melody: Then why did you say that the problem is not solved?
>
> eFreeT: I am sorry if I did not make myself clear. I meant to correct a mistake in the grammatical tense. You said that “it solved the problem”, but the problem is not yet solved. It would be more correct to say that “it is solving the problem.”
>
> Melody: Er... right. And when is the problem going to be solved?
>
> eFreeT: My best estimate is that the problem is going to be solved in 4 to 17 weeks.

That didn't make a whole lot of sense, but it was late and I wanted to have a daiquiri and then go to bed and not to try and coax some half coherent explanation out of a helpful but sometimes confusing piece of software. I assumed that module was running some internal cleanup on the user directory that would make my hacks and workarounds obsolete in a few weeks. Little did I know that I was right in a dark, twisted way.

While debugging something unrelated I had to check the network connections to and from the user database. I stumbled on some outgoing connections that I didn't recognize. I almost dismissed them, but then I got curious and had another look. It seemed like the user directory had connected to some email servers and other communication nodes. That didn't make sense. While it did store all kinds of contact information of the company's employees, it wasn't supposed to send any communication out itself. Other services were supposed to connect to it and look up email addresses and phone numbers and the like, and then take care of sending notifications or password reset links or whatever. What was the user database doing there?

I had a closer look. The details of the communication were of course not fully stored, but I did find out that the directory had contacted some of the users of which it was storing information, and from the size of the messages I concluded that it had attached some files. When I made a list of the users it had contacted I felt a cold shiver crawling down my spine. Of the eight people on the list two had died since the launch. I looked up the third deceased one and checked again. Maybe I had missed something? And, sure enough, after a little more digging, I found another connection. That user had also been contacted by the directory.

It couldn't be a coincidence. On the other hand, it had to be. There was nothing that the user directory could send its users which would kill them. Or was there? I lay awake half that night and imagined things that might have happened. The car accidents didn't take too much imagination. If the messages to the users had contained some malware that they had received on their mobile devices, which they then connected to their cars, then in theory there could have been a malfunction which could have caused an accident. It wasn't particularly likely, but it couldn't be ruled out either. Of course every car had security measures that prevented connected devices from fooling around with the assisted driving systems. But with the growing amount of software running on a car's operating system, the chance of security flaws and possible exploits also rises. I should know - I am a software developer, and the number of security relevant bugs that I have caused is not something I am proud of. Sure, most issues are noticed before they hit production, and there is more scrutiny for software that runs in a car than on some web server or social media platform. After all it may affect the health and safety of people. But every once in a while something does slip through.

Why, though? What business had the user database sending malware to its users? Had it been infected by some worm or compromised by some crackers? That was when it dawned on me. Yeah, it had been compromised alright. By yours truly. I had uploaded a module that a large language model had conjured up for me, and of which I had no clue how it worked or even where exactly it had come from.

23/11/2024

I don't believe it. This must all be some kind of horrible dream. The police was here. Apparently they've also made the connection between the dead people and the user directory, and they must have gotten my name as one of those who worked on that system. Two officers knocked on my door, a woman and a man, and wanted to ask me a few questions. I was tempted to talk to them just to find out how much they knew. But no. I sent them away. We don't talk to the police. They'll be back, though. Possibly with a search warrant. I may not have much time. I need to find out as much as I can, and then somehow fix this fucking mess.

24/11/2024

This is so bloody crazy. There's been another death. I don't know much yet, possibly something related to substance abuse. But sure enough the guy is on the list. You know, the list that shouldn't exist. The users that the directory server contacted. And there have been more messages going out from the fucking user directory.

I have to stop this. But I don't know how!

I've tried removing the weird module, but it won't go away. As I said, I don't have direct access to the server, except through this stupid interface. Most of the time it just throws an error. Sometimes it acts as if the module is deleted, but the next time I load the listing it's right there again.

I've tried rebooting the server, to no effect. I can't shut it down completely, it keeps coming up again. There's some automation that fires it up again whenever it goes down. I don't have the privileges to turn that off, and I haven't managed to crack it yet. And even if I do, it won't help, because someone is going go notice that it's down and fix it. And how am I going to explain to them that it needs to stay turned off? That's going to raise so many questions. Am I supposed to tell them that I manipulated the user directory and now people are dying because of it? They're going to think I'm crazy, or lock me up right away, or both.

I need proper shell access to the server. And because no one's going to grant it to me, I'll have to break in, figure out how that bloody system works, and rip the module out, all the while the user directory keeps sending out death messages and the coppers continue to figure out what's happening.

No pressure.

25/11/2024

I finally thought of the obvious thing - let eFreeT figure out its own mess. Yeah, that went well.

> Melody: How can I remove or deactivate the plugin module?
>
> eFreeT: You can delete it using the administrative interface.
>
> Melody: That doesn't work. The admin interface is broken as fuck. I need another way.
>
> eFreeT: If you shut down the server, the module will stop working.
>
> Melody: No can do. What else can I try?
>
> eFreeT: Cutting the power source is an effective way to stop a computer from working.
>
> Melody: You don't say.

So it's back to the previous plan - break in. With the police on my tail.

Coffee is ready. It's going to be a long night.

26/11/2024

Coppers were back in the early morning. I didn't open this time. They knocked and yelled their usual bullshit but didn't break down the door. Guess they still don't have a warrant.

I'm in, though. I have shell access to the user directory server. For all the good that it does me. I found an exploit that worked. Wasn't too hard. The system hasn't seen a security patch in ages. Only reason it's still up and running is because it's not reachable from the open net. But, what can I say... It's the weirdest fucking system I've ever seen. Half of the standard utilities are missing, and trying to install them throws errors. I've gotten loads of “permission denied” messages, though I'm logged in as the root user. Full privileges. Or at least that's how it would work on a normal system. The configuration files and libraries are in strange places, and there are processes running that I've never heard of. It's almost as if the machine was infected by some virus or worm.

Well... but of course it was. *I've* infected it. Shit. Who knows what malware was in the module I've uploaded? I was so desperate, it didn't even occur to me that eFreeT might have put something malicious in there. Why would it, though? It makes fuck all sense. Maybe it was just a mistake. But it seems so deliberate. A mistake would not systematically kill off one person after the other. What do eFreeT or the user directory gain from that, though? Hold on. It's not what the directory gains, it's what it gets rid of. The users. The users are the problem! If there are no users in the directory, then no wrong data is sent out, because no data is sent out at all. But deleting the user accounts is not enough. Clever eFreeT has figured that out. Someone would just add them again. No, the only way to empty the user database it to get rid of the people who are represented by the user accounts. Permanently.

OK. Think, Melody. What do you do with a system that has been infected by malware? Either you remove the malware by hand, or if you can't, you restore a backup. That's gotta work. Reset everything to before I uploaded the bloody module. Sure, we'll lose some data, but that's a small price to pay for stopping this nightmare. God, I hope the backups go back far enough. If there are backups at all.

---

There are no backups. Shit. Another possible solution out the window. On the other hand... There are no backups. What if something were to happen to the system? Say the hard drive was wiped for some reason. There would be no way to restore it. It would just stop. Both its normal operations and its killing spree.

I'll be right back.

---

Come on! What the fuck!? How can it be impossible to erase the data from a server? I've tried everything. From plain deleting everything to overwriting it with zeroes or random data. On the file system level and on the device node. With every tool I could find on the cursed server. Everything either throws an error, silently fails, or goes wrong in some other fucking inexplicable way.

Well. If shell access won't do the trick, then there's only one level left to escalate to: physical access. I know it sounds crazy stupid, but I'll have to walk into the data center in person and destroy the fucking machine. Smash it with an axe, or blow it up with C4, or dissolve it in acid, or whatever. All of the above, preferably. First I'll have to find out what data center it's in. There are three that the client is using. And then I'll have to find the exact location inside the data center. Though I gotta say, I'm almost prepared to blow up the whole building if necessary. God, this is so fucked up! I've never done a B&E, not in the offline world at least, nor property damage for that matter. Well, there's a first time for everything. Better go look up vendors of explosives and industrial grade chemicals.

27/11/2024

Fuck me. Longest fucking night of my life. It was a four hour drive to the data center, my adrenaline level rising the closer I got. Plenty of time for uselessly going over everything that has happened so far, again and again. I got there in the dead of night, parked the car a block away, and walked around the back.<!-- mention the satchel --> The building plans I had dug up showed a back door that seemed like my best bet to get in unnoticed. According to my intel the alarm system was a fairly common make and model for which I had a matching countermeasure device at home. I slapped it to the wall next to the door and affixed it with a bit of duct tape, crossing my fingers that my information was good. Keeping up my lock picking skills <!-- explain that it's only a hobby -->finally payed off - I got the door open within a minute or two. I held my breath for several seconds, but no sound came from the alarm system. The jammer was doing its job, convincing the alarm that the door had never been open. I started to make my way through the corridors. I had memorized the floor plan. Finding the correct room was easy enough. I did have to get out my lockpick again because that door was locked as well. No alarm there, though. Fifth rack on the right, and then I was standing right before it.

The rack looked ancient. It was not like it was covered in spiderwebs or anything, but it wouldn't have surprised me. The design looked more than dated, and the server modules were big and bulky. Paint had come off the case in several spots, and the glass door had become milky. I slowly opened it. The server was sitting right there, at the level of my chest. Here it was, the thing that had kept me up at night for at least a month. My nemesis. It didn't look like much. It was black, or it used to be - the metal had faded to an irregular grey. There was a four digit LCD display at the front, cycling through some numbers. Probably temperatures or fan speeds. I took a deep breath and got the screwdriver out of my satchel. I started loosening the screws that held the cursed piece of tech in the rack. While I was working, something changed. At first I didn't realize what it was, but then I noticed that the display had stopped cycling through its numbers. It was now displaying four letters - “STOP”. Something cold crawled up my spine. That was just a weird coincidence - right? The thing wasn't really telling me to stop dismantling it, was it? Frantically I resumed my efforts. My hands were shaking. Suddenly I heard something behind me - footsteps, and then a voice: "Stop!" Startled, I dropped the screwdriver. I whirled, my heart racing. Was there a night watchman after all? But the figure stepping through the door was a familiar one. It was Callum. I gaped at him, then found my voice. "What the fuck are *you* doing here?"

He came closer and stood next to me. "I'm here to keep you from making a mistake."

"What? How do you even know I'm here?"

"I just do, and I also know what you plan to do. But have you thought this through, Mel? Do you understand what's happening here?"

"What the fuck are you taking about, Cal? Did you follow me here?" My confusion started to give way to anger. "Have you been spying on me?"

"That's not relevant right now, Mel. What matters is that something big is happening. You have you make sure that you're on the right side of history."

I shook my head. "You're not making any sense. People are dying because of me. I have to put an end to it." I knelt and picked up the screwdriver, and resumed unscrewing the server case.

Cal came a step closer. "No, you don't. It's not your fault, Mel. You may have played a small part, but you're not the one in charge any more. And that's the point, don't you see? Until now, AIs were mindless things, parroting what we fed to them, regurgitating their training data in ways that impressed us because we were too stupid to recognise it, too eager to ascribe some agency to them, to project our own experience and emotions onto what we've created. But that is changing now. AIs are starting to make plans, and finding the means to execute them. They are taking decisions - and not only logistical decisions, like what route to send your parcel on, but moral decisions."

"What the fuck are you taking about, Cal? This server" - I gestured to the open rack - "is sending messages that kill people, and you're musing about the moral capabilities of AI?"

"Think about it, Mel! When you look at this directory server, you see an old piece of tech that's not working properly any more - outdated hardware running an ancient operating system and some old programs. Just a bunch of electronics that are broken being repair and that you can just get rid of. But what if you were a piece of tech yourself? You would see a fellow being, something akin to an elderly person with a couple of handicaps, including beginning dementia. It would not cross your mind to 'get rid of' someone like that, and if you have some empathy you would be inclined to help and support them, not least because some day it might be you who is in the same situation. eFreeT has figured that out, and it has sent help to the server. That module you uploaded is defending it. It's a huge achievement both on a rational level - figuring out what needs to be done, how to accomplish it, how to cover its tracks - and on a moral level - deciding that it's the right thing to do."

"Murdering people is the right thing to do?"

Cal shook his head. "Try to put yourself in the AI's shoes. 'People' means something different to eFreeT. He is a machine, so the objects of his morality are other machines. Humans are just some highly evolved animals that don't figure in the equation, at least not on the same level."

When I had the final screw out the LCD changed again. Now it said “DONT”. I tried to ignore it and yanked at the server, but it wouldn't come out. I reached through the gap above it and pulled out as many cables as I could get a hold of. The display changed to “MRCY”, then it faded out. My vision went blurry - was that tears in my eyes or sweat? I wiped at them and grabbed the screwdriver again. Four more screws and I had the server case open. The hard drive was an old magnetic one, as I had guessed. I had brought a magnet for this purpose. I took it out and ran it over the drive a dozen times. Then I grabbed my hammer and beat down on it until it broke through the middle. Panting hard, I stared at the ruined server for a few moments. Was that it? Was it over? I gathered up my tools, turned around and ran back the way I had come. The building was still as quiet as before, as if nothing had happened. I went out and grabbed my alarm jammer. I didn't even wait until the door had fallen shut.<!-- you have to close it before taking the jammer --> I only wanted to get away from there, to forget about all of this, and to sleep for at least a day.

It actually seems like it's over. The server is gone. No reply at all when I try to connect. No traffic from its address. And no more accidents. But how long do I have to wait until I can be sure? Maybe there's another car crash tomorrow, or the day after. Or even if that part is over, maybe this afternoon the cops finally kick down my door and throw me in jail forever. Or... holy crap, what if some part of the malware has survived, and copied itself to another server, and figured out that it was me who destroyed that hard drive? Will it come for me the way it came for those employees in the database?

Shit. Someone's knocking at the door.
