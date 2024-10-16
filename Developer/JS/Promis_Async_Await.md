
- Cho 2 func A và B return về 1 số bất kì
- funcA settimeout 2s, funcB 3s
- Cộng giá trị của funcA, funcB

---
Cách 1:

```js
Promise.all([funcA(), funcB()])
```


Cách 2: 

```js
const a = await funcA()
const b = await funcB()
```


Cách 3:

```js
// cách này tương tự Promise.all
const a = funcA()
const b = funcB()

const x = await a;
const y = await b;

```