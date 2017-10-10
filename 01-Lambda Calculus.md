# Lambda Calculus and Combinators

## Chapter 1 - λ-Calculus

### Exercise 1.4
Insert the full number of parentheses and λ's into the following abbreviated λ-terms:

**(a)** `xyz(yx)`,

**(b)** `λx.uxy`,

**(c)** `λu.u(λx.y)`,

**(d)** `(λu.vuu)zy`,

**(e)** `ux(yz)(λv.vy)`,

**(f)** `(λxyz.xz(yz))uvw`.

**Solutions:**

**(a)**
```
xyz(yx) ≡
(xyz)(yx) ≡
((xy)z)(yx) ≡
(((xy)z)(yx))
```

**(b)**
```
λx.uxy ≡
λx.(uxy) ≡
λx.((ux)y) ≡
(λx.((ux)y))
```

**(c)**
```
λu.u(λx.y) ≡
λu.(u(λx.y)) ≡
(λu.(u(λx.y)))
```

**(d)**
```
(λu.vuu)zy ≡
(λu.(vuu))zy ≡
(λu.((vu)u))zy ≡
((λu.((vu)u))z)y ≡
(((λu.((vu)u))z)y)
```

**(e)**
```
ux(yz)(λv.vy) ≡
(ux)(yz)(λv.vy) ≡
((ux)(yz))(λv.vy)≡
((ux)(yz))(λv.(vy)) ≡
(((ux)(yz))(λv.(vy)))
```

**(f)**
```
(λxyz.xz(yz))uvw ≡
(λx.(λyz.xz(yz)))uvw ≡
(λx.(λy.(λz.xz(yz))))uvw ≡
(λx.(λy.(λz.(xz)(yz))))uvw ≡
(λx.(λy.(λz.((xz)(yz)))))uvw ≡
(λx.(λy.(λz.((xz)(yz)))))u)vw ≡
(((λx.(λy.(λz.((xz)(yz)))))u)v)w ≡
((((λx.(λy.(λz.((xz)(yz)))))u)v)w)
```

### Exercise 1.8

**(a)** Mark all the occurrences of `xy` in the term `λxy.xy`.

**(b)** Mark all the occurrences of `uv` in the term `x(uv)(λu.v(uv))uv`.

**(c)** Does `λu.u` occur in `λu.uv`?

**Solutions:**

**(a)**
```
λxy.xy =
λx.(λy.xy) =
λx.(λy.(xy)) =
(λx.(λy.(xy))) =
         ^^
```

**(b)**
```
x(uv)(λu.v(uv))uv =
(x(uv))(λu.v(uv))uv =
(x(uv))(λu.(v(uv)))uv =
((x(uv))(λu.(v(uv))))uv =
(((x(uv))(λu.(v(uv))))u)v =
((((x(uv))(λu.(v(uv))))u)v) =
      ^^         ^^
```

**(c)**

No. Because `λu.u = (λu.u)` and `λu.uv = (λu.(uv))`.

### Exercise 1.14
Evaluate the following substitutions:

**(a)** `[(uv)/x] (λy.x(λw.vwx))`

**(b)** `[(λy.xy)/x] (λy.x(λx.x))`

**(c)** `[(λy.vy)/x] (y (λv.xv))`

**(d)** `[(uv)/x] (λx.zy)`

**Solutions:**

**(a)** 
```
[(uv)/x] (λy.x(λw.vwx)) = (1.12f)
(λy.[(uv)/x] x(λw.vwx)) = (1.12c)
(λy.[(uv)/x] x [(uv)/x] (λw.vwx)) = (1.12f)
(λy.[(uv)/x] x(λw.[(uv)/x] vwx)) = (1.12a)
(λy.(uv)(λw.[(uv)/x] vwx)) = (1.12a)
(λy.(uv)(λw.vw(uv))) = 
λy.uv(λw.vw(uv))
```

**(b)**
```
[(λy.xy)/x] (λy.x(λx.x)) = (1.12f)
(λy.[(λy.xy)/x] x(λx.x)) = (1.12c)
(λy.[(λy.xy)/x] x [(λy.xy)/x] (λx.x)) = (1.12a)
(λy.(λy.xy)[(λy.xy)/x] (λx.x)) = (1.12e)
λy.(λy.xy)(λx.x)
```

**(c)**
```
[(λy.vy)/x] (y (λv.xv)) =(1.12c)
([(λy.vy)/x] y [(λy.vy)/x] (λv.xv)) = (1.12b)
(y [(λy.vy)/x] (λv.xv)) = (1.12g)
(y (λz.[(λy.vy)/x][z/v] xz)) = (1.12a)
y (λz.(λy.vy)z)
```

**(d)**
```
[(uv)/x] (λx.zy) = (1.12e)
λx.zy
```

### Exercise 1.28
Reduce the following terms to β-normal forms:

**(a)** `(λx.xy)(λu.vuu)`,

**(b)** `(λxy.yx)uv`,

**(c)** `(λx.x(x(yz))x)(λu.uv)`,

**(d)** `(λx.xxy)(λy.yz)`,

**(e)** `(λxy.xyy)(λu.uyx)`,

**(f)** `(λxyz.xz(yz))((λxy.yx)u)((λxy.yx)v) w`.

**Solutions:**

**(a)**
```
(λx.xy)(λu.vuu) β> [(λu.vuu)/x](xy) =
(λu.vuu)y β> [y/u](vuu) = vyy
```

**(b)**
```
(λxy.yx)uv β> ([u/x](λy.yx))v =
(λy.yu)v β> [v/y](yu) =
vu
```
**(c)**
```
(λx.x(x(yz))x)(λu.uv) β> [(λu.uv)/x](x(x(yz))x) =
(λu.uv)((λu.uv)(yz))(λu.uv) β> (λu.uv)([(yz)/u](uv)(λu.uv) =
(λu.uv)((yz)v)(λu.uv) β> [((yz)v)/u](uv)(λu.uv) =
((yz)v)v(λu.uv) = yzvv(λu.uv)
```

**(d)**
```
(λx.xxy)(λy.yz) β> [(λy.yz)/x](xxy) =
(λy.yz)(λy.yz)y β> [(λy.yz)/y](yz)y =
((λy.yz)z)y β> [(z/y)(yz)]y =
zzy
```

**(e)**
```
(λxy.xyy)(λu.uyx) β> [(λu.uyx)/x](λy.xyy) = [(λu.uyx)/x](λz.xzz) =
λz.(λu.uyx)zz β>  λz.([z/u](uyx))z =
λz.(zyx)z = λz.zyxz
```

**(f)**
```
(λxyz.xz(yz))((λxy.yx)u)((λxy.yx)v) w β> [((λxy.yx)u)/x](λyz.xz(yz))((λxy.yx)v) w =
(λyz.((λxy.yx)u)z(yz))((λxy.yx)v) w β> (λyz.([u/x](λy.yx))z(yz))((λxy.yx)v) w =
(λyz.(λy.yu)z(yz))((λxy.yx)v) w β> (λyz.[z/y]yu(yz))((λxy.yx)v) w =
(λyz.zu(yz))((λxy.yx)v) w β> [((λxy.yx)v)/y](λz.zu(yz)) w =
(λz.zu(((λxy.yx)v)z)) w β> (λz.zu(([v/x](λy.yx))z)) w =
(λz.zu((λy.yv)z)) w β> (λz.zu([z/y](yv))) w =
(λz.zu(zv)) w β> [w/z]zu(zv) =
wu(wv) = wuwv
```

### Exercise 1.35
Do not confuse *being* a β-nf with *having* a β-nf: first prove that

**(a)** `[N/x]M` *is a β-nf* ⇒ *M has a β-nf*

then, in contrast (hrader), find terms `M` and `N` s.t.`[N/x]M` has a β-nf but `M` does not;
this will prove that

**(b)** `[N/x]M` *has a β-nf* ⇏ *M has a β-nf*

**Solutions:**

**(a)**

**(b)**

### Exercise 1.36
(Harder) Find terms `P`, `Q` s.t. neither of `P`, `Q` has a β-nf, but `PQ` has a β-nf.

### Exercise 1.38
Prove that `(λxyz.xzy)(λxy.x) =β (λxy.x)(λx.x)`

### Exercise 1.42
**(a)** Prove that if the equation `λxy.x = λxy.y` was added as an extra axiom to the definition of β-equality, then all
terms would become equal. (Adding an equation `P = Q` as an extra axiom means allowing any occurrence of `P` in a term
to be replaced by `Q` and vice versa.)

**(b)** Do the same for the equation `λx.x = λxy.yx`.

### Exercise 1.44 (Extra practice)
**(a)** Insert all missing parentheses and λ’s into the following abbreviated λ-terms:
- `xx(xxx)x`,
- `vw(λxy.vx)`,
- `(λxy.x)uv`,
- `w(λxyz.xz(yz))uv`.

**(b)** Mark all the occurrences of xy in the following terms:
- `(λxy.xy)xy`,
- `(λxy.xy)(xy)`,
- `λxy.xy(xy)`.

**(c)** Do any of the terms in **(a)** or **(b)** contain any of the following terms as subterms?
If so, which contains which?
- `λy.xy`,
- `y(xy)`,
- `λxy.x`.

**(d)** Evaluate the following substitutions:
- `[vw/x] (x(λy.yx))`,
- `[vw/x] (x(λx.yx))`,
- `[ux/x] (x(λy.yx))`,
- `[uy/x] (x(λy.yx))`.

**(e)** Reduce the following terms to β-normal forms:
- `(λxy.xyy)uv`,
- `(λxy.yx)(uv)zw`,
- `(λxy.x)(λu.u)`,
- `(λxyz.xz(yz))(λuv.u)`.

**Solutions:**

**(a)**
```
xx(xxx)x =
(xx)(xxx)x =
((xx)(xxx))x =
((xx)((xx)x))x
```

```
vw(λxy.vx) =
(vw)(λxy.vx) =
(vw)(λxy.(vx)) =
(vw)(λx.(λy.(vx)))
```

```
(λxy.x)uv =
(λx.(λy.x))uv =
((λx.(λy.x))u)v
```

```
w(λxyz.xz(yz))uv =
w(λxyz.(xz)(yz))uv =
w(λxyz.((xz)(yz)))uv =
w(λx.(λyz.((xz)(yz))))uv =
w(λx.(λy.(λz.((xz)(yz)))))uv =
(w(λx.(λy.(λz.((xz)(yz)))))u)v
```

**(b)**
```
(λxy.xy)xy = ((λx.(λy.(xy)))x)y
                       ^^
```

```
(λxy.xy)(xy) = (λx.(λy.(xy)))(xy)
                        ^^    ^^
```

```
λxy.xy(xy) = (λx(λy.x)y)(xy)
                         ^^
```

**(c)**
- `λy.xy` *first* and *second*
- `y(xy)` *none*
- `λxy.x = λx.(λy.x)` *third*

