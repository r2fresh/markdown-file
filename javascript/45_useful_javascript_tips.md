영문으로 보다가 나중에 제게 도움이 될듯해서 번역을 했습니다.

번역이나 제가 해석을 잘못한게 있으면 알려주세요^^

**1. 처음 변수에 값을 지정할 때 'var' 키워드를 잊지말자** 

**2. "\=\=" 대신에 "\=\=\=" 를 사용하자**

"\=\=" 는 문법에서 자동으로 Type을 변경한다. 편한 기능 일 수 있지만 정확한 비교가 어렵다. "\=\=\="는 자동으로 Type이 변경이 되지 않는다. 그래서 비교가 조금다 빠르고 정확하다.

```javascript
[10] === 10    // is false
[10]  == 10    // is true
'10' == 10     // is true
'10' === 10    // is false
 []   == 0     // is true
 [] ===  0     // is false
 '' == false   // is true but true == "a" is false
 '' ===   false // is false 
 ```
**3. undefined, null, 0, false, NaN, ''(empty string)은 모두 false(거짓)으로 된다.**

**4. 라인의 종료 표시는 세미콜론을 사용하자**

**5. 객체의 생성자를 만들자**

```javascript
function Person(firstName, lastName){
    this.firstName =  firstName;
    this.lastName = lastName;
}

var Saad = new Person("Saad", "Mousliki");
```

**6. typeof, instanceof, constructor의 사용은 조심해야한다.**

```javascript
var arr = ["a", "b", "c"];
typeof arr;   // return "object" 
arr  instanceof Array // true
arr.constructor();  //[]
```

**7. 자기 호출 함수를 만들자**

이것은 종종 자기호출익명함수 또는 즉시호출함수이라고 합니다. 이것은 만들때 자동으로 실행됩니다.

```javascript
(function(){
    // some private code that will be executed automatically
})();

(function(a,b){
    var result = a+b;
    return result;
})(10,20)
```

**8. 배열에서 랜덤 아이템을 가지고 오자**

```javascript
var items = [12, 548 , 'a' , 2 , 5478 , 'foo' , 8852, , 'Doe' , 2145 , 119];

var randomItem = items[Math.floor(Math.random() * items.length)];
```

**9. 특정 범위에서 랜덤 숫자를 가지고 오자**

최소와 최대 사이에서 각각의 급여를 테스트 할 목적으로 가상의 데이터를 만들때 사용하면 좋습니다.

```javascript
var x = Math.floor(Math.random() * (max - min + 1)) + min;
```

**10. 0과 최대에서 숫자를 배열로 만들때 사용하자**

```javascript
var numbersArray = [] , max = 100;

for( var i=1; numbersArray.push(i++) < max;);  // numbers = [0,1,2,3 ... 100]
```

**11. 알파벳 문자들에서 랜덤으로 세트를 만들때**

```javascript
function generateRandomAlphaNum(len) {
    var rdmstring = "";
    for( ; rdmString.length < len; rdmString  += Math.random().toString(36).substr(2));
    return  rdmString.substr(0, len);

}
```

**12. 숫자 배열을 썪을때**

```javascript
var numbers = [5, 458 , 120 , -215 , 228 , 400 , 122205, -85411];
numbers = numbers.sort(function(){ return Math.random() - 0.5});
/* the array numbers will be equal for example to [120, 5, 228, -215, 400, 458, -85411, 122205]  */
```

**13. 문자열에 trim 기능 함수를 만들자**

```javascript
String.prototype.trim = function(){return this.replace(/^\s+|\s+$/g, "");};
```

**14. 배열에 다른 배열을 추가 할때**

```javascript
var array1 = [12 , "foo" , {name "Joe"} , -2458];

var array2 = ["Doe" , 555 , 100];
Array.prototype.push.apply(array1, array2);
/* array1 will be equal to  [12 , "foo" , {name "Joe"} , -2458 , "Doe" , 555 , 100] */
```

**15. arguments는 배열의 객체로 변환**

```javascript
var argArray = Array.prototype.slice.call(arguments);
```

**16.주어진 argument가 숫자인지 확인**

```javascript
function isNumber(n){
    return !isNaN(parseFloat(n)) && isFinite(n);
}
```

**17. 주어진 argument가 배열인지 확인**

```javascript
function isArray(obj){
    return Object.prototype.toString.call(obj) === '[object Array]' ;
}
```

혹시 toString을 오버라이드 해서 사용하시는 경우, 위와 같은 함수를 사용할 수 없을 수 있습니다.
새로운 Array 메소드인 isArray를 사용하시면 됩니다.

```javascript
Array.isArray(obj); // its a new Array method
```

여러 프레임으로 작동하지 않을 경우에도 instanceof를 사용할 수 있습니다. 그러나 많은 contexts가 있다면 당신은 잘못된 결과를 얻을 수 있습니다.

```javascript
var myFrame = document.createElement('iframe');
document.body.appendChild(myFrame);

var myArray = window.frames[window.frames.length-1].Array;
var arr = new myArray(a,b,10); // [a,b,10]

// instanceof will not work correctly, myArray loses his constructor
// constructor is not shared between frames
arr instanceof Array; // false
```

**18. 숫자 배열에서 작은수 또는 큰수를 가지고 올때**

```javascript
var  numbers = [5, 458 , 120 , -215 , 228 , 400 , 122205, -85411];
var maxInNumbers = Math.max.apply(Math, numbers);
var minInNumbers = Math.min.apply(Math, numbers);
```

**19. 빈 배열 만들기**

```javascript
var myArray = [12 , 222 , 1000 ];
myArray.length = 0; // myArray will be equal to [].
```

**20. 배열에서 item을 제거하기 위해 delete를 사용하지 말자**

delete 대신에 splice를 사용하여 배열의 item을 삭제한다. delete를 사용하여 배열에서 제거를 하면 undefined이 item으로 교체가 될것이다.


```javascript
//delete를 사용
var items = [12, 548 ,'a' , 2 , 5478 , 'foo' , 8852, , 'Doe' ,2154 , 119 ];
items.length; // return 11
delete items[3]; // return true
items.length; // return 11
/* items will be equal to [12, 548, "a", undefined × 1, 5478, "foo", 8852, undefined × 1, "Doe", 2154,       119]   */
```

```javascript
//use splice
var items = [12, 548 ,'a' , 2 , 5478 , 'foo' , 8852, , 'Doe' ,2154 , 119 ];
items.length; // return 11
items.splice(3,1) ;
items.length; // return 10
/* items will be equal to [12, 548, "a", 5478, "foo", 8852, undefined × 1, "Doe", 2154,       119]   */
```
delete는 객체의 property를 삭제하는 데 사용하는 것이다.

**21. length를 이용하여 배열의 줄이는 법**

19번의 예제와 마찬가지로 length를 이용하여 자를 수 있다.

```javascript
var myArray = [12 , 222 , 1000 , 124 , 98 , 10 ];
myArray.length = 4; // myArray will be equal to [12 , 222 , 1000 , 124].
```
보너스로 배열의 길이를 더 높은 값으로 설정을 하면, 길이도 변경되고 새로 추가된 곳에는 undefind로 생성 됩니다. 배열의 길이는 읽기 전용 속성이 아닙니다.

```javascript
myArray.length = 10; // the new array length is 10 
myArray[myArray.length - 1] ; // undefined
```

**22. 논리적 and/or 조건을 사용하자**

추가적으로 잘 쓰면 좋을 듯 하다. 간단히 조건이 맞으면 실행하는 함수를 할 경우 꼭 쓰임새가 많을 듯 합니다.(개인적 의견)

```javascript
var foo = 10;
foo == 10 && doSomething(); // is the same thing as if (foo == 10) doSomething();
foo == 5 || doSomething(); // is the same thing as if (foo != 5) doSomething();
```

논리적 AND는 함수의 인수 값을 기본으로 설정하게 곳에도 사용할 수 있습니다.

```javascript
Function doSomething(arg1){ 
    Arg1 = arg1 || 10; // arg1 will have 10 as a default value if it’s not already set
}
```

**23. 배열의 item을 loop를 돌리면 함수의 메소드를 적용하는 map()을 사용하자 **

```javascript
var squares = [1,2,3,4].map(function (val) {
    return val * val;
});
// squares will be equal to [1, 4, 9, 16]
```

**24. N 진수 자리에 숫자를 반올림**

```javascript
var num =2.443242342;
num = num.toFixed(4);  // num will be equal to 2.4432
```

**25. 부동소수점 문제**

```javascript
0.1 + 0.2 === 0.3 // is false
9007199254740992 + 1 // is equal to 9007199254740992
9007199254740992 + 2 // is equal to 9007199254740994
```

이런 현상이 나타나는 이유가 무엇일까요? 그것은 모든 자바스크립트의 숫자는 IEEE 754 표준에 따라 64 비트 이진 내부적으로 표현 부동 소수점 이라는 입니다.

이러한 문제를 해결하기 위해서는 toFixed() 또는 toPrecision()을 사용하십시오

**26. fon-in loop를 사용하여 객체의 속성을 체크하자**

이 코드는 객체의 prototype에서 properties의 반복을 피하는 방법이다.

```javascript
for (var name in object) {
    if (object.hasOwnProperty(name)) {
        // do something with name
    }
}
```

**27. 쉽표 연산자**

```javascript
var a = 0;
var b = ( a++, 99 );
console.log(a);  // a will be equal to 1
console.log(b);  // b is equal to 99
```

**28. 계산이나 쿼리가 필요한 캐시 변수**

jQuery의 selector의 경우에, DOM 요소를 캐시 할수 있다.

```javascript
var navright = document.querySelector('#right');
var navleft = document.querySelector('#left');
var navup = document.querySelector('#up');
var navdown = document.querySelector('#down');
```
**29. isFinite()에 넘겨주기전에 argument를 확인하자**

```javascript
isFinite(0/0) ; // false
isFinite("foo"); // false
isFinite("10"); // true
isFinite(10);   // true
isFinite(undifined);  // false
isFinite();   // false
isFinite(null);  // true  !!!
```

**30. 배열에서 마이너스 인덱스를 피하자**

```javascript
var numbersArray = [1,2,3,4,5];
var from = numbersArray.indexOf("foo") ;  // from is equal to -1
numbersArray.splice(from,2);    // will return [5]
```
indexOf에 전달되는 인수가 음수인지 확인하자

**31. 직렬화와 역직렬화(with json)**

```javascript
var person = {name :'Saad', age : 26, department : {ID : 15, name : "R&D"} };

var stringFromPerson = JSON.stringify(person);
/* stringFromPerson is equal to "{"name":"Saad","age":26,"department":{"ID":15,"name":"R&D"}}"   */

var personFromString = JSON.parse(stringFromPerson);
/* personFromString is equal to person object  */
```

**32. eval()과 Function 생성자를 피하자**

eval과 Function 생성자의 사용은 스크립트 엔진이 실행코드의 소스코드를 변환을 해야하기 때문에 각각 어려운 작업이다.

```javascript
var func1 = new Function(functionCode);
var func2 = eval(functionCode);
```

**33. with() 사용을 피하자**

with()를 사용하면 전역 범위에 변수를 만듭니다. 또 다른 변수와 같은 이름이라면 값을 덮어쓰거나 혼란을 줄수 있습니다.

**34. 배열에 for-in loop 사용을 피하자**

이거 대신에
```javascript
var sum = 0;
for (var i in arrayNumbers) {
    sum += arrayNumbers[i];
}
```

이것을 사용하는 것이 좋습니다.
```javascript
var sum = 0;
for (var i = 0, len = arrayNumbers.length; i < len; i++) {
    sum += arrayNumbers[i];
}
```

보너스로, i와 len의 인스턴스는 for loop의 첫번째 statement에 있기 때문에 한번만 실행된다. 이것을 사용하여 보다 빠를수...

```javascript
for (var i = 0; i < arrayNumbers.length; i++)
```

왜 arrayNumbers의 배열의 길이는 loop가 반복되면 다시 계산됩니다.

**35. setTimeout()과 setInterval()은 문자열이 아닌 함수를 전달한다.**

setTimeout()과 setInterval()에 문자열로 전달을 하면, 문자열은 eval과 같은 방법으로 평가될 것이고, 엄청나게 느릴 것이다. 아래를 사용하는 대신에

```javascript
setInterval('doSomethingPeriodically()', 1000);
setTimeOut('doSomethingAfterFiveSeconds()', 5000);
```

이것을 사용하자

```javascript
setInterval(doSomethingPeriodically, 1000);
setTimeOut(doSomethingAfterFiveSeconds, 5000);
```

**36. if/else 를 사용하는 대신 switch/case를 사용하자**

switch/case는 2개 이상의 경우에는 더 빠르며,더 나은 코드이며 우아할 것이다.
10개 이상일 경우에는 사용을 피하자

**37. 숫자의 범위와 switch/case문을 같이 사용하자**

숫자 범위와 switch/case문을 같이 사용하면 트릭이 가능하다.
완전 맘에 드는 트릭(개인적인 생각)

```javascript
function getCategory(age) {
    var category = "";
    switch (true) {
        case isNaN(age):
            category = "not an age";
            break;
        case (age >= 50):
            category = "Old";
            break;
        case (age <= 20):
            category = "Baby";
            break;
        default:
            category = "Young";
            break;
    };
    return category;
}
getCategory(5);  // will return "Baby"
```

**38. 프로토타입에 주어진 객체의 객체를 만들자**

포로토타입에 이와 같이 주어진 인수는 객체를 만들어서 함수에 쓰는 것이 가능하다

이 부분은 잘 이해가 되지 않는 부분이다. 조금 더 생각해 봐야지(개인적인 생각)

```javascript
function clone(object) {
    function OneShotConstructor(){};
    OneShotConstructor.prototype= object;
    return new OneShotConstructor();
}
clone(Array).prototype ;  // []
```

**39. HTML을 escaper 함수를 사용하자**

```javascript
function escapeHTML(text) {
    var replacements= {"<": "&lt;", ">": "&gt;","&": "&amp;", "\"": "&quot;"};
    return text.replace(/[<>&"]/g, function(character) {
        return replacements[character];
    });
}
```

**40. 루프안에서 try-catch-finally를 사용하는 것을 피하자**

try-catch-finally 구성은 예외 객체를 변수에 할당하는 경우 catch 문구를 실행 할때마다 런타임의 현재 스코프에서 새로운 변수를 만든다.

이렇게 사용하는 대신

```javascript
var object = ['foo', 'bar'], i;
for (i = 0, len = object.length; i <len; i++) {
    try {
        // do something that throws an exception
    }
    catch (e) {
        // handle exception
    }
}
```

이렇게 사용하도록 하자

```javascript
var object = ['foo', 'bar'], i;
try {
    for (i = 0, len = object.length; i <len; i++) {
        // do something that throws an exception
    }
}
catch (e) {
    // handle exception
}
```

**41. XMLHttpRequests에 타임아웃을 설정하자**

XHR(예를 들어 네트워크 문제로) 시간이 오래 걸리는 경우 XHR호출과 함께 setTimerout()을 사용하여 접속된것을 중단할 수 있다

```javascript
var xhr = new XMLHttpRequest ();
xhr.onreadystatechange = function () {
    if (this.readyState == 4) {
        clearTimeout(timeout);
        // do something with response data
    }
}
var timeout = setTimeout( function () {
    xhr.abort(); // call error callback
}, 60*1000 /* timeout after a minute */ );

xhr.open('GET', url, true);

xhr.send();
```

보너스로 일반적으로 동기 Ajax을 완벽하게 호출하는 것은 피하자

**42. 웹소켓의 타임아웃 처리**

일반적으로 웹 소켓의 연결에서, 서버가 비활성 30초 후에 연결 시간을 제한 할 수 있습니다. 방화벽은 또한 일정 시간이 지난 후 연결 시간을 제한 할 수 있습니다.

타임아웃 이슈는 서버에 주기적으로 빈 메세지를 보내어 처리 할 수 있습니다.
코드에 두개의 함수를 추가: 하나는 살아있도록 연결을 유지하고, 다른 하나는 연결되어 있는 것을 취소하는 것입니다. 이 트릭은 타임아웃을 컨트롤 할 수 있습니다.

timerID를 추가
```javascript
var timerID = 0;
function keepAlive() {
    var timeout = 15000;
    if (webSocket.readyState == webSocket.OPEN) {
        webSocket.send('');
    }
    timerId = setTimeout(keepAlive, timeout);
}
function cancelKeepAlive() {
    if (timerID) {
        cancelTimeout(timerId);
    }
}
```

keepAlive() 함수는 webSocket 연결의 onOpen() 메소드 끝에 cancelKeepAlive()는 onClonse()메소드 끝에 추가가 되어야 한다.

**43. 원초적인 작업은 함수 호출보다 빠를 수 있다는 것을 명심하자. VanillaJS를 사용하자.**

예를 들어 아래의 보다는

```javascript
var min = Math.min(a,b);
A.push(v);
```
이것이 더빠르다
```javascript
var min = a < b ? a b;
A[A.length] = v;
```

**44. 코딩할 때 코드를 아름답게 하는 것을 잊지말자. 실제로 적용하기 전에 JSLint와 minification(압축)을 사용하자**

**45.JavaScript is awesome: Best Resources To Learn JavaScript**






























**출처**
> http://flippinawesome.org/2013/12/23/45-useful-javascript-tips-tricks-and-best-practices/





















