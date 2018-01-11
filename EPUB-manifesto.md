# If it ain't broke: The Past, Present, and Future of EPUB

Consider this HTML fragment:

```html
<font color=red>hello</font>
```

Firefox 57.0.4, released last week, knows exactly what to do with this markup, even though the `font` element was deprecated twenty years ago, and removed entirely four years ago. The text is indeed red. *On the web, the old and the new coexist, if uneasily.*

`font` was a mistake. People realized that, and specs changed. But why does `font` still work? Because of one rule: **don't break the web**. If even three in ten thousand web sites use a feature, and removing a feature might render those sites unreadable, browsers won't remove it. The web has to be careful, because mistakes are permanent. 


Twenty years into the age of ebooks, our community is trying to figure out what to do with our mistakes. But we don't even agree on what our mistakes are, let alone what to do about them. Was EPUB 3.1 a mistake? Was `ncx`? Was `epub:switch`? At least we're finally talking seriously about backward compatibility, about how to “manage” change.


---

### SIDEBAR: 3.1 vs 3.02 vs 3.2 vs 3.1.1

Late last year, work began quietly on a proposal to undo some of the changes in EPUB 3.1, create a new EPUB 3.0.2 spec, and then abandon EPUB 3.1. The stated motivation was for EPUB 3.0.2 to be entirely backward-compatible with EPUB 3.0.1—that all existing EPUB 3.0.1 files would automatically be valid EPUB 3.0.2s. I believe the unstated motivation was for existing files to be automatically compatible with the "newest" version of EPUB, without having to make any changes (especially to the `package` version attribute).

I consider most of the changes in 3.1 to be welcome—removing unused and unimplemented features like `epub:trigger` and `epub:bindings`. 

---

We work in publishing because we love books. We work with ebooks because we're idealists, as well as gluttons for punishment. We are full of frustration with the present and hope for the future. We want things to be better; we want change; we need change.

But does anyone else want change? Laura Brady wrote an article here on the [slow adoption of EPUB 3](http://epubsecrets.com/on-the-slow-adoption-of-epub-3.php) just last month; the very same EPUB 3 which became an official recommendation in October of 2011. After more than six years of EPUB 3, EPUB 2 is alive and well. Even my employer, one of the largest publishers in the world, makes EPUB 3s which are as close to EPUB 2 as possible. The `ncx` refuses to die.

There are two problems. First, EPUB 2 is often "good enough". Most books are better without video. It's hard to use some HTML5 features due to poor implementations in older reading systems. Many of the benefits of better accessibility are more theoretical than actual right now—how many reading systems do useful things with `epub:type`? 

Second, the lines between versions of EPUB are often blurry. Many of us remember fixed-layout EPUB 2, or EPUB 2 with audio. Our EPUB 3's have ncx files. Reading system support is far more variable than the specs are. Most EPUB 3.0.1 files are indistinguishable from EPUB 3.0 files.

The question remains: how do we move forward? Perhaps we can learn something from the web, and make old and new coexist more easily. But we need to be aware of how different EPUB-Land is from Web World:


1. Unlike the web, the EPUB ecosystem depends on formal validation. One interesting aspect of this is that many formally invalid EPUBs actually work. Many reading systems already support `package version="3.1"`. You can use regular HTML without the "X" in many places. And, of course, we all know about the many valid EPUBs which don't work

2. There are many fewer browsers than EPUB Reading Systems, making research, testing, and QA much harder, and sometimes impossible.

3. Browsers are well-tested and constantly upgraded.

4. Web sites don't have intermediaries rewriting their content, injecting scripts, and generally changing their behaviour randomly.  


## What can be done?

### 1. Find the EPUB that *is*, not the EPUB we want.

Before we change EPUB any more, we need to find out what is supported today. EPUB creators are less interested in what should work than in what does work. Let's create a version of epub that is tested, that includes *only* features that are widely implemented, a spec that's fact instead of fiction.

To do this we need tests, and we need lots of reading systems that pass the tests. What is the EPUB we can trust? Let's find out.

### 2. More nuanced validation.

### 3. Trust HTML

One of the strengths of HTML is that it knows how to handle almost anything. Consider this fragment:

```html
<epub-secrets>
  <h7 style="color: red;">Editors</h7>
  <simple-list>
    <simple-list-item>Laura Brady</simple-list-item>
  </simple-list>
</epub-secrets>
```

This works perfectly well in my browser. HTML has a rule for unknown elements: ignore them, but process their children. This is what makes it possible for past and future to co-exist. I could actually implement what you see above using HTML custom elements. So it might be magical in a cutting-edge browser, but still readable in an executive's old copy of Internet Explorer.

### 4. Make change compelling

Creating EPUB 3.2, or 3.0.2, is not going to make more people adopt a new version. The cost is too high; the benefits too small or too uncertain. 

### 5. Build, then specify

TK





#### Appendix: The Original Rant (to be deleted)
```
1:27 dauwhe: I've been thinking about "don't break the web" and epub
11:27 dauwhe: browsers have to support every feature forever, more or less
11:27 dauwhe: even the mistakes
11:27 dauwhe: if even one in ten thousand web sites uses something, it won't be removed
11:30 dauwhe: is epub in the same situation? I think 3.x is. As much was we want to fix our mistakes, we can't.
11:31 dauwhe: and people see no value in fixing mistakes. 3.1 is better in every way than 3.0.1, but nobody cares.
11:31 dauwhe: does 3.1 allow new kinds of books? no.
11:31 dauwhe: does 3.1 guarantee that you can use script now? no.
11:31 dauwhe: so where's the incentive to switch?
11:32 dauwhe: Even with EPUB4 or WP or PWP, how can we make it compelling enough for people to want to use them?
11:32 dauwhe: James Patterson works in OEB 1.0. Everything since has been minor details.
```


