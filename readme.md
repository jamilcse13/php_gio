- echo: 
    - can print separate portions with comma separte in a single line
    - exp: echo "Hello", " ", "World"       => Hello World
- print:
    - can not print separate portions with comma separte in a single line
    - exp: print "Hello", " ", "World"       => syntax error, unexpected ',' 


## variable:
- by value:
    ```javascript
    $a = 1; 
    $b = $a; 
    
    $a = 5; 
    echo $b;       // => 1
    ```
- by reference:
    ```javascript
    $a = 1; 
    $b = &$a; 
    $a = 5; 
    echo $b;      // => 5
    ```

- variable inside quotes:
    ```javascript
    $name = 'John'
    echo 'Hello $name';      //  => Hello $name
    echo "Hello $name";      //  => Hello John
    echo "Hello {$name}";    //  => Hello John
    echo "Hello " . $name;   //  => Hello John
    ```

- *variable variables*:
    ```javascript
    $foo = 'bar';
    // $$foo => $bar
    $$foo = 'baz';

    echo $bar;     //  => baz
    echo $$foo;    //  => baz
    ```


- define **constant**:
    - use *define* function
    - define('name', 'value)
    - we can not change the value of the variable later
    ```javascript
    define('STATUS_PAID', 'paid);
    echo STATUS_PAID;     //  => paid
    ```
    - check if a variable is defined
    ```javascript
    echo defined('STATUS_PAID');       //  => 1
    ```

    - use *const* keyword
    ```javascript
    const STATUS_PAID = 'paid';
    echo STATUS_PAID;      //  => paid
    ```

    - define vs const:
        - we use variable in a variable name using define, but can't use const
        ```javascript
        $paid = 'PAID';
        define('STATUS_' . $paid, 'paid');
        echo STATUS_PAID;      //   => paid
        ```

