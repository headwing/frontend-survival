# Typescript

#### REPL

```
npx ts-node
```

#### 변수에 대한 타입을 선언

```javascript
  let name : string

  let human : {
    name : string;
    age : number;
  }
```

#### 타입 정의하기

```javascript
type Human = {
  name : string;
  age : number;
}

interface Person {
  name : string;
  age : number;
}

function add(x : number, y : number) : number{
    return x + y
}
```

#### 배열과 튜플

```javascript
let numbers : number[];
numbers =[1,2,3]

let pair : [string,  number];
pair = ['hp', 256]
```

#### 타입 추론

```javascript
const name = '홍길동';
```

#### Union Type (합집합)

```javascript
type Category = 'food' | 'toy' | 'bag'

let c : Category;
c = 'desk' // error
  
function greeting({name?: string}) : string {
  return `Hello ${name || 'world'}`
}

function greeting({name :string = 'world'}){
  return name;
}

type Person = {
  name : string;
  age?: number
}

function greeting({name, age} : Person) {
  return `${name}, ${age}` 
}
```

#### Intersection Type (교집합)

<pre class="language-javascript"><code class="lang-javascript"><strong>interface Colorful {
</strong>  color: string;
}
interface Circle {
  radius: number;
}

type ColorfulCircle = Colorful &#x26; Circle;
</code></pre>
