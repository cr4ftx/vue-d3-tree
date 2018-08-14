<template>
  <div>
    <tree
      id="vue-d3-tree"
      :width="700"
      :height="500"
      :duration="1000"
      :data="data"
      @click="click"
      :link-class="linkClass"
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

    render () {
      console.log('render')
    },

    linkClass (element) {
      return element.name.length % 2 === 0
        ? 'tree-link--red'
        : 'tree-link--green'
    }
  }
}
</script>

<style>
  html {
    text-align: center;
  }
  svg {
    border: solid 1px lightgray;
    border-radius: 3px;
  }
  .tree-text {
    font: 12px sans-serif;
  }
  .tree-link {
    fill: none;
    stroke: #ccc;
    stroke-width: 2px;
  }
  .tree-circle {
    stroke: steelblue;
    stroke-width: 2px;
    fill: white;
    transition: fill .75s;
  }
  .tree-circle-hide {
    fill: lightsteelblue;
    transition: fill .75s;
  }
  .tree-link--red {
    stroke: lightcoral;
  }
  .tree-link--green {
    stroke: lightgreen;
  }
</style>
