# Notes from the Essential CSS Module

<!-- If note file have it's own folder, use './../readme.md' path to go one back. However if note file doesn't have it's own folder, you should use './readme.md' path to go one back. -->
* [Click here to go one back](./readme.md).

* When an element touches its parent, its top and bottom margins will merge with the margins of the parent element. We can give padding to the parent element to solve this problem, even giving 1px is solving this! Yeah you can also play with the margins thats another thing but mainly looks like proper solution lies on using padding. Additionally, this is not a problem when using flexbox or grid because they deal with margins and they don't collapse.
    * For example, let's say your sections have a headers on top of it. You will make your sections keep apart with a little spacing. You give a background color to your sections and saw that headers margin, margin top in this and most cases(because there is a content below the heading and that's not creating a problem). First instinct might be to remove the margin top of headers but that's not the best practice for it(though you can remove margin-top for a design purpose because that might cause a different spacing, be mind of that). If we would give enough space, a padding to our section I mean, we would solve our problem. Look at the 'CSS Fundamentals: Challenge #5 - Breathing Room' lesson from Fullstack path on scrimba.
        * Also I liked the solution both I created and the teacher's for that problem that's a good attitude for that problem and a lesson. We wrapped section's content with the fixed size container class. With that structure our background color of the sections were working full width, so we were be able to code somethings both for full width and fixed width.

* Don't write too much code! Many CSS properties have inheritance, be aware of that! Additionally be aware of the default values and know them too.

* When too much element get many different spacing, it gets hard to debug and understand the situation. I suggest you to centralize your margins to less element as much as possible because it can make debugging and coding easier, but if this is creating a bad designed code, then don't do it.

* Pseudo Selector. ':hover', ':active', ':focus' are a pseudo selector examples. ':focus' represents the element that browser is focused, is on. So if you are tabbing with the keyboard and came to an element, focus is valid for that element for the time you stayed focused. Do not remove the outline property of the focus pseudo selectors because that is making the website less accessible.

* Don't mess up with the order of selectors. For example think both an active and a focus selector for an 'a' element. You should keep the focus is on the top of active, if not, you messed up and ':active' can't work then.
    * Link (a), Visited, Hover, Active. This is the order from top to bottom you should follow in css file, if not, code will be messed up. You can code that like 'LoVeHAte' mnemonically.
    * Using these pseudo selectors and making the website more understandable for the actions is crucial.

* We have different sections in website and what proper action can we take when we want to align them in a position. For example think of all the different sections in main, and you want them to have same spacing alignment from right and left. A proper solution would be creating a container class and wrapping the content of those sections with a div with container class, each one of them. We can give a width and center that div, that way we can achieve that. Creating a seperate container in parent and putting the elements of parent inside of that container is crucial in the interest of some properties(like background-color) that needs to apply themselves to the all space(for example 'width' in our example right above).

* Don't repeat yourself. For example for CSS, you can group CSS selectors for common properties that will be applied.

* [**CSS Specificity**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_cascade/Specificity) is important. You can give an element a property with very different selector combinations and they will different order of importance weights for browser. CSS is based on weights and the property with the highest weight selector will win.
    * For a very basic understanding, id selector is heavier than class selector and class selector is heavier than an element selector.
    * Let's think in a point like structure for the weight of selector specificities. More points means more weight therefore they will effect. Then:
        * element selector gets 1 point
        * class selector gets 10 points
        * id selector gets 100 points
        * To calculate the specificity when using a compound selector, all you need to do is add the points of selectors together.
    * Not using compound selectors or using them as less as possible is a good approach. Because CSS files in real projects will get complicated and calculating the specificity of your selectors will be really annoying. Moreover, you will really wish your file to be simple, easily understandable, and well designed. So, do it like that.

* Ids are generally used for JavaScript side instead of CSS. But there is no such a rule like that, that's just about personal taste.

* Compound Selectors have more specificity then just styling an element with it's pure element selector. An example: ".footer-links a{color: blue;}"

* If you code a property in more than one place, and if they have same specificity weight. The one at the most bottom of the code will effect the website.

* In CSS, "," comma is used to seperate different selectors.

* !important keyword. Deal with the problem at it's root, don't use the !important keyword in for a bad lazy reason and disrupt the natural working way of your code. How can it be useful then? It might be useful about a topic on accessibility. A user might want to manipulate the websites font size, color theme etc and use a widget, an extension. That additional code piece will want to respect user's choice and apply them strongly, right? Well in a case like that !important keyword is really useful. So there are legitimate uses for it and you should be aware of it, but don't use it as a shortcut!

* Buttons VS Links(meant anchor tag for HTML). Think of a button, when clicked, leads you a page. That's called navigation and buttons shouldn't be doing that! This is an accessibility issue. Speed readers and assistive technologies rely on the developer making the right decisions. So, when should I use a link, and when should I use a button?
    * Note: Links can be shown as buttons with CSS, that's not our problem here! Our those elements with the right purpose in the code.
    * Links are for navigation, buttons are for interaction(opens a model, for example).
    * Buttons for actions that affect the website's front-end or back-end. We are generally using JS for buttons to reach our purpose.
    * Links for navigation(linking to another location) to somewhere on the same page, within the site, or elsewhere on the internet.

* We can set height, margin top and bottom of block elements but **we can't set height, margin *top and bottom* of inline elements**. Inline-block elements will also sit side by side like inline elements when there is enough space, **though we can set height, margin *top and bottom* for inline-block elements**.
    * div, p, h1 are examples for block elements
    * span and a are examples of inline elements
    * button and input are examples of inline-block elements
    * Because the inline elements don't have a height, giving padding top and bottom will work but not affect the website flow, so therefore it will create a weird overlap if there is another close element.

* **Note**: CSS consolidation is the process of combining multiple CSS files into a single file to improve website performance by reducing loading times. This technique minimizes the number of requests a browser must make, leading to faster page rendering. (This note is taken from duckduckgo's genAI search assist)

* **Advice**: Let's say you have a card structure in your page, but with various types. That various types has different coloring etc. We are having this kind of situations most of the time for many things. In this situation, you should add a main class and a modifier class. You can share the mutual properties with main class, modifier classes are for the variations of it. This way, CSS will be more clean, readible and maintainable.

* Most of the time, [overflow](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/overflow) happens when there's too much content for the available size of the container. It's an intended behaviour and designed to prevent data loss, for content to be visible even if container is not enough.
    * Problems overflow can cause:
        * Layout issues: It is disrupting the intended layout. It can create overlapping on other elements and make content unreadable.
        * Accessibility concerns with users changing text size.
        * Aesthetic Disruption: Visible overflow can make a website look messy or unprofessional.
    * overflow hidden can lead to inaccessible content.
    * overflow scroll will add a scrollbar to the container *even if there is no overflow*.
    * When you set overflow to scroll, browsers with visible scroll bars will always display the scroll bars or it's corners for that container, even if there's not enough content to overflow.
    * Overflow auto will show the scroll bars only when needed
    * Scroll bars are operating system specific, as well as browser specific to some extent.
    * overflow-x and overflow-y properties control the overflow behavior seperately for horizontal and vertical content to some extent. **Warning**: You can't give one of them hidden and visible to other, idk why but it is not working with that value couple. Though you can give one of them scroll and hidden to another, that works.

* You shouldn't use float property for layouts because now we have advanced layout methods like flexbox and grid. You can use to place images around paragraphs and such basic cases like that. 'clear' is also using with float.
    * **flow-root** display property will strech the container around the thing that is floating. An example use case: You have a text and an image in a div with black borders. Image is floating left. There is not much text content and therefore image is overflows the border. You can fix this situation with flow-root then. This works because when we use float on an element, it actually takes it outside of the **flow of the document**. What flow-root does is, it ensures the floated element is contained inside the parent element where display flow-root set. So that element is rooted in the flow of it's parent and no longer outside of the flow.
    * Other usage of floats:
        * Drop caps
        * Floating quotes (idk what this meant exactly)
        * Floating information boxes (idk what this meant exactly)

* This resource is **important**: [WebAIM, web accessibility in mind](https://webaim.org/).
    * [Click to go to a video about it](https://www.youtube.com/watch?v=i9ilul5fihw).

* There is a video that I saw a value in it. It's about making projects. There is a vision and a mindset in it, and that's really valuable. That is seperating valuable people from the people that just do shallow works and not understand why are even doing it. [Click to go to the video](https://www.youtube.com/watch?v=tr4saJGic4o).

* https://stackoverflow.com/questions/34552116/why-doesnt-margin-auto-center-an-element-vertically/34552265#34552265

* Instead of styling your paragraphs font-size, give that to body. That would be a good practice, because paragraphs are generally taking the default font size, with giving a default good font-size to body, we can also cover other kind of things we may forgot. I mean, the thing here is, giving a general font-sizing to body might be better than styling the paragraph like things.

* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas

* header tag is shows the introductory first top part of the website. It's often for the logo and navigation but we can also use for the top introduction content of the page like a first section.

* The "inverse" is a common class name that used in HTML that typically refers to a class that applies to invert the colors of an element, effectively switching light colors to dark and vice versa.

* Creating utility classes for common problems is a good solution most of the time.

* Remember, all text elements come with spacing on the top and bottom of them by default. **Warning**: A big part of styling websites is just fixing this little spacing issues, and a lot of it comes from your text. So therefore there might be lots of work to do about spacing and some other little touches for text elements.
    * removing margin-top for headers and margin-bottom for paragraphs is sometimes a common solutions for common problems but I'm not saying do this all the time everywhere!

* For links (a tags), we might have some problem with styling and doing somethings with them if we don't give an href. For a temporary href we can give them # sign.

* While styling links to a button look. Don't use width or height to create the size. Use paddings. But why? So setting actual width and height is dangerous. Always do things like this with padding and that way, no matter how long or how short the text is, it's always going to work. Also you won't deal with problems like centering the text. Also you will want to change their display property. Links are inline, you should give inline block to them as display property. Why not block? Because if you gave display of block, you would run into an issue or it would stretch the full size and it wouldn't be centered anymore even if you gave it a width.
    * make sure to include the `:focus` state alongside `:hover` for better accessibility.

* Understanding the box model is a fundamental important thing to know.

* Block level elements will fit their parent.

* The <time> HTML element represents a specific period in time. It may include the datetime attribute to translate dates into machine-readable format, allowing for better search engine results or custom features such as reminders. Text is from [mdn website](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/time).

* In CSS, while making a selector, every time you add a space, you are creating a more complex CSS selector and **more importantly you are raising the level of specificity**. You have to be careful with it. You might have an *unintended consequence* about it. Keep that in mind.

* Instead of creating mini spacing among elements, think of using gap for appropriate places. That might fit better than a padding or margin solution. For example, creating gaps between header navbar elements. Most of the time we are using flex for header navbar styling, so, gap will work then, and it will just give space between the elements, that's perfect for most of cases.

* When we reflect an image with CSS. That creates a huge accessibility issue, because Assistive Technologies will not be able to express the meaning of that image or AT tools didn't structured for that kind of thing, and we can't give an alt attribute to an image when we add with CSS (with background property). That's why the best way to display an image that is forming an essential part of your content, is to use an HTML image tag and give it a description using 'alt' attribute. That's not needed purely for decorative image which has no relation to the content. If you find yourself in a situation where using an image tag is not possible? Find the element you give the image with CSS and give that element a 'role="img"' attribute. This role attribute with img value will flag to the assistive technologies(for example screen readers) that this element(div for example) is behaving as an image. We should then give aria-label attribute to our element, and our value will be the image's description(it's equivalent to the alt attribute but for CSS images). After this, most screen readers will take that entire div which has the role of the img and treat it as one big image. Therefore they will actually not access the individual content which is inside the div. So for example if there is a text, like a header or a paragraph for example, screen readers will not look for that content and therefore not read it. Because of that, **we need to make sure our aria-label is covers the entirety of this div**.
    * An example aria-label text where our element has a meme image of a smiling dog and there is a text that writes 'When the cat gets blamed for something you did' on it. An example proper aria-label text would be "A cheeky smiling dog with text saying 'when the cat gets blamed for something you did'."
    * As a tip: put a period at the end of your sentences, that might help and give a break to the screen readers.

* We can position an element in a 9 different spot with using margin auto values for different axes. In an axis, if you just give margin auto to the one side, element will be slide to the side that you didn't give margin auto.
    * Think of a scenario where you have 5 flex children. You want to move one of them to a corner. I would usually go and take other four in a div but **I learned that there is a better way**. We can use margin: auto to move it in this scenario.

* When we use [position absolute](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/position#absolute) for an element. That element gets out of the document's normal flow and the element is positioned relative to its closest positioned ancestor (if any) or to the initial [**containing block**](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Display/Containing_block#identifying_the_containing_block). We might think that element will still position itself on somewhere of it's parent's area even if it's out of flow, but that won't happen unless we give a property value like 'position: relative'(this is the most common one).

* An Accessibility Tip: Think of a weather forecast map, and there are two emojis on different areas about temperature and heat quantity. We could give an alt text to the map image and screen readers can translate emoji into words. However, this is not a good solution from an accessibility perspective. If this were a complex map with several weather symbols and temperatures, things would get very very confusing and it would not be clear which emoji was over which area. It would be better to dynamically create the forecast image and then add alt text which describes not just the map but the entire forecast. That would be a much better solution. As a manual solution, we can give our weather forecast parent element an img role and give a detailed weather forecast information, this would make it more accessible and smartly designed than before.

* When we take a block level element like this div and we set it to position absolute, it takes on some of the behavior of an inline element and stretches only to the width needed, to hold it's content. But of course, if we preferred a special width look, we could just set a width property we desired.

* **There is a small and weird problem, a problem that taught me more than I could imagine, what is it?** When we add an image with img tag, there is a little space below. But why we have a space there? I felt a discontentedness to the workaround solutions comes from stackoverflow and geeksforgeeks, I wanted to understand it deeply and grasp it. I wanted to see the reasoning behind solutions and really be able to understand which one would fit into which situation. Also, with this excuse, I wanted to unveil not so familiar topics and learn. Moreover I'm curious about tinkering the real documentations, specifications, standards, and taste the information from the first hand. So I read pieces of CSS specifications where I needed from [CSS Working Group](https://wiki.csswg.org/) and also use MDN Web Docs. MDN Web Docs guided me to the specifications I needed but also make the process easier to grasp sometimes.
    * **ANSWER**: Actually, answer lies on the deep understanding of many CSS concepts, I did read and visit many different place and also cite them right below too. After reading them, I ended up on the [initial(default) value of the vertical align property](https://drafts.csswg.org/css-inline-3/#transverse-alignment), I intentionally searched and find that in specs because I knew probably that was the root reason and yes, that was right! "[inline-level boxes are aligned to each other along the block axis, typically by the baselines of their text.](https://drafts.csswg.org/css-inline/#model)". So we have something called 'baselines' and we align our content according to those. "[A baseline is a line along the inline axis of a line box along which individual glyphs of text are aligned.](https://drafts.csswg.org/css-inline/#baseline-intro)" 'vertical-align' property's initial value was baseline, and **we have another line below that, and that 'bottom' baseline at down below is the baseline that creates our extra little space below!!**. We can play with the vertical-align property and make our content's position on bottom, that way there would be no other extra space.
    * Some of my research notes with citations from valuable source links:
        * A quotation from the 'CSS Inline Layout Module Level 3' document's 'Baseline Alignment' title: "While most CSS formatting contexts position content by aligning boxes with respect to their container’s edges, inline layout positions boxes in the block axis by aligning them with respect to each other using their baselines." Resource link: ["CSS Inline Layout Module Level 3" document](https://drafts.csswg.org/css-inline-3/#alignment)
        * Very useful on topic -> [Block and inline layout in normal flow](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Display/Block_and_inline_layout), [Introduction to formatting contexts](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Display/Formatting_contexts). Second one is for understanding the first one better.
            * Everything on a page is part of a [formatting context](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Display/Formatting_contexts), or an area which has been defined to lay out content in a particular way. A block formatting context (BFC) will lay child elements out according to block layout rules, a flex formatting context will lay its children out as flex items, etc. Each formatting context has specific rules about how layout behaves when in that context. Inline formatting context is deciding how the display inline or inline-block elements will be formatted in the page.
            * A beautiful quotation note from the first one: "Elements participating in a BFC use the rules outlined by the CSS Box Model, which defines how an element's margins, borders, and padding interact with other blocks in the same context."
        * [CSS Inline Layout Module Level 3](https://drafts.csswg.org/css-inline/#model)
            * "In inline layout, a mixed, recursive stream of text and inline-level boxes forming an inline formatting context within a block container are laid out by fragmenting them into a stack of line boxes. Within each line box, **inline-level boxes are aligned to each other along the block axis, typically by the baselines of their text.**"
        * [In flow and out of flow](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Display/In_flow_and_out_of_flow) -> "All elements that are in flow will be laid out using this method."
        * [CSS inline layout - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Inline_layout) -> this also might be helpful around the topic
        * Note: "Line boxes and inline boxes and inline-level boxes are each different things! See [CSS-DISPLAY-3](https://drafts.csswg.org/css-inline-3/#biblio-css-display-3) for an in-depth discussion of box types and related terminology." Source: [CSS Inline Layout Module Level 3](https://drafts.csswg.org/css-inline-3/#line-box)

* The questions like 'why we cannot use vertical margin' and 'why inline elements can't use some properties' are explained here: [Formatting Contexts](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Display/Formatting_contexts#inline_formatting_contexts)
    * Quotation from the "Inline formatting contexts" title: The box model does not fully apply to items participating in an inline formatting context. In a horizontal writing mode line, horizontal padding, borders and margin will be applied to the element and push the text away left and right. However, margins above and below the element will not be applied. Vertical padding and borders will be applied but may overlap content above and below as, in the inline formatting context, the line boxes will not be pushed apart by padding and borders.