<template>
  <div class="table_container">
    <div></div>
    <div class=" table_header_col" v-for="item in tableXAxisMetaDatas" :key="item">{{ item }}</div>
    <template v-for="(row) in gridDatas" :key="row.yAxisKey">
      <div class="table_header_row">{{ row.yAxisKey }}</div>
      <div class="table_item" v-for="cell in row.cells" :key="cell.xAxisKey">
        <draggable class="drag-container" v-model="cell.elemets" itemKey="id" group="people" @start="drag = true"
          @end="drag = false">
          <template #item="{ element }">
            <div class="list-group-item">
              {{ element?.name || '' }}
            </div>
          </template>
        </draggable>
      </div>
    </template>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
export default {
  name: "table-example",
  display: "Table",
  components: {
    draggable
  },

  data() {
    return {
      tableXAxisMetaDatas:
        ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H']
      ,
      tableYAxisMetaDatas:
        ['1', '2', '3', '4', '5', '6', '7', '8']
      ,
      gridDatas: [
        {
          yAxisKey: '1', cells: [
            {
              xAxisKey: 'A', elemets: [
                { name: "Juan", id: 5 },
                { name: "Edgard", id: 6 },
                { name: "Johnson", id: 7 }
              ]
            },
            { xAxisKey: 'B', elemets: [] },
            { xAxisKey: 'C', elemets: [] },
            { xAxisKey: 'D', elemets: [] },
            { xAxisKey: 'E', elemets: [] },
            { xAxisKey: 'F', elemets: [] },
            { xAxisKey: 'G', elemets: [] },
            { xAxisKey: 'H', elemets: [] }]
        },
        {
          yAxisKey: '2', cells: [
            { xAxisKey: 'A', elemets: [] },
            { xAxisKey: 'B', elemets: [] },
            { xAxisKey: 'C', elemets: [] },
            { xAxisKey: 'D', elemets: [] },
            { xAxisKey: 'E', elemets: [] },
            { xAxisKey: 'F', elemets: [] },
            {
              xAxisKey: 'G', elemets: [
                { name: "Juan", id: 5 },
                { name: "Edgard", id: 6 },
                { name: "Johnson", id: 7 }
              ]
            },
            { xAxisKey: 'H', elemets: [] }]
        },
        {
          yAxisKey: '3', cells: [
            { xAxisKey: 'A', elemets: [] },
            { xAxisKey: 'B', elemets: [] },
            { xAxisKey: 'C', elemets: [] },
            { xAxisKey: 'D', elemets: [] },
            { xAxisKey: 'E', elemets: [] },
            { xAxisKey: 'F', elemets: [] },
            { xAxisKey: 'G', elemets: [] },
            { xAxisKey: 'H', elemets: [] }]
        },
        {
          yAxisKey: '4', cells: [
            { xAxisKey: 'A', elemets: [] },
            { xAxisKey: 'B', elemets: [] },
            { xAxisKey: 'C', elemets: [] },
            { xAxisKey: 'D', elemets: [] },
            { xAxisKey: 'E', elemets: [] },
            { xAxisKey: 'F', elemets: [] },
            { xAxisKey: 'G', elemets: [] },
            { xAxisKey: 'H', elemets: [] }]
        },
        {
          yAxisKey: '5', cells: [
            { xAxisKey: 'A', elemets: [] },
            { xAxisKey: 'B', elemets: [] },
            { xAxisKey: 'C', elemets: [] },
            { xAxisKey: 'D', elemets: [] },
            { xAxisKey: 'E', elemets: [] },
            { xAxisKey: 'F', elemets: [] },
            { xAxisKey: 'G', elemets: [] },
            { xAxisKey: 'H', elemets: [] }]
        },
        {
          yAxisKey: '6', cells: [
            { xAxisKey: 'A', elemets: [] },
            { xAxisKey: 'B', elemets: [] },
            { xAxisKey: 'C', elemets: [] },
            { xAxisKey: 'D', elemets: [] },
            { xAxisKey: 'E', elemets: [] },
            { xAxisKey: 'F', elemets: [] },
            { xAxisKey: 'G', elemets: [] },
            { xAxisKey: 'H', elemets: [] }]
        },
        {
          yAxisKey: '7', cells: [
            { xAxisKey: 'A', elemets: [] },
            { xAxisKey: 'B', elemets: [] },
            { xAxisKey: 'C', elemets: [] },
            { xAxisKey: 'D', elemets: [] },
            { xAxisKey: 'E', elemets: [] },
            { xAxisKey: 'F', elemets: [] },
            { xAxisKey: 'G', elemets: [] },
            { xAxisKey: 'H', elemets: [] }]
        },
        {
          yAxisKey: '8', cells: [
            { xAxisKey: 'A', elemets: [] },
            { xAxisKey: 'B', elemets: [] },
            { xAxisKey: 'C', elemets: [] },
            { xAxisKey: 'D', elemets: [] },
            { xAxisKey: 'E', elemets: [] },
            { xAxisKey: 'F', elemets: [] },
            { xAxisKey: 'G', elemets: [] },
            { xAxisKey: 'H', elemets: [] }]
        }],
      dragging: false
    };
  },

  methods: {
    onAddDraggable(event, xAxisKey, yAxisKey) {
      console.log({ event, xAxisKey, yAxisKey })
    },
    onLogChange(event) {
      console.log(event)
    }
  }
};
</script>
<style scoped>
.table_container {
  margin: 16px;
  display: grid;
  grid-template-columns: repeat(9, 1fr);
}

.table_header_row {
  display: flex;
  align-items: start;
}

.table_header_col {
  display: flex;
  align-items: end;
}

.table_item {
  border: 1px grey solid;
  min-width: 250px;
  min-height: 100px;
  width: max-content;
  height: auto;
  align-items: center;

}

.list-group-item {
  margin: 8px;
  background-color: gray;
  cursor: pointer;
  min-height: 50px;
  min-width: 90px;
  padding: 8px;
  border-radius: 4px;

}

.drag-container {
  padding: 8px;
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>