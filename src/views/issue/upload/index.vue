<template>
  <el-table :data="tableData" border>
    <el-table-column v-for="(column, index) in tableColumns" :key="index" :label="column.label">
      <template v-for="(element, elementIndex) in column.elements" :key="elementIndex">
        <template v-if="element.type === 'text'">
          <span>{{ element.value }}</span>
        </template>
        <template v-else-if="element.type === 'button'">
          <el-button>{{ element.value }}</el-button>
        </template>
        <!-- Add more conditions for other element types -->
      </template>
    </el-table-column>
  </el-table>
</template>

<script>
export default {
  data() {
    return {
      tableColumns: [
        { 
          label: 'Column 1', 
          elements: [
            { type: 'text', value: 'Text 1' }
          ]
        },
        { 
          label: 'Column 2', 
          elements: [
            { type: 'button', value: 'Button 1' },
            { type: 'text', value: 'Text 2' }
          ]
        },
        { 
          label: 'Column 3', 
          elements: [
            { type: 'text', value: 'Text 3' },
            { type: 'button', value: 'Button 2' },
            { type: 'text', value: 'Text 4' }
          ]
        },
        // Add more columns with different numbers and types of elements
      ],
      tableData: [
        // Add your data rows here
      ],
    };
  },
};
</script>
