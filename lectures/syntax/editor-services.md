---
layout: page
title: "Lecture 3: Syntactic Editor Services"
excerpt: "Syntactic Editor Services"
tags: ["lectures"]
context: lectures
subcontext: syntax
# image:
#    feature: "lecture.jpg"
#    credit: Delft University of Technology
#    creditlink: http://repository.tudelft.nl/view/MMP/uuid%3Aa2f25709-c56e-453e-9394-4a05acf603a4/
---

In this lecture we take a further look at declarative syntax definition, with the specification of lexical syntax and the desugaring of context-free syntax and lexical syntax into a core grammar formalism.
Further we study applications of syntax definitions in various _syntactic editor services_, tools that are applied by integrated development environments (IDEs) to assist programmers, such as syntax checking, syntax coloring/highlighting, formatting, and code completion. In particular, we look into how such tools can be automatically and generically be generated from syntax definitions.

### Topics

- lexical syntax, layout, whitespace, comments
- syntactic editor services
- pretty-printing, template productions
- syntactic completion
- error recovery

### Slides

- [PDF](https://github.com/TUDelft-CS4200-2018/lectures/raw/master/03-syntactic-services/CS4200-2018-3-syntactic-services.pdf)
- [github](https://github.com/TUDelft-CS4200-2018/lectures/tree/master/03-syntactic-services)

<iframe src="//www.slideshare.net/slideshow/embed_code/key/70PkRXSeHag2hI" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/eelcovisser/compiler-construction-lecture-3-syntactic-editor-services" title="Compiler Construction | Lecture 3 | Syntactic Editor Services" target="_blank">Compiler Construction | Lecture 3 | Syntactic Editor Services</a> </strong> from <strong><a href="https://www.slideshare.net/eelcovisser" target="_blank">Eelco Visser</a></strong> </div>

### Reading material

- Tobi Vollebregt, Lennart C. L. Kats, Eelco Visser. [Declarative specification of template-based textual editors](https://doi.org/10.1145/2427048.2427056). In Anthony Sloane, Suzana Andova, editors, International Workshop on Language Descriptions, Tools, and Applications, LDTA '12, Tallinn, Estonia, March 31 - April 1, 2012. pages 1-7, ACM, 2012. <https://doi.org/10.1145/2427048.2427056>

- Luis Eduardo de Souza Amorim, Sebastian Erdweg, Guido Wachsmuth, Eelco Visser. [Principled syntactic code completion using placeholders](https://doi.org/10.1145/2997364.2997374). In Tijs van der Storm, Emilie Balland, Dániel Varró, editors, Proceedings of the 2016 ACM SIGPLAN International Conference on Software Language Engineering, Amsterdam, The Netherlands, October 31 - November 1, 2016. pages 163-175, ACM, 2016. <https://doi.org/10.1145/2997364.2997374>
