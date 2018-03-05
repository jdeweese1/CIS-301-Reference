# List of logika proofs #
1. [implies](./proofs.html#implies)
2. [or](./proofs.html#or)
3. [and](./proofs.html#and)
4. [negation](./proofs.html#negation)

## Implies ##
<a name ="implies">
```Java
p → (q → r) ⊢ (p → q) → (p → r)
// Module: Natural Deduction
// Lecture: Implies
// FYTD #2
// Author: John Hatcliff
// Last revised: February 11, 2016
{
    1. p -> (q -> r) premise
    2.
    {
        3.(p -> q) assume
        4.
        {
            5. p assume
            6. q -> r ->e 1 5
            7. q ->e 3 5
            8. r ->e 6 7
        }
        9. p -> r ->i 4

    }
    10. (p -> q ) -> (p -> r) ->i 2
}
```
```Java
(p ^ r) V (q ^ r) |- (p V q) ^ r
// CIS 301
// Module: Natural Deduction
// Lecture: Disjunction
// FYTD #1
//
{
  1. (p ^ r) V (q ^ r)    premise
  2. {
       3. p ^ r           assume
       4. p               ^e1 3
       5. r               ^e2 3
       6. p V q           Vi1 4
       7. (p V q) ^ r     ^i 6 5
     }
  8. {
       9. q ^ r           assume
       10. q              ^e1 9
       11. r              ^e2 9
       12. p V q          Vi2 10
       13. (p V q) ^ r    ^i 12 11
       }
  14. (p V q) ^ r         Ve 1 2 8
}
```
```Java
(p ∧ q) → r,  p → q,  p  ⊢  r
{
  1. (p ∧ q) → r              premise
  2. p → q                    premise
  3. p                        premise
  4. q                        →e 2 3
  5. p ∧ q                    ∧i 3 4
  6. r                        →e 1 5
}
```
```Java
(p ∨ q) → r,  q  ⊢  r
{
  1. (p ∨ q) → r              premise
  2. q                        premise
  3. p ∨ q                    ∨i2 2
  4. r                        →e 1 3
}
```
```Java
p, (q ∧ p) → r  ⊢  q → r
{
  1. p                  premise
  2. (q ∧ p) → r        premise
  3. {
       4. q             assume
       5. q ∧ p         ∧i 4 1
       6. r             →e 2 5
     }
  7. q → r              →i 3
}
```
## HW 3 ##
1.logika
```Java
(p → q) → r ⊢ p → (q → r)
{
    1.  {
        2.  p                   assume
        3.  {
            4.  q               assume
            5.  {
                6.  p           assume
                7.  q           premise
            }
            8.  p → q           →i 5
            9.  (p → q) → r     premise
            10. r               →e 9 8
        }
        11. q → r               →i 3
    }
    12. p → (q → r)             →i 1
}
```
2.logika
```Java
(p ∧ q ∧ r) ∨ s ⊢ (p ∨ s) ∧ (q ∨ s) ∧ (r ∨ s)
{
    1.  (p ∧ q ∧ r) ∨ s                     premise
    2.  {
        3.  p ∧ q ∧ r                       assume
        4.  p ∧ q                           ∧e1 3
        5.  p                               ∧e1 4
        6.  q                               ∧e2 4
        7.  r                               ∧e2 3
        8.  p ∨ s                           ∨i1 5
        9.  q ∨ s                           ∨i1 6
        10. r ∨ s                           ∨i1 7
        11. (p ∨ s) ∧ (q ∨ s)               ∧i 8 9
        12. (p ∨ s) ∧ (q ∨ s) ∧ (r ∨ s)     ∧i 11 10
    }
    13. {
        14. s                               assume
        15. p ∨ s                           ∨i2 14
        16. q ∨ s                           ∨i2 14
        17. r ∨ s                           ∨i2 14
        18. (p ∨ s) ∧ (q ∨ s)               ∧i 15 16
        19. (p ∨ s) ∧ (q ∨ s) ∧ (r ∨ s)     ∧i 18 17
    }
    20. (p ∨ s) ∧ (q ∨ s) ∧ (r ∨ s)         ∨e 1 2 13
}
```
3.logika
```Java
p ∨ (q ∨ r) ⊢ (p ∨ q) ∨ r
{
    1.  p ∨ (q ∨ r)             premise
    2.  {
        3.  p                   assume
        4.  p ∨ q               ∨i1 3
        5.  (p ∨ q) ∨ r         ∨i1 4
    }
    6.  {
        7.  q ∨ r               assume
        8.  {
            9.  q               assume
            10. p ∨ q           ∨i2 9
//            11. (p ∨ q) ∨ r     ∨i1 10
        }
        12. {
            13. r               assume
//            14. (p ∨ q) ∨ r     Vi2 13
        }
        15. (p ∨ q) ∨ r         Ve 7 8 12
    }
    16. (p ∨ q) ∨ r         Ve 1 2 6
}
```
4.logika
```Java
p → s ⊢ p ∧ q → r ∨ s
{
    1.  {
        2.  p ∧ q       assume
        3.  p           ∧e1 2
        4.  p → s       premise
        5.  s           →e 4 3
        6.  r ∨ s       ∨i2 5
    }
    7.  p ∧ q → r ∨ s   →i 1
}
```
5.logika
```Java
p → q ∨ r, q → s, r → t ⊢ p → (t ∨ s)
{
    1.  p → q ∨ r       premise
    2.  {
        3.  p           assume
        4.  q ∨ r       →e 1 3
        5.  {
            6.  q       assume
            7.  q → s   premise
            8.  s       →e 7 6
            9.  t ∨ s   ∨i2 8
        }
        10. {
            11. r       assume
            12. r → t   premise
            13. t       →e 12 11
            14. t V s   Vi1 13
        }
        15. t ∨ s       ∨e 4 5 10
    }
    16. p → (t ∨ s)     ->i 2
}
```
6a.logika
```Java
p ∧ q ⊢ p → q
{
    1.  {
        2.  p       assume
        3.  p ∧ q   premise
        4.  q       ^e2 3
    }
    5.  p -> q      ->i 1
}
```
6b.logika
```Java
*
---------------------
p q | (p → q) → p ∧ q
---------------------
T T |    T    T   T
T F |    F    T   F
F T |    T    F   F
F F |    T    F   F
---------------------

Contingent
-T : [T T] [T F]
-F : [F T] [F F]
```
6c.logika
```Java
p ∧ q → r ⊢ p → q → r
{
    1.  {
        2.  p               assume
        3.  {
            4.  q           assume
            5.  p ∧ q       ∧i 2 4
            6.  p ∧ q → r   premise
            7.  r           →e 6 5
        }
        8.  q → r           →i 3
    }
    9.  p → q → r           →i 1
}
```
6d.logika
## Or ##

<a name="or">
```Java
(p ^ r) V (q ^ r) |- (p V q) ^ r
// CIS 301
// Module: Natural Deduction
// Lecture: Disjunction
// FYTD #1
//
{
  1. (p ^ r) V (q ^ r)    premise
  2. {
       3. p ^ r           assume
       4. p               ^e1 3
       5. r               ^e2 3
       6. p V q           Vi1 4
       7. (p V q) ^ r     ^i 6 5
     }
  8. {
       9. q ^ r           assume
       10. q              ^e1 9
       11. r              ^e2 9
       12. p V q          Vi2 10
       13. (p V q) ^ r    ^i 12 11
       }
  14. (p V q) ^ r         Ve 1 2 8
}
```
```Java
(p V q) ^ (p V r) |- p V (q ^ r)
// CIS 301
// Module: Natural Deduction
// Lecture: Disjunction
// FYTD #3
//
// Answer: the sequent above is valid, as demonstrated by
// the deduction below.
{
  // start with what we know
  // (add the antecedents of the sequent to the proof as premises)
  1. (p V q) ^ (p V r)         premise
  // break down the conjunction
  2. p V q                     ^e1 1
  3. p V r                     ^e2 1
  // at this point, we cannot prove the consequent directly
  // so we must break on or more of the current facts down
  // (use the Ve rule)
  //
  // What should we try to prove? Intuitively, we will need
  // to do nested case reasoning.  Let's start with the
  // Ve rule applied to p V q.
  //
  // Setting up for Ve rule for p V q
  4. { // Case p for p V q
       5. p                    assume
       // proving the consequent is easy here
       6. p V (q ^ r)          Vi1 5
     }
  7. { // Case q for p V q
       8. q                    assume
       // Here, we can't prove the consequent directly,
       // but if we consider p V r, we can see that if
       // p is true, then we can immediately prove the consequent.
       // If r is true, then since we are currently under the
       // hypothetical case that q is true, we will be able to
       // prove q ^ r, which by Vi2 will allow us to prove the
       // consequent.
       //
       // Setting up for Ve rule for p V r
       9. { // Case p for p V r
            10. p              assume
            // Here, we can easily prove the consequent again
            11. p V (q ^ r)    Vi1 10
          }
       12. { // Case r for p V r
            13. r              assume
            // Now the cool stuff happens, because of where
            // we are in our case reasoning, we have enough
            // facts to prove q ^ r, so we can then prove
            // the consequent
            14. q ^ r          ^i 8 13
            15. p V (q ^ r)    Vi2 14
           }
       // now we have proved the consequent for both cases
       // of p V r
       16. p V (q ^ r)         Ve 3 9 12
     }
  // now we have proved the consequent for both cases
  // of p V q
  17. p V (q ^ r)              Ve 2 4 7
}
```
## and ##
<a name="and">
```Java
p ^ (q ^ r) |- (r ^ q) ^ p
{
  1. p ^ (q ^ r)      premise
  2. p                ^e1 1
  3. q ^ r            ^e2 1
  4. q                ^e1 3
  5. r                ^e2 3
  6. r ^ q            ^i 5 4
  7. (r ^ q) ^ p      ^i 6 2
}
```
## Negation ##
<a name="negation">
```Java
p → ¬q  ⊢  ¬(p ∧ q)
{
  1. p → ¬q                   premise
  2. {
       3. p ∧ q               assume
       4. p                   ∧e1 3
       5. q                   ∧e2 3
       6. ¬q                  →e 1 4
       7. ⊥                   ¬e 5 6
     }
  8. ¬(p ∧ q)                 ¬i 2
}
```
```Java
p, q → ¬p  ⊢  ¬q
{
  1. p                        premise
  2. q → ¬p                   premise
  3. {
       4. q                   assume
       5. ¬p                  →e 2 4
       6. ⊥                   ¬e 1 5
     }
  7. ¬q                       ¬i 3
}
```
```Java
p ∨ q,  ¬p  ⊢  q
{
  1. p ∨ q                    premise
  2. ¬p                       premise
  3. {
       4. p                   assume
       5. ⊥                   ¬e 4 2
       6. q                   ⊥e 5
     }
  7. {
       8. q                   assume
     }
  9. q                        ∨e 1 3 7
}
```
4
```Java
¬p  ⊢  p → q
{
  1. ¬p                       premise
  2. {
       3. p                   assume
       4. ⊥                   ¬e 3 1
       5. q                   ⊥e 4
     }
  6. p → q                    →i 2
}
```
5
```Java
p  ⊢  ¬¬p
{
  1. p                        premise
  2. {
       3. ¬p                  assume
       4. ⊥                   ¬e 1 3
     }
  5. ¬¬p                      ¬i 2
}
```
6
```Java
¬¬p  ⊢  p
{
  1. ¬¬p                      premise
  2. {
       3. ¬p                  assume
       4. ⊥                   ¬e 3 1
     }
  5. p                        pbc 2
}
```
8
```Java
⊢  p ∨ ¬p
{
  1. {
       2. ¬(p ∨ ¬p)           assume
       3. {
            4. p              assume
            5. p ∨ ¬p         ∨i1 4
            6. ⊥              ¬e 5 2
          }
       7. ¬p                  ¬i 3
       8. p ∨ ¬p              ∨i2 7
       9. ⊥                   ¬e 8 2
     }
 10. p ∨ ¬p                   pbc 1
}
```
```Java
~(p V q) |- ~p ^ ~q
{
	1. ~(p V q) premise
	2.{
		3. p assume
		4. p V q Vi1 3
		5. _|_ ~e 4 1
	}
	6. ~p ~i 2
	7.
	{
		8. q assume
		9. p V q Vi2 8
		10. _|_ ~e 9 1
	}
	11. ~q ~i 7
	12. ~p ^ ~q ^i 6 11
}
```
```Java
p -> q, q -> r, ~r |- p -> z
{
  1.p -> q premise
  2. q -> r premise
  3. ~r premise
  4.
  {//begin ->i to prove p -> z
    5. p assume
    6. q ->e 1 5
    7. r ->e 2 6
    8.  _|_ ~e 7 3
    9. z _|_e 8
  }
  10. p -> z ->i 4

}
```
```Java
p -> q, q -> r, ~r |- ~p
{
	1. p -> q premise
	2. q -> r premise
	3. ~r premise
	4.
	{
		5. p assume
		6. q ->e 1 5
		7. r ->e 2 6
		8. _|_ ~e 7 3
		//9. ~p _|_e 8
	}
	9. ~p ~i 4
}
```
```Java
¬(p ∨ q ∨ r) ⊢ ¬p ∧ ¬q ∧ ¬r
{
	1. ~(p V q V r ) premise
	2.
	{
		3. p assume
		4. p V q Vi1 3
		5. p V q V r Vi1 4
		6.  _|_ ~e 5 1
	}
	7. ~p ~i 2
	8.
	{
		9. q assume
		10. p V q Vi2 9
		11. p V q V r Vi1 10
		12. _|_ ~e 11 1
	}
	13. ~q ~i 8
	14.
	{
		15. r assume
		16. q V r Vi2 15
		165. p V q V r Vi2 15
		166. _|_ ~e 165 1
	}
	17. ~r ~i 14
	18. ~p ^ ~q ^i 7 13
	19. ~p ^ ~q ^ ~r ^i 18 17
}
```
```Java
¬p ∨ q ⊢ p → q
{
    1. ~p V q premise
    2.
    {// can we prove p -> q
        3. p assume
        4.
        {//get to q
            5. ~p assume
            6. _|_ ~e 3 5
            7. q  _|_e 6
        }
        8.
        {
            9. q assume

        }
        10. q Ve 1 4 8         
    }
    11. p -> q ->i 2
}
```
```Java
p → q, q → r, ¬r ⊢ p → z
{
  1. p -> q     premise
  2. q -> r     premise
  3. ~r         premise
  4. { // begin ->i to prove p -> z
       5. p     assume
       6. q     ->e 1 5
       7. r     ->e 2 6
       8. _|_   ~e 7 3
       9. z     _|_e 8
     } // end ->
  10. p -> z     ->i 4
}
```
```Java
~(p V q) |- ~p ^ ~q
{
	1. ~(p V q) premise
	2.
	{
		3. p assume
		4. p V q Vi1 3
		5. _|_ ~e 4 1
	}
	6. ~p ~i 2
	7.
	{
		8. q assume
		9. p V q Vi2 8
		10. _|_ ~e 9 1
	}
	11. ~q ~i 7
	12. ~p ^ ~q ^i 6 11
}
```
