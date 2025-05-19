# OGTRTA v0.4

(working draft)

OGTRTA (the One Grammar To Rule Them All) is a template for making constructed languages. The idea is that with a short wordlist and a few decisions about grammar, you can create a fully-functioning, self-consistent, complete, and unique conlang, suitable for further elaboration.

I created OGTRTA for my own use, because I suck at finishing conlang grammars. I wanted a way to create a conlang that was "complete" (if short on vocabulary) in a few minutes, so that most of the remaining work would be crafting the lexicon and tweaking the morphology. Essentially, I wanted the walking skeleton pattern, but for conlangs instead of computer programs.

However, in order to arrive at a system that would work, the way I had to develop OGTRTA was to create several actual (half-finished) conlangs, peruse grammars of natural languages, and then figure out what framework could produce them all. OGTRTA is not some pie-in-the-sky idea I dreamed up. It's derived from observations of actual languages both natural and artificial.

In creating OGTRTA, I had to strike a balance between a maximally-comprehensible system and a maximally-flexible one. As a result, OGTRTA is not right for every language. For example, if you want a language with very free word order, tons of noun classes, and head-marking, OGTRTA is probably not a good choice — but then again, you don't need OGTRTA for a language like that, because the main problem OGTRTA solves is syntax. On the other hand, if you want a language with fairly fixed word order, which is either consistently head-initial or consistently head-final, OGTRTA might work well for you.

OGTRTA strives to be formal and logically consistent. As you peruse the list of naturalistic extensions, many of which hack around OGTRTA's underlying formality, you might wonder what the point of this formality is. If you want a naturalistic conlang, wouldn't it be better to start from something closer to traditional grammar?

The problem with informal rules is, they don't generalize. If you start from an informal foundation, your grammar will be riddled with exceptions and special cases, and it will very hard to know when you're "done," or whether the language you've described is actually the one you want. The purpose of OGTRTA's formality is not to restrict you. Rather, it is meant to give you confidence in the consistency of your results, and thus more freedom to make your language how you want it.

OGTRTA comprises two parts: a syntax, and a skeletal lexicon with about 100 morphemes. This document describes both parts, beginning with the syntax.

## Syntax

The syntax of OGTRTA is characterized by several key concepts.

**Reversibility.**
The syntax described below is that of a head-initial, VOS language. However, OGTRTA is a reversible syntax. The right-hand-side of each expansion rule can be reversed to create a head-final, SOV language (far more typical of human languages). Additionally, various extensions to the basic syntax can create the other four word orders (SVO, OVS, VSO, and OSV).

**Extensibility.**
OGTRTA is designed with extensibility in mind. Indeed, to get a naturalistic result, one practically has to extend the basic syntax. The extensions that have been worked out so far are described on the extensions page.

**No view to semantics.**
The basic syntax of OGTRTA is designed with no view to semantics. The syntax defines only the structural relationships that can exist among words and phrases; it has no opinion about what those relationships *mean*. Meaning comes from the lexicon.

This is one of the core principles of OGTRTA, and it is what allows extensions to do things like build relative clauses out of questions. We don't have to ponder philosophical issues like whether relative clauses "are really" questions or anything silly like that. There's no need to square the circle. The meaning in a linguistic construction is purely a matter of convention.

### Parts of Speech

OGTRTA recognizes four parts of speech or **word classes**. These are subdivided into open classes and closed classes. An open class of words is one in which new words can be freely coined, derived, or borrowed from other languages. A closed class is one with a fixed set of words, which expands very rarely.

The **Open classes** (content words) are **Nouns** and **Verbs**.

The **Closed classes** (grammar words) are **Conjunctions** and **Nominalizers**.

**Nouns** are straightforward: a noun refers to a person, place, thing, or idea. Noun nodes are written N in the formal syntax.

**Verbs** in OGTRTA are a little bit different from English verbs. OGTRTA has no adjectives or prepositions, so verbs fill the role of both. It is possible, though, to emulate adjectives and prepositions; see the extensions page for ideas. Verb nodes are written V in the formal syntax.

**Conjunctions** connect syntax nodes (phrases and sentences) as peers — i.e. without subordinating one node to the other. English conjunctions include such useful words as "and", "or", "while", "because", "so", and so on. Conjunction nodes are written CONJ in the formal syntax.

**Nominalizers** turn an entire sentence into a noun phrase, allowing it to be embedded in another sentence. Nominalizer nodes are written NOM in the formal syntax.

### Valence

Every noun and verb has a valence, a number which determines how many complements must follow it in the syntax tree. The complements of a word are always noun phrases, and are similar to objects (e.g. the direct object and indirect object of a verb) in traditional grammar. Knowing the valence of each word enables the listener to parse OGTRTA sentences. In the formal syntax, a word of valence n is denoted N/n (for nouns) and V/n (for verbs).

When viewed in relation to its complements, a noun or verb is called a complend.

Valence is comparable to the concept of transitivity from traditional grammar. A transitive verb is one that takes an object, like "poke" or "throw"; an intransitive verb like "swim" or "jump" takes no object. In OGTRTA, a "transitive verb" in OGTRTA would have valence 1 (V/1), while an intransitive verb would have valence 0 (V/0).

Note that valence is a grammatical concept, not a logical one. In English, a verb like "eat" can be used transitively or intransitively: you can say "I eat" or "I eat beans" and both are grammatical sentences. In OGTRTA, every word must have a well-defined valence when it is actually used; ambiguity on this point is not allowed. However, OGTRTA languages often have morphological affixes to modify the valence of a word, so your language can have both eat/1 and eat/0 by deriving one from the other. The valence-changing affixes can also be realized as null morphemes, so eat/1 and eat/0 can be homophones if that's what you want.

In theory, there is no upper limit to the valence of a word. In practice, though, I have not found use for valences higher than 2.

### Metasyntax

```
//      // Two slashes begin a comment.
A -> B; // an A consists of B
A B     // A and B in sequence
A | B   // either A or B
A*      // zero or more As
A?      // an optional A
A/n     // an A with valence n.
A{n}    // exactly n As
```

### OGTRTA syntax rules

```
S  -> NP             // A sentence is a noun phrase
    | VP NP          // ...or a verb phrase followed by a subject.
    | S CONJ S;      // ...or a pair of conjoined sentences.
NP -> N/n VP* NP{n}  // A noun phrase is an n-valence noun, its modifiers, and n complements
    | NOM S          // ...or a nominalized sentence
    | NP CONJ NP;    // ...or a pair of conjoined noun phrases.
VP -> V/n VP* NP{n}  // A verb phrase is an n-valence verb, its modifiers, and n complements
    | VP CONJ VP;    // ...or a pair of conjoined verb phrases.
```

## Extensions

So far, we have not discussed any of the language features you'd likely encounter in a grammar textbook for a typical human language: plurals, verb tenses, pronouns, etc. Those features are not part of OGTRTA proper; they are left up to the individual language designer.

One of the nice things about OGTRTA is that it provides a consistent backdrop against which to compare different implementations of various language features. Using OGTRTA, we can clearly see how different implementations make tradeoffs between conciseness, flexibility, and ambiguity.

Still, it can be somewhat tricky to figure out how to work some of these features into an OGTRTA language without disrupting the syntactic and lexical architecture that OGTRTA provides. This page aims to solve that problem with how-to guides and examples.
