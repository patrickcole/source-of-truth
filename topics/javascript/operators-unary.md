# Unary Operators

## Unary +

```js
+"87"                   // 87
+{}                     // NaN
+null                   // 0
+undefined              // NaN
+{ valueOf: () => 87 }  // 87
+"test87"               // NaN
```

## Unary -

```js
-"23"                   // -23
-{}                     // NaN
-null                   // -0
-undefined              // NaN
-{ valueOf: () => 67 }  // -67
-"test87"               // NaN
```

## Notes

```js
- +0  // -0
- -0  // 0
```
