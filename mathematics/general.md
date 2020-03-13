# Mathematics

## Proof

**Definition.** A mathematical *proof* of a *proposition* is a chain of *logical deductions* leading to the proposition from a base set of *axioms*.

A proof is a method of establishing truth.

## Propositions

**Definition.** A proposition is a statement (communication) that is either true or
false.

`2 + 3 = 5` and `1 + 1 = 3` are both propositons, while `where is 2` and `this is 5` are not.

## Predicates

A predicate can be understood as a proposition whose truth depends on the value
of one or more variables. "n is a perfect square" is true when n = 4 and false when n = 5.

Can be written as `P(n) ::= “n is a perfect square”`.
P(4) is true, P(5) is false.

Note the difference between predicates and functions. P(n) is either true or false. p(n) (like `n+1`) is a numerical quantity.

## Axioms

Propositions that are simply accepted as true.

ZFC: Zermelo-Fraenkel with Choice axioms. ZFC with a few logical deduction is sufficient to derive essentially all of mathematics.

### Different roles of propositions regarding axioms

- Theorems: Important true propositions.
- Lemma: A preliminary proposition useful for proving later propositions.
- Corollary: A proposition that follows in just a few logical steps from a
theorem.

### Logical Deductions

*Logical deductions*, also called *inference rules*, are used to prove new propositions using previous proved ones.

Example rule: modus ponens -  a proof of P together with a proof that P IMPLIES Q is a proof of Q. The notation is below

```
P, P IMPLIES Q
______________
      Q
```

When the statement above the line (*antecedents*) are proved, then we can consider the statement below the line (*conclusion* or consequent) to also be proved.

[Back](../README.md)
