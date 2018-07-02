<template>
    <div class="hello">
        showValue:{{move({})}}
        <div>
            templateString:{{templateStringTest()}}
            <div style="white-space: pre;">
                {{templateStringTest()}}
            </div>
            <pre style="">{{templateStringTest()}}</pre>
        </div>
    </div>
</template>

<script>
    //数组解构
    let [a, b, c] = [1, 2, 3];
    let [foo, [[bar], baz]] = [1, [[2], 3]];
    let [head, ...tail] = [1, 2, 3, 4];
    //解构时的默认值
    let [a1, b1 = "222"] = ["111", null];
    let [a2, b2 = "222"] = ["111", undefined];
    let isCheckQuery = null === undefined;
    let [a3 = "1", b3 = a3] = ["2"];
    //对象解构
    let {objA, objB} = {objA: "1", objB: "2"};
    //====上面的 声明等于
    let {objA2: objA2, objB2: objB2} = {objA2: "1", objB2: "2"};
    let {objA2: o2, objB2: o3} = {objA2: "1", objB2: "2"};
    //更复杂的对象解构
        let objLv1 = {
            child1: [
                "value1",
                {cChild1: "cValue1"},
                ]
        };
        let {child1: [param1, {cChild1: param2}]} = objLv1;
    //更复杂的对象解构2
        let objLv2 = {
            childLv2: {
                cChildLv2: {
                    min: 0,
                    max: 99,
                }
            }
        };
        let {childLv2, childLv2: {cChildLv2}, childLv2: {cChildLv2: {min, max}}} = objLv2;

    //对象解构的默认值问题
    var {x: y = 3} = {x: 5};

    //运用
    let { log, sin, cos } = Math;
    let arr = [1, 2, 3];
    let {0 : first, [arr.length - 1] : last} = arr;





    export default {
        data() {
            return {
                showValue: last
            }
        },
        created() {

        },
        mounted() {

        },
        watch: {},
        methods: {
            //函数的参数解构
             move({x = 0, y = 0}={}) {
                return [x, y];
            },
            //模板字符串
            templateStringTest(){
                let valueA = "111";
                let valueB = "222";
                let result = `valueA is ${valueA} <br>
                          valueB is ${valueB}`;
                return result;
            }
        },
        computed: {},
        components: {}
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    pre{
        font-size: 14px;
        font-family:宋体;
        white-space: pre;
        margin: 0;
    }
</style>
