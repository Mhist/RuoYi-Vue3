<template>
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="col1" label="产品需求">
        <template #default="scope">
                    <el-table :data="scope.row.col1" style="width: 100%">
                    <el-table-column prop="code" label="code"/>
                    <el-table-column prop="title" label="title" />
                    </el-table>
         
        </template>
      </el-table-column>


      <el-table-column prop="col2" label="技术需求">
        <template #default="scope">
                    <el-table :data="scope.row.col2" style="width: 100%">
                    <el-table-column prop="code" label="code"/>
                    <el-table-column prop="title" label="title" />
                    </el-table>
         
        </template>
      </el-table-column>


      <el-table-column prop="col3" label="设计">
        <template #default="scope">
                    <el-table :data="scope.row.col3" style="width: 100%">
                    <el-table-column prop="code" label="code"/>
                    <el-table-column prop="title" label="title" />
                    </el-table>
        </template>
      </el-table-column>
    </el-table>
  </template>
  
  <script lang="ts" setup>
import {ref} from 'vue';
  let resData =[
  {
    "id": 1,
    "leader": "Leader 1",
    "status": "Status 1",
    "title": "Title 1",
    "type": "Type 1",
    "code": "Code 1",
    "allFieldsValue": {
        workItemTypeCode:'soft-requirement',
    },
    "workItemTypeCode": "Work Item Type Code 1",
    "children": [
      {
        "id": 2,
        "leader": "Leader 2",
        "status": "Status 2",
        "title": "Title 2",
        "type": "Type 2",
        "code": "Code 2",
        "allFieldsValue": {
        workItemTypeCode:'soft-requirement',
        },
        "children": [
          {
            "id": 3,
            "leader": "Leader 3",
            "status": "Status 3",
            "title": "Title 3",
            "type": "Type 3",
            "code": "Code 3",
            "allFieldsValue": {
            workItemTypeCode:'design',
        },
          }
        ]
      }
    ]
  },
  {
    "id": 4,
    "leader": "Leader 4",
    "status": "Status 4",
    "title": "Title 4",
    "type": "Type 4",
    "code": "Code 4",
    "allFieldsValue": "All Fields Value 4",
    "workItemTypeCode": "Work Item Type Code 4",
    "children": [
      {
        "id": 5,
        "leader": "Leader 5",
        "status": "Status 5",
        "title": "Title 5",
        "type": "Type 5",
        "code": "Code 5",
        "allFieldsValue": "All Fields Value 5",
        "workItemTypeCode": "Work Item Type Code 5",
        "children": [
          {
            "id": 6,
            "leader": "Leader 6",
            "status": "Status 6",
            "title": "Title 6",
            "type": "Type 6",
            "code": "Code 6",
            "allFieldsValue": "All Fields Value 6",
            "workItemTypeCode": "Work Item Type Code 6"
          }
        ]
      }
    ]
  }
]
console.log(resData);

const tableData = ref();
tableData.value = [
    {
        col1: [
        {
            code:'xxxxx1',
            title:'yyyyy1'
        },
        {
            code:'xxxxx2',
            title:'yyyyy2'
        },
        {
            code:'zzzzz3',
            title:'zzzzz3'
        },
   
      ],

      col2: [
        {
            code:'xxxxx1',
            title:'yyyyy1'
        },
        {
            code:'xxxxx2',
            title:'yyyyy2'
        },
        {
            code:'zzzzz3',
            title:'zzzzz3'
        },
   
      ],

      col3: [
        {
            code:'xxxxx1',
            title:'yyyyy1'
        },
        {
            code:'xxxxx2',
            title:'yyyyy2'
        },
        {
            code:'zzzzz3',
            title:'zzzzz3'
        },
      ],
    },

    {
        col1: [
        {
            code:'xxxxx1',
            title:'yyyyy1'
        },
        {
            code:'xxxxx2',
            title:'yyyyy2'
        },
        {
            code:'zzzzz3',
            title:'zzzzz3'
        },
   
      ],

      col2: [
        {
            code:'xxxxx1',
            title:'yyyyy1'
        },
        {
            code:'xxxxx2',
            title:'yyyyy2'
        },
        {
            code:'zzzzz3',
            title:'zzzzz3'
        },
   
      ],

      col3: [
        {
            code:'xxxxx1',
            title:'yyyyy1'
        },
        {
            code:'xxxxx2',
            title:'yyyyy2'
        },
        {
            code:'zzzzz3',
            title:'zzzzz3'
        },
      ],
    },
  ]
  </script>
  
  