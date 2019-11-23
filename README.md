# Week one homework

## Building a website using only HTML and CSS, to recreate a site from an image

### [Link](https://agtravis.github.io/homework-week-1/index.html) to uploaded webpage (most recent commit)

## First Commits

My very first commit was simply to upload the blank files, and check that the repository accepted them.

Next, I wanted to code styling elements of the css first. The instructions recommended writing all the HTML first, but with some prior understanding of a lot of these concepts, I wanted to achieve some basic design elements before writing the content. I started by coding the CSS styles provided in the brief.

Next in the HTML I wrote a very basic `<header>` and checked the styles matched the brief.

## Header

I wrote my links out as a `<ul>`. I have chosen to do it this way to make this collection of links more of a cohesive unit (as opposed to a custom `<div>` with `<a>` elements contained).

In the CSS I used ```float``` to position the header title and links as I wanted them, floating the title left and the links right, and setting their widths to add up to less than 100%. *NOTE: I later edited this after learning about ```flex```.*

I applied more style elements until I was happy with the header aesthetic, in comparison to the brief image. I also made the header ```fixed``` position to keep it always on top.

*NOTE: There **IS** a ```z-index: 2;``` property applied here, I coded this later on in the commits, and I will explain my reasoning at that point.*

## Main Page Content

I split the main content box in to two ```<div>```s, one for the sub-header, and one for the actual content. Within the content I floated the image left, and then grabbed some Ipsem Lorem for the content to make sure it wrapped the way I wanted it to.

I also applied styling to this HTML, especially with focus on the borders and dimensions (width) of everything. Some styling I decided was inconsequential if I deviated from the brief - an example of this is I increased the margin between the right side of the image and the text.

In order to make sure that the main content clears the fixed header, I applied margin, and increased this in dev tools in Chrome until I thought it looked good.

## Working Links

At this point I was ready to go ahead and make multiple pages and make sure they all linked correctly together, at least as far as the three HTML pages detailed in the brief. I did this by literally copying all the HTML from index.html, and pasting it in to the other two files. Then I removed everything in the main content div below the sub-header div, and left placeholder text. On clicking between the links, it now appears as though the header is not changing because of the identical HTML.

*At a later date I expect to be using something similar or equal to the concept of **views** to write a header. From this point on if I make changes to the header in the index.html, I will need to apply those exact changes on each page. By **views** I mean something similar to how the CSS can be written in a seperate file and accessed by multiple HTML pages at once, therefore only needing to write the HTML once.*

I then wrote and styled a footer as well.

## Adding/Converting to ```flex```

After learning in class about the concept of ```flex```, I immediately deployed this to update where my use of ```float: left/right;``` combined with ```width: #%;``` was considered deprecated code. Specifically, in my header where I had floated the ```<ul>``` right, I now removed this property and applied ```flex``` instead, using ```flex-grow: [1/2];``` to define how much space I wanted each section to take up.

I was also having 2 issues with borders.

![Border Issues](https://github.com/agtravis/homework-week-1/blob/master/assets/images/border-issues.PNG)


1. The title background is sitting on top of the border between the header and the main content, created an *indent* which looks rather unpleasant and unfinished. I could not get this to disappear, even by inserting an empty ```<div>``` with a ```clear: both;``` property attached.
1. This may not be perceptable to most people, but I have pretty good eyesight, and this was bugging me - the border of the main content gives the div a new increased width, which means it no longer is perfectly in line with the width of the header. This would be easily fixable if I changed the width of the main content or header, but I didn't want to do this since the brief was very specific about the width *NOTE: 960px was the brief, I have 20px of padding in the main content, so the ```<div>``` is actually 920px. By the same logic I could therefore set the width of the ```<div>``` to 918px, but to me that is an imperfect solution.*

![Border Issues: Fixed](https://github.com/agtravis/homework-week-1/blob/master/assets/images/border-issues-fixed.PNG)

1. Elrey helped me with this one. He suggested giving a margin to one of the offending ```<div>```s. I applied the margin, and played with the amount using the dev tools in Chrome to get it perfect, turns out it was ```0.5px```. I do have one concern - I understand using a half a pixel measure on a high-definition monitor means that it is not a literal half pixel, however that means there may be a small-screened mobile device that might recreate the issue. I'm happy to cross that bridge when I am better versed in responsive HTML.
1. I used Google to help with this. I discovered that if I used ```outline``` instead of ```border```, I could then go ahead and apply ```outline-offset``` to place the border technically *inside* the ```<div>```.

## Scrolling

I decided to add some extra content ```<p>``` on the 'About Me' section to enable scrolling to see how the webpage behaved. All good and as intended.

## Portfolio Page

Everything here is obviously placeholder content. I think a 3x3 grid looks best here, based on increasing what is showed in the brief, so I have coded nine links in my HTML. Each link has the following syntax:

```<a class="no-underline" href=""><img src="assets/images/kitten.jpeg" width="250px"><p class="project-link">Project Name 1</p></a>```

The ```class``` removes text decoration (the default underline), the ```href``` is blank, and the ```width``` attribute is set to ```250px``` right now, to auto shrink all images to that size. To keep proportions in check, both of the images and the grid, I will need to ensure all replacement images (for when I have real content) are the same ```height```.

The containing ```<div>``` is set to ```{display: flex; justify-content: space-between; flex-wrap: wrap;}``` in order to align the items in the grid in an attractive manner.

Next, using the selector ```div#portfolio-links a``` to select all the links specifically within this ID, I set all their positions to be ```relative```, so that I can position the children of these elements ```absolute```ly within them. I also assigned those links a class with ```{display: flex; justify-content: center; align-items: center;}``` applied to get the text positioned correctly.

*NOTE: This is where I now realized I had to apply a ```z-index``` to my header. For some reason unknown to me, related to the flex and relative positioning I assume, when I scrolled now, the images appeared in front of the fixed header, but not the rest of the content. ```z-index``` was a quick way of fixing this, and as long as I apply it to the header and nothing else, I hope it won't have any knock-on unintended effects. I can revisit this if necessary.*

![Adjusting z-index](https://github.com/agtravis/homework-week-1/blob/master/assets/images/z-index.PNG)

## Contact Page

The contact ```<form>``` is very simple. In the HTML I have three fields:

1. **Name**  ```type="text"```
1. **Email** ```type="email"```
1. **Message** ```<textarea>```

I have defined sizes for each of them to fit the design of the page, and also applied a ```name``` attribute which I know will be useful if I end up making this form do anything with JavaScript or something.

The submit button is not a ```<button>```, but just a ```<a>``` styled to look like a button. This has ```flex``` applied to it to position the child-node (text).

The form itself has minimum CSS applied to it, just some margin to pleasantly space it out.

## Comments

In order to a) help me understand and remember my code better, and b) explain to anyone reviewing my code why I made certain choices, I have left detailed comments. Especially since this is an assignment.

## CSS Reset

At this point in my creation, there were some mild aesthetics that weren't lining up for me, especially when the browser was not full screen. Using dev tools in Chrome I discovered that the browser was applying some default styles, so I wrote some CSS to overwite this. In the very next class I learned about the concept of CSS Resets, so this was interesting to learn about. I decided not to reset all the CSS, but I included a commented out link in my ```<head>``` just as a reminder.

I also fixed the position of my background so it wouldn't scroll - and at this point I understood why these should have been two seperate commits to github.

## Finishing Touches

At this point I am very happy with my work so far, and have only really made minor adjustments or made attemps to incorporate ```flex``` more.

After learning about semantic tags, I updated those, however I think I prefer to just use ```<div>```s for the future, unless this is explicity defined as incorrect practice. My reasoning would be that if I am giving my containing divs an ID, it would most likely reflect the semantic tag in essence and creates an extra layer of identity.

I tried, and did a lot of research, to try to remove any references to ```float``` in my code per an updated brief, however the only thing I am now using ```float``` for is actually the intended purpose, and that is to change a ```block``` item to ```inline``` and therefor enable ```<p>``` to wrap around ```<img>```. 

![Border Issues: Fixed](https://github.com/agtravis/homework-week-1/blob/master/assets/images/float-img-left.PNG)

## Future Endeavors

As homework briefs are applied and my understanding increases, I expect to add the following features or technologies:

1. Responsive features. Layout adjustments for smaller screens, from reducing margins/font-sizes etc. to displaying content in different arrangements.
1. Obviously when I have projects I can actually link to them, or create more ```.html``` pages describing them, and adjust the portfolio page accordingly.
1. The contact form will be active. I expect to eventually utilize multiple technologies here: JavaScript/jQuery or some scripting language to make the form active; possibly implement a regular expression to check the email address; create and communicate with a database to store this information; actually make the form send an email.