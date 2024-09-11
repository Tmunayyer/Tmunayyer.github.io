# Making This Blog
09/11/2024

The first post in my blog will be how I made what you are reading.
# Requirements
I really want to keep things simple to start.
- should use either markdown or HTML as syntax 
	- preferably markdown so I can use Obsidian (which I have been using for other stuff) for composition
- should have the ability to easily add images
	- I would like to write about my recent trip to Sardinia, Corsica, and Paris. The ability to Attach images would be super nice
- should be low friction to publish
	- I want to literally click one button and have it be live 5-10 minutes later
# Research
While I was traveling I was googling around and found some decent notes about starting a blog.
## Domains
Someone on Hackernews mentioned having your own domain so you don't have to change it if you change platforms. My plan is to use Github pages. By default it has a format of *your-domain*.github.io. This would tie me to Github pages if I ever want to swap to a different service. Github pages does support custom domains out of the box and it looks relatively simple to set up.
## Assets
Besides domains, hosting assets like images can apparently be tedious. People discussed migrating platforms and having to re-upload images to new content management systems. Lets try to keep this also agnostic of the hosting platform. Since I will probably purchase my domain through Cloudflare, I'll see if I can also use them as a CDN provider to host my images.
## Syntax
I already knew I wanted to keep the syntax as basic as possible. As appealing as it would be to flex the Javascript muscles and do something fancy, I want to build a process of publishing first. If I can add stuff later, the effort to keep things platform agnostic will pay off and I can do a V2 later.
# Execution
## Buying a Domain
This took maybe five minutes using Cloudflare, and it only took that long because I needed to create an account. I used them because of name recognition and the potential to also use them as a CDN for assets. 

Luckily for me, my last name is very unique. Despite a big family, not many people spell it the exact same way. I know there is another Thomas Munayyer out there (who is very good at soccer/football) but, you snooze you lose!

The domain *tmunayyer.com* cost ~$10.
## Github Pages: Hello World
Getting setup is super simple with [this guide](https://docs.github.com/en/pages/quickstart). The custom domain is *not* as simple as changing a setting in Github alone. Following [this guide](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site), I went into Cloudflare and had to set up some A and AAAA proxies so that traffic going to *tmunayyer.com* will resolve to Github Pages IP addresses.

This is now working, *tmunayyer.com* is alive.

![hello world github pages screenshot](https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/f2b6d899-94ba-487d-1e2f-e11652c3a500/public)

This took about 20-30 minutes, but only because I am a bit unfamiliar with the Cloudflare dashboard and setting up proxies in general. If I had to do this again I bet it would be 5 minutes.

The guide recommends adding in proxies for *www* as well. Trying to navigate to that right now ends up hanging. Ill do this now so it doesn't somehow end up being a problem later.
## Private vs Public
For some basic workflow to separate in progress and finished posts, I'll just use a simple file structure. It will look like this:

- Blog
	- Private
		- Projects
			- making-this-blog.md
		- README
	- Public
		- Projects
			- making-this-blog.md
		- README

The first step to publishing will be to copy and paste the contents from the Private file, to the Public counterpart. Only the Public folder will be tied to the Github Pages repository. This will probably be enough to avoid publishing unfinished work.
## Github Pages: First Publish
I want to get this exact file in its current state onto my new website. I think its as easy as committing and pushing the changes. Ill copy this over to the public folder.

It looks like I haven't used my personal Github account with SSH keys before and need to [set this up](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key). This took a few minutes since I needed to readjust the remote url so it would stop asking for a username and password, but we finally have a successful push. Just waiting on the Github Pages action now...

Because of the SSH setup, this took 20-30 min.
### Routing
This requires relative file path routing which should be good enough for now. Im sure there is some plugin that could make Obsidian vault references auto translate to relative file paths but thats a project for another day.

After pushing up the changes and figuring out the route, I can confirm this post is now out in the world!

![first publish of this post screenshot](https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/7ca63979-39ba-45c5-2c2e-b1f2cbb64100/public)

## Better Publishing
One of the goals of this project was to create a blog that requires a single click to publish. 

At the moment it requires:
1. copy contents from the Private folder to the Public folder
2. opening the terminal
3. adding the changes
4. committing the changes
5. pushing to main

What I really want is a single button that says publish. Theres a few Github interaction plugins but I'll go with the [Git plugin first](https://github.com/Vinzent03/obsidian-git). It seems less bloated with tangential features that I don't need at the moment *and* has actual buttons instead of running commands.

While its not *exactly* what I wanted, this is good enough for MVP. The Git plugin allows me to preview changes, add, commit, and push with buttons.

![buttons to control git in obsidian screenshot](https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/5b234d37-9448-4611-5cb9-9d58967ede00/public)

The process is now:
1. copy contents from the Private folder to the Public folder
2. review the changed lines (in the future it should be the whole file)
3. click the add button
4. click the commit button
5. click the push button

After writing this out, this feels like I didn't do anything haha. Ill revisit this another time.

Maybe Ill need to roll my own plugin that copies the file then adds, commits, and pushes the changes.

This took 20 minutes to look through plugins then configure the one I decided to go with.
## Assets
The final piece to call this MVP finished is to enable platform agnostic assets. Looks like Cloudflare has an option to store 100k images for $5/month. Not stoked about the monthly charge but I want to finish this. To be sure I want to go this route I spent ~15 min googling solutions. It seems like I *could* avoid this monthly charge with a bit more work. I think I am more inclined to cross the finish line quickly rather than saving the few bucks at this moment.

In a few months if I am still posting, I will migrate to something either cheaper or free.

While working on this I had to step away. There was some internal error with the images being displayed on Cloudflare's side. After emailing support and a little back and forth it looks like its resolved! Blog platform asset agnosticism (is this a real word) achieved.

This probably ended up taking about 45 minutes if I take out the time I was waiting for support to reply. 
# Following Through
What spurred this particular effort is to get outside my comfort zone and start putting myself out in the world a bit more. Many of my hobbies and work is quite solitary.

The final step here is to post it to Hackernews. If you read this and thought of starting a blog, hopefully it gives you some good ideas (or bad ones to avoid).

Total time to create this was ~120 minutes.

### Wish List
As an aside, here is a wishlist I had while writing this document.
- free image hosting
- single button publish
- some writing helping me with wording since I am probably not very good