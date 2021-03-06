# 연산자
연산자는 피연산자로 값을 만들어 낸다. 피연산자가 요리를 만들기 위한 재료라면, 연산자는 재료를 손질하는 연장이라 할 수 있다.

## 산술 연산자

산술 연산자는 피연산자의 개수에 따라 단항과 이항 산술 연산자로 구분된다. 두 산술 연산자 사이에는 **부수 효과**라는 차이가 있다. 

> **부수 효과(side effect)** 란 함수 내부에서의 실행이 외부 함수에도 영향을 미치는 것을 말한다. 할당 연산자, 증감 연산자, delete 연산자는 부수 효과가 일어 나는 연산자이다.

산술 연산으로 부수 효과가 일어나면 피연산자의 값도 함께 변경되는데, 단항 연산자 중에서도 증감 연산자는 부수 효과가 일어 나지만, 이항 연산자는 부수 효과가 없다. 

### 1. 단항 산술 연산자

단항 연산자는 1개의 피연산자로 산술이 가능하다.

```js
var cnt = 1;
cnt++; // cnt = cnt + 1;
console.log(cnt); // 2

// cnt 의 값이 2 로 증가하면서 변경된 피연산자의 값이 cnt 변수에 암묵적으로 재할당된다.
```

- **증감 연산자** :  피연산자의 앞이나 뒤에 `++` 가 붙으면 점차 증가하고, `--` 가 붙으면 점차 감소한다. 증감 연산자는 부수 효과가 일어나 산술 시 피연산자의 값도 함께 변경된다.

    증감 연산자가 피연산자의 앞에 붙으면 **전위**, 뒤에 붙으면 **후위** 연산자라 하는데, 둘의 결과값의 차이는 다음과 같다.

    ```js
    var x = 3;

    // 전위 연산자
    var result = ++x; // 연산 수행 전에 피연산자의 값이 먼저 증가함
    console.log(result, x); // 4, 4 

    // 후위 연산자
    result = x++; // 연산이 먼저 수행된 후 피연산자의 값이 증가함
    console.log(result, x); // 3, 4
    ```

- `-` 는 양수를 음수로, 음수를 양수로 반전시킬 수 있지만 부수 효과는 일어나지 않는다.
- `+` 는 숫자 타입이 아닌 피연산자에 `+` 를 사용하면 피연산자를 숫자 타입으로 바꿀 수가 있다. 단, 부수 효과가 없기 때문에 피연산자의 값이 변경되지는 않는다.

### 2. 이항 산술 연산자

이항 산술 연산자는 2개의 피연산자를 산술해 값을 생성한다.  부수 효과가 없기 때문에 새로운 값을 만들어 낼 뿐, 피연산자의 값이 바뀌지는 않는다.

```js
var x = 2;
var y = 1;

x + y; // 3; => 덧셈
x - y; // 1; => 뺄셈
x * y; // 2; => 곱셈
x / y; // 2; => 나눗셈
x % y; // 0; => 나머지
```

### 3. 문자열 연결 연산자

산술 연산자 중에서  `+` 는 피연산자 중 하나 이상이 문자열인 경우,  [암묵적 타입 변환](https://github.com/heejinna/TIL/blob/main/JavaScript/data-type.md#%EC%95%94%EB%AC%B5%EC%A0%81-%ED%83%80%EC%9E%85-%EB%B3%80%ED%99%98)이 일어나 문자열을 단순히 연결시켜주는 역할을 하게 된다.

```js
'1' + 2; // '12'
1 + '2'; // '12'
```

## 할당 연산자

할당 연산자는 첫 번째 피연산자의 값에 두 번째 피연산자의 값을 산술하여 다시 첫 번째 피연산자에 할당하는 역할을 하는 연산자이다. 재할당이 일어나기 때문에 변수 값이 바뀌는 부수 효과가 있다.

```js
var x;

x = 10;
x += 5; // x = x + 5; // 15
x -= 5; // x = x - 5; // 10
x *= 5; // x = x * 5; // 50
x /= 5; // x = x / 5; // 10
x %= 5; // x = x % 5; // 0
```

## 비교 연산자

첫 번째와 두 번째의 피연산자를 비교해 결과값을 `true` 나 `false` 의 불린 값으로  반환하는 연산자이다. 비교 연산자는 부수 효과가 **없다**.

### 1. 동등 비교 연산자

비교 연산을 처리하는 과정에서 피연산자 간의 데이터 타입이 다른 경우 [암묵적 타입 변환](https://github.com/heejinna/TIL/blob/main/JavaScript/data-type.md#%EC%95%94%EB%AC%B5%EC%A0%81-%ED%83%80%EC%9E%85-%EB%B3%80%ED%99%98) 후 비교한다.

```js
5 == '5'; // true
```

- `==` : 피연산자 간의 값이 같은지 비교
- `!=` : 피연산자 간의 값이 다른지 비교

### 2. 일치 비교 연산자

일치 비교 연산자는 피연산자 간의 타입과 값이 모두 일치해야 `true` 를 반환한다. 동등 비교 연산자보다 일치 비교 연산자가 더 예측하기 쉽기 때문에 일치 비교 연산자를 사용하는 편이 좋다.

- `===` : 피연산자 간의 타입이 일치하는지 비교
- `!==` : 피연산자 간의 타입이 다른지 비교

단, `NaN` 값을 비교할 때는 함수 `isNaN` 을 사용한다.

```js
NaN === NaN; // false
```

### 3. 대소 비교 연산자

피연산자의 크기를 비교하는 연산자로, `>`, `<`, `>=`, `<=` 가 있다.

## 삼항 조건 연산자

```js
// syntax
조건식 ? 조건식이 true 일 때 반환할 값 : 조건식이 false 일 때 반환할 값
```

삼항 조건 연산자는 표현식이므로 값처럼 사용할 수 있지만, `if...else` 문은 표현식이 아닌 문이기 때문에 값처럼 사용할 수 없다.

## 논리 연산자

논리 연산자에는 논리곱(AND)를 의미하는 `&&`, 논리합(OR)를 의미하는 `||` , 부정(NOT)을 의미하는 `!` 가 있다.

`!` 연산자는 boolean 값이 아닌 피연산자일 경우 boolean 타입으로 암묵적 타입 변환을 하므로 항상 boolean 값을 반환한다. 반면 `&&` 와 `||` 는 언제나 boolean 값만 반환하는 것은 아니다. 

### 🔥 단축 평가

`&&` 와 `||` 연산자는 피연산자가 boolean 값이 아니더라도 피연산자를 타입 변환없이 그대로 반환하는데, 이를 **단축 평가(short-circuit evaluation)** 라 한다.

<table align="center">
  <thead>
    <th>표현식</th> 
    <th>결과</th> 
  </thead>
  <tbody align="center">
    <tr>
      <td>true || anything</td>
      <td>true</td>
    </tr>
    <tr>
      <td>false || anything</td>
      <td>anything</td>
    </tr>
    <tr>
      <td>true && anything</td>
      <td>anything</td>
    </tr>
    <tr>
      <td>false && anything</td>
      <td>false</td>
    </tr>
  </tbody>
</table>

```js
// 논리곱(&&) 연산자
'coffee' && 'donut'; // 'donut'
false && 'donut'; // false
'coffee' && false; // false 

// 논리합(||) 연산자
'coffee' || 'donut'; // 'coffee'
false || 'donut'; // 'donut'
'coffee' || false; // 'coffee'
```
논리합(||) 연산자는 두 개의 피연산자 중 하나만 truthy 값이어도 `true` 를 반환한다.

단축평가는 에러를 피할 때 자주 사용된다.
- 객체 프로퍼티 참조 시 변수의 값이 `null` 또는 `undefined` 로 인한 타입 에러를 피하고 싶을 때
- 함수 파라미터에 기본값 설정 시 `undefined` 로 인한 에러를 방지하고 싶을 때


## 쉼표 연산자

쉼표 연산자는 각각의 피연산자를 왼쪽부터 차례대로 평가하고, 마지막 연산자의 값을 반환한다.

```js
var x, y, z;

x = 1, y = 2, z = 3; // 3
```

## 그룹 연산자

그룹 연산자인 `()` 을 사용하면 표현식의 우선순위를 조정할 수 있다.

## typeof 연산자

typeof 연산자는 피연산자의 데이터 타입을 반환해주는 연산자이다. 

단, typeof 연산자가 반환하는 데이터 타입은 실제 데이터 타입과 완벽하게 일치하지 않음에 주의해야 한다. 

- typeof 연산자로 `null` 을 연산할 경우, `object` 를 반환하기 때문에, typeof 가 아닌 일치 연산자 `===` 를 사용하는 것이 맞다.

    ```js
    var tired = null;

    typeof tired // "object"
    tired === null; // true
    ```

- 선언하지 않은 식별자를 typeof 연산자로 연산해보면, 참조될 수 없기 때문에 `ReferenceError`가 반환되어야 함에도 `undefined` 가 반환된다.

## 지수 연산자

지수 연산자 `**` 는 첫 번째 피연산자를 두 번째 피연산자로 거듭 제곱한 결과값을 반환해주는 연산자이다.

```js
3 ** 5; // 243 == 3^5

// 할당 연산자와 함께 사용 가능하다.
var num = 3;
num ** 5; // 243
```
