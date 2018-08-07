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
import data from '../static/data.json'

export default {
  name: 'app',

  components: {
    Tree
  },

  data () {
    return {
      data
    }
  },

  methods: {
    click ({ name }) {
      console.log(name)
    },

    operationsClass (element) {
      return element.name.length % 2 === 0
        ? 'link--operations'
        : 'link--no-operations'
    }
  }
}
</script>

<style>
  #vue-d3-tree svg {
    outline: solid 2px lightgray;
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
  .link--operations {
    stroke: red;
  }
  .link--no-operations {
    stroke: green;
  }
  html {
    text-align: center;
  }
</style>
