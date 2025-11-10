 # Notes from the Accessible Development Module

<!-- If note file have it's own folder, use './../readme.md' path to go one back. However if note file doesn't have it's own folder, you should use './readme.md' path to go one back. -->
* [Click here to go one back](./readme.md).

## ATs - Assistive Technologies

* Screen readers
* Speech recognition software
* Screen magnifiers
* Alternative input devices, designed for people with motor skill impairments.

## The Accessibility Tree
* Accessibility tree is a part of website's DOM. All accessible objects are created in the accessibility tree for each DOM element that needs to be exposed to assistive technologies.
* Use semantic HTML in proper way, this helps.

## Accessibility Testing
* Using AT
    * Screen reader
* Contrast Checkers
* Automated Tools
    * Lighthouse in Chrome
    * Accessibility Inspector in Firefox
    * aXe
* AI assistants
    * You can interact and get help from AI assistants to improve accessibility

## WCAG - Web Content Accessibility Guidelines

* These are the set of recommandations developed by the World Wide Web Consortium (W3C) to make web content more accessible, especially for people with disabilities.
* Our goal is to reach the AAA level every time we can, it is the best level of accessibility for the WCAG.

* AA requirements
    * 4.5:1 contrast for normal text
    * 3:1 for large text (>=24px)
* AAA requirements (our goal)
    * 7:1 contrast for normal text
    * 4.5:1 for large text (>=24px)

## Notes along the course

### Titleless notes
* Use texts and shapes with the colors. Make it more understandable and accessible with combining them.
* background-blend-mode with background-color. This two property is useful when the background image is preventing our contents accessibility.

### About the accessibility of Images
* Add *clear and concise* **alt(alternative) text** for your image contents. Do not specify to your alternative text a part like "An image of.." because screen readers is already doing that, you shouldn't do that, just explain the image. Try to end your alt text with a dot.
    * If an image is purely decorative(for example an abstract image for the website background that is not important for the visually impaired person, icons combined with text is also an example), we don't need to write any descriptive text as the value for that attribute. **We should add an empty alt attribute in this situation** because without it, a screen reader may read out the image file name instead and that can be disturbing. Adding the decorative images with CSS might be smart because you don't have to deal with alt text because screen readers ignore those CSS images, because that image isn't part of the HTML DOM as an actual content then.
    * If the image has a label or adherent text that describes the image, an alternative text also becomes redundant. Do not misunderstood, text should be on HTML content, not on the image as image in this situation!
    * Who this help:
        * People with little or no vision
        * People who have turned off images
        * Search engines like Google

### About links:
* Links should be recognizable as links.
* If you're making a card a link then you shouldn't just wrap with the a tag, that would force the visually impaired person to read all of the text inside of the card before saying it's a link. Also with this bad implementation, images in the card may not be readable too. Instead, the link should be positioned inside the card without wrapping any text. With a little CSS trick, you can make card clickable and more understandable that it's a link. Also, use *aria-label* in this situation too, it would be good. Suggestion, make the text of the link bold and your link text should be explanatory independently. Don't do "click me" but do something like "Check out more of their awesome art by clicking this card.".
* They should have non-ambiguous text. Examples of bad practice are "click here", "more", "continue", etc.
* Know how to use the properties like aria-label and other things about accessibility
* Put a dot in the end of your explanations. This would help them to take a breath and serve a better experience.

### About Labels:
* According to the WCAG, the accessibility guidelines, placeholder text is not an accessible replacement for the label element. The placeholder should only be used as a brief example of the text to be entered, mainly because of inconsistent support for screen readers. Try to use both a label and a placeholder that gives an explanatory example about input field.
    * Note, if your design is really focused with not using labels somehow, try to change that design if you can, if you can't, try to add labels in an invisible way that screen readers can use. But if you can, add the labels, because we are trying to be accessible to everyone. Adding a visible label would also help the people that don't visually impared, remember!
* Associate the labels with input fields. So the important note here is, you should know how to use semantic HTML in the right way and always make your designs in an accessible way.


### Radio buttons:
* We should know that the radio buttons could have even more semantically correct HTML than they currently have. We should use the fieldset tag to group the set and legend tag to provide a context for screen reader users.

### About semantic HTML tags
* Use semantic HTML tags, for example 'main', 'nav', 'section', 'footer', 'button' and so on. When we use semantic HTML tags, our changes manifest in easier navigation using assistive technologies like screen readers because they can quickly identify these landmarks and provide shortcuts or navigation commands to jump directly these sections. For example, a user can skip directly to the main content or quickly access the navigation menu. This reduces time and effort required to navigate through unneccessary content, enhancing the efficiency of the user experience. This also provide a better communication/accessibility among the software technologies like search engines and many other softwares that somehow interact with our web page.
    * Additional note about why this helps to the Search Engine Optimization: Search engines index our websites with their technologies and want to put that website to the place where it belongs to when someone search something. So while indexing our website, search engine also takes informations from our website and tries to understand what is it all about. It is doing that with the help of semantic HTML, how can it understand your website if didn't use semantic HTML. Then how can search engines understand which tag contains which information?
    * Use unordered lists for your consecutive items like nav items on top your page or any other consecutive ones. 
* Text inside links and buttons actually act as labels and providing an accessible name in the browser's accessibility layer. If, for whatever reason, we want to create a custom button without using the button element, we would need to add a so called *aria-label* attribute that substitutes the regular button label.
    * **Important Note**: People may think why do we need the use default semantic html elements when we can create our own special ones. Here's the thing, using the semantic elements help us keep ourselves on the way of standards. We have many different kind of standards to keep web more meaningful and accessible. With semantic HTML, we are making our design follow the standards more properly. For example, a semantic button element has built-in accessibility features, but when we create a button without the semantic button element, we need to use aria-label to give that accessibility features. W3C, WHATWG, ECMA International, Wasm, these are some popular organizations and standards that help us create an accessible web. Accessibility isn't just for disabled persons. Every piece of the web is interacting with each other on many aspects, if we don't have a known structure, a standard, then how can we sustain and keep up this web alive. Accessibility is meant for every person and software.
* Use the assistive technologies, look up to how search engines work and how other softwares communicate and consume our website to understand. This way, you can have a grounded experience to how to program your website!

### About text size
* Use rem instead of px. Users can change the browsers default font size, your website's font-size change with that browser change when you use rem, but pixels are fixed values.
* Because I said try to be AAA on WCAG level. I'm not mentioning evey detail of WCAG for every 'About..' note here. Here, I just add additional useful notes.

### About headings
* Use them correctly and properly! One web page must have one h1 and other tags come in logical order. Headings work like the way of book contents work. 

### ARIA - Accessible Rich Internet Applications
* ARIA is a set of attributes that you can add to HTML elements to provide more context and information to assistive technologies. It helps fill in the gaps where HTML's native semantics fall short.
* We want to use ARIA when we're creating a UI component that doesn't exist in HTML. We need to provide additional information or context to assistive technologies, which can't be achieved with HTML alone. *However*, avoid using ARIA if the same functionality can be achieved with native HTML elements.
* 'role' attribute defines the role of an element to assistive technologies.
* 'tabindex' attribute allows to control keyboard accessibility.
* 'aria-checked' attribute indicates the current state of checkboxes and similar widgets, with possible values of 'true', 'false' or 'mixed'. It helps assistive technologies convey the state of these elements to users.
* When we dynamically change the parts of a page, this changes are visually apparent to sighted users but they may not be obvious to users of assistive technologies. ARIA live regions fill the gap and provide a way to programmatically expose dynamic content changes in a way that can be announced by assistive technologies. We should only use live regions for essential updates, avoid overuse of focus management, as it can easily disorient users if not done logically.
    * 'aria-live'. With this, we can specify how important this change. Screen readers translate this to it's users. 'off' is default one. 'polite' is common one, we are using for updates that is important for user to receive. Screen reader will be announce this change when there is a natural pause in their speech. 'assertive' is another value, it should be only used for time sensitive or critical notifications that absolutely require the user's immediate attention. Generally, a change to an assertive live region will interrupt any announcement a screen reader is currently making. As such, it can be both annoying and disruptive and should only be used sparingly.
    * 'aria-controls'. Use it for the responsible element for change. Give the element that will come out an id to create a relationship.
* Accessible focus management is a practice of using programmatic focus changes to enhance comprehension and usability of a website. Focus management benefits a variety of users including those using assistive technology (AT) such as a screen reader, those using a keyboard to navigate, and those who may have increased the zoom of their browser to make reading more comfortable. This practice involves controlling the browser's focus in response to certain user actions. Common use cases are when opening modals or menus, after completing actions like focus submissions to bring focus to relevant content, to maintain a logical flow of navigation.
    * [cloudspace.design focus management principles](https://cloudscape.design/foundation/core-principles/accessibility/focus-management-principles/)
    * After a live region triggered, adding a focus function for the element that user needs to go at it is one of the fundamental practices. For example, directing the user's focus to the 'back to home page' link after they signed up.
* We should always think about the action we're expecting the user to take and then ask ourselves if all our users can be expected to take that action. And if we come to the realization that, for example, not all users use mouse cursor to navigate an application, we should adapt the behavior of our app accordingly.
    * Javascript events are fundamental to interactive web experiences. However, relying solely on mouse specific events like mouseover or mouseout can exclude users who navigate with keyboards or touch screens. <u>**We should consider using more inclusive event handlers.**</u>
    * Built your website in an accessible way about every needed aspect.
    And you can play with it's opacity and make it visible that way to the sighted users
* Be aware of text contrast and fix them, for example placeholders are natural fixable things.
* You can make accessible navigation management for your website. For example adding a skip navigation link(you can hide visually when not focused).
* Don't forget, you can be creative and create good solutions, make life easier about accessibility!
* 'display:none' and 'visibility:hidden' removes the element from accessibility tree, be aware of it. Because when you use this kinda method to remove something visually. You are removing all from the accessibility tree!
    * Instead of visibility hidden or display none, we should consider techniques that visually hide content but keep it in the accessibility tree. Some common methods are:
        * Position the content off screen using CSS (i.e. chatgpt sidebar)
        * Make it invisible with using opacity, and if you want it to don't take space, you can do that with CSS too, but be careful about being the item accessible.
    * About modals: While there are genuine good use cases for modals, many modals are inaccessible, confusing, confusing, negatively affect the user experience, all while being unnecessary. And when building apps, we should always ask ourself the question: does this really need to be a modal?