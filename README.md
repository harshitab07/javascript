# Javascript Interview Questions

<ol>
  <li>Explain call(), apply() and, bind() methods.</li>
  <p>call() method allows an object to use the method (function) of another object.</p>
  <pre>
  var person = {
    age: 23,
    getAge: function(){
      return this.age;
    }
  }        
var person2 = {age:  54};
person.getAge.call(person2);      
</pre>
  Arguments in call() method:
<pre>
  function saySomething(message){
  return this.name + " is " + message;
}     
var person4 = {name:  "John"};     
saySomething.call(person4, "awesome");
</pre>
  <br>
  apply() method is same is call(), but it accepts arguments in form of array.
<pre>
  function saySomething(message){
  return this.name + " is " + message;
}        
var person4 = {name:  "John"};
saySomething.apply(person4, ["awesome"]);
</pre>
  <br>
  bind() method: 
<pre>
  var bikeDetails = {
    displayDetails: function(registrationNumber,brandName){
    return this.name+ " , "+ "bike details: "+ registrationNumber + " , " + brandName;
  }
}
   
var person1 = {name:  "Vivek"};
var detailsOfPerson1 = bikeDetails.displayDetails.bind(person1, "TS0122", "Bullet");
      
// Binds the displayDetails function to the person1 object
detailsOfPerson1();
//Returns Vivek, bike details: TS0122, Bullet
</pre>

<br>
<li>What is the difference between exec () and test () methods in javascript?</li>
<p>test() and exec() are RegEx expression methods.</p>
<p>exec() searches for a specific pattern in a string. If the pattern is present, it returns the pattern directly, if not it return an empty result.</p>
<p>test() searches for a specific pattern in a string. If the pattern is present it return true, else false.</p>

<br>
<li>Scope Chain</li>
<p>If the javascript engine does not find the variable in local scope, it tries to check for the variable in the outer scope. If the variable does not exist in the outer scope, it tries to find the variable in the global scope.<br>
If the variable is not found in the global space as well, a reference error is throw</p>

<br>
<li>What are closures?</li>
<p>Closures are an ability of a function to remember the variables and functions that are declared in its outer scope.</p>
<pre>
  function randomFunc(){
  var obj1 = {name:"Vivian", age:45};
  return function(){
    console.log(obj1.name + " is "+ "awesome"); // Has access to obj1 even when the randomFunc function is executed

  }
}
var initialiseClosure = randomFunc(); // Returns a function
initialiseClosure(); 
</pre>
<p>When the function randomFunc() runs, it seems that the returning function is using the variable obj1 inside it.</p>
<p>Therefore randomFunc(), instead of destroying the value of obj1 after execution, saves the value in the memory for further reference. This is the reason why the returning function is able to use the variable declared in the outer scope even after the function is already executed.</p>
<p>This ability of a function to store a variable for further reference even after it is executed is called Closure</p>

<br>
<li>What are object prototypes?</li>
<p>All javascript objects inherit properties from a prototype. For example,</p>
<ul>
  <li>Math objects inherit properties from the Math prototype</li>
  <li>Array objects inherit properties from the Array prototype.</li>
</ul>
<p>A prototype is a blueprint of an object. The prototype allows us to use properties and methods on an object even if the properties and methods do not exist on the current object.</p>
<pre>
var arr = [];
arr.push(2);
console.log(arr); // Outputs [2]
</pre>
<p>In the code above, as one can see, we have not defined any property or method called push on the array “arr” but the javascript engine does not throw an error.</p>
<p>The javascript engine sees that the method push does not exist on the current array object and therefore, looks for the method push inside the Array prototype and it finds the method.</p>
<p>Whenever the property or method is not found on the current object, the javascript engine will always try to look in its prototype and if it still does not exist, it looks inside the prototype's prototype and so on.</p>

<br>
<li>Explain Higher Order Functions in javascript.</li>
<p>Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions.</p>
<pre>
  function higherOrder(fn) {
  fn();
}
higherOrder(function() { console.log("Hello world") });  
</pre>
<pre>
  function higherOrder2() {
  return function() {
    return "Do something";
  }
}      
var x = higherOrder2();
x()   // Returns "Do something"
</pre>
</ol>
