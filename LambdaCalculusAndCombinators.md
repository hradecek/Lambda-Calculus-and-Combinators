# Lambda Calculus and Combinators

## Chapter 1

**Exercise 1.4**
Insert the full number of parentheses and λ's into the following abbreviated λ-terms:

**(a)** xyz(yx),

**(b)** λx.uxy,

**(c)** λu.u(λx.y),

**(d)** (λu.vuu)zy,

**(e)** ux(yz)(λv.vy),

**(f)** (λxyz.xz(yz))uvw.

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

**Exercise 1.8**

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

No. Because `λu.u = (λu.u)` and `λu.uv = (λu.(uv))`
