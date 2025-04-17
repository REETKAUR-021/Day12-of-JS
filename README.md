//Asynchronous

console.log("Monday");
console.log("Tuesday");

function App(){
    console.log("I create a app");
}

setTimeout(App,3000);  //setTimeout function print func after some time 

console.log("Wednesday");

//Callbacks   pass one function to another function

function calculator(a,b){
    console.log(a+b);
}
function calculate(a,b,calculatorCallback){
    calculatorCallback(a,b);
}
calculate(3,2,calculator);

//Nesting statement

let age = 23;
if(age>=10){
    if(age<=18){
        console.log("below 18");
    }else{
        console.log("above 18");
    }
}else{
    console.log("under age");
}

//Nested loop

for(let i=0 ; i<5 ; i++){
    for(let j=0 ; j<5 ; j++){
        console.log(j);
    }
}

//Callback Hell

function getData(dataId,getNextData){
    console.log("data",dataId);
    if(getNextData){
        getNextData();
    }
}

//Nested callbacks
getData(1,()=>{
    getData(2)
});

setTimeout(getData,3000);

//Promises
let promise=new Promise((resolve,reject) => {
    console.log("i comleted my promise");
    resolve("success");

});

function data(id,nextData){
    return new Promise ((resolve,reject)=>{
        setTimeout(()=>{
            console.log("id",id);
            resolve("success");
            if(nextData){
                nextData();
            }
        },5000);
    });
}

//Promise.then
const getPromise=()=>{
    return new Promise((resolve,reject)=>{
        console.log("here i complete my promise");
        resolve("successfully complete promise");
        reject("error");
    });
};

let promiser=getPromise();
promiser.then((res)=>{
    console.log("promise fulfilled");
    
});

//Promise.catch
promiser.catch((err)=>{
    console.log("rejected");
});

//promise chain

function asyncFunc(){
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            console.log("some data1");
            resolve("success");
        },4000);
    });
}

console.log("fetching data1");
let p1 = asyncFunc();
p1.then((res)=>{
    console.log(res);
})

//Async-Await

function hello(){
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            console.log("hello");
            resolve("success");
        },4000);
    });
}

async function getWeatherData() {
    await hello();
    await hello();
}
