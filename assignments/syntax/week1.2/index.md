---
layout: page
title: "Homework Assignments Week 1.2: Syntax Definition"
excerpt: "Assignments"
tags: ["assignments"]
context: assignments
subcontext: assignments_syntax
---

Submit your answers in [WebLab](https://weblab.tudelft.nl/cs4200/2018-2019/) ([Assignment Week 1.2](https://weblab.tudelft.nl/cs4200/2018-2019/assignment/20429/view)).

### Java Syntactic Categories

Consider the following Java program (from the [MiniJava Project](http://www.cambridge.org/us/features/052182060X/)). What are the elements (building blocks) of the program and how are they called? What are the syntactic categories of Java programs?

```
package syntaxtree;
import visitor.Visitor;
import visitor.TypeVisitor;

public class Plus extends Exp {
  public Exp e1,e2;

  public Plus(Exp ae1, Exp ae2) {
    e1=ae1; e2=ae2;
  }

  public void accept(Visitor v) {
    v.visit(this);
  }

  public Type accept(TypeVisitor v) {
    return v.visit(this);
  }
}
```

### Syntax trees

Answer the following questions:

- Why do we need syntax trees when constructing compilers?
- What are the fundamental differences between parse trees and abstract syntax trees?
- How can we represent trees as terms? Illustrate your explanation with an example.

### Testing Syntax Definitions

Read the paper [Integrated language definition testing: enabling test-driven language development.](https://doi.org/10.1145/2076021.2048080) and answer the following questions:

- Why does testing a syntax definition require more than a collection of example programs?
- What is the use of a domain-specific testing language for syntax definition (e.g. compared to a programmatic unit testing framework)?
- What does it mean that SPT is language parametric?
- How does SPT support interactive language design?

Create a Spoofax project with a small syntax definition for arithmetic expressions (e.g. starting with the productions from Lecture 2) and write a small test suite for the language. Can you confirm the ideas presented in the paper? (See also the [SPT documentation](http://www.metaborg.org/en/latest/source/langdev/meta/lang/spt/index.html))

### Abstract Syntax from Concrete Syntax

Given the following syntax definition, define the algebraic signature defining its abstract syntax.

```
module json

imports Common

context-free start-symbols Value

lexical syntax

  String = "\"" StrChar "\""

  StrChar = ~[\"\\]*
  StrChar = "\\" [\"\\\/bfnrt]
  StrChar = "\\u" [0-9A-F] [0-9A-F]
	                [0-9A-F] [0-9A-F]

  Number = "-"? ("0" | [1-9][0-9]*)
	         ("." [0-9]*)?
					 ([eE] [\+\-]? [0-9]+)?

context-free syntax

  Value.String = String
  Value.Number = Number
  Value.Object = "{" {NameValue ","}* "}"
  Value.Array  = "[" {Value ","}* "]"
  Value.True   = "true"
  Value.False  = "false"
  Value.null   = "null"

  NameValue.NV = String ":" Value
```

What is the abstract syntax term for the following program in this language:

```
{
  "x" : 42,
  "y" : 0,
  "name" : "point",
  "color" : [3.4, 5.6, null],
  "visible" : false
}
```

Create a Spoofax project and create the signature and AST automatically.

### Concrete Syntax from Abstract Syntax

Consider the following algebraic signature defining the abstract syntax of a language. Create a Spoofax project and define a syntax definition that (a) has the algebraic signature as its underlying abstract syntax, and (b) provides a concrete notation for the language. Is the syntax definition unambiguous? Write tests to check that concrete and abstract syntax correspond.

```
signature
  sorts RE
  constructors
          : String -> CC
    Wld   : RE
    Str   : STRING -> RE
    CC    : CC -> RE
    EOL   : RE
    Seq   : RE * RE -> RE
    Alt   : RE * RE -> RE
    Plus  : RE -> RE
    Star  : RE -> RE
    Opt   : RE -> RE
```

Fill in the concrete syntax in the tests below such that parsing succeeds and produces the expected abstract syntax terms.

```
module re

language re

start symbol RE

test cc [[
]] parse to CC("[a]")

test alt [[
]] parse to Alt(CC("[a]"),CC("[b]"))

test identifier [[
]] parse to Seq(CC("[a-z]"),Star(CC("[a-zA-Z]")))


test real [[
]] parse to
Seq(
  Alt(
    Seq(
      Seq(Plus(CC("[0-9]")), CC("[.]"))
    , Star(CC("[0-9]"))
    )
  , Seq(CC("[.]"), Plus(CC("[0-9]")))
  )
, Opt(Seq(CC("[e]"), Plus(CC("[0-9]"))))
)

test comment [[
]] parse to Seq(Seq(Str("\"//\""),Star(CCN("[\n]"))),EOL())
```


### Syntax from Examples

Consider the following examples in a language that may look familiar; let's call it XML. Design an abstract syntax (algebraic signature) to represent the structure of documents in this language. For the same language, define a concrete syntax definition. Develop tests to check that concrete and abstract syntax definition align. Create a Spoofax project with concrete syntax and tests. Submit signature, SDF3, and tests.

Example document
```
<languages>
 <language>
  <name>SDF3</name>
    <purpose>Syntax Definition</purpose>
    <implementedin>SDF3</implementedin>
 </language>
 <language>
   <name>Stratego</name>
    <purpose>Transformation</purpose>
    <implementedin>SDF3</implementedin>
    <implementedin>Stratego</implementedin>
    <target>Java</target>
 </language>	 
</languages>
```

Another example document
```
<catalogue>
 <book>
  <title>Modern Compiler Implementation in ML</title>
  <author>Andrew Appel</author>
  <publisher>Cambridge</publisher>
 </book>
 <book>
  <title>Parsing Schemata</title>
  <author>Klaas Sikkel</author>
  <publisher>Springer</publisher>
 </book>
</catalogue>
```

### Syntax of Signatures

Define the syntax of algebraic signatures as defined in Lecture 2.

### Syntax of Grammars

Define the syntax of context-free grammars as defined in Lecture 2.



<!--
### Syntax from Term

Consider the following term, providing the abstract syntax representation of a program in some language. Based on the term reconstruct, the abstract syntax (algebraic signature) of the language. Next create a concrete syntax definition from the abstract syntax.

```

```
-->

### Templates

Consider SDF3 template productions as discussed in Lecture 3.

- Enumerate the syntactic differences between pure context-free grammar productions and SDF3 template productions
- Discuss the purpose of these features

### Syntactic Completion

Read the paper "Principled syntactic code completion using placeholders" and summarize its approach to syntactic code completion.

- What mechanisms are used to realize code completion?
- What properties are guaranteed by the approach?
- How does this compare to code completion in IDEs such as Eclipse?
- What features does and does it not support?
