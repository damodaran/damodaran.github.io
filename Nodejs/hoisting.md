#Hoisting- Javascript

Javascript is an extremely flexible language. It allow variable declaration anywhere. Hoisting is the JavaScript interpreter’s action of moving all variable and function declarations to the top of the current scope. However, only the actual declarations are hoisted. Any assignments are left where they are.

Step 1: Consider following immediately-invoked function expression (IIFE)
>(function() {
  var a = 1;
  var b = 2;
  var c = 3;
  alert(a + ” ” + b + ” ” + c);
})();

It displays the string “1 2 3″.

Step 2: Now what happen if we move the alert one step higher.

>(function() {
  var a = 1;
  var b = 2;
  alert(a + ” ” + b + ” ” + c);
  var c = 3;
})();

This is a valid JavaScript code, which does not generate any exception.It will alert “1 2 undefined“.

Step 3:

>(function() {
  var a = 1;
  var b = 2;
  alert(a + ” ” + b + ” ” + c);
  var c = 3;
})();

Step 4: Now remove the variable declaration var c = 3 and our code will look like

>(function() {
  var a = 1;
  var b = 2;
  alert(a + ” ” + b + ” ” + c);
})();

But this will make a ReferenceError about the variable c is not defined. So what is the difference between Step 3 and Step 4? This is due to Javascript behaviour known as “hoisting”. Now what is hoisting?

>Hoisting is the JavaScript interpreter’s action of moving all variable and function declarations to the top of the current scope. 

However, only the actual declarations are hoisted. Any assignments are left where they are. So our IIFE will look like

>(function() {
  var a;
  var b;
  var c;
  a = 1;
  b = 2;
  c = 3;
  alert(a + ” ” + b + ” ” + c);
})();

So our Step 3 code will look like

>(function() {
  var a;
  var b;
  var c;
  a = 1;
  b = 2;
  alert(a + ” ” + b + ” ” + c);
  c = 3;
})();

The interesting points to remember here are

1. JavaScript does not have block statement scope; rather, it will be local to the code that the block resides within.
2. Javascript’s declaration of variables in a function scope, meaning that variables declared in a function are available anywhere in that function, even before they are assigned a value (value will be undefined if not assigned and no ReferenceError).

No another interesting problem related to hoisting. What will be the value alerted in the following code?
>var myvar = 1;
function foo() {
    myvar = 10;
    return;
    function myvar() {}
}
foo();
alert(myvar);

* In the first statement global variable myvar is set to 1
* Then the function foo() is called
* Function myvar() {} is hoisted and creates a local variable myvar that masks the global myvar.
* The local variable myvar is set to 10 (overwriting the function a) in the function foo.
* As the function foo() return it will alert the global variable myvar which is still 1. Remember the local variable myvar inside the function foo() will lost the scope as the function return.

Here the important point to note is that  within the body of a function, a local variable takes precedence over a global variable with the same name. If you declare a local variable or function parameter with the same name as a global variable, you effectively hide the global variable.

###Block-level scope: 
When control enters a block, such as the if statement, new variables can be declared within that scope, without affecting the outer scope.  Example C
###Function-level scope:  
Blocks, do not create a new scope. Only functions create a new scope( example Javascript )

###From the documentation ECMAScript Standard
>If the variable statement occurs inside a FunctionDeclaration, the variables are defined with function-local scope in that function, as described in section 10.1.3. Otherwise, they are defined with global scope (that is, they are created as members of the global object, as described in section 10.1.3) using property attributes { DontDelete }. Variables are created when the execution scope is entered. A Block does not define a new execution scope. Only Program and FunctionDeclaration produce a new scope. Variables are initialised to undefined when created. A variable with an Initialiser is assigned the value of its AssignmentExpression when the VariableStatement is executed, not when the variable is created.