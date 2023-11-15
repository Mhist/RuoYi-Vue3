<template lang="">
    <div>
        <download-excel
        types="xls"
        :data="dataArr"
        :fields="fields"
        :name="exportName"
        :worksheet="exportSheet"
        :header="exportHeader"
        :footer="exportFooter"
        :defaultValue="exportDefaultValue"
>
        <el-button type="success">导出</el-button>
</download-excel>
    </div>
</template>
<script lang="ts" setup>
import {ref,onMounted} from 'vue';
const dataArr = ref();
let fields = ref(); 
let exportName = ref();
let exportSheet = ref();
let exportHeader = ref();
let exportFooter = ref();
let exportDefaultValue = ref(); 
dataArr.value =  [
                {
                    name: '小明',
                    age: 15,
                    city: '北京市',
                    school: '北京第一中学',
                    tel: '888810001'
                },
                {
                    name: '小红',
                    age: 14,
                    city: '上海市',
                    school: '上海第一中学',
                    tel: '888810002'
                },
                {
                    name: '小强',
                    age: 13,
                    city: '深圳',
                    school: '深圳第一中学',
                    tel: '888810003'
                },
                {
                    name: '小丽',
                    age: 16,
                    city: '广州',
                    school: '广州第一中学',
                    tel: '888810004'
                }
            ];
            fields.value = {
                    姓名: 'name',
                    年龄: 'age',
                    城市: 'city',
                    学校: 'school',
                    电话: 'tel'
            };

            exportName.value =  '这是文件的名称';
            exportSheet.value =  '这是表格sheet的名称';
            exportHeader.value =  '这是表格的标题';
            exportFooter.value =  '这是表格的页脚';
            exportDefaultValue.value =  '这是一个默认的数据';  

</script>
<style lang="scss" scoped> 
    
</style>
  