alert("Alert on incoming malicious virus!!");

//1) make a Rectangle class that stores width and Height, make a few instances and print out the proprties. Modify a few of the properties
//and print out the results again.

var Rectangle = function(width,height) //declaring object with "constructor function"
{
    this.width = width;
    this.height = height;
    this.area = function()
    {
        console.log("Area of the Rectangle is : " +this.width * this.height);
    }
} 

var myRect1 = new Rectangle(10,20); //calling objects/making intances
var myRect2 = new Rectangle(30,40);
var myRect3 = new Rectangle(50,60);
var myRect4 = new Rectangle(30,90);

console.log(myRect1.width); //calling objects' properties
console.log(myRect1.height);
myRect1.area();
console.log("---------------------");
//document.write(myRect1.width);
//document.write(myRect1.height);
console.log(myRect2.width); //calling objects' properties
console.log(myRect2.height);
myRect2.area();
console.log("---------------------")
console.log(myRect3.width); //calling objects' properties
console.log(myRect3.height);
myRect3.area();
console.log("---------------------")
console.log(myRect4.width); //calling objects' properties
console.log(myRect4.height);
myRect4.area();
console.log("---------------------")




//2) Adding getArea method using prototype property
Rectangle.prototype.getArea = function()
{
    console.log("Getting Area using prototype property : " +this.width * this.height);
}

console.log(Rectangle.prototype);
myRect1.getArea(); //calling method which is created using prototype property
myRect2.getArea();
myRect3.getArea();
myRect4.getArea();


//3) Assuming that the Rectangle contructor takes a width and height, why does the following output 20 instead of 200?
//this keyword is used to differentiate between Global var and Local Var.

Rectangle.prototype.getAreaForRect = function(width,height)  //this is because of Global scope and LOcal scope.
{
    console.log("Getting Area using prototype property : " +width * height);
}

console.log(Rectangle.prototype);
myRect1.getAreaForRect(4,5); //calling method which is created using prototype property
myRect2.getAreaForRect(5,6);
myRect3.getAreaForRect(7,8);
myRect4.getAreaForRect(11,2);


//4) make a variable whose value is an object with firstName and lastName properties
var obj = {
    firstName : "aa",
    lastName : "cc"
};
console.log(obj);

//5) try reading the middleName from a property by assigning to it.

var obj1 = {
    firstName : "aa",
    middleName : "bb",
    lastName : "cc"
};
console.log(obj1);


//6)Create a string with what looks like an object with firstName and lastName,use eval() property.

var myString = new String('2 + 2')
eval(myString.toString());
console.log(eval(myString.toString()));

/*var String = {
    firstName:"aa",
    lastName:"cc"
}
console.log(String.prototype);*/

//7) Using JSON.parse() method and following the rules of JSON.parse() method.
/*
const myString = '{"firstName":"John",  "lastName":"Kumar"}';
const obj = JSON.parse(myString);
obj.firstName = eval("(" +obj.firstName+")");*/



//8) Creating a Person dynamic object
function Person(firstName,lastName,age,skills,dateOfbirth,address,married,profession)
{
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
    this.skills = skills;
    this.dateOfbirth = dateOfbirth;
    this.address = address;
    this.married = married;
    this.profession = profession;
}

Person1 = new Person("aa","cc",99,['java','c#'],"01/01/1947",{city:"Bangalore",pincode:67856},"false","AnalystA4");
Person2 = new Person("ss","tt",3,["c","c#"],"02/02/1948",{city:"Mumbai",pincode:564309},"false","AnalystA10");

console.log(Person1);
console.log(Person2);

print=function()       //printing the object using Global print method.
{
    console.log(Person1);
    console.log(Person2);
}();



//9) Abhishek and Amithab program
function Person(firstName,lastName,age,skills,dateOfbirth,address,married,profession)
{
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
    this.skills = skills;
    this.dateOfbirth = dateOfbirth;
    this.address = address;
    this.married = married;
    this.profession = profession;
}
Amithabh = new Person("Amithabh","Bacchan",99,['java','c#'],"01/01/1947",{city:"Bangalore",pincode:67856},"false","AnalystA4");
Abhishek = new Person("Abhishek",55,["html","css"],"05/06/1975","false","JrAnalyst");
Aaradhya = new Person("Aaradhya",10,"01/01/2005","false","film");

var Abhishek = Object.create(Amithabh); //inheriting the common properties/storing Amithabh object in Abhishek
var Aaradhya = Object.create(Abhishek);  //it has become Heirarchical inheritance now--> Amithabh is a supermost class 
//var Aaradhya = Object.create(Amithabh);
print = function()
{
    console.log(Amithabh);
    console.log(Abhishek.lastName);
    console.log(Abhishek.address);
    console.log(Aaradhya.lastName);
    console.log(Aaradhya.skills);
    console.log(Aaradhya.address);
    console.log(Aaradhya.firstName);
}();



//10) Bank Account Application

function Account(accountNumber,accountHolderName,accountBalance) 
{
    this.accountNumber = accountNumber;
    this.accountHolderName = accountHolderName;
    this.accountBalance = accountBalance;
}
function Savings(isSalary,accountNumber,accountHolderName,accountBalance)
{
    this.isSalary = isSalary;
    this.accountNumber = accountNumber;
    this.accountHolderName = accountHolderName;
    this.accountBalance = accountBalance;
    this.withdraw = function(amount)
    {
        if(this.accountBalance > 0 && this.accountBalance < 100)
        {
            console.log("Insuffient balance! You have less than 100 rs.");
        } 
        if((this.accountBalance >= 100 && this.accountBalance <= 500) && amount === 200)
        {
            this.accountBalance = this.accountBalance - amount;
            console.log("Your money after debiting : " + this.accountBalance);
        }
        if((this.accountBalance > 500 && this.accountBalance <= 5000) && amount === 500 || amount === 2000);
        {
            this.accountBalance = this.accountBalance - amount;
            console.log("Your money after debiting : " + this.accountBalance);
        }
        if((this.accountBalance > 5000) && amount === 200 || amount === 500 || amount ===2000)
        {
            this.accountBalance = this.accountBalance - amount;
            console.log("Your money after debiting : " + this.accountBalance);
        }
        if(this.accountBalance <= 0)
        {
            console.log("ATM says! I cant give you the money, Please deposit some amount to withdraw later, Now Please goo!");
        }
      
    };
    this.getCurrentBalance = function()
    {
        console.log("Your current Account balance is : " + this.accountBalance);
    };
}
function Current(odLimit,accountNumber,accountHolderName,accountBalance)
{
    this.odLimit = odLimit;
    this.accountNumber = accountNumber;
    this.accountHolderName = accountHolderName;
    this.accountBalance = accountBalance;
    this.withdraw = function(amount)
    {
        if(odLimit > 500)
        {
            if((this.accountBalance > 500 && this.accountBalance < 2000) && amount === 200 || amount === 500)
            {
                this.accountBalance = this.accountBalance - amount;
                console.log("Your balance after debiting the money is : " +this.accountBalance);
            }
            if((this.accountBalance > 2000) && amount=== 200 || amount === 500 || amount === 2000)
            {
                this.accountBalance = this.accountBalance - amount;
                console.log("Your balance after debiting the money is : " +this.accountBalance);
            }
        } 
        else
        {  
            console.log("Your odLimit for Current acocunt is less than 500");
        }  
    };
    this.getCurrentBalance = function()
    {
        console.log("Your current Account balance is : " + this.accountBalance);
    };
       
}

var obj1 = new Account(12345,"Kishan",65546);
console.log(obj1);
//var Savings = Object.create(Account); //inheriting the common properties
//var Current = Object.create(Account); //inheriting the common properties

var objSavings = new Savings("true",98765,"Virat",546776); //creating Savings object
console.log(objSavings);
console.log(objSavings.withdraw(500));
console.log(objSavings.getCurrentBalance());

var objCurrent = new Current(550,9876543,"Nihar",5467878); //creating Current object
console.log(objCurrent);
console.log(objCurrent.withdraw(2000));
console.log(objCurrent.getCurrentBalance());