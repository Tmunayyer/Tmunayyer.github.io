# Photo Formatting in Markdown
09/22/2024

<head>
    <style>
        .text-with-photo {
            display: flex;
            flex-direction: row;
        }

        .text-with-photo>p {
            width: 65%;
        }

        .text-with-photo>figure {
            width: 35%;
        }

        /* Extra small devices (phones, 600px and down) */
        @media only screen and (max-width: 600px) {
            .text-with-photo {
                display: flex;
                flex-direction: column;
            }

            .text-with-photo>p {
                width: 100%;
            }

            .text-with-photo>figure {
                width: unset;
                max-width: 80vw;
                align-self: center;
            }
        }
    </style>
</head>
This blog's MVP project was to get stuff out into the world. In order to focus on execution and building a process, I decided to forego any kind of formatting. Today I want to iterate and make things flow a little bit better. I really want to have photos and text side by side and/or the ability to add photo carousels.
## Why
One non-project article I want to write is about my recent trip to Sardinia, Corsica, and Paris. I have tons of photos and putting them directly into the article with no formatting will bother me.

I also think it will be beneficial for project articles to have explanations and visuals side by side when appropriate.
## Requirements
1. I can have two "columns", where text is on the left, photos are on the right.
2. I can easily add photo descriptions.
3. (Bonus) I can have a photo carousel.
## Research
Note: While writing this section, I started, then backtracked, then thought of redoing my blog, then finally found a good enough solution for now. It turns out you can literally just add HTML to markdown and it works. My process suffers quite a bit though.
### Sizing
For an image, you can resize by simply placing an `img` tag with height, width, or both attributes set.

```html
<img 
	 height="300" 
	 alt="A picture of a cat with a height attribute."
	 src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">
```

<img height="300" alt="A picture of a cat with a height attribute." src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">

The problem here is I want something more dynamic, so again, HTML "just works", which means I can also add style attributes and write CSS.

```html
<img 
	 style="width: 30%;" 
	 alt="A picture of a cat with a style attribute."
	 src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">
```

<img style="width: 30%;" alt="A picture of a cat with a style attribute." src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">

Its nice to know HTML and CSS work. Positioning makes thing a bit more complicated however.
### Positioning
Immediate results googling around seem to be pretty outdated. There are many recommendations of `float: right;` which is pretty old. There is also the `align` attributes which have been deprecated since early 2000's.

In the end, sort of knowing I wanted to also account for mobile devices, I decided to use `display: flexbox;`. On mobile, I think it should be a singular column and read fluidly instead of side by side.

Since HTML works, it means I can add a style tag, define some classes, and have some basic structure around the formatting. What I don't like is that Obsidian doesn't register these things with its live previews. Its a Markdown formatter/previewer so even though it might work in  Github Pages, it wont be visible until after I publish. Its kind of intruding on my "minimal friction" process, but for the sake of getting something done, lets go for the MVP and find a way to refine from there.
### Photo Descriptions
The last thing I was not sure about when starting was adding photo descriptions. After trying a few different tags listed on [MDN](https://developer.mozilla.org/en-US/), I decided on the `figure` tag. It seems to group the photo and text nicely paired with `figcaption`.
## Execution

### Sizing & Positioning
Instead of hardcoding an image width or height, I wanted it to be a bit more dynamic. I figured a 65%, 35% split between written content and image would be sufficient on everything except mobile devices. Knowing I have access to media queries, all I really had to do was write a bit of HTML and CSS. Below is the result:

```html
<head>
    <style>
        .text-with-photo {
            display: flex;
            flex-direction: row;
        }

        .text-with-photo>p {
            width: 65%;
        }

        .text-with-photo>figure {
            width: 35%;
        }

        /* Extra small devices (phones, 600px and down) */
        @media only screen and (max-width: 600px) {
            .text-with-photo {
                display: flex;
                flex-direction: column;
            }

            .text-with-photo>p {
                width: 100%;
            }

            .text-with-photo>figure {
                width: unset;
                max-width: 80vw;
                align-self: center;
            }
        }
    </style>
</head>

<div class="text-with-photo">
    <p>
	    testing 123here is some text and some even more text here is some text and some even more text here is some text and some even more text here is some text and some even more text here is some text and some even more text here is some text and some even more text here is some text and some even more text here is some text and some even more text here is som
    </p>
    <figure>
        <img alt="A picture of a cat."
            src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public" />
        <figcaption>A picture of a cat.</figcaption>
    </figure>
</div>
```
<div class="text-with-photo">
    <p>
        The above accomplishes more or less what I want in the end. I have a bit of flexibility when it comes to different viewport sizes, and can easily add more with more media queries. I attain the ability to place text and images side by side as well. See figure 2 as the end result of the above HTML. The problem is the development environment.
    </p>
    <figure>
        <img alt="A screenshot of the rendered html and css."
            src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/de56d21c-3b07-4607-aa37-8e27e35f3c00/public" />
        <figcaption>Figure 2</figcaption>
    </figure>
</div>
### Growing Pains
Maybe I chose wrong when I started (I did). I optimized to just start writing and publishing which, if I weigh it against my original goal, worked, but the stack is already showing its weaknesses. Just adding a little bit of HTML and CSS is already breaking it.

<div class="text-with-photo">
    <p>
        I lose the ability to live preview what my article might look like in Obsidian. This is actually a major hurdle in my opinion. I don't want to be guessing and I don't want to have a feedback loop of minutes by pushing to Github and waiting for Github Pages to deploy. Figure 3 is an example of what the live preview looks like in Obsidian. Compare this to the end result seen in Figure 2.
    </p>
    <figure>
        <img alt="A screenshot of the Obsidian live preview broken."
            src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/c332ecea-df5c-4c49-1189-8a4075da7b00/public" />
        <figcaption>Figure 3: *Obsidian not using the script tag.*</figcaption>
    </figure>
</div>

Also, obviously Obsidian is not used for writing code (or at least it definitely shouldn't be). So now, I need to use VSCode for formatting then copy and paste the result into Obsidian. This got messy way faster than I would have guessed.
### Insult to Injury
Any decent webdev would probably think, "ok whatever, I'll use the browser to render the page and just keep hitting refresh, that will be fast"! *Whoops, all these files are markdown and don't render on the browser.*

Despite this, I want to finish here then think of a better, low friction way to compose these articles. Maybe the composition and formatting need to be separate but I hate that idea. I want to write, read, rewrite, and publish. Any more steps than that and I fear I would be inconsistent.

As a side note, living with your own mistakes is usually a sign you are learning, I just thought it would take longer than *a single iteration*.
## Following Through
I really didn't think this would take as long as it did, and I also didn't think it would blow up my process as much as it did. As I write this, I have:
- Cloudflare open to upload and copy image urls 
- Obsidian to compose the copy
- VSCode to write the HTML, CSS, and handle formatting
- The browser with a WIP version of this article to see how it will render

I also really thought I would make it to the photo carousel portion today but I am out of time. I had more catching up to do on HTML than I would like to admit.

I think the next project concerning this blog, and likely the next one I do will be to get something a bit more sustainable up and running in terms of process. I might have to convert to something that uses HTML, then this might be a bit easier, but then I would lose out on having a centralized location for blog writing, publishing, and personal use of Obsidian.

After some searching, It looks like any Obsidian solution too might just be a hacky way of getting it done. It might just be that the blog composition takes place elsewhere. Problem for another day.

Today I will say, this is done. I set out to figure out how to do text next to images in Markdown and it turns out you just use HTML. Kind of a failure on my part but at least I know what I will work on next.

*I set out with the goal of doing things more in public. I am going to post this to hackernews.com. Here is the post: https://tmunayyer.com/Projects/photo-formatting-in-markdown.html*
