# return-fn_vs_return-await-fn
Do you know the difference between "return await bar()" and "return bar()" inside an async function?

Using the `await` keyword to reslove an async function.
```javascript
async function foo () {
  return await asyncFn()
}
```

Resloves the async function without `await` keyword.
```javascript
async function foo () {
  return asyncFn()
}
```

With the `await` keyword we can catch errors inside `foo`
```javascript
async function foo () {
  try {
    return await asyncFn()
  } catch (error) {
    // here we catch errors from asyncFn.
  }
}
```


Without the `await` keyword the error is passed outside `.catch`
```javascript
async function foo () {
  try {
    return asyncFn()
  } catch (error) {
    // errors from asyncFn do not land here.
  }
}

foo()
  .catch((error) => {
    // error from foo will land here.
  })
```
