# Books in Browsers

Is a book a web site? A progressive web app? Something more? Does the web need new features to truly support books? What can we learn from experiments with web books, from the experience of EPUB, from the history of browsers? What features/affordances/behaviors are needed for something to be a book on the web?

## What Makes a Book a Book?

Books have a beginning and an end. They are long, and long-lasting. Users may spend dozens or hundreds of hours with a book. Readers may come back an hour, a week, or a year later, hoping to return to where they left off. They may still refer to it a year, or a decade, after first reading it. They may read it dozens of times. They want the book to be available even if the publisher goes away. They want a reading environment that will remember where they are, and adapt to their needs.

But it's not that useful to talk about books in the abstract. 

## The State of the Art: An Evaluation of a current Web Book

When talking about web books, I like to look at Jeremy Keith's [Resilient Web Design](https://resilientwebdesign.com/) (henceforth "RWD"). I think of this as the state of the art for books on the web today.

### Navigation

When you go to the book's URL, you see a landing page with a table of contents. You can click on "Introduction," which comes next. The "begin reading now" link takes you to the same place. Navigation through the book works entirely via HTML links. The reader is gently encouraged to read in sequence. Note that this means there are nine copies of the TOC in the book (not counting those in the AMP version of each page). Even the famously-duplicative EPUB doesn't have that many copies of a TOC.

But, if you're using Opera 12, you can read the entire book just by clicking the space bar. That's because of the magic of `rel=next`, HTML’s way of defining a sequence of documents. Sadly, current browsers don't seem to do much with [sequential link types](https://html.spec.whatwg.org/#sequential-link-types).

### Search

Browsers let me search in the current page, but not in the whole book. I have to go to google and type a search term followed by site:resilientwebdesign.com.

It's much easier in iBooks, where I get a list of every occurence of the search term, across files.

Almost uniquely, for something on the web, RWD does have an index. But if I find "Postel" in the index, it only links to the chapter 4 discussion, not the mention in chapter 5.

### Personalization

If I want to change the background color, or use an easier-to-read font, I have several choices:

1. Use Firefox's Reader View. Sadly, this also removes the navigation, so you can't move to the next chapter without turning off reader view (or guessing the URL and typing it in the URL bar). Safari Reading Mode also removes navigation, but doesn't have customization of font choice or "night mode".

2. It's possible to make global font changes in some browser's preferences.  

3. Create a user stylesheet. This is so simple I could *probably* do it.

4. Fork the project on GitHub and edit the CSS.

### Access

People want unfettered access to their books. The book shouldn't disappear because the proverbial train went in the tunnel, the router broke, or the website shut down. RWD does have a service worker, so the content can be cached. But that cache is at risk of being deleted by the browser itself.

I could try to save the individual pages from the browser interface. But this gets messy quickly, and what if I need a web server to properly view the content?



### Annotations

Human-text interaction has been in incubation for thousands of years. People write in their books, highlight them, dog-ear the pages, use bookmarks. These things have also proved useful for reading long-form electronic texts. Now all I have to do to make these things work on the book is to install a browser extension and sign up for an account with some annotation service. 


## Principles


### 1. A Book is finite, bounded, and ordered.

Chapter two comes after chapter one. There is a beginning and an end. Order matters. 



### Possible Techniques for expressing order and boundedness

1. Using `<nav>` element to describe ordered list of links that make up the publication.

Pros: very webby, needed anyway, just the right semantics.

Cons: not JSON, doesn't work well for more experimental publications?, people keep saying their book doesn't need a TOC.

2. XML. EPUB has an xml package file, that contains an ordered list of primary resources ("the guide" as well as an unordered list of all resource "the manifest")

Pros: Works. 

Cons: XML, some duplication, confusing id/idref structure

3. rel=prev/next/first/last

Pros. Webby. 

Cons. Still need global information. Browsers do nothing with this information.

4. Scope. 

Pros: Webby. 

Cons: Can express membership but not order.


## 2. Retaining State

I read half of chapter three, and then had to do something else with my browser. 

If I can get back to the URL with the forward or back button on my browser, it will remember that I'm halfway down the page because of the back/forward cache. If I have to reload the URL, or if I quit the browser, I'm out of luck.

My ebook reader even remembers where I was after I switched from my phone to my tablet.

### What we've tried

I actually don't know how ebook reading systems do this.



## 4. This Font Hurts My Eyes: Personalization

With regular browser pages, if you want to change the font, you have to figure out how user stylesheets work, and write some CSS. It's not so simple that a C-level executive can do it.

If I switch to a browser reading mode, the situation is better. I might be able to choose a serif or sans-serif font. I can change the background. I can easily make the text bigger. But why is it now telling me how long this will take to read? What happened to the design? [Why did my H2 disappear](link needed)?

All these features are routine in ebook readers. 

### What we've tried

1. Creating menu bar with JS with customization controls, then write style information to document 




## 5. Reading on the Train: Offline

I'm reading RWP on the train, and go into a tunnel (let's pretend we're in Europe, where there are trains). I can keep reading because the book works offline, thanks to service workers and appcache. Good job.

### What we've tried

Service workers! They work. Bigbluehat even found a sneaky way to cache secondary resources without an explicit list of them :)

Issue: what happens when I come back to my book after a year?

Issue: what happens when I have a thousand books saved?





## 6. Mine.

I want to save a copy of the book. Easy on Android, harder on iOS, really difficult on desktop. 

What happens if the server goes away? What if I want to back up my copy of the book? 

### What we've tried

From a SW cache, you can programmatically create EPUB, ZIP, the new Google Web Package, the old Jeni Tennison web package, whatever. 

## 7.  Search

What if I want to find something in the book? I hit command-F in my browser, and I can search the current document, but not the book. 

### What we've tried

I did a prototype where the <nav> element defined the book contents and structure. I created link/@rel=import for each item, and then used HTML imports to add them to the original DOM. Kinda messy, but browser search then works for the whole publication :)

## 8. Show me. Share with me. Cite me. Address me. Point to me. 

A scientist or scholar or student needs to be able to point to anything from an entire book to a single word. 

## 9. Highlights.

Highlights, bookmarks, annotations--the web is working on this. 

## 10. Navigate




### What we've tried

## 11. Bookshelves

I have lots of books. I try to keep them organized. 







## Epilogue: What Have We learned?

1. We have a finite sequence of web resources,

2. With user requirements around 

search, 
personalization, 
annotation,
saving state,
and robust offline support.

3. That's it!






