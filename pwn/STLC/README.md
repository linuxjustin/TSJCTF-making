# STLC

## Author

@satos

## Description

I learned simply typed lambda calculus in a lecture, so I implement STLC interpreter.
STLC terms are strongly normalizing, therefore it won't stuck in infinite loop! ([https://github.com/hamukazu/lets-get-arrested](https://github.com/hamukazu/lets-get-arrested))

The flag is located at `/home/user/flag`.

`nc [host] 30007`

---

講義で単純型付きラムダ計算(STLC)を習ったので、STLCのインタプリタを実装してみました。
単純型のつくプログラムのみを実行すれば無限ループも起こらないし安全([https://github.com/hamukazu/lets-get-arrested](https://github.com/hamukazu/lets-get-arrested))ですね！

フラグは `/home/user/flag` にあります。

`nc [host] 30007`

---

example)
```
> f = (\x:A. y)
y is free variable
(\x:A.y) can't be simply typed
> f = (\x:A. x)
f = (\x:A.x) :: (A->A)
> g = (\p:A->A. p)
g = (\p:(A->A).p) :: ((A->A)->(A->A))
> h = (\q:B->B. q)
h = (\q:(B->B).q) :: ((B->B)->(B->B))
> v1 = g f
v1 = (\x:A.x) :: (A->A)
> v2 = h f
type mismatched for typing (h f)
with applying ((B->B)->(B->B)) to (A->A)
(h f) can't be simply typed
> sub2 = (\x:I. dec (dec x))
sub2 = (\x:I.(dec (dec x))) :: (I->I)
> 3times = (\f:I->I. \n:I. f (f (f n)))
3times = (\f:(I->I).(\n:I.(f (f (f n))))) :: ((I->I)->(I->I))
> v3 = (3times sub2) 13
v3 = 7 :: I
```

---

Difficulty estimate: Hard


## Difficulty Estimate

med-hard
