<template>
  <div>
    <tree
      id="vue-d3-tree"
      :width="700"
      :height="500"
      :duration="1000"
      :data="data"
      @click="click"
      :customClass="operationsClass"
    ></tree>
  </div>
</template>

<script>
import Tree from './components/Tree'

export default {
  name: 'app',

  components: {
    Tree
  },

  data () {
    return {
      data: {
        name: 'root',
        children: [
          {
            name: 'son1',
            children: [{ name: 'grandgrandson1' }, { name: 'grandson2' }]
          },
          {
            name: 'son2',
            children: [{ name: 'grandson3', children: [{ name: 'grandgrandson1' }, { name: 'grandgrandson2' }] }, { name: 'grandson4' }]
          }
        ]
      }
    }
  },

  methods: {
    click ({ name }) {
      console.log(name)
    },

    operationsClass (element) {
      return element.children ? 'aaaaaaaaaa' : 'bbbbbbbbbbbbbb'
    }
  }
}
</script>

<style>
  #vue-d3-tree {
    border: solid 2px lightgray;
  }
  .node-circle {
    fill: white;
    stroke: steelblue;
    stroke-width: 2px;
  }
  .node-circle-children {
    fill: lightsteelblue;
    stroke: steelblue;
    stroke-width: 2px;
  }
  .link {
    fill: none;
    stroke: #ccc;
    stroke-width: 2px;
  }
  .node text {
    font: 12px sans-serif;
  }
</style>
