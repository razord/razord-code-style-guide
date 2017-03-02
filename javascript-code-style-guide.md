# JavaScript 代码规范

## 规则

 - 应使用 **2个空格** 缩进
 
    ```js
    function hello (name) {
      console.log('hi', name)
    }
    ```
 
 - 除非为了避免因字符串中的单引号引起的问题，否则字符串使用 **单引号** 
 
    ```js
    console.log('hello there')
    $("<div class='box'>")
    ```
    
 - 不应该声明 **不使用** 的变量
 
    ```js
    function myFunction () {
        var result = something()   // ✗ avoid
    }
    ```
    
 -  应在 **关键字前面** 加入一个空格
 
    ```js
    if (condition) { ... }   // ✓ ok
    if(condition) { ... }    // ✗ avoid
    ```
    
 - 应在 **函数声明的括号前** 加上空格

    ```js
    function name (arg) { ... }   // ✓ ok
    function name(arg) { ... }    // ✗ avoid

    run(function () { ... })      // ✓ ok
    run(function() { ... })       // ✗ avoid
    ```
    
 - **总是** 使用 `===` 而不是 `==`（例外：`obj == null` 允许判断 `null || undefined`.）

    ```js
    if (name === 'John')   // ✓ ok
    if (name == 'John')    // ✗ avoid
    
    if (name !== 'John')   // ✓ ok
    if (name != 'John')    // ✗ avoid
    ```
    
 - 应在 **连接运算符的两端** 加上空格
 
    ```js
    // ✓ ok
    var x = 2
    var message = 'hello, ' + name + '!'

    // ✗ avoid
    var x=2
    var message = 'hello, '+name+'!'
    ```
    
 - 应在 **逗号后面** 加上空格
 
    ```js
    // ✓ ok
    var list = [1, 2, 3, 4]
    function greet (name, options) { ... }

    // ✗ avoid
    var list = [1,2,3,4]
    function greet (name,options) { ... }
    ```
    
 - 应 **保持 `else` 和 `if` 块的结束大括号** 在同一行
 
    ```js
    // ✓ ok
    if (condition) {
      // ...
    } else {
      // ...
    }

    // ✗ avoid
    if (condition) {
      // ...
    }
    else {
      // ...
    }
    ```
    
 - 应对 **多行的代码** 使用大括号

    ```js
    // ✓ ok
    if (options.quiet !== true) console.log('done')

    // ✓ ok
    if (options.quiet !== true) {
      console.log('done')
    }

    // ✗ avoid
    if (options.quiet !== true)
      console.log('done')
    ```

 - 一定要 **处理函数的 `err` 参数** 

    ```js
    // ✓ ok
    run(function (err) {
      if (err) throw err
      window.alert('done')
    })

    // ✗ avoid
    run(function (err) {
      window.alert('done')
    })
    ```
    
 - 一定要 **给全局变量的开头加上 `window.`**

    ```js
    window.alert('hi')   // ✓ ok
    ```
    
 - **不允许** 无用的多个换行

    ```js
    // ✓ ok
    var value = 'hello world'
    console.log(value)

    // ✗ avoid
    var value = 'hello world'


    console.log(value)
    ```
    
 - 如果是三目运算符，**要么全部写一行，要么把 `?` 和 `:` 与对应的代码写一行**

    ```js
    // ✓ ok
    var location = env.development ? 'localhost' : 'www.api.com'

    // ✓ ok
    var location = env.development
      ? 'localhost'
      : 'www.api.com'

    // ✗ avoid
    var location = env.development ?
      'localhost' :
      'www.api.com'
    ```
 
 - 对于变量声明，**给每个声明单独写一行表达式**

    ```js
    // ✓ ok
    var silent = true
    var verbose = true

    // ✗ avoid
    var silent = true, verbose = true
    
    // ✗ avoid
    var silent = true,
      verbose = true
    ```
    
 - 条件循环语句如果有赋值，应使用括号括起来

    ```js
    // ✓ ok
    while ((m = text.match(expr))) {
      // ...
    }

    // ✗ avoid
    while (m = text.match(expr)) {
      // ...
    }
    ```

## 分号

 - **不写分号，看1，2，3**    

    ```js
    window.alert('hi')   // ✓ ok
    window.alert('hi');  // ✗ avoid
    ```
 
 - 语句永远不要使用 `(`, `[` 或者 `` ` `` 开头，没有写分号的时候，这会有潜在的问题

    ```js
    // ✓ ok
    ;(function () {
      window.alert('ok')
    }())

    // ✗ avoid
    (function () {
      window.alert('ok')
    }())
    ```

	```js
    // ✓ ok
    ;[1, 2, 3].forEach(bar)

    // ✗ avoid
    [1, 2, 3].forEach(bar)
    ```
    
    ```js
    // ✓ ok
    ;`hello`.indexOf('o')

    // ✗ avoid
    `hello`.indexOf('o')
    ```

    如果你经常写这样的语句，你需要放弃他
    
    虽然放弃他很令人沮丧，但是为了写出更通俗易懂的语句，你必须这么做
    
    如果你这么写：
    
    ```js
    ;[1, 2, 3].forEach(bar)
    ```
    
    那你必须改成这样：
    
    ```js
    var nums = [1, 2, 3]
    nums.forEach(bar)
    ```
