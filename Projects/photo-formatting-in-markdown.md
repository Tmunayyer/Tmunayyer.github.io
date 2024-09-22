# Photo Formatting in Markdown

<head>
    <style>
        .text-with-photo {
            display: flex;
        }

        .text-with-photo>p {
            width: 65%;
        }

        .text-with-photo>figure {
            width: 35%;
        }
    </style>
</head>

This blog's MVP was to get stuff out into the world. In order to focus on execution and building a process I decided to forego any kind of formatting. Today I want to iterate and make things flow a little bit better. I really want to have photos and text side by side and/or the ability to add photo carousels.
## Why
One non-project article I want to write is about my recent trip to Sardinia, Corsica, and Paris. I have tons of photons and putting them directly into the article with no formatting will look really low quality.

I also think it will be beneficial for project articles to have explanations and visuals side by side moving forward.

## Requirements
1. I can have two "columns", where text is on the left, photos are on the right in a article.
2. I can easily add photo descriptions.
3. (Bonus) I can have a photo carousel.
## Research
This might only be a project due to my unfamiliarity with markdown in general. Lets find out.

Someone named [David Wells](https://davidwells.io/snippets/how-to-align-images-in-markdown) has a nice little article on just inserting HTML into markdown. Below is the result of using:

```html
<img 
	 alt="A picture of a cat."
	 src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">
```

<img alt="A picture of a cat." src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">

I honestly did not know I could intermingle HTML and markdown together like this. This might be easier than I thought. This makes sizing easy but what about positioning. *Sidenote:* How easy would it be to add a bit of Javascript with a `<script />` tag? 

This honestly might be enough information to start iterating. Some notes from just reading through MDN `img` documentation:
-  [it looks like you can use media queries with pure html now which is amazing](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#using_the_srcset_and_sizes_attributes)
	- I definitely thought I would need Javascript for anything viewport dynamic.
## Execution

### Sizing
Hardcoding sizing should be as simple as height and width:

```html
<img 
	 height="100" 
	 width="100" 
	 alt="A picture of a cat."
	 src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">
```

<img height="100" width="100" alt="A picture of a cat." src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">

This obviously has an issue with aspect ratios. I think I can just pass one or the other to maintain aspect ratios.

```html
<img 
	 height="100" 
	 alt="A picture of a cat."
	 src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">
```

<img height="100" alt="A picture of a cat." src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">

And here is an example of just width set.

```html
<img 
	 width="100" 
	 alt="A picture of a cat."
	 src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">
```

<img width="100" alt="A picture of a cat." src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public">

### Positioning
<div class="text-with-photo">
    <p>
        testing 123here is some text and some even more text here is some text and some even more text here is some text
        and some even more text here is some text and some even more text here is some text and some even more text here
        is some text and some even more text here is some text and some even more text here is some text and some even
        more text here is som
    </p>
    <figure>
        <img alt="A picture of a cat."
            src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public" />
        <figcaption>A picture of a cat.</figcaption>
    </figure>
</div>



<div style="display:flex;">
    <p style="width: 65%;">
        testing 123here is some text and some even more text here is some text and some even more text here is some text
        and some even more text here is some text and some even more text here is some text and some even more text here
        is some text and some even more text here is some text and some even more text here is some text and some even
        more text here is som
    </p>
    <figure style="width: 35%;">
        <img 
	        style="width: 100%;"
	        alt="A picture of a cat."
            src="https://imagedelivery.net/XM0rX8WdEGAqoK0m1yhClg/972c77fc-2365-42a5-1786-b12c3c6cc100/public" />
        <figcaption>A picture of a cat.</figcaption>
    </figure>
</div>

#### Difficulties
While writing this, the markdown looks how I would want it, but when entering reader mode, its clearly broken. How do I define photos to have width


### 
## Following Through
the final steps to call this "done"
