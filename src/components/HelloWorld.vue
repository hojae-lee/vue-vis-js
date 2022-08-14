<template>
  <div class="">
    <h2>{{msg}}</h2>
    <vis-network class="network" ref="network" :nodes="nodes" :edges="edges" :options="options"></vis-network>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      nodes: [
        {id: "ap1", label: "ap1", hidden: false, shape: "image", image: "./logo.png"},
        {id: "pro1", label: "pro1", hidden: false},
        {id: "pro2", label: "pro2", hidden: false},
        {id: "pro3", label: "pro3", hidden: false},
        {id: "pro4", label: "pro4", hidden: false, color: {border: "#666", highlight: {border:"#666"}}},
      ],
      edges: [
        { id: 'e1', from: "ap1", to: "pro1", label: "33" },
        { id: 'e2', from: "ap1", to: "pro2", label: "11", dashes: true },
        { id: 'e3', from: "ap1", to: "pro3", label: "134", background: { enabled: true, color: "#000", size: 5 }},
        { id: 'e4', from: "ap1", to: "pro4", label: "", dashes: [1, 4], color: "#666" },
      ],
      options: {
        nodes: {
          shape: "dot",
          font: {
            size: 15,
            color: "#ffffff"
          },
          color: {
            background: "#222222",
            highlight: {
              background: "#222222"
            }
          }
        },
        physics: {
          enabled: false,
          barnesHut: {
            centralGravity: 0,
            springLength: 10,
            springConstant: 0.04,
            damping: 0.09,
            avoidOverlap: 1
          }
        },
        layout: {
          randomSeed: 3
        }
      }
    }
  }
}
</script>

<style scoped>

.network {
  width: 800px;
  height: 800px;
  border: 1px solid #444444;
  background-color: #222222;
}
</style>