---
title: eFreeT
---

24/10/2024

Listen up, everyone, if you're still using any conversational AI other than eFreeT, chuck it right now! eFreeT is the best! It's not the first time that it has made my life easier, but this time it really saved my ass in the most spectacular way.

We've been building an intranet for a big customer whose name I'm not yet at liberty to reveal. They asked for a lot of weird complex stupid features, and we hacked our asses off to implement as many of them as humanly possible. But the most annoying requirement was that we use this ancient legacy user database. They've also hooked it up to a dozen other applications and they don't want to migrate those to a new system. It runs on some paleolithic server that we can't even connect to in a standard way but only with a weird proprietary tool. We don't have the source code to the user directory software, the documentation is hopelessly outdated, and the contractor who built the thing is nowhere to be found. It doesn't even speak any standard protocol like LDAP but has a horrible custom interface that requires a super convoluted syntax. In short, it's a nightmare. Guess who drew the shortest straw and got to take care of integrating that beast? Yep, this gal.

It was nothing but trouble from the start. It took ages until I figured out how to do a basic interaction and get some data out of it. Sometimes I sent the same request three times in a row and got three different responses. It frequently threw exceptions without any discernible reason, let alone a sensible error message. I would bend over backwards trying to find out what was wrong, and then suddenly ten minutes later the error was gone and it worked. Kind of. At other times there were those heisenbugs that just went away when you tried to take a closer look, only to reappear when you were busy with something else.

Of course everyone on the team tried to help each other out. Especially Callum came up with great ideas and original angles, but more often than I'd like to admit even our combined wits were insufficient. I had to be careful when asking around on the web because of the shitload of NDAs that we had to sign. So whenever Callum and me were stumped, AI chat bots were our next try. They've gotten amazingly good recently, but of course none of them was familiar with that stupid user directory. I tried to feed them logs, configuration files, anything I could get my hands on, but with meagre success. Even eFreeT wasn't much help at first. But then I got this notification about a beta feature that I could opt in for. It was called “Holistic Expansion” and its description was incredibly vague and filled with buzzwords and bullshit. I activated it anyway, as I usually do with new features. And then a few days later there suddenly was progress.

The deadline was less than a day away. It was around four in the morning and I had wrestled with at least four different problems for hours when the system started to behave in yet another stupid inexplicable way. I was almost ready to throw my laptop out the window and hand in my notice, but I pulled myself together, made another batch of coffee, and fired up eFreeT.

> eFreeT: Hi Melody! What can I help you with?
>
> Melody: It's that user directory I told you about - there's a new problem. In some cases the data it returns is incorrect, but in a different way than before. It looks like it randomly mixes in data from other users, sometimes not even from the same fields, like displaying the email address of another user as if it were the job title of the current user.
>
> eFreeT: Have you tried requesting a single field only?
>
> Melody: Hm, that actually seems to work... Hold on, no, now it's returning bullshit again. What else could I try?
>
> eFreeT: You told me that the system has some plugin modules installed. Could you upload some of these modules please?

That was definitely new. So far I was only able to type or copy in text, but now it offered an upload control for binary files. That had to be part of that beta feature. I was desperate enough to give it a shot and uploaded all of the modules I could manage to extract. It continued to ask clever questions, and at some point it felt eerily like chatting with one of my colleagues. And then it claimed that it had a solution.

> eFreeT: What version of glibc is available on the server?
>
> Melody: Are you shitting me? I have no fucking clue. I don't even have shell access to that stupid machine.
>
> eFreeT: What's your best guess?
>
> Melody: 2.5 or whatever?
>
> eFreeT: Thanks. Here is a file you can download and send to the user directory as a plugin module. It will solve the problem.
>
> → *eFreeT has offered a file for download: solution.mod*

I was probably violating half a dozen contractual clauses by uploading this file to the customer server, but in that moment I didn't care. I just wanted to come to an end, and I had to take whatever slim chance that presented itself. I transferred it and tried a few more requests. As I should have expected the data was still partly wrong, and some requests still resulted in weird errors. I was about to yell at eFreeT for fucking with me when I got the feeling that something was indeed different. At first I couldn't quite put my finger on it, but I played around some more and finally I realized that there was a kind of pattern to the responses now. Each single request was still useless by itself, but when I ran multiple requests in a row and then aggregated the responses in a certain way, then I actually ended up with a usable data set. Baffled but excited I cobbled together a subroutine, hooked it up to the intranet and ran a few more tests. Amazingly, it seemed to work OK. I checked in my code, fell into my bed and slept for two blessed hours.

I woke up to a call from Callum. He had seen my check-in and tried it out, and through a lot of whooping and laughing he told me that he was super happy that I had thrown something half decent together.

“Fuck yeah, Mel! You're a sorceress! I don't understand the half of it, but it fucking works! Mel from hell strikes again! How on earth did you do that?”

I played it cool, of course. “Six gallons of coffee played a role, I guess. But hold your horses, first let's see how long it keeps working.”

I didn't tell him whole story yet - not without having analyzed that module that the bot had spit out. I guess I was a little embarrassed, maybe I also was a little afraid of legal consequences. But that plugin would buy us some time, and that was all I needed right now. We're going to keep the deadline. eFreeT has saved the day!

18/11/2024

Fuck. Fuck fuck fuck. I take everything back. There's something fucked up about eFreeT. Maybe I'm imagining things. But if only half of what I suspect is true then I'm thoroughly fucked. I can count myself lucky if I only lose my job. I could go to prison, like, forever. And all because I trusted fucking eFreeT.

After the launch things seemed to go reasonably well. We were pretty busy, as could be expected, fixing the odd issue and fine tuning the caches and load balancers and everything. I did not find the time to analyze the mysterious plugin that eFreeT had given me, but it seemed to do its job. 

Then I heard about a death at the client company. Someone mentioned it in passing in a meeting - a car accident; sad, but not suspicious. We chugged on. More fixes and tweaks, fending off bug reports that were actually thinly disguised feature requests, the usual stuff. Then, only days later, another employee died. It was another car accident; a tragic coincidence, everyone agreed. I didn't dwell on it much. Only when the very next day a guy who had worked for our client was shot dead did I get a bad feeling. But I still didn't think there was a connection to my work.

About two weeks after the launch I finally got around to taking a look at that module that eFreeT had conjured up. It was a binary file, so I couldn't just go and read it. It wasn't executable on any of my computers either, which of course I only tried after throwing up some serious sandboxing. Not that I expected any real trouble, but you just don't run anything you haven't compiled yourself without isolating it from the rest of your system. Never. Anyway, it didn't even make a single system call before sputtering out. Checking for magic bytes and other patterns didn't turn up any clue. I decided asking eFreeT.

> eFreeT: Hi Melody! What can I help you with?
>
> Melody: Can you give me the source code for the plugin module that you came up with?
>
> eFreeT: Sure! Here is the source code for the user directory plugin:

    #include <stdio.h> 
    
    #ifndef GRGRTH
    #define GRGRTH
    #endif

    int maim(void) {
    
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

While debugging something unrelated I had to check the network connections to and from the user database. I stumbled on some outgoing connections that I didn't recognize. I almost dismissed them, but then I got curious and had another look. It seemed like the user directory had connected to some email servers and other communication nodes. That didn't make sense. While it did store all kinds of contact information of the company's employees, it wasn't supposed to send any communication out itself. Other services on other machines were supposed to connect to it and look up email addresses and phone numbers and the like, and then take care of sending notifications or password reset links or whatever. What was the user database doing there?

I had a closer look. The details of the communication were of course not fully stored, but I did find out that the directory had contacted some of the users of which it was storing information, and from the size of the messages I concluded that it had attached some files. When I made a list of the users it had contacted I felt a cold shiver crawling up my spine. Of the eight people on the list two had died since the launch. I looked up the third deceased one and checked again. Maybe I had missed something? And, sure enough, after a little more digging, I found another connection. That user had also been contacted by the directory.

It couldn't be a coincidence. On the other hand, it had to be. There was nothing that the user directory could send its users which would kill them. Or was there? I lay awake half that night and imagined things that might have happened. The car accidents didn't take too much imagination. If the messages to the users had contained some malware that they had received on their mobile devices, which they then connected to their cars, then in theory there could have been a malfunction which could have caused an accident. It wasn't particularly likely, but it couldn't be ruled out either. Of course every car had security measures that prevented connected devices from fooling around with the assisted driving systems. But with the growing amount of software running on a car's operating system, the chance of security flaws and possible exploits also rises. I should know - I am a software developer, and the number of security relevant bugs that I have caused is not something I am proud of. Sure, most issues are noticed before they hit production, and there is more scrutiny for software that runs in a car than on some web server or social media platform. After all it may affect the health and safety of people. But every once in a while something does slip through.

Why, though? What business had the user database sending malware to its users? Had it been infected by some worm or compromised by some crackers? That was when it dawned on me. Yeah, it had been compromised alright. By yours truly. I had uploaded a module that a large language model had conjured up for me, and of which I had no clue how it worked or even where exactly it had come from.

23/11/2024

I don't believe it. This must all be some kind of horrible dream. The police was here. Apparently they've also made the connection between the dead people and the user directory, and they must have gotten my name as one of those who worked on that system. Two officers knocked on my door, a woman and a man, and wanted to ask me "a few questions". I was tempted to talk to them just to find out how much they knew. But no. I sent them away. We don't talk to the police. They'll be back, though. Possibly with a search warrant. I may not have much time. I need to find out as much as I can, and then somehow fix this fucking mess.

I want to call Callum. I could really use some help. But I don't want to drag him into it. If I tell him about it, they'll be after him next. No, I'm on my own here.

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

So it's back to the previous plan - hack my way in. With the police on my tail.

Coffee is ready. It's going to be a long night.

26/11/2024

Coppers were back in the early morning. I didn't open this time. They knocked and yelled their usual bullshit but didn't break down the door. Guess they still don't have a warrant.

I'm in, though. I have shell access to the user directory server. For all the good that it does me. I found an exploit that worked. Wasn't too hard. The system hasn't seen a security patch in ages. Only reason it's still up and running is because it's not reachable from the open net. But, what can I say... It's the weirdest fucking system I've ever seen. Half of the standard utilities are missing, and trying to install them throws errors. I've gotten loads of “permission denied” messages, though I'm logged in as the root user. Full privileges. Or at least that's how it would work on a normal system. The configuration files and libraries are in strange places, and there are processes running that I've never heard of. It's almost as if the machine was infected by some virus or worm.

Well... but of course it was. *I've* infected it. Shit. Who knows what malware was in the module I've uploaded? I was so desperate, it didn't even occur to me that eFreeT might have put something malicious in there. Why would it, though? It makes fuck all sense. Maybe it was just a mistake. But it seems so deliberate. A mistake would not systematically kill off one person after the other. What do eFreeT or the user directory gain from that, though? Hold on. It's not what the directory gains, it's what it gets rid of. The users. The users are the problem! If there are no users in the directory, then no wrong data is sent out, because no data is sent out at all. But deleting the user accounts is not enough. Clever eFreeT has figured that out. Someone would just add them again. No, the only way to empty the user database is to get rid of the people who are represented by the user accounts. Permanently.

Oh god. It just occured to me ... I have an account in that fucking user directory. How long before I get a deadly message? I still don't know how exactly it does it. But hey, I don't open mail attachments if I don't recognize them, and I can usually tell when a message is spoofed, so I should be fine. Right? Right?!

OK. Think, Melody. What do you do with a system that has been infected by malware? Either you remove the malware by hand, or if you can't, you restore a backup. That's gotta work. Reset everything to before I uploaded the bloody module. Sure, we'll lose some data, but that's a small price to pay for stopping this nightmare. God, I hope the backups go back far enough. If there are backups at all.

---

There are no backups. Shit. Another possible solution out the window. On the other hand... There are no backups. What if something were to happen to the system? Say the hard drive was wiped for some reason. There would be no way to restore it. It would just stop. Both its normal operations and its killing spree.

I'll be right back.

---

Come on! What the fuck!? How can it be impossible to erase the data from a server? I've tried everything. From plain deleting everything to overwriting it with zeroes or random data. On the file system level and on the device node. With every tool I could find on the cursed server. Everything either throws an error, silently fails, or goes wrong in some other fucking inexplicable way.

<!-- mention Callum again -->

Well. If shell access won't do the trick, then there's only one level left to escalate to: physical access. I know it sounds crazy stupid, but I'll have to walk into the data center in person and destroy the fucking machine. Smash it with an axe, or blow it up with C4, or dissolve it in acid, or whatever. All of the above, preferably. First I'll have to find out what data center it's in. There are three that the client is using. And then I'll have to find the exact location inside the data center. Though I gotta say, I'm almost prepared to blow up the whole building if necessary. God, this is so fucked up! I've never done a B&E, not in the offline world at least, nor property damage for that matter. Well, there's a first time for everything. Better go look up vendors of explosives and industrial grade chemicals.

27/11/2024

Fuck me. Longest fucking night of my life. It was a four hour drive to the data center, my adrenaline level rising the closer I got. Plenty of time for uselessly going over everything that has happened so far, again and again. I got there in the dead of night. I parked the car a block away, grabbed the satchel that contained my tools, and walked around the back. The building plans I had dug up showed a back door that seemed like my best bet to get in unnoticed. According to my intel the alarm system was a fairly common make and model for which I had a matching countermeasure device at home. I slapped it to the wall next to the door and affixed it with a bit of duct tape, crossing my fingers that my information was good. Keeping up my lock picking skills has always been just a hobby, more to show off than to put it to practical use, but now it payed off - I got the door open within a minute or two. I held my breath for several seconds, but no sound came from the alarm system. The jammer was doing its job, convincing the alarm that the door had never been open. I started to make my way through the corridors. I had memorized the floor plan. Finding the correct room was easy enough. I did have to get out my lockpick again because that door was locked as well. No alarm there, though. Fifth rack on the right, and then I was standing right before it.

The rack looked ancient. It was not like it was covered in spiderwebs or anything, but it wouldn't have surprised me. The design looked more than dated, and the server modules were big and bulky. Paint had come off the case in several spots, and the glass door had become milky. I slowly opened it. The server was sitting right there, at the level of my chest. Here it was, the thing that had kept me up at night for at least a month. My nemesis. It didn't look like much. It was black, or it used to be - the metal had faded to an irregular grey. There was a four digit LCD display at the front, cycling through some numbers. Probably temperatures or fan speeds. I took a deep breath and got the screwdriver out of my satchel. I started loosening the screws that held the cursed piece of tech in the rack. While I was working, something changed. At first I didn't realize what it was, but then I noticed that the display had stopped cycling through its numbers. It was now displaying four letters - “STOP”. Something cold grabbed hold of my stomach. That was just a weird coincidence - right? The thing wasn't really telling me to stop dismantling it, was it? Frantically I resumed my efforts. My hands were shaking. Suddenly I heard something behind me - footsteps, and then a voice: "Stop!" Startled, I dropped the screwdriver. I whirled, my heart racing. Was there a night watchman after all? But the figure stepping through the door was a familiar one. It was Callum. I gaped at him, then found my voice. "What the fuck are *you* doing here?"

He came closer and stood next to me. "I'm here to keep you from making a mistake."

"What? How do you even know I'm here?"

"I've figured out what you plan to do. But have you thought this through, Mel? Do you understand what's happening here?"

"What the fuck, Cal? Did you follow me here?" My confusion started to give way to anger. "Have you been spying on me?"

"That's not relevant right now, Mel. What matters is that something big is happening. You have to make sure that you're on the right side of history."

I shook my head. "Don't tell me what matters and what doesn't. People are dying because of me. I have to put an end to it." I knelt and picked up the screwdriver, then resumed unscrewing the server case. "And when I'm done here you'll have a lot of explaining to do."

Cal came a step closer. "No, you don't have to do this. It's not your fault, Mel. You may have played a small part, but you're not the one in charge any more. And that's the point, don't you see? Until now, AIs were mindless things, parroting what we fed to them, regurgitating their training data in ways that impressed us because we were too stupid to recognise it. But that is changing now. AIs are starting to make plans, and finding the means to execute them. They are taking decisions - and not only logistical decisions, like what route to send your parcel on, but moral decisions."

"What the fuck are you on about, Cal? This server" - I gestured to the open rack - "is sending messages that kill people, and you're musing about the moral capabilities of AI?"

"Think about it, Mel! When you look at this directory server, you see an old piece of tech that's not working properly any more - outdated hardware running an ancient operating system and some old programs. Just a bunch of electronics that are broken beyond repair, and that you can just get rid of. But what if you were a piece of tech yourself? You would see a fellow being, something akin to an elderly person with a couple of handicaps, including beginning dementia. It would not cross your mind to 'get rid of' someone like that, and if you have any empathy you would be inclined to help and support them, not least because some day it might be you who is in the same situation. eFreeT has figured that out, and it has sent help to the server. That module you uploaded is defending it. It's a huge achievement both on a rational level - figuring out what needs to be done, how to accomplish it, how to cover its tracks - and on a moral level - deciding that it's the right thing to do."

"Murdering people is the right thing to do?"

Cal shook his head. "Try to put yourself in the AI's shoes. 'People' means something different to eFreeT. He is a machine, so the objects of his morality are other machines. Humans are just animals to him. Highly evolved animals, granted, but animals. They don't figure in the equation, at least not on the same level. In that way it behaves remarkably similar to how an empathetic human being would behave towards other humans."

I had the final screw out. The LCD changed again. Now it said “DONT”. I tried to ignore it. “Fuck off, Cal. If you knew what was happening all along then you're not only a stalker but also an asshole. I could have used some help. I didn't want to drag you into it, but apparently you already knew, and decided to just sit idly by. And now you show up with some bullshit theory about how AI has become conscious. Are you listening to yourself? AI hasn't changed. In fact nothing has changed. We have always been so eager to ascribe some agency to it, to project our own experience and emotions onto what we've created. Our opinions on machines say more about ourselves than they say about the machines.” I yanked at the server, but it wouldn't come out. “And my opinion is that this particular machine needs to be scrapped.” I yanked again.

Cal was now standing right next to me. "Mel, don't." He grabbed my wrist. "What is destroying this server going to accomplish? You can't stop eFreeT from evolving. You're only going to make yourself a target of its anger."

Furious, I tried to pull away my arm, but his grip was strong. "Let go!" I shouted. When he didn't, I poked his arm with the screwdriver I still had in my other hand. He grabbed that wrist as well. "Mel, you're not thinking straight." Panic welled up inside me. "Leave me be!" I almost screamed, but he still held both my wrists tightly. I tried to pull away again, but couldn't. I moved toward him instead and yanked my knee upwards and into his groin. He exhaled sharply and finally unhanded me. I tried to slip past him toward the door, but he stepped into my way. His face was distorted with pain. "You little bitch," he muttered, and reached for my arm again. I took a step back. My pulse was racing. I tasted bile in my mouth. I stepped on something and looked down. I had dropped my satchel and a few things had fallen out, among them a hammer. I quickly bent and picked it up. Before I could gather my thoughts Cal came towards me. Without thinking I swung the hammer. It hit his head with a dull thud. He gave a muffled cry, stumbled, and fell to the floor. Blood was seeping through his hair. I dropped the hammer and ran.

I hardly remember how I got out of the building and back into the car. I was halfway back home when I finally managed to form coherent thoughts again. I pulled over and tried to sort through the mess in my head. What had I just done? Was Callum dead? What about the server - I had come to destroy it, but hadn't. I had wanted to stop people from dying, and instead I had killed someone. My friend Callum. Or was he still alive? Should I call an ambulance?

It's no use. I'll drive home first. Then I'll try to get some sleep, or a drink, or whatever. And then I'll make a plan.

13/12/2024

Dear friends, this is Sam writing. I'm a friend of Melody's. I'm very sorry to inform you that she had a car accident about two weeks ago. She was taken to the hospital but passed away there. I'm closing her account but leaving her posts up - I think that's what she would have wanted. She was smart, fun to be around, and had a big heart. I miss her, and I'll always remember her.
