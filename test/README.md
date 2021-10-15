# Concept 
Tools and testing
# References
- [테스트 자동화와 Mocha](https://ko.javascript.info/testing-mocha)
- [toBe 와 toEqual 차이 Jest](https://jestjs.io/docs/using-matchers)
- [Jest로 테스트 해보기](https://thinkforthink.tistory.com/129)

# Summary

### describe("title", function() { ... })
-   구현하고자 하는 기능에 대한 설명이 들어갑니다. 우리 예시에선 함수 pow가 어떤 동작을 하는지에 대한 설명이 들어갈 겁니다. it 블록을 한데 모아주는 역할도 합니다.

### it("유스 케이스 설명", function() { ... })
-   it의 첫 번째 인수엔 특정 유스 케이스에 대한 설명이 들어갑니다. 이 설명은 누구나 읽을 수 있고 이해할 수 있는 자연어로 적어줍니다. 두 번째 인수엔 유스 케이스 테스트 함수가 들어갑니다.

### assert.equal(value1, value2)
-   assert.equal(value1, value2)
기능을 제대로 구현했다면 it 블록 내의 코드 assert.equal(value1, value2)이 에러 없이 실행됩니다.
함수 assert.*는 pow가 예상한 대로 동작하는지 확인해줍니다. 위 예시에선 assert.equal이 사용되었는데, 이 함수는 인수끼리 동등 비교했을 때 다르다고 판단되면 에러를 반환합니다. 예시에선 pow(2, 3)의 결괏값과 8을 비교하겠죠. 비교나 확인에 쓰이는 다른 함수들은 아래에서 다시 소개해 드리겠습니다.

(JEST)
###  expect().toBeTruthy();
###  expect().toEqual()
-   test('대신에 객체의 내용이 같은지를 확인하려면 toEqual을 써야 한다', () => {
    const obj = {};
    expect({ name: 'John' }).toEqual({ name: 'John' }); // true
});

###  expect().toBe();
-   test('toBe는 obj가 같은 객체를 가리키고 있는지 확인한다', () => {
    const obj = {};
    expect(obj).toBe(obj); // true
});

-   test('객체의 내용이 같더라도 서로 다른 메모리에 있는 객체이기 때문에 toBe를 쓰면 false가 나온다.', () => {
    expect({ name: 'John' }).toBe({ name: 'John' }); // false
});

 

