# The ultimate typescript


Annotate Type

```javascript
let sales: number = 123_456_789;
let course: string = 'The Ultimate TypeScript';
let isPublished: boolean = true;
```

> Automatic infer or detect type of our variable based on assigned value, do not need to annotate type

```javascript
// automatic infer or detect type of our variable based on assigned value, do not need to annotate type
let sales = 124_456_789;
let course = 'The Ultimate TypeScript';
let isPublished = true;

console.log(sales, course, isPublished); // number, string, boolean
```

## 5 Classes, Interfaces and Object-oriented Programming (55m)

### 1) Introduction

- Introduction to Object-Oriented Programming
- Classes
- Constructors
- Properties and Methods
- Access Control keyword
- Getter and Setter
- Statice method
- Create dynamic properties using index signatures
- Inheritance
- Polymorphism
- Abstract classes
- Interfaces

### 2) What is Object-oriented Programming

- Programming Paradigms
  - Procedural
  - Functional
  - Object-Oriented
  - Event-driven
  - Aspect-Oriented
  - so on...

Those are ways of writing programming.

**_Object Oriented is way of writing programming_**

in object oriented programming object is building block of our application

### 3) Creating Classes:

To Create an object first we need create a **class**.

**A class** is a **blueprint** for creating Objects

A **constructor** is a **special function or special method inside a class** that is use for **initializing a object**

This function can **not have return type** **annotation** because it should always **return an instance of class or object**

```TS
class Account {
  id: number;
  owner: string;
  balance: number;

  constructor(id: number, owner: string, balance: number) {
    this.id = id;
    this.owner = owner;
    this.balance = balance;
  }
  deposit(amount: number): void {
    if (amount <= 0) {
      throw new Error('Invalid Amount');
    } else {
      this.balance += amount;
    }
  }
}
```

### 4) Creating Objects

`let account = new Account()`

using the `new` operator we can create an **instance or and object** from an existing class

```TS

class Account {
  id: number;
  owner: string;
  balance: number;

  constructor(id: number, owner: string, balance: number) {
    this.id = id;
    this.owner = owner;
    this.balance = balance;
  }
  deposit(amount: number): void {
    if (amount <= 0) {
      throw new Error('Invalid Amount');
    } else {
      this.balance += amount;
    }
  }
}

const account = new Account(1, 'Wayne Bruce', 0);
console.log(account); // { id: 1, owner: 'Wayne Bruce', balance: 0 }

account.deposit(100);

console.log(account.balance); // 100

// console.log(typeof account); // object

// to know instance of a given class use instanceOf operator


console.log(account instanceof Account); // true

```

`instanceof` use for check instance of given class

### 5) Read-only and optional Operators

```TS
class Account {
  readonly id: number; // can not re-assign, only read after initialization
  owner: string;
  balance: number;
  nickname?: string; // optional

  constructor(id: number, owner: string, balance: number) {
    this.id = id;
    this.owner = owner;
    this.balance = balance;
  }
  deposit(amount: number): void {
    if (amount <= 0) {
      throw new Error('Invalid Amount');
    } else {
      this.balance += amount;
    }
  }
}

const account = new Account(1, 'Wayne Bruce', 0);
console.log(account); // { id: 1, owner: 'Wayne Bruce', balance: 0 }

account.deposit(100);

console.log(account.balance); // 100

// console.log(typeof account); // object

// to know instance of a given class use instanceOf operator


console.log(account instanceof Account); // true

```

### 6) Access Control Keywords

3 Access Modifiers

- Public
- Private:- *Access it anywhere within a **class** but we can not access it from the outside of class*
- Protected - same as `Private` the differences is it inheritance but private not.

```TS
class Account {
  readonly id: number; // can not re-assign, only read after initialization
  owner: string;
  private _balance: number;
  nickname?: string; // optional

  constructor(id: number, owner: string, balance: number) {
    this.id = id;
    this.owner = owner;
    this._balance = balance;
  }
  deposit(amount: number): void {
    if (amount <= 0) {
      throw new Error('Invalid Amount');
    } else {
      this._balance += amount;
    }
  }

  // accessible only within this class
  private calculateTax(): number {

  }

  getBalance(): number {
    return this._balance;
  }
}

const account = new Account(1, 'Wayne Bruce', 0);
console.log(account); // { id: 1, owner: 'Wayne Bruce', balance: 0 }

account.deposit(100);

// console.log(account.balance); // 100

// console.log(typeof account); // object

// to know instance of a given class use instanceOf operator


console.log(account instanceof Account); // true

// account.balance = -1;

// console.log(account.balance);


console.log(account.getBalance());

// account.




```

### 7) Parameter Properties

>A cool feature of TypeScript called **Parameter Properties**

```TS
class Account {
  // readonly id: number; // can not re-assign, only read after initialization
  // owner: string;
  // private _balance: number;
  nickname?: string; // optional

  constructor(
    public readonly id: number,
    public owner: string,
    private _balance: number
  ) {
    // this.id = id;
    // this.owner = owner;
    // this._balance = balance;
  }
  deposit(amount: number): void {
    if (amount <= 0) {
      throw new Error('Invalid Amount');
    } else {
      this._balance += amount;
    }
  }

  // accessible only within this class
  private calculateTax(): number {}

  getBalance(): number {
    return this._balance;
  }
}

const account = new Account(1, 'Wayne Bruce', 0);
console.log(account); // { id: 1, owner: 'Wayne Bruce', balance: 0 }

account.deposit(100);

// console.log(account.balance); // 100

// console.log(typeof account); // object

// to know instance of a given class use instanceOf operator

console.log(account instanceof Account); // true

// account.balance = -1;

// console.log(account.balance);

console.log(account.getBalance());

// account.

```

```Ts
class Account {
  nickname?: string; // optional

  constructor(
    public readonly id: number,
    public owner: string,
    private _balance: number
  ) {

  }
  deposit(amount: number): void {
    if (amount <= 0) {
      throw new Error('Invalid Amount');
    } else {
      this._balance += amount;
    }
  }

  // accessible only within this class
  private calculateTax(): number {}

  getBalance(): number {
    return this._balance;
  }
}

const account = new Account(1, 'Wayne Bruce', 0);
console.log(account); // { id: 1, owner: 'Wayne Bruce', balance: 0 }

account.deposit(100);

// console.log(account.balance); // 100

// console.log(typeof account); // object

// to know instance of a given class use instanceOf operator

console.log(account instanceof Account); // true

// account.balance = -1;

// console.log(account.balance);

console.log(account.getBalance());

// account.


```


### 8) Getters and Setters


```TS
class Account {
  // readonly id: number; // can not re-assign, only read after initialization
  // owner: string;
  // private _balance: number;
  nickname?: string; // optional

  constructor(
    public readonly id: number,
    public owner: string,
    private _balance: number
  ) {
    // this.id = id;
    // this.owner = owner;
    // this._balance = balance;
  }
  deposit(amount: number): void {
    if (amount <= 0) {
      throw new Error('Invalid Amount');
    } else {
      this._balance += amount;
    }
  }



  get balance (): number {
    return this._balance;
  }

  // We can not directly update balance because read-only that why we update using setters method, and get using getters method
  set balance(value: number) {
    if (value < 0) {
      throw new Error('Invalid Value');
    }
    this._balance = value;
  }
}

const account = new Account(1, 'Wayne Bruce', 0);
console.log(account); // { id: 1, owner: 'Wayne Bruce', balance: 0 }

account.deposit(100)

console.log(account.balance);

account.balance = 888;

console.log(account.balance);


```


### 8) Index Signature

TypeScript **very strict about its shape of object**

```ts
const person: {} = {};

console.log(person.name) // !!ERROR
```

```ts
const person = {};

console.log(person.name) // !!ERROR
```

Above the TypeScript code not working


In TypeScript **must define object shape** to working with object (access, update, delete, so on...)

```ts
const person: {name: string} = {name: 'John Doe'};

console.log(person.name) // John Doe
```

Some situation arise when we need to add properties to and object dynamically this is where we use Index Signatures


Declaring Object properties if very repetitive, so many properties declaration is bad 
```TS
class setAssignment {
  constructor(A1: string, A2: string, so on .....)
}
```
so we can add properties dynamically **using Index Signatures**

**Index Signature is a special type of keyword**


```TS
class seatAssignment {
  
  // A1: string - Harry Potter
  // A2: string - John Doe


  // Index Signature Properties
  [seatNumber: string]: string
}

const seats = new seatAssignment();


seats.A1 = 'Harry';
seats.A2 = 'John';


console.log(seats);
```


### 9) Static Member

create individual object instance on memory for each rider, and show different value for each rider

```TS
class Ride {
  activeRide: number = 0;

  start() {
    this.activeRide++;
  }

  stop() {
    this.activeRide--;
  }
}

const ride1 = new Ride();

console.log('rid1', ride1.start());
console.log('rid1', ride1.start());
console.log('rid1', ride1.start());

const ride2 = new Ride();
console.log('ride2', ride2.start());
console.log('ride2', ride2.start());

console.log('ride2', ride2.start());

console.log('ride1', ride1.activeRide);
console.log('ride2', ride2.activeRide);
```


using `Static`, we need to single global place where we keep track `activeRide` for every `Ride`

```Ts
class Ride {
  static activeRide: number = 0;

  start() {
    Ride.activeRide++;
  }

  stop() {
    Ride.activeRide--;
  }
}

const ride1 = new Ride();
ride1.start();
ride1.start();
ride1.start();

const ride2 = new Ride();
ride2.start()
ride2.start()
ride2.start();


Ride.activeRide = 100; // problem fix issue using private

console.log('ride1', Ride.activeRide);
console.log('ride2', Ride.activeRide);
```


ride
here one problem we can directly change `activeRider` value to fix we should use `private`

```TS
class Ride {
  private static _activeRide: number = 0;

  start() { Ride._activeRide++;}

  stop() { Ride._activeRide--;}

  // not this activeRide is now Ride Object, to fix add static
  static get activeRide() {
     return Ride._activeRide
  }
}

const ride1 = new Ride();
ride1.start();
ride1.start();
ride1.start();

const ride2 = new Ride();
ride2.start()
ride2.start()
ride2.start();


// Ride.activeRide = 100; // problem fix issue using private

console.log('ride1', Ride.activeRide);
console.log('ride2', Ride.activeRide);

//  now we have single place we can keep track of activeRides

```


`static` : crate single instance of memory


if we need make property or method `static`, that property or method become part of a class and only have single instance of them in memory


### 10) Inheritance

Inheritance is a Mechanism that allow us to reuse our code

`super()` - Reference to base class, when we extend something or Inherit from base class


`constructor(public id: string, public firstName)` - When we use and access modifier like `public` or `private` here we are accenssally creating parameter property , so TypeScript compiler will create a property by this name and initialize for us. 


- `Parent / Base / Super` - where form derive member
- `Child / Derived / Sub` - where to derive 


**code**:

```TS

// Parent / Base / Super
class Person {
  constructor(public firstName: string, public lastName: string) {}

  get fullName() {
    return this.firstName + ' ' + this.lastName;
  }

  walking() {
    console.log('Walking');
  }
}

const person = new Person('John', 'Doe');
console.log(person); // { firstName: 'John', lastName: 'Doe' }


// This is inheritance
/* Child / Derived / Sub */
class Student extends Person{
  // here no need to apply access modifier because we all ready defined  this property in Person constructor
  constructor(public id: number, firstName: string, lastName: string) {
    super(firstName, lastName) // to call the constructor of base class
  }

  takeTest() {
    console.log('Taking a Test');
    
  }
}

const student = new Student(1, 'Harry', 'Potter')
console.log(student) // { firstName: 'Harry', lastName: 'Potter', id: 1 }

//  now we can access all property and method

// REMEMBER:- Best practice we should implement each class in a separate file
```



### 11) Method Overriding

```Ts
// Parent / Base / Super
class Person {
  constructor(public firstName: string, public lastName: string) {}

  get fullName() {
    return this.firstName + ' ' + this.lastName;
  }

  walking() {
    console.log('Walking');
  }
}

const person = new Person('John', 'Doe');
console.log(person); // { firstName: 'John', lastName: 'Doe' }

// This is inheritance
/* Child / Derived / Sub */
class Student extends Person {
  // here no need to apply access modifier because we all ready call this property in Person constructor
  constructor(public id: number, firstName: string, lastName: string) {
    super(firstName, lastName); // to call the constructor of base class
  }

  takeTest() {
    console.log('Taking a Test');
  }
}

const student = new Student(1, 'Harry', 'Potter');
console.log(student); // { firstName: 'Harry', lastName: 'Potter', id: 1 }

//  now we can access all property and method

class Teacher extends Person {
  override get fullName() {
    // no need write this.firstName + " " + this.lastName instead of call super.fullName
    return 'Professor' + super.fullName;
  }
}

const teacher = new Teacher('John', 'Smith');

console.log(teacher.fullName)



// REMEMBER:- Best practice we should implement each class in a separate file


```


### 12) Polymorphism

One of the core principle of object-oriented programming is **Polymorphism**

Polymorphism stands for
- Poly - Many
- morphi - Form
  
so, Polymorphism means Many-forms and this refer to situation where an objects take many different forms


**Open Closed Principle**: Class should be **Open** for **extension** and **closed** for **modification**



```TS
// Parent / Base / Super
class Person {
  constructor(public firstName: string, public lastName: string) {}

  get fullName() {
    return this.firstName + ' ' + this.lastName;
  }

  walking() {
    console.log('Walking');
  }
}

const person = new Person('John', 'Doe');
console.log(person); // { firstName: 'John', lastName: 'Doe' }

// This is inheritance
/* Child / Derived / Sub */
class Student extends Person {
  // here no need to apply access modifier because we all ready call this property in Person constructor
  constructor(public id: number, firstName: string, lastName: string) {
    super(firstName, lastName); // to call the constructor of base class
  }

  takeTest() {
    console.log('Taking a Test');
  }
}

const student = new Student(1, 'Harry', 'Potter');
console.log(student); // { firstName: 'Harry', lastName: 'Potter', id: 1 }

//  now we can access all property and method

class Teacher extends Person {
  override get fullName() {
    // no need write this.firstName + " " + this.lastName instead of call super.fullName
    return 'Professor ' + super.fullName;
  }
}

const teacher = new Teacher('John', 'Smith');

class Principle extends Person {
  override get fullName() {
    return 'Principle ' + super.fullName;
  }
}

printName([
  new Student(1, 'Tony', 'Stark'),
  new Teacher('Wayne', 'Bruce'),
  new Principle('Steve', 'Rogers'),
]);

function printName(people: Person[]) {
  for (let person of people) {
    console.log(person.fullName);
  }
}

// REMEMBER:- Best practice we should implement each class in a separate file


```

Many form



### 13) Private vs Protected Members

- Private: Only access within the class can not access outside
- Protected: Same as Private but differences is it can inheritance. We can access any child class



```TS


// Parent / Base / Super
class Person {
  constructor(public firstName: string, public lastName: string) {}

  get fullName() {
    return this.firstName + ' ' + this.lastName;
  }

// often should not use this, because cupling 
  protected walking() {
    console.log('Walking');
  }

  // only accessible within this Person class, can access outside of Person Class even not child
  private swimming() {
    console.log('swimming');
  }
}

const person = new Person('John', 'Doe');
console.log(person); // { firstName: 'John', lastName: 'Doe' }

// This is inheritance
/* Child / Derived / Sub */
class Student extends Person {
  // here no need to apply access modifier because we all ready call this property in Person constructor
  constructor(public id: number, firstName: string, lastName: string) {
    super(firstName, lastName); // to call the constructor of base class
  
  }

  takeTest() {
    console.log('Taking a Test');
    this.walking() // we access it from parent
  }
}

const student = new Student(1, 'Harry', 'Potter');
console.log(student); // { firstName: 'Harry', lastName: 'Potter', id: 1 }

```


### 13) Abstract Class Method

TODO


### 14) Interface

In Object-oriented programming we have another building block  called an **interface**

**Class:** Blueprint for creating **object**


**Interface:** To define the shape / Interface of an object

TODO


---



## Generic Classes

- Generic Classes
- Generic Function
- Generic Interfaces
- Generic Constraints
- Type Mapping



