# [fit] The __economics__ of
# [fit] package management

^ I’m going to tell you a story about who owns the JavaScript language commons, how we got here, and why we need to change it. It’s a story about money as much as it is about Javascript— money and ownership and control.

---

# [fit] C J Silverio
# [fit] __@ceejbot__

^ I'm going to tell you the version of the story I know how to tell. I'm one human with imperfect knowledge and a point of view, so the story is not the only story anybody could tell about it, not by a long way. But I can tell you a good version of one slice of this story, because I was part of it. I was at its heart, because until last year I was CTO of npm Inc, the company that runs the Javascript package registry. This gives me an expertise on the topic that few people in the world have. It also comes along with a point of view, which I invite you to keep in mind as you listen to this story.

---

# [fit] __you__ are in this story

^ _You_ are part of this story about Javascript package management. I bet you didn’t know that. By the time I'm done with this story, you'll know why you're part of it, and why that matters.

---

# [fit] a story about
# [fit] __money__

^ This is a story about money, and people who have money, and how the people who make money from open source software are mostly not the people who write it. It's a story of an accidental decision that you made without knowing about it, and one that I made consciously, and how that decision worked out today. It’s a story about ownership, control, and their consequences.

---

# [fit] a story about
# [fit] __power__

^ It’s also a story about power—who has it, how much of it you have, and what we can do with it.

^ You ready? Here we go.

---

# [fit] remember __Yahoo__?
# [fit] __ypm__ was its package manager

^ Our story starts with the late Yahoo back in its glory days, the mid-2000s. Yahoo was the heart of a lot of Javascript activity back then. It employed a lot of Javascript thought leaders, like Douglas Crockford, and it was pushing the state of the art forward. It might not have had a good business plan, but it had a good tech stack.

^ One thing Yahoo had in its tech stack was a package manager, called ypm, that apparently did some neat things.

---

# [fit] JSConfEU __2009__
# [fit] __node.js__ announced

^ At the same time Javascript was starting to be very interesting as a programming language, thanks to jquery and modern browsers adhering to a spec. Server-side Javascript was a hot topic, and this very conference was part of the server-side javascript action. It was here, in 2009, at JSConfEU, where Ryan Dahl announced node.js. Node turned out to be the javascript platform we wanted.

---

# [fit] early node had
# [fit] package managers __plural__

^ The early node community swept up interesting people who enjoyed the bleeding edge and the possibilities of a brand-new ecosystem where nobody had done much invention yet. Several of the people involved in early node figured out early on that package management for node would be very useful, and started writing package managers. Yes, more than one-- there were several competitors.

^ One of these people was a Yahoo employee who was extra-into node. He quit his job so he could write something inspired by the Yahoo package manager, but open source and for node.js. This particular programmer was clever in a couple of useful ways. For one, he got deeply involved in the node project, and this let him work on the implementation of the CommonJS module spec in node, and make his own installer work right. And he did things to beat other package managers, like give projects pull requests to support his package manager instead of the others.

---

# [fit] __one__ got official status

^ This package manager was good enough and supported inside node well enough that it won. The node package manager, or `npm`, started being packaged with node instead of living as a separate third-party thing that you downloaded right after you downloaded node. That official status granted by the node project continues to today.

---

# [fit] Joyent __bought__ node

^ Somewhere around this time, Joyent bought node from Ryan Dahl for a paltry amount of money. You’ll notice that we’re already in interesting economic territory. The man who invented node.js, the tool used by millions of people daily to develop Javascript, made a few tens of thousands of dollars from it. Whoever’s making money from node today, it’s not its inventor. He did at least make a living from it, because Joyent also hired him.

---

# [fit] Joyent did __not__ buy
# [fit] node's package manager

^ The programmer who wrote npm was also hired by Joyent to work on node but-- important plot point-- he retained ownership of the the npmjs.org domain name, the npm source code, and any inventions in it as his own intellectual property. He didn’t turn it all over to Joyent the way the node source had been turned over to Joyent.

---

# [fit] open-__source__ doesn't mean
# [fit] open __ownership__ or __control__

^ This decision matters later, so take note. The fact that you can read the source for part of something doesn't mean you have any control over it.

---

# [fit] node grows through __2013__

^ In 2012 Dahl left the node project, and npm's owner stepped up to lead it in his stead. Right about here is where you all started trickling onto the scene, or some of you anyway. You're Javascript programmers. You like writing Javascript. If you can write a tool in Javascript, you will! So you started writing Javascript with node and you liked it. Meanwhile people like me figured out that node was handy for writing I/O multiplexing services. As 2013 went on, more people joined us on this fun Javascript train, and node got pretty popular. And that meant npm got popular too.

^ Great, right? Well.


---

# [fit] success is a __catastrophe__
# [fit] you need to survive

^ Success for the open-source version of npm was a catastrophe.

---

# [fit] the package __registry__
# [fit] is __centralized__

^ The thing about npm is that it's not just a cli tool that grabs code and slams it onto your hard drive into node_modules. In fact, the cli is probably the least important part of the npm machinery, despite how frequently you interact with it. npm is most importantly a centralized package *registry* and *repository*. Right from the beginning, the registry was there, running inside a CouchDB database, on the same domain it's on today. A "registry" is a list of a whole lot of Javascript packages, their names, their authors, their many versions. This registry made node's packages *easy to find*. The repository part stores all those packages in a centralized spot, which made installing them *fast and reliable*.

^ There's a lot to unpack here, but I think it's worth a moment of our time.

---

# [fit] centralization has __advantages__

^ The key here is _centralization_. The npm registry is _centralized_. Centralization has some usability wins— you need to go to only one place to look for something. That one place can enforce some rules about the things you’re looking for— they all look the same, provide the same kinds of information, and maybe even don’t vanish on a whim when the person who made them gets bored.

^ Centralization's advantages matter for users. I've been doing a lot of Go programming recently, and it's very strange to try to find Go packages, because they're everywhere, and the only way to find them is to Google for them, or look at old-fashioned text lists maintained by hand— you know, Yahoo’s original thing. And when I install Go packages, I install from Github repos that could just go away on me. I have expectations that come from using npm for 8 years or so. The absence of a central registry for Go helps me appreciate what node's package registry gave me.

---

# [fit] centralization has been the __trend__

^ Centralization has been a trend for the Internet. Blogs, for example, were once something people hosted on their own. It's moved to centralized hosting platforms that stick around for a while, like MySpace, Posterous, and LiveJournal. Okay, like Tumblr and Medium. Social media centralized itself on Twitter and Facebook. Open source has centralized on Github.

^ So npm is a centralized registry for all the node packages there are, and this is great, except that in 2013, as node started taking off, it started not to be so great. Why?

---

# [fit] centralization of __costs__

^ The downside of centralization is that _costs_ are centralized too. The downside of npm's registry is that all that use centered on a single database with an app embedded in it.

---

# [fit] servers cost __money__
# [fit] who __pays__ for them?

^ Servers cost money. Where was the money coming from?

---

# [fit] __donations__ work when you're small

^ For years, node’s package manager ran on donated hosting. It was written with help from some of the people involved with implementing CouchDB, so CouchDB was its database, and it freeloaded on CouchDB hosting services. It was, for a long time, treated as an advertisement for CouchDB and the services offered by IrisCouch. IrisCouch was bought by NodeJitsu and they continued to host npm's registry as a cheap ad for their CouchDB and node hosting services.

---

# [fit] success is __expensive__
# [fit] \(for centralized services)

^ But as 2013 went on, and you all started using node, the node package registry started getting some serious use, and it needed heftier servers. It stopped being a cheap ad. Various lazy shortcuts taken in implementing the registry caused pain once the registry saw real use. In October 2013, the registry was down more than it was up.

---

# [fit] npm needed __money__

^ npm needed better servers. npm needed a maintainer who didn't mostly ignore it for his day job. npm needed money.

---

# [fit] this is not a novel __problem__

^ This is not an unusual problem for language ecosystems to face. RubyGems costs money to run, too. Perl solved its problem long ago with a network of CPAN mirrors.

---

# [fit] __founding a company__
# [fit] was a novel choice

^ npm's sole owner decided to try something other language package managers hadn't tried: he decided to turn his software into a company. This was possible because he'd retained ownership of npm, even while he was running the node project.

^ So he quit Joyent, founded a company-- npm, Inc.-- and took seed funding from a VC firm.

---

# [fit] the __node project__ decided this was fine

^ The node project made a decision to allow this, and to continue to give npm Inc special privileges as software packaged along with node. I don't know if there was internal controversy about this, because I wasn't part of it. The node project was entering its moribund period at the end of 2013, so it's possible the decision was made through inaction. Anyway, the node project has continued to decide to give a privately-owned company special privileges by bundling its product. They're fine with it.

---

# [fit] __you__ decided this was fine

^ You made the decision to allow this too. You made a critical decision right here, you and the entire rest of the Javascript community. You all voted with your feet, and kept using npm's registry.

^ But Ceej, I hear you say, we weren't using npm then! We weren't around! Yes! Most of you weren't! You inherited this decision. You probably never realized it *was* a decision. npm exists out there, a fact of Javascript life that you never questioned. You might not have been aware or even cared that it was a company at all.

---

# [fit] __not everybody__ thought it was fine

^ At the time, it was a controversial decision. Nodejitsu, which had been hosting npm free of charge, wasn't happy about this. They had been up to their own fix with a `#scalenpm` campaign, which ended up raising money for it at the same time npm's owner was raising VC money. There were legal maneuverings, most of which I know little about. I do know that npm exited Nodejitsu hosting very quickly and messily because the two companies were fighting and it involved lawyers. And later on, npm exited Joyent’s hosting very quickly because those two companies were also fighting.

---

# [fit] __money__ changes everything

^ When money is at stake, relationships can dissolve. Friendships made when it's all just open source fun can end under the strain of competing for money.

---

# [fit] __I__ decided this was fine

^ At this moment in time, I made a decision: I also decided to let Javascript's language commons be owned by VCs. I didn’t frame it that way to myself, though. The decision I told myself I was making was the decision to contribute what I could toward making node successful. I really liked programming in node, and npm was the first place I’d ever participated in open source development.

---

# [fit] I was employee __number two__

^ So our story has taken us to 2014. npm Inc is a company; it has VC money; it starts hiring people. The first hire was Raquel Vélez, somebody you've heard speak at this very conference. The second hire was me. I was thrilled to be able to make it go better. And I believed the story told by npm’s IP owner that we would make npm Inc self-sustaining and the servers would hum along happily dispensing packages to the masses.

---

# [fit] those __large numbers__
# [fit] sure are large

^ I ended up leading npm's engineering team, and well, you know this part of the story. We did in fact scale npm rather ludicrously. We scaled it so well that node exploded. You all started using node to build everything you do in Javascript, and npm became an unquestioned part of every Javascript programmer's workflow. You all reinvented web development in ways you couldn't do before npm was there. Great success! It was the highlight of an excellent career, and I felt pretty great about it.

^ Let’s pause here for a moment, at the successful zenith of the node package manager.

---

# [fit] let's talk about __money__

^ Let’s talk about money.
^ Why isn’t Ryan Dahl living on a tropical island?
^ Why isn't James Halliday retired on his tropical island?
^ Why isn’t Dominic Tarr living on a yacht instead of a sailboat?
^ Why does Doug Wilson have a day job?

---

# [fit] open source generates
# [fit] a lot of __value__

^ Do you know those names? They're the authors of software you have on your laptops right now, in software that is the beating heart of a thousand open-source programs you use every day. And not just you-- every Fortune 500 company there is runs the software written by those people, and dozens of others who contributed software to node and npm in the early days. They aren't wealthy, despite the enormous value created by the software they wrote.

---

# [fit] __capitalism__ does not reward
# [fit] open source authors

^ Capitalism is supposed to reward people like them, but in practice it does not.

---

# [fit] most of us give away source code
# [fit] __not expecting money__

^ I think most of the people who contributed to Javascript’s commons did so without expecting or wanting money in return. They might wish they had tropical islands, but they never expected them. Money wasn’t on their minds when they wrote those modules and invented the node ecosystem, back in the early days of node, when the users of the node package manager mostly knew each other.

^ They were exchanging gifts of open source with their peers, and the wider ecosytem.

---

# [fit] open source __vs__ free software

^ You are likely aware of the difference between _free software_ — Richard Stallman style— and _open source_ — Eric Raymond style. Stallman's GNU license aims to require users of shared source code to give what they build with it away freely as well. Or at least to give their code away freely. We can argue about whether the GNU license achieves that goal or not, and people do argue about that at length. I don’t want to rehash the question here. I will merely observe that ESR’s style of open source, where you give away code with permissive licenses, is the style that has won. It’s _most likely_ the style that you practice-- you probably use "permissive" MIT & BSD licenses on your software, and you treat the GPL like poison.

---

# [fit] __capitalism__ loves open source

^ Capitalism loves ESR-open-source because companies get a lot of good stuff for free. Capitalism takes this even further by telling you all that you _have_ to do this to get hired. “Github is your resume,” they tell you, hand outstretched to take free code from you and sell what they make with it.

^ Dominic Tarr gives away pull-stream and every Fortune 500 company there is gets to use his work without compensating him. This is our reality.

---

# [fit] one person in this story
# [fit] __didn't__ give his stuff away

^ The person in this story who _did not_ give away his intellectual property is the person in this story who’s most likely to make a pile of money. He planned ahead in ways the people around him didn't. Of course, he’s not going to make anywhere near as much as the venture capital funds that paid for everything— the people who truly do well in this story are the people who had money to begin with. The people who had nothing to do with Javascript are the people who effectively own its commons.

---

# [fit] javascript's __commons__

^ Let's talk about this term I keep using-- the Javascript commons. What do I mean by that?

---

# [fit] commons: the __resources__
# [fit] available to __everybody__

^ The commons! It's a singular noun, meaning the collection of resources accessible to all members of a society. This could be natural resources, like the air we all breathe. It could also mean the field we all share to graze our sheep in.

---

# [fit] the language __spec__

^ For us, in the Javascript community, our commons includes the language spec itself. That's owned by an organization set up to allow all Javascript's stakeholders to cooperate to design and build it. TC39 has done pretty well by Javascript.

---

# [fit] all our __shared code__

^ Another thing our commons includes is all our shared code. The source code for Babel, the source code for webpack, the source code for TypeScript, for React, for Angular— these and thousands of other packages make up our commons. The _registry that lists all of this shared code_ is also part of our commons. It’s how we share all that stuff with each other, how we find it. Another thing that’s part of our commons is the set of conventions we've evolved around that -- the ways we agree to name and update the things we share.

---

# [fit] our common registry of shared code
# [fit] is owned by a __private company__

^ But all of _that_ is wholly owned by a VC-funded private company.

---

# [fit] __Ryan Dahl__ was here again last year

^ Last year at this conference, Ryan Dahl, the inventor of node, came back to make another announcement. He talked about [design mistakes](https://tinyclouds.org/jsconf2018.pdf) he thought he’d made with node. Here's one.

---

> It’s unfortunate that there is a centralized (privately controlled even) repository for modules. --Ryan Dahl

^ When I first saw that, I was inclined to argue with Dahl about centralization, but I had to agree with his comment about private control.

---

# [fit] what are the consequences
# [fit] of __private control__?

^ Let's talk about that for a moment. The list of shared Javascript packages we all made to share with each other is under private control. What does that mean?

---

# [fit] no input into registry __policies__

^ Policies for managing that list are controlled by a single company, not by the Javascript community. What gets a package removed? How are disputes among people using package names resolved? This is a controversial topic! Remember left-pad?

^ That was an incident where a package that was a dependency of a dependency of babel vanished from the registry suddenly, breaking every CI build that depended on installing babel. Why did left-pad suddenly vanish? Buy me a drink and I'll tell you! But the unpublication policy didn't exist before this incident, because it didn't occur to npm to think about this use case. They have not acted pro-actively to deal with problems until pushed to change.

---

# [fit] no input into registry __features__

^ Want package signing? Good luck! That feature doesn't make the company money, so you are unlikely to see it. Perhaps fear of a security incident, or major public outcry would get this done. It has to be an existential threat, though.

---

# [fit] the __registry__ is what matters
# [fit] not the clients

^ Note here that I’m talking about the _package registry_ almost exclusively here. The registry is closed source, and the policies that regulate it are not open to our influence. The npm cli is open source, but it is unimportant. The API is open, for now, and the key building blocks you would need for writing your own cli are all open-source and not under npm’s control. About a third of you use another client to interact with npm, anyway. The final tip-off that the cli doesn't matter because they seek out community participation in it.

---

# [fit] the management of our commons
# [fit] is __opaque__ to us

^ The management of your commons is opaque to you. It will remain opaque to you until the company that owns it has a financial incentive to change that. You do not know what it's doing with your package data-- you cannot know. You have to trust it.

---

# [fit] there is __no trust__
# [fit] without accountability

^ There can be no trust without accountability, and we as the Javascript community have no way to hold npm Inc accountable.

---

# [fit] you had no way to
# [fit] hold __me__ accountable

^ Now, when I was there, I could tell myself that I trusted myself and my team, and I knew our motivations were good. This was not a good answer and I was wrong to have relied on it. You had no way to hold _me_ accountable and to test that I was trustworthy.

^ Whoops.

---

# [fit] so is npm __evil__?
# [fit] mu. ask a different question.

^ So npm Inc is a private entity in control of our commons, and we are not. Does that make it evil? No. It doesn’t. It doesn’t make it good, either. The question of its benevolence is the wrong question to ask.

---

# [fit] npm is a __financial instrument__

^ npm is not a benevolent institution. It *cannot* be one. The possibility of it being that ended the day its owner took VC funding instead of putting it into a foundation or some other form of community ownership. That decision turned npm into a *financial instrument*. I mean something very specific when I say that.

---

# [fit] __financial instruments__
# [fit] are monetary contracts

^ Financial instruments are monetary contracts between parties. They're widgets that can be traded. npm Inc the company— the thing that owns our language ecosystem, the thing that owns the registry of packages, the collection of software packaged as the cli you use every day— that is a thing that might as well be a collection of pork bellies as far as its owners are concerned. They make contracts with each other and trade bits of it around.

---

# [fit] npm Inc is a means for turning
# [fit] some money into __more money__

^ npm-the-company is a means for turning some money into more money for the people who own it.

^ It’s important to keep this in mind as you evaluate all your interactions with it, and as you evaluate all your interactions with the people who represent it. What this means is *look at incentives*. Money turns out to be the incentive for the key actors in this story.

---

# [fit] __companies__ don’t love you
# [fit] not even ones that make things you like

^ Companies don’t love you, not even ones that make things you like. They can't.

^ That phrase is a marketing message, designed to get you to mistake the financial instrument for something that might be your friend. That marketing message has been pretty powerful over the years, hasn't it? You've got a cuddly wombat mascot and awesome stickers. Add a red emoji heart and you're on board, right?

---

# [fit] npm does __not__ love you

^ npm does not love you. npm cannot love you. npm Inc is a Delaware corporation founded as a financial instrument intended to turn money into more money for a handful of men.

---

# [fit] nobody __believes it__ anymore

^ When I initially knew I wanted to start talking about this problem in public, instead of in corners with friends, I thought I’d be fighting an uphill battle. The VC-funded package management company was beloved, and my work was one of the reasons why. I had participated in this whole rise to prominence— I made it possible. I stood on stage in front of you all and parroted that marketing message. What I meant by it was, "I, C J Silverio, feel affection for you all," and that was true.

^ Now I don't think anybody can stand up in front of you and say "npm loves you" believably. npm has burned all of its goodwill over the last few months. It didn't have to happen-- it was a choice made by the people who run the company. They made that choice, though, and they doubled-down on it, and here we are.

---

# [fit] how did the __fall__ happen?

^ How did that happen? Why did the cuddly wombat get set on fire? Let's move our story forward, shall we?

---

# [fit] It's 2017. Packages
# [fit] flow like __water__.

^ We pick up in, oh, I don’t know, 2017. You all have been drinking from the firehose of Javascript packages which have been, for you, free. You do not think about or care about where they come from, or who is paying for the servers. You just type `install` and the packages arrive.

---

# [fit] packages __cost money__ even if
# [fit] you're not paying for them

^ But the bandwidth costs money, and somebody pays for it.

^ In this case, npm had been spending the dollars given to it by its venture capital investors to pay for the servers and the bandwidth. And eventually the inevitable consequences of taking VC money started to knock on the door and clear their throats. *Ahem. Remember us? We want our money.* We've established that VC-funded companies are financial instruments. They have to start making that famous 10x return on investment. They have to promise somehow that their owners are going to end up winners. This isn’t always about being profitable, but if you don’t manage to do that you have to tell a persuasive enough story that you can raise more money and keep the scheme going.

---

# [fit] VCs want to go big or __go home__

^ There is absolutely nothing wrong with taking VC money inherently, in my opinion. Many ventures have goals well-aligned with the goals of VC money, and not all VC money is shaped alike. Some funds play long games. Funds like Futureshape are explicitly interested in bettering the world. But mostly, VC money is interested in returning the investment. The goal is to be sold to new owners for enough money to return the investment ten times over. Grow fast. Go big or go home. VCs don't mind if a pile of their companies fail, so long as one succeeds.


---

# [fit] npm is obligated to
# [fit] its __owners__ not us

^ Remember that npm Inc’s obligations are to the people who own it, not the people who donated their work toward its dragon hoard of packages.

---

# [fit] __make__ money or __raise__ money
# [fit] by telling a story about spending money to make money
# [fit] in some kind of money-ception. you can't fool me; it's money all the way down

^ So npm Inc has to make money, or failing that tell a story about making more money so it can raise money to spend on making money.

---

# [fit] they hired a CEO who made
# [fit] some, um, __interesting__ moves

^ The ex-Yahoo employee who thought that sharing the Yahoo package manager with the world was a pretty neat idea was right about that, but he didn’t have many ideas beyond that, and it turns out running companies is a lot of work. So in 2017 he hired a new CEO to do that work for him, and well, here we go. The first thing this new CEO wanted to do was change npm’s culture— you know, the thing it had exported as its marketing message. The sustainable, compassionate culture was the first thing to go when this new guy arrived. Everybody, including me, learned it was just a marketing message, not deeply held values.

^ npm’s PR troubles as a result are probably known to you now. We’re a community that enjoys our drama. It's possible that if a saint were in charge, I wouldn't be standing here. But maybe I would be, because even a decent human being in that spot has a big problem to solve.

^ Here’s the problem.

---

# [fit] the centralized registry is __expensive__

^ The public registry — the place where all your packages are indexed and stored— that’s the part you care about. That’s the part that is an enormous drain on npm’s budget _and_ simultaneously its value to investors. It controls all Javascript development, because all Javascript development proxies through it willingly. That data — the data gathered from your usage of it— is the valuable part. Every package-lock file npm has ever seen is sitting in an s3 bucket somewhere, chock-full of interesting data nuggets about what you've been up to. It’s also a perverse incentive influencing API design. The company has no incentive to reduce the number of times a client has to phone home when installing, because those calls homeward generate valuable data.

^ The registry is a drain on npm. The work of keeping up with continuous near-exponential growth is itself continuous. During my time there this work occupied most of a very tiny engineering team. npm has managed to keep the free Javascript flowing to you, but hasn't managed to make a profit with its products. Eventually the VC were going to lose patience. And here we are.

---

# [fit] the situation today is __uneasy__
# [fit] & probably __short-lived__

^ Today npm Inc hasn’t fully had its reckoning with its true destiny as a way to make money for some people who aren’t Javascript programmers. Maybe it's going to show growth. Maybe it's going to die. Maybe it's going to do something none of us like to make money, leveraging that enormous data trove that is their view of the development habits of every single one of you. You know the story about how if you're not paying for it, you're the product? That threat is dangling over your head right now.

^ We are all aware now that npm doesn't love us, and it doesn't love its employees either. It has no more good will from us, but we are all still installing packages through it. I, for one, find this situation uneasy. I suspect it won't last very long.

---

# [fit] this was __not__ the only option

^ Our story didn't have to go this way. Our major actors could have chosen differently, right up to and including their choices in recent months. But here we are. Our commons are in the hands of something I do not believe we can trust, because its incentives are not aligned with what we, as a community of Javascript programmers, need from it.

---

# [fit] what are we going to __do__ about it?

^ What are we going to do about it?

---

# [fit] do __nothing__?

^ One answer is, we do nothing. Say we can't do anything. We made our community decision in 2013 and we're stuck with it. We wait for npm Inc to fail and when it does, we have a nasty couple of months replacing the registry.

^ I don’t much like this answer.

---

# [fit] imagine npm run by a
# [fit] __non-benevolent__ entity

^ Imagine npm Inc in the hands of a corporate pirate, somebody who takes over ailing companies adversarially and shakes them down for pocket change. Somebody like this might have no incentive to keep the public registry running, or might not hesitate to mine it for your usage data. Somebody like this might threaten to take it down, just to see what we'd do in response. I find this scenario quite possible, because frankly npm's board of directors that hasn't done a very good job thus far.

---

# [fit] maybe we'll be saved by
# [fit] some __large company__

^ This is a more optimistic outcome. A larger corporate savior might swoop in and rescue npm, our beloved package registry, and keep our commons alive. But even if the registry ends up owned by a secure company, I think this merely punts the problem down the road. Microsoft is a benevolent actor today, but they sure haven't always been. Google was once a benevolent actor, but they're now acting exactly like the monopolist Microsoft was in the 90s.

^ I'd like us to avoid a repeat of this talk a decade from now.

---

# [fit] I agree with __Ryan Dahl__

^ I think, in the end, I agree with Ryan Dahl. Javascript's package registry should not be privately controlled. I think centralization is a burden that will inevitably lead toward private control, because, well, the servers always cost money. If we can diffuse the load out among many people, we can share the burden. Who knows, maybe once it's out from under the burden of the public registry, npm might find a way to make a profit for itself.

---

# [fit] do you think that's __impossible__?

^ This probably sounds impossible to you all. You're thinking that npm is entrenched. A few months ago I might have agreed, but then the company set on fire every bit of goodwill it had ever had for no reason anybody can see, all the trust people like me had ever earned it as benevolent stewards. Just poof. Up in flames. It was so total and comprehensive that it looks intentional. The solid ground shifted under our feet, and now we're aware that this thing we all depend on isn't what we thought it was.

---

# [fit] I believe in __giving__ source code away

^ Also, I’m not much for hand-wringing. The do-nothing answer doesn’t sit well with me as a human.

^ The other confession I’ll make is that I believe in open source despite everything. I think it's good for us as humans to give things to each other, and I think I'm at peace with the idea that some corporations will make money from it.

---

# [fit] Chris Dickinson __@isntitvacant__
# [fit] & I have an announcement

^ So I have an announcement. I would like to give away something to you all today. And it’s not just me giving this away. My colleague Chris Dickinson and I have been working on this together.

---

# [fit] __entropic__: a federated package manager
# [fit] https://www.entropic.dev

^ Today I'd like to introduce you to entropic, a federated package manager for Javascript.

---

# [fit] Apache 2.0 licensed
# [fit] entirely __open source__ (sorry RMS)

^ Entropic is Apache 2 licensed, and everything you need to run your own registry is included.

---

# [fit] new __cli__ & new __api__
# [fit] decentralized: many registries

^ Entropic comes with its own cli, which we’re calling `ds` , the entropy delta,.
^ Entropic offers a new API for publication and for installation, one that drastically reduces the amount of network traffic needed. The unit of installation is a single file, not a tarball.
^ Entropic is federated. You can depend on packages from any other Entropic instance, and your home instance will mirror all your dependencies for you so you remain self-sufficient.
^ Entropic will mirror all packages you install from the legacy package manager.
^ The requirements list is short, and we’ve dockerized it all.
^ You sign in with your GitHub account, and any oauth provider is pluggable.

---

# [fit] no, __don't use__ entropic yet

^ The project is only a month old. It's not ready for anybody but people developing it to use yet.

---

![fit,inline](./qr-code.png)
# [fit] but we do want __your help__
# [fit] github/entropic-dev

^ There are more features, and a fairly huge to-do list. It doesn’t have a web site to speak of right now, for instance, and it needs one. The repo has a long list of issues if you’re interested.

---

# [fit] entropic's __goals__

^ What are my goals with entropic?

---

# [fit] first, prove we have __power__

^ First, I want to prove to you all that there are options beyond doing nothing. We don’t have to sit here and wait for npm to shut down before we do something. Be optimistic. Be pro-active. You have power.

---

# [fit] second, share our __expertise__

^ Second, Chris and I are among a handful of humans who deeply understand the problems a language package registry needs to solve, particularly at scale. That expertise is needed by our community right now, and we want to share it. We choose to give something valuable away: our expertise & our labor.

---

# [fit] third, promote __federation__

^ Third, I think it’s right that the pendulum is swinging away from centralization and I want to lend my push to the swing. The last decade has been about consolidation and monolithic services, but the coming decade is going to be federated. Federation spreads out costs. It spreads out control. It spreads out policy-making. It hands control of your slice of our language ecosystem to you.

---

# [fit] __take back__ the commons

^ My hope is that by giving Entropic away, I’ll help us take our language commons back. We'll take it back so we’re not held hostage by the needs of venture capitalists. Take it back so it's possible for us all to make a decision different from the decision we all made at the end of 2013. We are a community of millions of developers, and we have enormous power. Entropic is our kick-start to this movement to take our language back.

---

# [fit] go do something __amazing__

^ There’s a lot more to say about Entropic, and a lot more work to do on it, but it’s time for me to share it with you.

^ If we’ve learned that npm doesn’t love you—and it doesn’t-- and we’ve learned that a private company shouldn’t control the commons—and it shouldn‘t, then it’s time to move with our feet. I believe the Javascript community is good, full of amazing people capable of building amazing things. We should not be owned by a single company, and we shouldn’t let that company control our destiny. We need to take back control. I'd like us all to rebuild the future together.

---

# [fit] ❤️ from ceej & chris

^ With love from two human beings, from us to you. What happens next is up to you.
