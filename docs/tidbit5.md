# PBS Tibit 5 of Y — Tips for the Vacationing Programmer

If bashing away on some code on a beach-side Mediterranean terrance  with a pitcher of sangria in a warm August evening breeze sounds likw your idea of heaven, this special instalment is for you 🙂 Those of us who really love programming love to get deep into some purely personal coding projects while we're on our summer vacation, but if often fails to go to plan because of a lack of planning. If you want your vacation coding projects to be stress free and fun, you absolutely need to do some prep work before you board that plane or start up that camper van!

Every situation will be different, but you'll fall somewhere on each of two spectra — from the same hardware you normally use to totally different hardware, and from the same level of connectivity you normally have to none at all. 

We'll be looking at this from the POV of a Programming by Stealth listener/reader, so we'll be assuming the PBS tool chain (HTML, CSS, JavaScript, jQuery, Bootstrap, NPM/NodeJS, JSDoc, Jest, Webpack & NPM), but the principles apply globally, and the specifics can be translated/adapted to other tool chains.

## Matching Podcast Episode

TO DO

## Before Departure

### Patchy Patchy Patch Patch 😉

If you know internet connectivity is going to be a problem, you definitely need to apply all software and OS updates before you leave. But I advise doing that anyway, regardless of your connectivity expectations for two reasons — firstly, your expectations might not pan out, and secondly, do you want to waste vacation time looking at progress bars?

I strongly recommend updating:

1. Your OS
2. All app-store apps
3. All other apps in your tool chain — though you'll need to manually launch and check those
4. Local server processes you rely on like web or DB servers (e.g. [MAMP](https://www.mamp.info/))

### Clone all the Repo(s)

Don't just clone the repos for code you plan to work on, clone any other repo you might want to work on when you get frustrated with the project you had planned (you know it will happen!), and, clone all the repos that use the same technologies you expect to be using so you have working examples of your own code to look at when you run into those inevitable stumbling blocks.

Given modern hard drive sizes, code is negligibly small, so better to clone more than you need than to find yourself wishing you could just have a quick look at some function or other you vaguely remember having taken you *ages* to figure out.

### Build your Projects

Depending on the complexity of the projects and the toolsets you'll be using you should do what ever you need to do to turn your checked out repos into working code.

If you use NPM then that means doing an `npm ci` at the very least. That way you'll know you have all of your prerequisites installed.

If the code has been un-updated for a while, consider updating the dependencies too, at least to their most recent minor version, with `npm outdated` and `npm upgrade` (and `git commit` & `git push`).

If your projects use other tools like documentation builders, test suites, or bundlers, also run those with commands like `npm run docs`, `npm run test`, and `npm run build`.

### Run an End-to-End Offline Test

Turn off your wifi & unplug form ethernet and try run through your entire build process again, including documentation generation, test suites, and and actually running your code.

If you need any other tools to write, test, or run your code, test those too. If you're working on server-side code that means testing your code on your local web server.

### Localise your Dependencies

One reason your off-line testing might fail is your code relying on CDN-hosted resources (likely web libraries like jQuery or Bootstrap). Your browser can only load these while you have internet access, so you may want to permanently or temporarily replace them with local copies.

#### A Quick & Dirty Temporary Fix

If you have an HTML file that's loading something from a URL, say a script, a stylesheet, or an image, the simplest things to do is to pop that URL into your browser, download what ever it is, add it to your project (by tradition in a folder named `contrib`), and update the URL to the appropriate relative URL to your downloaded file. This works great for entirely self-contained dependencies (files that don't reference other URLs), but it's not practical for nested dependencies. In those cases you'll need to go to the project's website and download their full distribution and install the lot into your `contrib` folder.

If you go this route, **it should be a temporary change**! My advice would be to comment out the existing references, replace them with the local ones, and reverse the process when you get home. Why? Because this approach just isn't practical in the long term for at least three reasons:

1. You've just taken responsibility for keeping your copy of these resources up to date from a security POV
2. If you publish your code in this form, you may be breaching the third party's license agreement
3. You've just made your project a lot bigger

#### Doing it Right — NPM + a Bundler

The right way to localise your dependencies is to add them to your project with a package manager like NPM, and then to bundle them into your builds using a bundler like [Webpack](https://webpack.js.org/). Note that we've not covered this Webpack use-case in the PBS series yet (in July 2022), but [this tutorial shows how it's done](https://www.sitepoint.com/bundle-static-site-webpack/).

### Off-line Docs

Believe it or not, there was a time when you bought dead-tree books to get the documentation you needed for your programming languages of choice. By far the leading publisher was O'Reilly press, and their so-called *animal series* was legendary (I even wrote a chapter for the one on the [Tomcat web server](https://tomcat.apache.org) many moons ago). Of course they all became out of date almost instantly, and they were **heavy** the cheap kinds of book cases students can afford are no match for them! I was once so proud of my massive shelf of O'Reilly books, but when I moved house I threw all but those with sentimental value out (the Tomcat one with my chapter in it and the famous *Camel Book* on Perl are the only two I kept).

Now, we just read docs online! Every project website has a documentation section, and we all just use that.

On the one hand, this is progress, no more heavy books to pack! On the other hand, how do we get at the docs when we have no internet access?

You have three choices:

1. Most major projects will make their documentation available in some kind of downloadable form if you look hard enough (a Git repo to check out, a ZIP file of HTML files to download, or a PDF).
2. O'Reilly still exist, they just sell eBooks now, so you could solve the problem with money 🙂
3. Use a documentation library app like [Dash](https://kapeli.com/dash) to fetch and download all the docs you need. As a bonus, you get a great searchable library with useful features for creating bookmarks and even annotations.

Unlike many programmers, I actually don't use the web even when I'm working at home or in the office, I find Dash so much better an experience that I just use that all the time, and not having to worry about internet access is just a bonus!

### Local Alternatives to Online Utilities

If you use online tools to help you with things related to code, but not strictly part of your code, you'll need to find stand-alone versions of those. 

If you're not sure what I mean, the two examples that come to mind for me are regular expression testers, and colour scheme generators, but other people will use other websites for other code-adjacent things. Not having access to these tools won't stop your code from building or running, but their absence might frustrate the heck out of you when you were planning on having fun, so don't forget about them!

### Checklist

1. OS patched?
2. All software installed?
3. All software patched?
4. All repos cloned?
5. All builds tested and working while off-line?
6. All build products tested and working while off-line?
7. All docs available while off-line?
8. All tools/utilities working while off-line?

## While You're Away

###  Commit Early & Commit Often

Remember – at a technological level, every copy of a Git repo is equal, all are full clones with a full version history because Git is a peer-to-peer technology. Commits get synchronised between repositories when you push and pull, so you can make as many commits in your local repo as you like and they will all get synced to your cloud repo next time you push.

You might wonder what the point is? Sure, Git can be used as a remote backup, but that's not it's primary purpose, it's primary purpose is to give you versioning, and that works just fine locally! Being away doesn't insulate you from making mistakes, you're just as likely to need to roll back on the beach than at your desk (more likely of you've had too much sun or too many sangrias! 😉).

### Push When You Can

The more work you do, the more not having a backup will bother you, so when ever you get a sip of internet, make use of it to push all your commits to cloud repo (GitHub or what ever you use).

Code is just text, and Git is efficient, so pushing your code should use very little of your precious bandwidth.

#### Consider Creating a Temporary Local 'Remote'

If not having any backups makes you uncomfortably nervous, consider adding an additional *remote* on a thumb-drive or external hard drive. You can keep it disconnected most of the time, plug it in, push, and then disconnect it again.

Remember that a *remote* is any other Git repo, even another one sharing your file system. The URL to a local remote is simply the path to the folder containing it. The simplest thing to do is to create your temporary remote by cloning the repo you're actually doing your work in, then adding the new clone to your primary repo as a sensibly named with a sensible named  remote (maybe `temp_backup` or something similar), and then pushing to that new remote periodically.

### Avoid Merge Conflicts — Use a Dedicated Branch

If you share a repo with other people, you run the risk of merge conflicts delaying your pushes and pulls when you sporadically get online. You could probably do without the stress of resolving merge conflicts when your internet connection is a scarce resource, so my advice is to avoid the problem by working on a branch that's just for you. I would suggest giving it a name that clearly marks it as yours, and letting your co-contributors know what the branch is, why you created it, and to please leave it well enough alone!

## When You Get Back

### Undo any Quick & Dirty Workarounds

If you used workarounds to localise your dependencies as opposed to using NPM and a bundler, un-do those changes and commit to the branch you've been working on before you merge your changes into the appropriate permanent branch. You don't want to confuse things with workarounds on a `main` or feature branch that's around for the long-haul!

### Merge, and Expect Conflicts to Resolve

Assuming you were working on a repo with multiple collaborators, you'll need to merge all your changes, and if you've been away for a while, and the others have been busy too, there's a good chance of a merge conflict. Assume there will be, clear some space in your schedule, make a big mug or glass of your beverage of choice, and just work through them slowly and carefully. Usually, there are much fewer conflicts than you feared, so you end up with some quiet time in your schedule, and a nice drink 🙂

### Clean Up!

Once you've safely merged your changes, remember to clean up any temporary branches or remotes you created.

## Final Thoughts

There's nothing more frustrating that finally having the time to get stuck into that code that's been burning a hole in your brain for months than finding you're missing the tools you need to get the job done. Conversely, there's nothing more satisfying that getting all those ideas out of your head and into working code. The difference between the two is simply preparation. Take the time to prepare, and you'll be rewarded with that wonderful feeling of satisfaction we all get from creating great software!

Enjoy your vacation 🙂