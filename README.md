# Typescript tutorial

## Type declaration - basic types
```typescript
let id: number = 5;
let company: string = 'Company name';
let isPublished: boolean = true;
```

## any type - can change to different types
```typescript
let x: any = 'hello';
x = false; 
```

## arrays
```typescript
let ids: number[] = [1,2,3,4,5];
// this will give error: 
// ids.push('hello');

// any with arrays:
let arr: any = [1, 2, 'hello', true];
```

## tuple
```typescript
let person: [number, string, boolean] = [1, 'Vivek', true];

// tuple array: 
let employees : [number, string][];

employees = [
    [1, 'sharad'],
    [2, 'surabhi'],
    [3, 'krishna']
];
```

## Union
```typescript
let pid : string | number = 22; 
pid = '23';
```

## enum
```typescript
// default values will be int starting from 0
enum Direction1 {
    up,
    down,
    left,
    right 
}

// you can assign values as well: 
enum Direction2 {
    up='up',
    down='down',
    left='left',
    right='right' 
}
```

## Objects
```typescript
type User: {
    id: number,
    name: string
}; 

const user : User = {
    id = 1,
    name = 'Radha'
}
```
## Type assertion (Typecasting)
```typescript
let cid: any = 1;
let customerId = <number>cid; // first method 
let customerId2 = cid as number; // second method 
```

## Functions
```typescript
function addNum(x: number, y: number): number {
    return x+y;
}

// no return value
function log(message: string): void {
    console.log(message);
}

// use union to pass argument with flexible type - message can be either string or number
function log(message: string | number): void {
    console.log(message);
}
```

## Interfaces
```typescript
interface UserInterface {
    id: number,
    name: string
}; 

const user2 : UserInterface = {
    id = 1,
    name = 'Radha'
}
```

## Differences b/w Objects/types and Interfaces
```typescript
// types can work with unions and primitives; but interfaces cannot use unions and primitives
type Point : number | string; 
```

## Optionals and Readonly
```typescript
interface UserInterface {
    id: number,
    name: string,
    address?: string,       // optional
    readonly phone: string  // readonly
}; 
```

## Interfaces with functions
```typescript
interface MathFunc {
    (x: number, y: number): number
}

const add: MathFunc = (x: number, y: number): number => x + y;
const sub: MathFunc = (x: number, y: number): number => x - y;
```

## Classes
```typescript
// properties are public by default
// access modifiers: public, private, protected
class Person {
    id: number;
    name: string;
    constructor(id: number, name: string) {
        this.id = id;
        this.name = name;
    }
}

const radha = new Person(1, 'Radha');
```

## Interfaces and classes
```typescript
interface PersonInterface {
    id: number;
    name: string;

    register(): string;
}

class Person implements PersonInterface {
    id: number;
    name: string;

    constructor(id: number, name: string) {
        this.id = id;
        this.name = name;
    }

    register() {
        return `${this.name} is registered`;
    }
}
```

## Inheritance
```typescript
class Employee extends Person {
    position: string;
    constructor(id: number, name: string, position: string) {
        super(id, name);
        this.position = position; 
    }
}

const emp = new Employee(3, 'Krishna', 'Architect');
```
## Generics
```typescript
function getArray<T>(items: T[]): T[] {
    return new Array().concat(items);
}

let numArray = getArray<number>([1,2,3,4]);
let strArray = getArray<string>(['Ram', 'Laxman', 'Sita']);

numArray.push(5);
```
