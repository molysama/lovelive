
# 实现js对象的深拷贝

## 1.   JSON.parse(JSON.stringify();
  优点：适用于数组和对象，JS内置，较方便


  缺点：会抛弃基础构造器，复制之后的对象均为Object

    var a = ['1', '2', '3'];
    var b = JSON.parse(JSON.stringify(a));
    a[2] = 10;

    var c = {
        name: 'lgqlee'
    };
    var d = JSON.parse(JSON.stringify(c));
    c['name'] = 'change';

    console.log('JSON------');
    console.log(a);
    console.log(b);
    console.log(c);
    console.log(d);
    console.log('\n');

##  2.  concat or slice
   优点：简单快


   缺点：只能用于一维数组

    b = a.concat();
    b[0] = 'love';

    console.log('concat or slice----');
    console.log(a);
    console.log(b);
    console.log('\n');

##  3.  自己实现一个clone函数
   优点：一次劳累，到处可用，适用于数组和对象


   缺点:无

    Object.prototype.clone = function clone(o){
        var k, ret= o, b;
        if(o && ((b = (o instanceof Array)) || o instanceof Object)) {
            ret = b ? [] : {};
            for(k in o){
                if(o.hasOwnProperty(k)){
                    ret[k] = clone(o[k]);
                }
            }
        }
        return ret;
    };

### clone的测试
    console.log('clone----');
    b = Object.clone(a);
    a[0] = 'IOJS';
    console.log(a);
    console.log(b);

    c = {
        name: 'fuda',
        sex: 'girl'
    };
    d = Object.clone(c);
    c.name = 'dashu';
    c.sex = 'girls';
    console.log(c);
    console.log(d);
    console.log('\n');


#欢迎指正
