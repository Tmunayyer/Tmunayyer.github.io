09/11/2024

The first post in my blog will be how I made this blog.
# Requirements
I really want to keep things simple to start.
- should use either markdown or HTML as syntax 
	- preferably markdown so I can use Obsidian (which I have been leveraging lately for notes) for composition
- should have the ability to easily add images
	- I would like to write about my recent trip, attaching pictures would be super nice
- should be low friction to publish
	- I want to literally click one button and have it be live 5-10 minutes later
# Research
While I was traveling I was googling around and some decent notes about starting sounded appealing.
## Domains
Someone on Hackernews mentioned having your own domain so you don't have to change it if you change platforms. My original plan is to use Github pages. By default it has a format of *your-domain*.github.io. This would tie me to Github pages if I ever want to swap. I should purchase my own domain, and Github pages does support custom ones.
## Assets
Besides domains, hosting assets like images can be tedious. People discussed migrating platforms and having to re upload images to new content management systems. Lets try to keep this also agnostic of any one provider. I will purchase my domain through Cloudflare. Ill see if I can also use them as a CDN provider to host my images.
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

*insert screenshot here*

This took about 20-30 minutes, but only because I am a bit unfamiliar with the Cloudflare dashboard and setting up proxies in general. If I had to do this again I bet it would be 5 minutes.

The guide recommends adding in proxies for *www* as well. Trying to navigate to that right now ends up hanging. Ill do this now so it doesn't somehow end up being a problem later.

## Github Pages: First Publish
I want to get this exact file in its current state onto my website. I think its as easy as committing and pushing the changes. Ill copy this over to the public folder.





