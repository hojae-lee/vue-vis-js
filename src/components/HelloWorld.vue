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
      {id: 2696, label: "2696", hidden: false},
      {id: 1205, label: "1205", hidden: false},
      {id: 2697, label: "2697", hidden: false},
      {id: 2021, label: "2021", hidden: true},
      {id: 2047, label: "2047", hidden: true},
      {id: 1696, label: "2696", hidden: false},
    ],
      edges: [
      {id: 'e1', from: 2696, to: 2697, hidden: false},
      {id: 'e2', from: 2696, to: 1205, hidden: false},
      {id: 'e3', from: 1205, to: 2021, hidden: true},
      {id: 'e4', from: 1205, to: 2047, hidden: true}
    ],
      options: {
        nodes: {
          shape: "dot"
        },
        edges: {
          width: 2,
          smooth: { type: "curvedCW", forceDirection: "none", roundness: 0.2 }
        },
        physics: {
          enabled: false,
          barnesHut: {
            theta: 0.5,
            // gravitationalConstant: gravitationalConstant,
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
  width: 600px;
  height: 600px;
  border: 1px solid lightgray;
}
</style>