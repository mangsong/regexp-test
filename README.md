# 정규 표현식 (RegExp)

정규식, Regular Expression

## 역활

- 문자 검색(search)
- 문자 대체(replace)
- 문자 추출(extract)

## 테스트 사이트

https://regexr.com/

### 정규식 생성

```js
// 생성자
new RegExp("표현", "옵션");
new RegExp("[a-z]", "gi") /
  // 리터럴
  표현 /
  옵션 /
  [a - z] /
  gi;
```

## 예제 문자

```js
const str = `
010-1234-5678
thedskdak@gmail.com
https://www.omdbapi.com/?apikey=7035c60c&s=frozen
The quick brown fox jumps over the lazy dog.
abbcccdddd
`;
```

## 메소드

| 메소드  | 문법                                | 설명                             |
| ------- | ----------------------------------- | -------------------------------- |
| test    | `정규식.test(문자열)`               | 일치여부(Boolean) 반환           |
| match   | `문자열.match(정규식)`              | 일치하는 문자의 배열(Array) 반환 |
| replace | `문자열.replace(정규식, 대체문자) ` | 일치하는 문자를 대체             |

## 플래그(옵션)

| 플래그 | 설명                                              |
| ------ | ------------------------------------------------- |
| g      | 모든 문자 일치(global)                            |
| i      | 영어 대소문자를 구분 않고 일치(ignore case)       |
| m      | 여러 줄 일치(multi line), 각줄을 시작과 끝으로 봄 |

## 패턴(표현)

| 패턴       | 설명                                                                        |
| ---------- | --------------------------------------------------------------------------- |
| ^ab        | 줄(Line) 시작에 있는 ab와 일치                                              |
| ab$        | 줄(Line) 끝에 있는 ab와 일치                                                |
| .          | 임의의 한문자와 일치                                                        |
| a&verbar;b | a 또는 b와 일치, 먼저 찾아지는걸 반환                                       |
| ab?        | b가 없거나 b와 일치, 물음표 앞의 문자가 있을수도 있고 없을수도 있는 걸 반환 |
| {n}        | n개 연속 일치                                                               |
| {n,}       | n개 이상 연속 일치                                                          |
| {n,m}      | n개 이상 m개이하(n~m개) 연속 일치                                           |
| [abc]      | a 또는 b 또는 c                                                             |
| [a-z]      | a부터 z 사이의 문자 구간에 일치(영어소문자)                                 |
| [A-Z]      | A부터 Z사이의 문자 구간에 일치(영어대문자)                                  |
| [0-9]      | 0부터 9사이의 문자 구간에 일치(숫자)                                        |
| [가-힣]    | 가부터 힣 사이의 문자 구간에 일치(한굴)                                     |
| \w         | 63개의 문자(Word, 대소영문52개 + 숫자 10개 + \_)에 일치                     |
| \b         | 63개 문자에 일치하지 않는 문자 경계 (Boundary),사이사이의 경계              |
| \d         | 숫자(Digit)에 일치                                                          |
| \s         | 공백(Space, Tab등)에 일치                                                   |
| (?=)       | 앞쪽일치(Lookahead) , 앞쪽에 일치 시킬려고 하는 문자를 넣는다.              |
| (?<=)      | 뒤쪽일치(Lookbehind) ,                                                      |

#### 앞쪽 일치, 뒤쪽 일치 예시

```js
console.log(str.match(/.{1,}(?=@)/g)) ..@기호 앞쪽의 한개이상의 문자를 찾아서 출력(아이디값)
console.log(str.match(/(?<=@).{1,}/g)) ..@기호의 뒷쪽의 한개이상의 문자를 찾아서 출력(도메인)
```
