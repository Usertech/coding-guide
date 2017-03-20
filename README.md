# U+ Coding Guide

This document describes best practices to follow when coding html, css, js, twig...

## TOC

- [Workflow](WORKFLOW.md)
	- [Understanding design](#design)
	- [Daily work on project](#daily-work-on-project)
	- [Pre deploy checklist](#pre-deploy-checklist)
- [Twig](./twig/TWIG.md)  
	  
- [Javascript](https://github.com/usertech/javascript-guide/)
	- [Build tool - Webpack](https://github.com/usertech/javascript-guide/blob/master/OUR_BUILD_TOOL.md)
- [Seed](./seed/SEED.md)

- Stylesheet architecture (#css-stylesheet-architecture)
  - [CSS](./css/CSS.md)
  - [Bliss](./css/BLISS.md)


## Workflow

### Understanding project desing <a id="design"></a>

- **Spend first day with design analysis** (All coders together)
	- Check if everything is correct and make sense - if not discuss it with PM and Designer
	- Ask designer for style guide (base elements, colors, sizes...)
	- Split design to modules (Section, Btn, Link, Headline...) - Write on paper

### Daily work on project
- Every day spend 15 minut with design analysis, everyone to know what is done and what remains to be done

### Pre deploy checklist
- [ ] Favicons
- [ ] robots.txt
- [ ] sitemap.xml
- [ ] Google Analytics
- [ ] more tracking codes?
- [ ] custom error pages exists (and properly set up in .htaccess if necessary)
- [ ] all links work (crawl it, baby!!! - e.g. W3C checklink)
- [ ] CSS and JS in least requests and minified
- [ ] All images are compressed
- [ ] titles and metas (particularly meta description)
- [ ] OpenGraph properties
- [ ] No errors in console
- [ ] No console.logs in cosole
=======

## CSS Stylesheet architecture

We adhere to component/module-based approach [css-bliss](https://github.com/gilbox/css-bliss) which shares common ideas with 
[BEM](http://bem.info), [SMACSS](https://smacss.com/), [OOCSS](http://oocss.org/), [SUITECSS](https://github.com/suitcss),
but adds further restrictions to **fix design flaws in CSS**.

To be studied in following order

- [Walkthrough](http://gilbox.github.io/css-bliss/walkthrough/release/)
- [Chapters in README](https://github.com/gilbox/css-bliss)
- [How css-bliss tackles problems with complex CSS identified by Facebook](https://github.com/gilbox/css-bliss/blob/master/solving-complexity.md)
- [Common mistakes](https://github.com/gilbox/css-bliss/blob/master/common-mistakes.md)

All credits go to [Gil Birman](https://github.com/gilbox)

This architecture is preprocessor independent. 
We are using SASS to make things DRY.