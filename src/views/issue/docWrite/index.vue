<template>
    <div class="custom-editor-wrapper">
    <Editor ref="editorRef"  v-bind="bindObj" v-model="modelValue" ></Editor>
      <h1>编辑器 </h1>
    <div v-for="item in resData">
    <h1 class="num-color">{{ item.num}}</h1>
    <h1>{{ item.title }}</h1>

    <div style="display: inline;" v-if="item.isShowText" v-html="item.textHtml" @click="handleTextClick(item,$event)"></div>
    <el-input v-if="item.isShowTextHtml" v-model="item.textHtml" type="textarea" @blur="txtHtmlBlur(item,$event)"></el-input>
    </div>


    </div>
</template>
<script lang="ts" setup>
import {nextTick, ref} from 'vue';
import  Editor  from './component/Editor.vue';
const resData = ref<any>([]);

const modelValue = ref();
const bindObj= ref({
    iShowEditor:true,
    toolbar:'undo redo |  formatselect | bold italic forecolor backcolor | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | lists image media table | removeformat',
});

const editorRef = ref();
resData.value = [
    {   
        id: 111,
        num:1,
        title:"测试001",
        textHtml:'<p>1223232323232</p>',
        isShowText:true,
        isShowTextHtml: false,
    },
    {   
        id: 222,
        num:2,
        title:"测试001",
        textHtml:'<p>1223232323232</p>',
        isShowText:true,
        isShowTextHtml: false,
    },

],
console.log(window);

const handleTextClick = (item:any,e:any) =>{
    console.log(item);
    console.log(e);
    item.isShowText = false;
    item.isShowTextHtml = true;
    bindObj.value.iShowEditor = true;
  


};
const txtHtmlBlur = (item:any,e:any) =>{
    console.log(item);
    console.log(e);
    item.isShowText = true;
    item.isShowTextHtml = false;
    
    nextTick(()=>{
        editorRef.value.setEditorValue(item.textHtml);
    })
};



const log = () => {
      console.log('editor instance: ', editorRef.value);
}
</script>
<style lang="scss" scoped>
    .custom-editor-wrapper{
        padding: 10px;


        .num-color{
            color: #901212;
        }
    }
</style>