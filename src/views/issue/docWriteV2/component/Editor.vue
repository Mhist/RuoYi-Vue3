<template>
    <div class="tinymce-editor">
    <textarea v-if="iShowEditor" id="tinymcedemo" v-model="content" :key="editorKey"></textarea>
    </div>
    <el-button @click="getEditorValue">获取值</el-button>
    <el-button @click="setEditorValue">设置值</el-button>
  </template>
<script lang="ts" setup>
import { onMounted } from 'vue';
const content = ref();
const editorKey = ref(0);
const props = defineProps({
    iShowEditor:{
        type: Boolean,
         default: false
    },
    modelValue:{
        type:String,
        default:''
    },
    toolbar: {
      type: [String, Array],
      default: 'undo redo |  formatselect | bold italic forecolor backcolor | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | lists image media table | removeformat'
    },
    disabled: {
      type: Boolean,
      default: false
    },
    plugins: {
      type: [String, Array],
      default: 'image'
    },
});

let configObj = {
   
    selector:"#tinymcedemo",
    language: 'zh_CN',
    browser_spellcheck: true, // 拼写检查
    elementpath: false,  //禁用编辑器底部的状态栏
    toolbar:props.toolbar,
    statusbar: false, // 隐藏编辑器底部的状态栏
    height: 300,
    plugins:props.plugins,
    branding: false,
    menubar: true,    
    paste_data_images: true, // 允许粘贴图像
};
console.log(props,"props");


const initTinyMCE = ()=>{
    window.tinymce.init(configObj);
}
onMounted(()=>{
    initTinyMCE();
})

const getEditorValue = ()=>{
   let a =  tinyMCE.activeEditor.getContent();
   console.log("文档内容为:" + a);
}

const setEditorValue = (val:any)=>{

    console.log("触发");
    editorKey.value++;
    initTinyMCE();
    tinyMCE.activeEditor.setContent(val);
}



defineExpose(
{
    getEditorValue,
    setEditorValue
}
)

</script>
<style lang="scss" scoped>
    
</style>