# iview-personal
基于iview3封装多功能组件



1. 搜索表单
    支持下拉框、输入框、数字输入口、单选框、时间日期选择框搜索功能

```
<tco-form 
    vertical
    :objData="aSearch" 
    :objDefault="objDefault"
    :bhidLable="false"
    btnName="试试"
    @handleFormSubmit="handleSearch"
    >
</tco-form>
```
#### tco-form prpps
属性 | 说明 | 类型 | 默认值
---|---|---|---
objData | 显示的结构化数据 |  Array | []
bhidLable | 是否显示label |  Boolean | true
vertical | 是否竖排 |  Boolean | false
objDefault | 表单默认值 |  Object | {}
btnName | 按钮文本 |  String | '提交'

#### objData 
> ==下拉框==

```
 {
    type: 'select',
    label: '下拉框',
    value: 'select',
    disabled:true,//是否禁用
    clearable: true,//是否可清除
    filterable: true,//是否可搜索
    //defaultValue: '1',//默认value
    required: true,//是否必须项
    placeholder: '请选择',
    data: [
        {
            name: 'option1',
            disabled:true,//是否禁用
            value: '1'
        },
        {
            name: 'option2',
            value: '2'
        }
    ]
}
```
> ==单选框==

```
 {
    type: 'radio',
    label: '单选框',
    value: 'radio',
    //defaultValue: '1',//默认value
    required: true,//是否必须项
    placeholder: '请选择',
    data: [
        {
            name: 'check1',
            disabled:true,//是否禁用
            value: '1'
        },
        {
            name: 'check2',
            value: '2'
        }
    ]
}
```
> ==输入框==

```
 {
    type: 'input',
    value: 'input',
    label: '输入框',
    disabled:true,//是否禁用
    prefix: 'ios-contact',//输入框头部图标
    suffix: 'ios-search',//	输入框尾部图标
    required: true,//是否必须项
    placeholder: '请输入'
}
```
> ==数字输入框==

```
 {
    type: 'inputNumber',
    value: 'inputNumber',
    disabled:true,//是否禁用
    label: '数字输入框',
    required: true,//是否必须项
    placeholder: '请输入'
}
```
> ==时间、日期选择器==

```
{
    type: 'date',
    label: '时间/日期',
    disabled:true,//是否禁用
    dateType: 'month',//date、daterange、datetime、datetimerange、year、month
    value: 'end',//当type为datarange是value为数组[value1,value2]
    format: 'yyyy-MM',//date | daterange：yyyy-MM-dd、datetime | datetimerange：yyyy-MM-dd
    required: true,//是否必须项
    placeholder: '选择结束时间',
    limit: {//时间范围
        up: '2018-01-01 00:00:00',
        down: '2015-01-01 00:00:00'
    }
}
```

#### tco-form events

事件名 | 说明 | 返回值
---|---|---
handleSearch | 搜索 | search：搜索参数
2. 分页table
    支持iview中table、page原有api

```
<table-paging 
    :columns="aTableColumns"
    :data="aTableData" 
    :pagination="objPageControl" 
    :loading="false" 
    :show-header="true" 
    :stripe="true" 
    :border="true" 
    :disHover="false" 
    :height="false" 
    :width="false" 
    :size="size"
    @selectChange="selectChange"
    @changePage="changePage" 
    @changePageSize="changePageSize">
</table-paging>
```
### API
#### Table props
属性 | 说明 | 类型 | 默认值
---|---|---|---
data | 显示的结构化数据 |  Array | []
columns | 表格列的配置描述 |  Array | []
pagination | 分页 |  Object | -
loading | 表格是否加载中 |  Boolean | false
show-header | 是否显示表头 |  Boolean | true
stripe | 是否显示间隔斑马纹 |  Boolean | false
border | 是否显示纵向边框 |  Boolean | false
disHover | 禁用鼠标悬停时的高亮 |  Boolean | false
height | 表格高度，单位 px，设置后，如果表格内容大于此值，会固定表头 |  Number/String | -
width | 表格宽度，单位 px |  Number/String | 自动
size | 表格尺寸，可选值为 large、small、default 或者不填 |  String | -

#### Table events

事件名 | 说明 | 返回值
---|---|---
selectChange | 在多选模式下有效，只要选中项发生变化时就会触发 | selection：已选项数据
changePage| 分页模式下有效，页码发生变化触发 | page:页码数 
changePageSize| 分页模式下有效，每页条数发生变化触发 | pageSize:每页条数


3.合并table

> ==columns增加属性==

属性 | 说明 | 类型 | 默认值
---|---|---|---
combine | 是否向下合并 |  Boolean | false

```
<table-combine 
    :columns="aTableColumns"
    :data="aTableData" 
    :pagination="objPageControl" 
    :loading="false" 
    :show-header="true" 
    :stripe="true" 
    :border="true" 
    :disHover="false" 
    :height="false" 
    :width="false" 
    :size="size"
    @selectChange="selectChange"
</table-combine>
```



4.编辑table

> ==columns增加属性==

属性 | 说明 | 类型 | 默认值
---|---|---|---
edit | 编辑参数 |  obj | null

```
<table-edit 
    :columns="aTableColumns"
    :data="aTableData" 
    :pagination="objPageControl" 
    :loading="false" 
    :show-header="true" 
    :stripe="true" 
    :border="true" 
    :disHover="false" 
    :height="false" 
    :width="false" 
    :size="size"
</table-edit>
```


```

edit: {
    type: 'input',//必填input、inputNumber、select
    key: 'key3',//必填
    option: []//可填：select必填时option下拉框数据
}
```


