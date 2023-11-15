<template lang="">
    <div class="table-excel-container">
        table-excel导出举例
        <el-row>
            <el-button @click="handleExport">导出</el-button>
        </el-row>
    </div>
</template>
<script lang="ts" setup>
import {ref} from 'vue';
import { ElMapExportTable } from "table-excel";

let fieldColumnArr = [
  {
    text:"软件研制任务书",
    fieldCode:"prodRequirementWis",
  },
  {
    text:"需求分析",
    fieldCode:"techRequirementWis",
  },
  {
    text:"设计-界面设计/软件部件",
    fieldCode:"techRequirementWis",
  },


];
let  res = {
  code:200,
  data:[
    // 第一大行的
    {
      prodRequirementWis:[
         {
        title:"项目模板",
        subType:"未定义的枚举值",
        id:49,
        code:"APP-11",
        changeLabel:"",
        description:"",
        children:[],
        allFieldsValue:{}
        }
      ],
      techRequirementWis:[
       
      ],
      designWis:[]
    },
       // 第二大行的
      {
      prodRequirementWis:[  
        {
        title:"我的技术需求01",
        subType:"未定义的枚举值",
        id:900,
        code:"APP-23",
        changeLabel:"",
        description:"",
        children:[],
        allFieldsValue:{}
        }
      ],
      techRequirementWis:[
      
      ],
      designWis:[]
    },

     // 第三大行的
    	      {
      prodRequirementWis:[
         {
        title:"产品需求01",
        subType:"接口需求",
        id:1314,
        code:"APP-12",
        changeLabel:"新增",
        description:"产品需求01描述",
        children:[],
        allFieldsValue:{}
        }
      ],
      techRequirementWis:[
          {
        title:"技术需求01",
        subType:"",
        id:1299,
        code:"APP-13",
        changeLabel:"新增",
        description:"",
        children:[],
        allFieldsValue:{}
        },
         {
        title:"cpxq01技术需求07",
        subType:"接口需求",
        id:1311,
        code:"APP-33",
        changeLabel:"新增",
        description:"",
        children:[],
        allFieldsValue:{}
        },
         {
        title:"cpxq01技术需求08",
        subType:"接口需求",
        id:1313,
        code:"APP-34",
        changeLabel:"变更",
        description:"",
        children:[],
        allFieldsValue:{}
        },
      ],
      designWis:[
             {
        title:"设计01",
        subType:"界面需求",
        id:64,
        code:"APP-34",
        changeLabel:"变更",
        description:"",
        children:[],
        allFieldsValue:{}
        },
      ]
    },
    
    
  ]
}

// 打印返回的数据
console.log(res.data,"res.data");

let column = [
        {
          title: "需求跟踪矩阵",
          children:[
            {
                title:"软件研制任务书",
                children: [
                { title: "标识", dataIndex: "code" },
                { title: "标题", dataIndex: "title" },
                { title: "变更标识", dataIndex: "changeLabel" },
                { title: "属性", dataIndex: "subType" },
                { title: "备注", dataIndex: "description" },
                ],
            },
            {
                title:"需求分析",
                children: [
                { title: "标识", dataIndex: "code2" },
                { title: "标题", dataIndex: "title2" },
                { title: "变更标识", dataIndex: "changeLabel2" },
                { title: "属性", dataIndex: "subType2" },
                { title: "备注", dataIndex: "description2" },
                ],
            },
            {
                title:"设计-界面设计/软件部件",
                children: [
                { title: "标识", dataIndex: "code3" },
                { title: "标题", dataIndex: "title3" },
                { title: "变更标识", dataIndex: "changeLabel3" },
                { title: "属性", dataIndex: "subType3" },
                { title: "备注", dataIndex: "description3" },
                ],
            }
          ]
  
        },
      
];
res.data.map((item:any)=>{
  // 需要根据返回的数据定义一个column 以及一个 data
  // console.log(item,"item");
  //  返回的数据顺序不保证一致
  // {prodRequirementWis:Array(1),techRequirementWis:Array(3),designWis:Array(1)}
  column[0].children.forEach((itemChild:any,index:any)=>{
      console.log(itemChild,index);
  })
})



let  data = [
        {
          code: "APP-1",
          title: "产品需求01",
          subType: "接口需求", // 接口需求 功能需求 非功能需求 界面需求
          changeLabel: "新增", // 新增 原始 删除  变更
          description:'自定义描述',

          code2: "2-APP-1",
          title2: "2-产品需求01",
          subType2: "2-接口需求", // 接口需求 功能需求 非功能需求 界面需求
          changeLabel2: "2-新增", // 新增 原始 删除  变更
          description2:'2-自定义描述',

          code3: "3-APP-1",
          title3: "3-产品需求01",
          subType3: "3-接口需求", // 接口需求 功能需求 非功能需求 界面需求
          changeLabel3: "3-新增", // 新增 原始 删除  变更
          description3:'3-自定义描述',


        },
        {
          code: "APP-2",
          title: "产品需求02",
          subType: "接口需求2", // 接口需求 功能需求 非功能需求 界面需求
          changeLabel: "新增2", // 新增 原始 删除  变更
          description:'自定义描述2',

          code2: "2-APP-2",
          title2: "2-产品需求02",
          subType2: "2-接口需求2", // 接口需求 功能需求 非功能需求 界面需求
          changeLabel2: "2-新增2", // 新增 原始 删除  变更
          description2:'2-自定义描述2',

        //   code3: "3-APP-3",
        //   title3: "3-产品需求03",
        //   subType3: "3-接口需求3", // 接口需求 功能需求 非功能需求 界面需求
        //   changeLabel3: "3-新增3", // 新增 原始 删除  变更
        //   description3:'3-自定义描述3',
        },

        {
          code: "APP-2",
          title: "产品需求02",
          subType: "接口需求2", // 接口需求 功能需求 非功能需求 界面需求
          changeLabel: "新增2", // 新增 原始 删除  变更
          description:'自定义描述2',

          code2: "2-APP-3",
          title2: "2-产品需求03",
          subType2: "2-接口需求3", // 接口需求 功能需求 非功能需求 界面需求
          changeLabel2: "2-新增3", // 新增 原始 删除  变更
          description2:'2-自定义描述3',


        },
];
const handleExport = () =>{
    const instance = new ElMapExportTable(
        {
            column,
            data,
            spanMethod: ({ rowIndex, columnIndex }) => {
                if ((columnIndex === 0 || columnIndex === 1 || columnIndex === 2 || columnIndex === 3 ||columnIndex === 4 || columnIndex === 5) && (rowIndex === 0 || rowIndex === 1)) {
              return {
                rowspan: 2,
                colspan: 1,
              };
            }
          },
        },
        {progress: progress => console.log(progress)}
      );
      instance.download("导出正常表格案例");
}
</script>
<style lang="scss" scoped>
    .table-excel-container{
        padding:10px;
    }
</style>