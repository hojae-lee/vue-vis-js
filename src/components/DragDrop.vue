<template>
  <div class="">
    <h2>{{ msg }}</h2>
    <table>
      <thead>
        <tr>
          <th>col1</th>
          <th>col2</th>
          <th>col3</th>
          <th>col4</th>
          <th>col5</th>
          <th>col6</th>
          <th>col7</th>
          <th>col8</th>
          <th>col9</th>
        </tr>
      </thead>
      <tbody>
        <tr
          draggable="true"
          @dragstart="startDrag($event, rowIdx)"
          @drop.prevent="onDrop($event, rowIdx)"
          @dragenter.prevent
          @dragover.prevent
          v-for="(row, rowIdx) in rows"
          :key="rowIdx"
        >
          <td
            v-for="(col, colIdx) in cols"
            :key="colIdx">
            {{ row[col] }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'DragDrop',
  props: {
    msg: String
  },
  data() {
    return {
      rows: [{'col1' : 1, 'col2': 2, 'col3': 3, 'col4': 4, 'col5': 5, 'col6': 6, 'col7': 8, 'col8': 9, 'col9': 10}, {'col1' : 1, 'col2': 2, 'col3': 3, 'col4': 4, 'col5': 5, 'col6': 6, 'col7': 8, 'col8': 9, 'col9': 10}, {'col1' : 1, 'col2': 2, 'col3': 3, 'col4': 4, 'col5': 5, 'col6': 6, 'col7': 8, 'col8': 9, 'col9': 10}],
      cols: ['col1', 'col2', 'col3', 'col4', 'col5', 'col6', 'col7', 'col8', 'col9']
    }
  },
  methods: {
    startDrag(event, startNum) {
      console.log('startDrag', event);
      event.dataTransfer.dropEffect = "move"
      event.dataTransfer.effectAllowed = "move"
      event.dataTransfer.setData("selectedItem", startNum)
    },
    onDrop(event, endNum) {
      const selectedItem = Number(event.dataTransfer.getData("selectedItem"))
      console.log('onDrop', event);
      console.log(this.rows[endNum], this.rows[selectedItem])
    }
  }
}
</script>

<style scoped>
  table {
    border-collapse: collapse;
    border: 0;
  }
  th,
  td {
    border: 1px solid #aaa;
    background-clip: padding-box;
    scroll-snap-align: start;
  }
  th,
  td {
    padding: 0.6rem;
    min-width: 6rem;
    text-align: left;
    margin: 0;
  }
  thead th,
  tbody th {
    background-color: #f8f8f8;
  }
</style>