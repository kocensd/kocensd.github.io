---
layout: post
title: 고차함수 사용하기
tags: [Swift]
sitemap :
  changefreq : daily
  priority : 1.0
---

- map, filter, reduce 사용하기

for문이 익숙해서, 가독성이 떨어져서 사용하지 않았지만 코드 수를 많이~ 줄여주고 코드가 깔끔하게 정리된다.
그래서 뒤늦게 정리

- map : 데이터를 변형하여 새로운 컨테이너를 생성하여 반환시킴

```c
let nums: [Int] = [0, 1, 2, 3, 4]
var result: [Int] = []
//for in
for num in nums {
    let data = num * 2
    result.append(data)
}
print(result) //[0, 2, 4, 6, 8]

//map
result = nums.map({ (num: Int) -> Int in
    return num * 2
})
print(result) //[0, 2, 4, 6, 8]

//map (매개변수, 반환 타입, return 생략도 가능하다. 생략이 많아지기 때문에 코드는 간결해지지만 가독성이 떨어진다.)
result = nums.map{ $0 * 2 }
print(result) //[0, 2, 4, 6, 8]
```

- filter : 기존 데이터에서 조건에 대한 필터링을 통해 새로운 컨테이너를 생성하여 반환시킴

```c
let nums: [Int] = [0, 1, 2, 3, 4]
var result: [Int] = []
//for in
for num in nums {
    if num % 2 == 0 {
        result.append(num)
    }
}
print(result) //[0, 2, 4]

//filter
result = nums.filter({ (num: Int) -> Bool in
    return num % 2 == 0
})
print(result) //[0, 2, 4]

//filter 또한 생략이 가능하다.
result = nums.filter{ $0 % 2 == 0 }
print(result) //[0, 2, 4]
```

- reduce : 컨테이너 내부의 데이터 통합시킴

```c
let nums: [Int] = [0, 1, 2, 3, 4]
var result: Int = 0
//for in
for num in nums {
    result += num
}
print(result) //10

//reduce (map,filter와는 다르게 초기값을 설정해줘야한다.)
result = nums.reduce(0, {(first: Int, second: Int) -> Int in
    return first + second
})
print(result) //10

//reduce 또한 생략이 가능하다.
result = nums.reduce(0) { $0 + $1 }
print(result) //10
```

