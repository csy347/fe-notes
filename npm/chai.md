
# 断言库

在我们使用`mocha`进行测试的时候，会结合断言库去使用，经常一起使用的是`chai`，但是还有`assert`，`expect`，`should`这几种断言库，那么接下来了解一下他们的区别

- chai.js
- should.js （TJ放弃维护后由新开发者接手）
- expect.js
- assert.js

## assert
TDD风格
API样例：
``` js
assert("mike" == user.name);
```

## should
BDD风格
API样例：
``` js
foo.should.be("aa");
```

## expect
BDD风格，基于should的简化
API样例：
``` js
expect(foo).to.be("aa");
```

## chai
BDD/TDD风格，同时支持should，assert，expect
API样例：
``` js
foo.should.be("aa");
assert("mike" == user.name);
expect(foo).to.be("aa");
```

如：
``` js
var should = chai.should();

describe("测试add函数", function(){
    it("1加1等于2", function()
    {
        var sum = add(1, 2);
        should.equal(sum, 3);
    });

    it("1加2等于3", function()
    {
        var sum = add(1, 2);
        should.equal(sum, 3);
    });
});
```

## should和expect的区别
当被测对象为undefined时，should就失效，而expect依然可以给出信息
例如使用should：
``` js
// foo === undefined
foo.should.equal('aa');
```

此时错误信息为： Cannot read property 'should' of undefined，如果使用expect：
``` js
// foo === undefined
expect(foo).to.equal('aa');
```

给出的信息为：expected undefined to equal 'foo'
故使用expect优于should

