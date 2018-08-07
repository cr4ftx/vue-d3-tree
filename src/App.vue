<template>
  <div>
    <tree
      id="vue-d3-tree"
      :width="700"
      :height="500"
      :duration="1000"
      :data="data"
      @click="click"
      :link-class="operationsClass"
      :type="type"
    ></tree>
    <select name="type" v-model="type">
      <option value="tree">Tree</option>
      <option value="cluster">Cluster</option>
    </select>
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
      data,
      type: 'tree'
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
  .node circle {
    stroke: steelblue;
    stroke-width: 2px;
    fill: white;
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
    stroke: lightcoral;
  }
  .link--no-operations {
    stroke: lightgreen;
  }
  html {
    text-align: center;
  }
</style>
