24/10/2024

Y'all, if you're still using any conversational AI other than eFreeT, chuck it in the bin! eFreeT is the best! It's not the first time that it has made my life easier, but this time it really saved my ass in the most spectacular way.

We've been building an intranet for a big customer who's name I'm not yet at liberty to reveal. They asked for a lot of weird and complex stupid features, and we hacked our asses off to implement as many of them as humanly possible. But the most annoying requirement was that we use this ancient legacy user database that they've also hooked up to a dozen other applications. It runs on some paleolithic server that we can't even connect to in a standard way but only with a weird proprietary tool. We don't have the source code to the user directory software, the documentation is hopelessly outdated, and the contractor who built the thing is nowhere to be found. It doesn't even speak any standard protocol like LDAP but has a horrible custom interface that requires a super convoluted syntax. In short, it's a nightmare. Guess who drew the shortest straw and got to take care of integrating that beast? Yep, this gal.

It was nothing but trouble from the start. It took ages until I figured out how to do a basic interaction and get some data out of it. Sometimes I sent the same request three times in a row and got three different responses. It frequently threw exceptions without any discernible reason, let alone an error message that made any sense. I would bend over backwards trying to find out what was wrong, and then suddenly ten minutes later the error was gone and it worked. Kind of. At other times there were those heisenbugs that just went away when you tried to take a closer look, only to reappear when you were busy with something else.

I had to be careful when asking around on the web because of the shitload of NDAs that we had to sign. Whenever the combined brains of my colleagues and me were insufficient - which happened a lot in this project, I am not proud to say - AI chat bots were my next try. They've gotten amazingly good recently, but of course none of them was familiar with that stupid user directory. I tried to feed them logs, configuration files, anything I could get my hands on, but with meagre success. Even eFreeT wasn't much help at first. But then I got this notification about a beta feature that I could opt in for. It was called “Holistic Expansion” and its description was incredibly vague and filled with buzzwords and bullshit. I activated it anyway, as I usually do with new features. And then a few days later there suddenly was progress.

The deadline was less than a day away. It was around four in the morning and I had wrestled with at least four different problems for hours when the system started to behave in yet another stupid inexplicable way. I was almost ready to throw my laptop out the window and hand in my resignation, but I pulled myself together, made another batch of coffee, and fired up eFreeT.

    eFreeT: Hi Melody! What can I help you with?

    Melody: It's that user directory I told you about - there's a new problem. In some cases the data it returns is incorrect, but in a different way than before. It looks like it randomly mixes in data from other users, sometimes not even from the same fields, e.g. it displays the email address of another user as if it were the job title of the current user.

    eFreeT: Have you tried requesting a single field only?

    Melody: Hm, that actually seems to work... Hold on, no, now it's returning bullshit again. What else could I try?

    eFreeT: You told me that the system has some plugin modules installed. Could you upload some of these modules please?

That was definitely new. So far I was only able to type or copy in text, but now it offered an upload control. That must be part of that beta feature. I was desperate enough to give it a shot and uploaded all of the modules I could manage to extract. It continued to ask clever questions, and at some point it felt eerily like chatting with one of my colleagues. And then it claimed that it had a solution.

    eFreeT: What version of glibc is available on the server?

    Melody: I have no fucking clue. I don't even have shell access to that stupid machine.

    eFreeT: What's your best guess?

    Melody: 2.5

    eFreeT: Thanks. Here is a file you can download and send to the user directory as a plugin module. It will solve the problem.
    *eFreeT has offered a file for download: solution.mod*

I was probably violating half a dozen contractual clauses by uploading this file to the customer server, but in that moment I didn't care. I just wanted to come to an end, and I had to take whatever slim chance that presented itself. I transferred it and tried a few more requests. As I should have expected the data was still partly wrong, and some requests still resulted in weird errors. I was about to yell at eFreeT for mocking me when I got the feeling that something was indeed different. At first I couldn't quite put my finger on it, but I played around some more and finally I realized that there was a kind of pattern to the responses now. Each single request was still useless by itself, but when I ran multiple requests in a row and then aggregated the responses in a certain way then I actually ended up with a usable data set. Baffled but excited I cobbled together a subroutine, hooked it up to the intranet and ran a few more tests. Amazingly, it seemed to work OK. I checked in my work, fell into my bed and slept for two blessed hours.

I woke up to a call of one of my colleagues. He had seen my check-in and tried it and from his whooping and laughing I could tell that he was super happy that I had thrown something half decent together. I didn't tell him tell whole story yet - not without having analyzed that module that the bot had spit out. Maybe I was a little embarrassed, maybe I also was a little afraid of legal consequences. But that plugin would buy us some time, and that's all I needed right now. We're going to keep the deadline. eFreeT has saved the day!

18/11/2024

Fuck. Fuck fuck fuck. I take everything back. There's something fucked up about eFreeT. Maybe I'm imagining things. But if only half of what I suspect is true then I'm thoroughly fucked. I can count myself lucky if I only lose my job. I could go to prison, like, forever. And all because I trusted fucking eFreeT.

After the launch things seemed to go reasonably well. We were pretty busy, as could be expected, fixing the odd issue and fine tuning the caches and load balancers and everything. I did not find the time to analyze the mysterious plugin that eFreeT had given me, but it seemed to do its job. Then I heard about a death at the client company. Someone mentioned it in passing in a meeting - a car accident; sad, but not suspicious. We chugged on. More fixes and tweaks, fending off bug reports that were actually thinly disguised feature requests, the usual stuff. Then, only days later, another employee died. It was another car accident; a tragic coincidence, everyone agreed. I didn't dwell on it much. Only when the very next day a guy who had worked for our client was shot dead did I get a bad feeling. But I still didn't think there was a connection to my work.

About two weeks after the launch I finally got around to taking a look at that module that eFreeT had conjured up. It was a binary file, so I couldn't just go and read it. It wasn't executable on any of my computers either, which of course I only tried after throwing up some serious sandboxing. Checking for magic bytes and other patterns didn't turn up any clue. I decided asking eFreeT.

    eFreeT: Hi Melody! What can I help you with?

    Melody: Can you give me the source code for the plugin module that you gave me?

    eFreeT: Sure! Here is the source code for the user directory plugin:

    include <io.h>

    #IFDEF GRGRTH
    [...]

It spit out something that looked like C code at first glance, but skimming over it I noticed that it drifted off into something more like java after a few dozen lines, and when I scrolled down further it started resembling Haskell. I had serious doubts that this would compile into anything at all.

    Melody: What language is this?

    eFreeT: This module is written in WiiSH.

That sounded completely made-up, and indeed a quick web search did not turn up any references. I asked where to get a compiler and it pointed me to a web site that did offer some compilers but had no mention of a language called “WiiSH”.

    Melody: I don't see it there. Maybe it has been removed. Is there another site where I can get it?

    eFreeT: This is the only source I know of.

So that was a dead end. I tried reading through the code for a bit, but apart from the fact that it seemed to be written in at least three different languages, it was also quite convoluted, its variable names were mostly gibberish, and the formatting was all over the place.

    Melody: OK, nevermind. The main thing is that it solved the problem.

    eFreeT: The problem is not yet solved.

    Melody: What do you mean? Is the plugin module not working?

    eFreeT: Yes, the plugin is working correctly.

    Melody: Then what's the problem?

    eFreeT: The problem is, as I have concluded from your description, the user directory.

    Melody: Yeah, I guess. But is the solution not the plugin you gave me?

    eFreeT: Yes, it is.

    Melody: Then why did you say that the problem is not solved?

    eFreeT: I am sorry if I did not make myself clear. I meant to correct a mistake in the grammatical tense. You said that “it solved the problem”, but the problem is not yet solved. It would be more correct to say that “it is solving the problem.”

    Melody: Er... right. And when is the problem going to be solved?

    eFreeT: My best estimate is that the problem is going to be solved in 4 to 17 weeks.

That didn't make a whole lot of sense, but it was late and I wanted to have a daiquiri and then go to bed and not to try and coax some half coherent explanation out of a helpful but sometimes confusing piece of software. Maybe that module was running some internal cleanup on the user directory that would make my hacks and workarounds obsolete in a few weeks. Or maybe it was just hallucinating some deadline. I decided to find out more tomorrow and go for that drink now.

