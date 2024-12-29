# Data Structures

In this topic, we will talk in detail about data structures. We will explore what a data structure is, what an array is, what an object is, and how to use arrays and objects.

- [Data Structures](#data-structures)
  - [Learning Outcomes](#learning-outcomes)
  - [What is a Data Structure?](#what-is-a-data-structure)
  - [Array](#array)
    - [Array Methods](#array-methods)
      - [Adding Values to an Array](#adding-values-to-an-array)
      - [Finding Values in an Array](#finding-values-in-an-array)
      - [Removing Values from an Array](#removing-values-from-an-array)
    - [Array Iteration](#array-iteration)
  - [Object](#object)
    - [`Object.keys()` Method](#objectkeys-method)
    - [`Object.values()` Method](#objectvalues-method)
    - [`Object.entries()` Method](#objectentries-method)
  - [Exercises](#exercises)
    - [Exercise 1 - Basic Array Operations](#exercise-1---basic-array-operations)
    - [Exercise 2 - Array Iteration](#exercise-2---array-iteration)
    - [Exercise 3 - Basic Object Operations](#exercise-3---basic-object-operations)
    - [Exercise 4 - Modifying Object Properties](#exercise-4---modifying-object-properties)

## Learning Outcomes

After completing this topic, you'll be able to:

- Define what a data structure is
- Explain what an array is
- Explain what an object is
- Use arrays and objects
- Use basic array methods

## What is a Data Structure?

We already know what variable is and that it is used to store data. But so far we were able to store only one value in a variable or describe only one thing. For example, we could have a variable named `firstName` that stores the first name of a person. But what if we want to store the first name, last name, age, and address of a person? We could create a variable for each of these values, but that would be very inefficient. Instead, we can use a data structure to store all of these values in one place.

A data structure is a way of organizing data in a computer's memory. Data structures are used to store collections of data. For example, we can use an **array** to store a list of numbers or a list of names. We can use an **object** to store information about a person (first name, last name, age, address, etc.). We can use a **set** to store a list of unique values. We can use a **map** to store a list of key-value pairs.

> Even though there are lot of different data structures, we'll focus on arrays and objects in this topic.

## Array

An array is a collection of values that are stored in a single variable. Arrays are used to store lists of values. Arrays are used to store collections of data that are related to each other. For example, we can use an array to store a list of numbers or a list of names.

To create an array, we use the `[]` operator. For example, we can create an array named `numbers` that contains the numbers `1`, `2`, and `3` like this:

```javascript
const numbers = [1, 2, 3];
```
Or we can create an array named `names` that contains the names `John`, `Jane`, and `Jack` like this:

```javascript
const names = ['John', 'Jane', 'Jack'];
```

We can access the values in an array using the index of the value. The index of the first value in an array is `0`. For example, if we want to access the first value in the `numbers` array, we can use the index `0` like this:

```javascript
const numbers = [1, 2, 3];

console.log(numbers[0]);
```
**Expected output**:

```
1
```

We can also use the index of the value to change the value in the array. For example, if we want to change the value of the first value in the `numbers` array to `10`, we can use the index `0` like this:

```javascript
const numbers = [1, 2, 3];

numbers[0] = 10;

console.log(numbers);
```
**Expected output**:

```
[10, 2, 3]
```

### Array Methods

Methods are functions that are associated with an object. It means that in Javascript we can do something with an object by calling a built-in function that is associated with that object.

There are lots of methods that we can use to manipulate arrays. For example, we can use the `push()` method to add a value to the end of an array, the `pop()` method to remove a value from the end of an array, the `shift()` method to remove a value from the beginning of an array, and the `unshift()` method to add a value to the beginning of an array.

All array methods are listed in the [Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) section of the MDN web docs.

#### Adding Values to an Array

We can use the `push()` method to add a value to the end of an array. For example, if we want to add the number `4` to the end of the `numbers` array, we can use the `push()` method like this:

```javascript
const numbers = [1, 2, 3];

numbers.push(4);

console.log(numbers);
```
**Expected output**:

```
[1, 2, 3, 4]
```


#### Finding Values in an Array

We can use the `indexOf()` method to find the index of a value in an array. For example, if we want to find the index of the number `2` in the `numbers` array, we can use the `indexOf()` method like this:

```javascript
const numbers = [1, 2, 3];

console.log(numbers.indexOf(2));
```
**Expected output**:

```
1
```

> If the value is not found in the array, the `indexOf()` method will return `-1`.

#### Removing Values from an Array

We can use splice() method to remove a value from an array. For example, if we want to remove the number `2` from the `numbers` array, we can use the `splice()` method like this:

```javascript
const numbers = [1, 2, 3];

numbers.splice(1, 1);

console.log(numbers);
```
**Expected output**:

```
[1, 3]
```

> The first argument of the `splice()` method is the index of the value that we want to remove and the second argument is the number of values that we want to remove.
> The `splice()` method will return an array of the removed values.
> If we don't specify the second argument, the `splice()` method will remove all values starting from the index that we specified in the first argument.
> If we specify the second argument as `0`, the `splice()` method will not remove any values.
> Remember, that to remove a value from array using this method, we need to know the index of the value that we want to remove.

### Array Iteration

We can use the `for` loop to iterate over an array. For example, if we want to print each value in the `numbers` array on a new line, we can use the `for` loop like this:

```javascript
const days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'];

for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i]);
}
```
**Expected output**:

```
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
```

> Pay attention to the condition of the `for` loop. We need to use the `length` property of the array in the condition of the `for` loop to make sure that we don't go out of bounds of the array.
> 
> The `length` property of an array returns the number of values in the array.
> 
> The `length` property of an array is always one more than the index of the last value in the array.
> 
> Also, remember, that `i` is the value, that increments on each iteration of the `for` loop. We can use the value of `i` to access the values in the array.
> 
> Index of the first value in an array is `0`, so the index of the last value in an array is `length - 1`.

## Object

An object is a collection of key-value pairs that are stored in a single variable. Objects are used to store information about something. For example, we can use an object to store information about a person (first name, last name, age, address, etc.).

To create an object, we use the `{}` operator. For example, we can create an object named `person` that contains the first name `John`, the last name `Doe`, and the age `25` like this:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};
```

We can access the values in an object using the key of the value. For example, if we want to access the first name in the `person` object, we can use the key `firstName` like this:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

console.log(person.firstName); // John
```

We can also use the key of the value to change the value in the object. For example, if we want to change the value of the first name in the `person` object to `Jane`, we can use the key `firstName` like this:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

person.firstName = 'Jane';

console.log(person); // { firstName: 'Jane', lastName: 'Doe', age: 25 }
```

As for arrays, there are lots of methods that we can use to manipulate objects also. For example, we can use the 

### `Object.keys()` Method
The `Object.keys()` method returns the keys of an object as an array. For example, if we want to get the keys of the `person` object as an array, we can use the `Object.keys()` method like this:
```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

console.log(Object.keys(person)); // [ 'firstName', 'lastName', 'age' ]
```
This can also be used for iterating over the properties of an object. For example, if we want to print each key in the `person` object, we can use the `Object.keys()` method like this:
```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

for (let key of Object.keys(person)) {
  console.log(key);
}

// Väljund:
// firstName
// lastName
// age

```
If we do not want to use a `for...of` loop, we can also use a `for` loop like this:

```javascript

const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

for (let i = 0; i < Object.keys(person).length; i++) {
  console.log(Object.keys(person)[i]);
}

// output:
// firstName
// lastName
// age

```
### `Object.values()` Method 
The `Object.values()` method returns the values of an object as an array. For example, if we want to get the values of the `person` object as an array, we can use the `Object.values()` method like this:
```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

console.log(Object.values(person)); // [ 'John', 'Doe', 25 ]
```
### `Object.entries()` Method 
The `Object.entries()` method returns an array of key-value pairs of an object. For example, if we want to get the key-value pairs of the `person` object as an array, we can use the `Object.entries()` method like this:
```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

console.log(Object.entries(person)); // [ [ 'firstName', 'John' ], [ 'lastName', 'Doe' ], [ 'age', 25 ] ]
```
If we want to output key-value pairs one by one, we can use a `for` loop like this:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

for (let i = 0; i < Object.entries(person).length; i++) {
  console.log(Object.entries(person)[i]);
}

// Output:
// [ 'firstName', 'John' ]
// [ 'lastName', 'Doe' ]
// [ 'age', 25 ]
```

All object methods are listed in the [Object Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) section of the MDN web docs.

## Exercises

Create a file named `index.js` (or another name of your choice) and start adding solutions to the exercises below.

> Always test your code by running the `index.js` file using the `node index.js` command.

### Exercise 1 - Basic Array Operations

**Objective**: Add elements to an array and print them.

**Description**: Create an array to store a list of three favorite fruits. Add two more fruits to the array using array methods. Finally, print each fruit in the array on a new line.

> You can use the `push()` method to add elements to an array.
> 
> Use the `for` loop to print each element in the array on a new line.

<details>
  <summary>Solution</summary>

```javascript
const fruits = ['apple', 'banana', 'orange'];

fruits.push('strawberry');
fruits.push('pineapple');

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```
![Array](array.gif)

</details>

### Exercise 2 - Array Iteration

**Objective**: Find the sum of all numbers in an array.

**Description**: Write a JavaScript program that creates an array of numbers. Iterate over the array and compute the sum of its elements. Print the final sum.

> Probably You need to use extra variable to store the sum of all numbers.

<details>
  <summary>Solution</summary>

```javascript
const numbers = [1, 2, 3, 4, 5];

let sum = 0;

for (let i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}

console.log(sum);
```
**Expected output**:

```
15
```
</details>

If you want to solve additional exercises, you can find some here: [Additional Exercises for Arrays](Exercises-Arrays.md).

### Exercise 3 - Basic Object Operations

**Objective**: Create an object and access its properties.

**Description**: Define a JavaScript object named `car` with properties `make`, `model`, and `year`. Assign appropriate values to each. Then, print the `make` and `year` of the car in a sentence.

> You can access the properties of an object using the `.` operator.
>
> You can use the `+` operator to concatenate strings or use template literals.

<details>
  <summary>Solution</summary>

```javascript
const car = {
  make: 'Toyota',
  model: 'Corolla',
  year: 2019
};

console.log(`I drive a ${car.year} ${car.make} ${car.model}.`);
```

**Expected output**:

```
I drive a 2019 Toyota Corolla.
```


</details>

### Exercise 4 - Modifying Object Properties

**Objective**: Update and add new properties to an object.

**Description**: Given an object `student` with properties `name`, `age`, and `grade`, update the `age`, add a new property `subject`, and then print the entire object.

Example `student` object:

```javascript
const student = {
  name: 'John Doe',
  age: 16,
  grade: 10
};
```

> You can update the properties of an object using the `.` operator.
>
> You can add new properties to an object using the `.` operator.
>
> You can use `console.log()` to print the entire object.

<details>
  <summary>Solution</summary>

```javascript
const student = {
  name: 'John Doe',
  age: 16,
  grade: 10
};

student.age = 17;

student.subject = 'Math';

console.log(student);
```

**Expected output**:

```
{ name: 'John Doe', age: 17, grade: 10, subject: 'Math' }
```

</details>

If you want to solve additional exercises on objects, you can find some here: [Addditional exercises.](Exercises-Objects.md)

# Veri Yapıları

Bu konuda, veri yapıları hakkında detaylıca konuşacağız. Veri yapısının ne olduğunu, bir dizinin ne olduğunu, bir nesnenin ne olduğunu ve diziler ile nesnelerin nasıl kullanıldığını inceleyeceğiz.

- [Veri Yapıları](#veri-yap%C4%B1lar%C4%B1)
  - [Öğrenme Amaçları](#%C3%B6%C4%9Frenme-ama%C3%A7lar%C4%B1)
  - [Veri Yapısı Nedir?](#veri-yap%C4%B1s%C4%B1-nedir)
  - [Dizi](#dizi)
    - [Dizi Metotları](#dizi-metotlar%C4%B1)
      - [Diziye Değer Ekleme](#diziye-de%C4%9Fer-ekleme)
      - [Dizide Değer Bulma](#dizide-de%C4%9Fer-bulma)
      - [Diziden Değer Silme](#diziden-de%C4%9Fer-silme)
    - [Dizi İterasyonu](#dizi-%C4%B0terasyonu)
  - [Nesne](#nesne)
    - [`Object.keys()` Metodu](#objectkeys-metodu)
    - [`Object.values()` Metodu](#objectvalues-metodu)
    - [`Object.entries()` Metodu](#objectentries-metodu)
  - [Alıştırmalar](#al%C4%B1%C5%9Ft%C4%B1rmalar)
    - [Alıştırma 1 - Temel Dizi İşlemleri](#al%C4%B1%C5%9Ft%C4%B1rma-1---temel-dizi-%C4%B0%C5%9Flemleri)
    - [Alıştırma 2 - Dizi İterasyonu](#al%C4%B1%C5%9Ft%C4%B1rma-2---dizi-%C4%B0terasyonu)
    - [Alıştırma 3 - Temel Nesne İşlemleri](#al%C4%B1%C5%9Ft%C4%B1rma-3---temel-nesne-%C4%B0%C5%9Flemleri)
    - [Alıştırma 4 - Nesne Özelliklerini Değiştirme](#al%C4%B1%C5%9Ft%C4%B1rma-4---nesne-%C3%B6zelliklerini-de%C4%9Fi%C5%9Ftirme)

## Öğrenme Amaçları

Bu konuyu tamamladığınızda:

- Veri yapısını tanımlayabileceksiniz.
- Dizinin ne olduğunu açıklayabileceksiniz.
- Nesnenin ne olduğunu açıklayabileceksiniz.
- Diziler ve nesneler kullanabileceksiniz.
- Temel dizi metotlarını kullanabileceksiniz.

## Veri Yapısı Nedir?

Bir değişkenin ne olduğunu ve veri depolamak için kullanıldığını zaten biliyoruz. Ancak, şu ana kadar bir değişkende yalnızca bir değer depolayabildik ya da yalnızca bir şeyi tanımlayabildik. Örneğin, bir kişinin adını depolamak için `firstName` adlı bir değişken kullanabiliriz. Ancak, bir kişinin adı, soyadı, yaşı ve adresini depolamak istersek ne olur? Her bir değer için ayrı bir değişken oluşturabiliriz, ancak bu çok verimsiz olur. Bunun yerine, tüm bu değerleri tek bir yerde depolamak için bir veri yapısı kullanabiliriz.

Veri yapısı, bilgisayar belleğinde veriyi düzenleme yöntemidir. Veri yapıları, veri koleksiyonlarını depolamak için kullanılır. Örneğin, bir liste veya isim listesini depolamak için bir **dizi** kullanabiliriz. Bir kişi hakkında bilgi depolamak için (ad, soyad, yaş, adres vb.) bir **nesne** kullanabiliriz. Benzersiz değerleri depolamak için bir **set** kullanabiliriz. Anahtar-değer çiftlerini depolamak için bir **map** kullanabiliriz.

> Çok sayıda farklı veri yapısı olmasına rağmen, bu konuda diziler ve nesneler üzerinde yoğunlaşacaktır.

## Dizi

Bir dizi, tek bir değişkende depolanan değer koleksiyonudur. Diziler, ilgili değerlerin listelerini depolamak için kullanılır. Örneğin, bir liste veya isim listesi depolamak için bir dizi kullanabiliriz.

Bir dizi oluşturmak için `[]` operatörünü kullanırız. Örneğin, `numbers` adlı bir dizi oluşturabilir ve `1`, `2` ve `3` sayılarını şu şekilde ekleyebiliriz:

```javascript
const numbers = [1, 2, 3];
```
Veya `names` adlı bir dizi oluşturup `John`, `Jane` ve `Jack` isimlerini şu şekilde ekleyebiliriz:

```javascript
const names = ['John', 'Jane', 'Jack'];
```

Bir dizideki değerlere, değerin dizindeki sırası (indeksi) kullanılarak erişilebilir. Dizideki ilk değerin sırası `0`'dır. Örneğin, `numbers` dizisindeki ilk değere erişmek istersek, indeks `0`'i kullanabiliriz:

```javascript
const numbers = [1, 2, 3];

console.log(numbers[0]);
```
**Beklenen çıktı**:

```
1
```

Bir dizideki değerleri değiştirebiliriz de. Örneğin, `numbers` dizisindeki ilk değeri `10` olarak değiştirmek istersek, indeks `0`'i kullanabiliriz:

```javascript
const numbers = [1, 2, 3];

numbers[0] = 10;

console.log(numbers);
```
**Beklenen çıktı**:

```
[10, 2, 3]
```

### Dizi Metotları

Metotlar, bir nesne ile ilişkili olan fonksiyonlardır. Bu, JavaScript'te bir nesne ile şu işlemleri yapabileceğimiz anlamına gelir: nesneye bağlı bir fonksiyon çağırabiliriz.

Dizilerle işlem yapmamıza olanak tanıyan birçok metod vardır. Örneğin, `push()` metodunu kullanarak bir değeri bir dizinin sonuna ekleyebiliriz, `pop()` metodunu kullanarak bir değeri dizinin sonundan silebiliriz, `shift()` metodunu kullanarak bir değeri dizinin başından silebiliriz ve `unshift()` metodunu kullanarak bir değeri dizinin başına ekleyebiliriz.

Tüm dizi metotlarını MDN web dokümanlarının [Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) bölümünde bulabilirsiniz.

#### Diziye Değer Ekleme

`push()` metodunu kullanarak bir değeri bir dizinin sonuna ekleyebiliriz. Örneğin, `numbers` dizisinin sonuna `4` sayısını eklemek istersek, `push()` metodunu şu şekilde kullanabiliriz:

```javascript
const numbers = [1, 2, 3];

numbers.push(4);

console.log(numbers);
```
**Beklenen çıktı**:

```
[1, 2, 3, 4]
```


#### Dizide Değer Bulma

`indexOf()` metodunu kullanarak bir dizide bir değerin indeksini bulabiliriz. Örneğin, `numbers` dizisinde `2` sayısının indeksini bulmak istersek, `indexOf()` metodunu şu şekilde kullanabiliriz:

```javascript
const numbers = [1, 2, 3];

console.log(numbers.indexOf(2));
```
**Beklenen çıktı**:

```
1
```

> Dizide değer bulunamazsa, `indexOf()` metodu `-1` döndürecektir.

#### Diziden Değer Silme

