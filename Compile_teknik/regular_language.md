# [What is a regular language?](https://stackoverflow.com/questions/6718202/what-is-a-regular-language)



In the context of computer science, a ***word*** is the concatenation of ***symbols***. The used **symbols** are called the ***alphabet***. For example, some words formed out of the alphabet `{0,1,2,3,4,5,6,7,8,9}` would be `1`, `2`, `12`, `543`, `1000`, and `002`.

**A *language* is then a subset of all possible words**. For example, we might want to define a language that captures all elite MI6 agents. Those all start with double-0, so words in the language would be `007`, `001`, `005`, and `0012`, but not `07` or `15`. For simplicity's sake, we say a **language is "*over* an alphabet"** instead of "a subset of words formed by concatenation of symbols *in* an alphabet".

In computer science, we now want to classify languages. We call a **language *regular* if it can be decided if a word is in the language with an algorithm/a machine** with constant (finite) memory by examining all symbols in the word one after another. The language consisting just of the word `42` is regular, as you can decide whether a word is in it without requiring arbitrary amounts of memory; you just check whether the first symbol is 4, whether the second is 2, and whether any more numbers follow.

All languages with a finite number of words are regular, because we can (in theory) just build a control flow tree of constant size (you can visualize it as a bunch of nested `if`-statements that examine one digit after the other). For example, we can test whether a word is in the "prime numbers between 10 and 99" language with the following construct, requiring no memory except the one to encode at which code line we're currently at:

```
if word[0] == 1:
  if word[1] == 1: # 11
      return true # "accept" word, i.e. it's in the language
  if word[1] == 3: # 13
      return true
...
return false
```

Note that all finite languages are regular, but not all regular languages are finite; our double-0 language contains an infinite number of words (`007`, `008`, but also `004242` and `0012345`), but can be tested with constant memory: To test whether a word belongs in it, check whether the first symbol is `0`, and whether the second symbol is `0`. If that's the case, accept it. If the word is shorter than three or does not start with `00`, it's not an MI6 code name.

Formally, the construct of a [finite-state machine](http://en.wikipedia.org/wiki/Deterministic_finite_state_machine) or a [regular grammar](http://en.wikipedia.org/wiki/Regular_grammar) is used to prove that a language is regular. These are similar to the `if`-statements above, but allow for arbitrarily long words. If there's a finite-state machine, there is also a regular grammar, and vice versa, so it's sufficient to show either. For example, the finite state machine for our double-0 language is:

```
start state:  if input = 0 then goto state 2
start state:  if input = 1 then fail
start state:  if input = 2 then fail
...
state 2: if input = 0 then accept
state 2: if input != 0 then fail
accept: for any input, accept
```

The equivalent regular grammar is:

```
start → 0 B
B → 0 accept
accept → 0 accept
accept → 1 accept
...
```

The equivalent [regular expression](http://en.wikipedia.org/wiki/Regular_expression#Formal_language_theory) is:

```
00[0-9]*
```

Some languages are *not* regular. For example, the language of any number of `1`, followed by the same number of `2` (often written as 1n2n, for an arbitrary *n*) is not regular - you need more than a constant amount of memory(= a constant number of states) to store the number of `1`s to decide whether or not a word is in the language.

This should usually be explained in the theoretical computer science course. Luckily, Wikipedia explains both [formal](http://en.wikipedia.org/wiki/Formal_language) and [regular languages](http://en.wikipedia.org/wiki/Regular_language) quite nicely.



