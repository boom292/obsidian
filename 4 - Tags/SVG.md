20th Jan '25, 11:58am

Status: #ProperNotes #InProgress 

Tags: [[Image Format]] [[Web Dev]]

# SVG

SVGs are a _scalable_ image format, which means they will easily scale to any size and retain their quality without increasing their filesize. They’re also very useful if you need to create or modify your images programmatically, because you can change their properties through CSS and JavaScript.

SVGs are often used for:

1. Icons
2. Graphs/Charts
3. Large, simple images
4. Patterned backgrounds
5. Applying effects to other elements via SVG filters

“SVG” stands for “Scalable Vector Graphics”. Vector graphics are images defined by math, as opposed to traditional “raster graphics”, where your image is defined by a grid of pixels. With raster graphics, the detail is limited to the size of that pixel grid. If you want to increase the size of the image (_scale_ it), you have to increase the size of that grid. How do you decide what all those new pixels should look like? There’s no simple solution. Additionally, the larger the grid, the bigger your filesize grows.

With vector graphics on the other hand, there’s no grid. Instead, you have formulas for different shapes and lines. Since these are just formulas, it doesn’t matter how large or small you want them to appear–they can scale to any size you want, and it will have no effect on the quality or the size of the file.

SVGs have another interesting aspect to them: they’re defined using XML. XML (aka, “Extensible Markup Language”) is an HTML-like syntax which is used for lots of things, from [APIs](https://en.wikipedia.org/wiki/API), to [RSS](https://en.wikipedia.org/wiki/RSS), to [spreadsheet and word editor software](https://en.wikipedia.org/wiki/Office_Open_XML).

The fact that SVG source-code is XML has a few key benefits.

First, it means that it is _human-readable_. If you were to open up a JPEG in a text editor, it would just look like gobbledygook. If you were to open up an SVG, however, it would look something like this:

```html
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
  <rect x=0 y=0 width=100 height=50 />
  <circle class="svg-circle" cx="50" cy="50" r="10"/>
</svg>
```

It might still be confusing, but hey–those are words! Tags! Attributes! Compared to [binary file formats](https://en.wikipedia.org/wiki/Binary_file) like JPEG, we’re definitely in familiar territory.

The second benefit of XML is that it’s designed to be interoperable with HTML, which means you can put the above code directly in an HTML file, without any changes, and it should display the image. And because these can become elements in the DOM just like HTML elements, you can target them with CSS and create them using the [Element WebAPI](https://developer.mozilla.org/en-US/docs/Web/API/Element) you’ve already been using!

### Drawbacks

So, clearly SVGs are awesome! Time to go convert all of our images to SVG, right? Well, not quite. SVGs are _great_ for relatively simple images, but because every single detail of the image needs to be written out as XML, they are extremely inefficient at storing complex images. If your image is supposed to be photo-realistic, or it has fine detail or texture (“[grunge textures](https://unsplash.com/s/photos/grunge-texture)” are a great example), then SVGs are the wrong tool for the job.

### Anatomy of an SVG

Typically, you will not want to create SVGs from scratch in your code. Most often, you will download the file or copy the code either from a website or from an image editor that can create them (Adobe Illustrator and Figma are two popular apps that can create SVGs). However, it’s pretty common to download an SVG and want to tweak or adjust it just a little bit, so knowing what all the bits and pieces are, and how they work is very useful.



# References
https://www.theodinproject.com/lessons/node-path-intermediate-html-and-css-svg