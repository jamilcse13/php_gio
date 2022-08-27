- echo: 
    - can print separate portions with comma separate in a single line
    - Example: 
        ```javascript
        echo "Hello", " ", "World";       //  => Hello World
        ```
- print:
    - can not print separate portions with comma separate in a single line
    - Example:
        ```javascript
        print "Hello", " ", "World";       //  => syntax error, unexpected ',' 
        ```
- print_r:
    - print mixture type array
    - Example:
        ````javascript
        $campanies = [1, 3, 4, 2.36, 'A', 'Hello', true];
        print_r($companies);
        ````


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

## Data Types
### Type Casting:
* Dynamically types (type checking happens at run time): php
* Statically types (type checking happens at compile time): java, c, c++

**_Data Types and Type Casting:_**
* Scalar Types:
  * bool
  * int
  * float
  * string


* Compound Types:
  * array
  * object
  * callable
  * iterable


* Special Types:
  * resource
  * null


* Type Juggling:
  * although the second parameter is string, but it will convert the type like first parameter.
  ```javascript
  function sum($x, $y) {
      return $x + $y;
  }
  
  $sum = sum(2, '3');
  echo $sum;      // 5
  ```

* Strict Type:
  * here we have passed string using the type hinting
  ```javascript
  function sum(int $x, int $y) {
      return $x + $y;
  }
  
  $sum = sum(2, '3');
  echo $sum;      // 5
  ```
  * but in using strict_types:
  ```javascript
  declare(strict_types=1)
  
  function sum(int $x, int $y) {
      return $x + $y;
  }
  
  $sum = sum(2, '3');
  echo $sum;      // error: expect int type data
  ```
  ```javascript
  $a = "5";     // => string, "5"
  $a = (int) "5";     // => int, 5
  ```
  

### Database on PHP:
```javascript
// establish connection
$connection = mysqli_connect('localhost', 'user_name', 'password', 'table_name');

// get input data
$username = $_POST['username'];
$password = $_POST['password'];


// clean up strinmg
// allow these ' , - ; : etc in a string
$username = mysqli_real_escape_string($connection, $username);
$password = mysqli_real_escape_string($connection, $password);

// encrypt password
// crypt(string $str, $optional_param_making_the_password_stronger)
$hashFormat = "$2jhh*1654$#";
$salt = "ilovetocode2022";
$hash_and_salt = $hashFormat . $salt;
$encrypted_password = crypt($password, $hash_and_salt);

// insert data
$query = "INSERT INTO table_name(username, password) ";
$query .= "VALUES('$username', '$encrypted_password')";


// execute query
$result = mysqli_query($connection, $query);

// throw error if failed operation
if (!$result) {
    die('QUERY FAILED' . mysqli_error());
}

// iterate each rows
while($row = mysqli_fetch_assoc($result)) {
    echo $row;
}
```