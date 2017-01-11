```
vertical steps of weui styles

<step :current="step1" background-color='#fbf9fe'>
    <step-item title="申报" :value="value1"></step-item>
    <step-item title="初审" :value="value2"></step-item>
    <step-item title="受理" :value="value3"></step-item>
    <step-item title="评估"></step-item>
    <step-item title="处室审核"></step-item>
    <step-item title="处室连审"></step-item>
    <step-item title="局长办公会"></step-item>
    <step-item title="立项"></step-item>
    <step-item title="申报变更"></step-item>
    <step-item title="合同签订(变更)"></step-item>
    <step-item title="中期检查"></step-item>
</step>

data(){
    return{
        step1: 2,
        value1: ["受理结果:通过受理, 2015-03-10"],
        value2: ["受理结果:通过受理, 2015-03-10"],
        value3: ["受理结果:通过受理, 2015-03-10", "受理结果:格式不符退回申报,2015-03-12"]
    }
}
```
![](https://github.com/NexusLee/vue-step/blob/master/screenshot/E3341B94-DFCA-4BB7-9FCC-2FEFA33097D7.png)
