# Adium-NG Preview

## What is this?
Adium-NG aims to be a fork of Adium <https://adium.im> with different goals. Adium original developers did great work in creating this nice application but today it suffers from too many problems, mostly stale development and outdated libraries. It also tries to do many things at the same time which I don't agree with.

Adium-NG aims to implement what I think a reasonable desktop secure instant messenger application should be. This is my main goal, a reasonable secure messenger that is more or less to maintain or at least to keep up to date all its external code and remove all binary dependencies that current Adium build has.
Because this is my thing it means it will go on the direction I want. If you don't like, bad luck, this is not a democracy. If it fits your needs then great. I am not in the mood to waste time discussing what it should be or not (ideas that make sense are more than welcome!). For example, Adium still ships with all logging, including OTR messages, enabled by default. This is beyond stupid and the argumentation to keep it this way is even worse.

The motto here is, do something, try do it right. Reduce the attack surface as much as possible.

## What are my changes?
Right now I already stripped the original Adium code of all messenger networks except Jabber/Google Talk. I don't care about anything else. Jabber, OTR, let's keep it simple.
I also stripped a ton of other stuff I am not interested in, such as Sparkle to check for updates (if you want updates check them yourself, no need for another remote server to care about), Growl/Notifications (notifications are a stupid way to leak information to other apps), Apple Scripting support (what the hell is this for?), Xtras (not fully yet but going to be - xtras are just backdoors), auto links generation (a secure messenger shouldn't make it easier to fuck up by clicking on a link), integration with AddressBook (one less thing to configure in the sandbox), write right to left (sorry, English only), localization (sorry, this only speaks English), and so on. I guess that by now you got the idea, all the fat must go out. Less is more, a minimal client with no fancy shit, using the nice Adium GUI.

All the original linked binary frameworks are gone. All code is compiled now. Build scripts are updated and fixed for some stuff. All the linked libraries are latest versions. Also no more downloads from the Internet, all the necessary packages are stored in the repo. The build system still has some dependencies on brew (automake/autoconf due to libpurple, to get rid of soon enough), but the goal is to make dependent only of Xcode. Install Xcode, clone repo, run build scripts, wait, enjoy. That's the goal.

## Why stick with Adium and not other client?
Because I like Adium GUI. And I abandoned this same project in the past and now I just got a click to give it a try.

## Why not Signal desktop?
Because I don't want to use it. It's great for the mobile but I like diversification. Nature diversifies and spreads risk, and I wasted a bunch of years of my life studying Economics and listening to the diversification is good mantra.

## But but C is insecure!
While I am not an elite C developer (hell I'm not even a developer!) I am not afraid of it. Honestly I hate this hipster shit that C is the root of all computer evil (even if it was it gives us nice jobs so why the hell hate it?). I love C (but I hate Objective-C!) and I like a challenge.

## Is this three letter agencies proof?
Nah, they have more resources than everyone else so that's not even the target. Definitely not trying to be a freedom fighter hero. Just want something for me and friends that is better than the original Adium and reasonably secure, and have some fun.

It doesn't aim at anonymity, only message secrecy as good as OTR and as secure as the endpoint (this is the real problem as latest leaks have shown, endpoint compromise is the way to go [well no real news there anyway]). But honestly we aren't all special snowflakes that are lucky enough to get infected by a CIA EFI level rootkit. If you are that snowflake there is no hope for you anyway. 

Trusting your life to a computer is a very dumb thing to do. Don't use a computer if you are preparing the next revolution!

## When can you get it?
I am still making a lot of changes, the current version works. I'll probably publish a binary version soon enough. Yes, binary. My name is on it, and I like my reputation so there's really no incentive for backdoors. If you already trust Adium why not me? :P

Source will be published when I am happy with its status. 

## Can you contribute?
Most definitely when the source is out. As long your contributions fit my goals you are more than welcome. Fat to remove, big fixes, code audits, bug reports are very helpful.

If you want to do hipster open source shit and just bitch about this and that and why I removed this and that and not supporting this and that, I have bad news for you: this is a 100% dictatorship project. If you don't like it, fork it and get the fuck out :P

## Thanks
* Original Adium developers for all their effort
* Apple for the code signing certificate

## Special Notes
* Adium-NG-29-03-2017-Release-signed-sandboxed.dmg

 This version is finally sandboxed. The sandbox is configured to run from /Applications, so if you want to test this you need to rename old Adium.app to something else. File transfers will not work since sandbox is already pretty tight. 

Sandbox profile in Resources/adium_sandbox.sb. Any sandbox errors reports are welcome. 

When you start AdiumNG it will try to create a folder ~/adium_sandboxtest to see if the sandbox is working. So error message in logs about this is expected. If it fails an alert will show up and app will not run.

BUG: when it asks for keychain access if you select always allow it will not work. Sandbox profile is missing some items for this. Will fix soon.

## TODO List
* Upgrade libotr to 4.x branch. Adium 1.6 already did this work so it's a matter of copying the necessary code
* Get rid of brew requirement for building
* Sandbox profile
* Get rid of file transfer support (less is more, file transfers have no place here)
* Get rid of libpurple or audit that shit (one of the reasons to support a single protocol)
* Remove more fat still there
* Some other stuff I can't remember right now :P

## Hashes
SHA256(Adium-NG-28-03-2017-Release-Debug.dmg)= 4787008bb3e58e731e8eef3e64818ba9c8d8c85e20ab365ca038d51d079c256f
SHA256(Adium-NG-29-03-2017-Release-signed-sandboxed.dmg)= 2dfdedee9ad7d24e8f5d86496a0ab4378ab7fb42f7c780658f17ccc9cb7e2f6a
