<template lang="">
    <div class="table-excel-container">
        table-excel导出举例
        <el-row>
            <el-button @click="handleExport">导出</el-button>
        </el-row>
    </div>
</template>
<script lang="ts" setup>
import { ref } from 'vue';
import { ElMapExportTable } from "table-excel";
// 外部表格表头及字段
let fieldColumnArr = [
  {
    text: "软件研制任务书",
    fieldCode: "prodRequirementWis",
  },
  {
    text: "需求分析",
    fieldCode: "techRequirementWis",
  },
  {
    text: "设计-界面设计/软件部件",
    fieldCode: "techRequirementWis",
  },
];
// 内部表格表头及字段
let innerColumnArr = [
  { title: "标识", dataIndex: "code" },
  { title: "标题", dataIndex: "title" },
  { title: "变更标识", dataIndex: "changeLabel" },
  { title: "属性", dataIndex: "subType" },
  { title: "备注", dataIndex: "description" },
]
let res = {
  code: 200,
  data: [
    // 第一大行的
    {
      prodRequirementWis: [
        {
          title: "项目模板",
          subType: "未定义的枚举值",
          code: "APP-11",
          changeLabel: "",
          description: "",
        }
      ],
      techRequirementWis: [

      ],
      designWis: []
    },
    // 第二大行的
    {
      prodRequirementWis: [
        {
          title: "我的技术需求01",
          subType: "未定义的枚举值",
          code: "APP-23",
          changeLabel: "",
          description: "",
        }
      ],
      techRequirementWis: [

      ],
      designWis: []
    },

    // 第三大行的
    {
      prodRequirementWis: [
        {
          title: "产品需求01",
          subType: "接口需求",
          code: "APP-12",
          changeLabel: "新增",
          description: "产品需求01描述",

        }
      ],
      techRequirementWis: [
        {
          title: "技术需求01",
          subType: "",
          code: "APP-13",
          changeLabel: "新增",
          description: "",
 
        },
        {
          title: "cpxq01技术需求07",
          subType: "接口需求",
          code: "APP-33",
          changeLabel: "新增",
          description: "",
        
        },
        {
          title: "cpxq01技术需求08",
          subType: "接口需求",
          code: "APP-34",
          changeLabel: "变更",
          description: "",
          
        },
      ],
      designWis: [
        {
          title: "设计01",
          subType: "界面需求",
          code: "APP-34",
          changeLabel: "变更",
          description: "",
        },
      ]
    },
  ]
}

// 打印返回的数据
console.log(res.data, "res.data");

let column: any = [
  {
    title: "",
    children: [
    ]
  },
];

column[0].title = "需求跟踪矩阵";  // 定制化顶部大标题
let innerItem: any = {
  title: "",
  children: [],
}
// 遍历字段、让子表格的code与返回的字段对应
fieldColumnArr.forEach((fieldColumnItem: any, index: any) => {
  column[0].children = [];
  innerItem.title = fieldColumnItem.text;
  // 
  let newArr = innerColumnArr.map((fieldMap: any) => {
    // 返回的字段 ：原来是驼峰式命名 、现在拼接的时候让它变成首字母大写、拼接后的dataIndex为驼峰式
    let code = fieldColumnItem.fieldCode.charAt(0).toUpperCase() + fieldColumnItem.fieldCode.slice(1)
    return {
      title: fieldMap.title,
      dataIndex: fieldMap.dataIndex + code,
    }
  })
  innerItem.children = newArr ?? [];
  // 
  column[0].children.push(innerItem);

})
console.log(column, "column--column--column");


let exportData: any = []; // 点击导出按钮前的数据
res.data.map((resItem: any) => {
  // 返回值遍历：
  console.log(resItem, "resItem");
    // 遍历 map 对象
    let beforeArr:any = [];
    for (const key in resItem) {
      if (resItem.hasOwnProperty(key)) {
        const array = resItem[key];
        // 遍历每个 key 对应的数组
        for (let i = 0; i < array.length; i++) {
          const item = array[i];
          // 获取每个元素的内部键值对
          const innerKeyValues = Object.entries(item);
          // 更新每个元素的内部键，加上外层的键
          let transKey = key.charAt(0).toUpperCase() + key.slice(1)
          const updatedInnerKeyValues = innerKeyValues.map(([innerKey, value]) => ({
            [`${innerKey}${transKey}`]: value
          }));
          console.log(updatedInnerKeyValues,"updatedInnerKeyValues");
          exportData.push(updatedInnerKeyValues);
          // exportData = exportData.concat(...updatedInnerKeyValues);
        }
      }
    }
    beforeArr.push(exportData);
    console.log(beforeArr);



})



let data: any = exportData;

// let  data = [
//         {
//           code: "APP-1",
//           title: "产品需求01",
//           subType: "接口需求", // 接口需求 功能需求 非功能需求 界面需求
//           changeLabel: "新增", // 新增 原始 删除  变更
//           description:'自定义描述',

//           code2: "2-APP-1",
//           title2: "2-产品需求01",
//           subType2: "2-接口需求", // 接口需求 功能需求 非功能需求 界面需求
//           changeLabel2: "2-新增", // 新增 原始 删除  变更
//           description2:'2-自定义描述',

//           code3: "3-APP-1",
//           title3: "3-产品需求01",
//           subType3: "3-接口需求", // 接口需求 功能需求 非功能需求 界面需求
//           changeLabel3: "3-新增", // 新增 原始 删除  变更
//           description3:'3-自定义描述',


//         },
//         {
//           code: "APP-2",
//           title: "产品需求02",
//           subType: "接口需求2", // 接口需求 功能需求 非功能需求 界面需求
//           changeLabel: "新增2", // 新增 原始 删除  变更
//           description:'自定义描述2',

//           code2: "2-APP-2",
//           title2: "2-产品需求02",
//           subType2: "2-接口需求2", // 接口需求 功能需求 非功能需求 界面需求
//           changeLabel2: "2-新增2", // 新增 原始 删除  变更
//           description2:'2-自定义描述2',

//         //   code3: "3-APP-3",
//         //   title3: "3-产品需求03",
//         //   subType3: "3-接口需求3", // 接口需求 功能需求 非功能需求 界面需求
//         //   changeLabel3: "3-新增3", // 新增 原始 删除  变更
//         //   description3:'3-自定义描述3',
//         },

//         {
//           code: "APP-2",
//           title: "产品需求02",
//           subType: "接口需求2", // 接口需求 功能需求 非功能需求 界面需求
//           changeLabel: "新增2", // 新增 原始 删除  变更
//           description:'自定义描述2',

//           code2: "2-APP-3",
//           title2: "2-产品需求03",
//           subType2: "2-接口需求3", // 接口需求 功能需求 非功能需求 界面需求
//           changeLabel2: "2-新增3", // 新增 原始 删除  变更
//           description2:'2-自定义描述3',


//         },
// ];
const handleExport = () => {
  const instance = new ElMapExportTable(
    {
      column,
      data,
      spanMethod: ({ rowIndex, columnIndex }) => {
        if ((columnIndex === 0 || columnIndex === 1 || columnIndex === 2 || columnIndex === 3 || columnIndex === 4 || columnIndex === 5) && (rowIndex === 0 || rowIndex === 1)) {
          return {
            rowspan: 2,
            colspan: 1,
          };
        }
      },
    },
    { progress: progress => console.log(progress) }
  );
  instance.download("导出正常表格案例");
}
</script>
<style lang="scss" scoped>
.table-excel-container {
  padding: 10px;
}
</style>