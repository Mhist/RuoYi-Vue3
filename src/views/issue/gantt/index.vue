<template>
    <div class="gantt-container">
        <div>甘特图</div>
        <div><span id="cont" v-html="previewHtml"></span></div>
    </div>
</template>
<script lang="ts" setup>
import {nextTick, ref} from 'vue';
// console.log(JSGantt);
let previewHtml = ref('');
previewHtml.value = `
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<link rel="stylesheet" href="/attach/css/jsgantt.css">
<title>文档标题</title>
<script>

var g = new window.JSGantt.GanttChart(document.getElementById('GanttChartDIV'), 'day');

g.setOptions({
  vCaptionType: 'Duration',  // Set to Show Caption : None,Caption,Resource,Duration,Complete,     
  vQuarterColWidth: 36,
  vDateTaskDisplayFormat: 'day dd month yyyy', // Shown in tool tip box
  vDayMajorDateDisplayFormat: 'mon yyyy - Week ww',// Set format to display dates in the "Major" header of the "Day" view
  vWeekMinorDateDisplayFormat: 'dd mon', // Set format to display dates in the "Minor" header of the "Week" view
  vLang: 'cn',
  vAdditionalHeaders: { // Add data columns to your table

    pPlanStart: {
      title: 'pPlanStart'
    },
    pPlanEnd: {
      title: 'pPlanEnd'
    },

  },
  vShowTaskInfoLink: 0, // Show link in tool tip (0/1)
  vShowEndWeekDate: 0,  // Show/Hide the date for the last day of the week in header for daily view (1/0)
  vUseSingleCell: 10000, // Set the threshold at which we will only use one cell per table row (0 disables).  Helps with rendering performance for large charts.
  vFormatArr: ['Day', 'Week', 'Month', 'Quarter'], // Even with setUseSingleCell using Hour format on such a large chart can cause issues in some browsers
  vScrollTo: new Date(),

  // EVENTS

  // OnChangee
  vEventsChange: {
    taskname: console.log,
    res: console.log,
  },
  // EventsClickCell
  vEvents: {
    taskname: console.log,
    res: console.log,
    dur: console.log,
    comp: console.log,
    start: console.log,
    end: console.log,
    planstart: console.log,
    planend: console.log,
    cost: console.log,
    additional_category: console.log, // for additional fields
    beforeDraw: ()=>console.log('before draw listener'),
    afterDraw: ()=>console.log('before after listener')
  },
  vEventClickRow: console.log,
  vEventClickCollapse: console.log
});

// Load from a Json url

JSGantt.parseJSON('/src/views/data.json', g);

// Or Adding  Manually
// g.AddTaskItemObject({
//   pID: 1,
//   pName: "Define Chart <strong>API</strong>",
//   pStart: "2017-02-25",
//   pEnd: "2017-03-17",
//   pPlanStart: "2017-04-01",
//   pPlanEnd: "2017-04-15 12:00",
//   pClass: "ggroupblack",
//   pLink: "",
//   pMile: 0,
//   pRes: "Brian",
//   pComp: 0,
//   pGroup: 1,
//   pParent: 0,
//   pOpen: 1,
//   pDepend: "",
//   pCaption: "",
//   pCost: 1000,
//   pNotes: "Some Notes text",
//   pBarText: "ex. bar text",
//   category: "My Category",
//   sector: "Finance"
// });

g.Draw();

<\/script>
</head>
<body>
  <div class="title">123</div>
  <div style="position:relative" class="gantt" id="GanttChartDIV"></div>

</body>
</html>

`;
	// 解析内部编辑器script
nextTick(()=>{
  
    let parser = new DOMParser();
  let dom = parser.parseFromString(previewHtml.value,'text/html'); // 其中是返回的模板引擎渲染的代码
  
  let scriptList = dom.querySelectorAll('script') as any;
  scriptList.forEach((element:any) => {
    console.log(element);
    eval(element.innerHtml);
    $('#cont').html(previewHtml.value);
    // document.body.appendChild(element);
  })
})

</script>
<style lang="scss">
    .gantt-container {
        padding: 10px;
    }
</style>