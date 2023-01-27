# Call-and-apply

let obj = {
 a: 1,
 b: 2,
 set: function (a, b) {
 this.a = a;
 this.b = b;
 }
};
obj.set(3, 7); // normal syntax
obj.set.call(obj, 3, 7); // equivalent to the above
obj.set.apply(obj, [3, 7]); // equivalent to the above; note that an array is used
console.log(obj); // prints { a: 3, b: 5 }
let myObj = {};
myObj.set(5, 4); // fails; myObj has no `set` property
obj.set.call(myObj, 5, 4); // success; `this` in set() is re-routed to myObj instead of obj
obj.set.apply(myObj, [5, 4]); // same as above; note the array
console.log(myObj); // prints { a: 3, b: 5 }
