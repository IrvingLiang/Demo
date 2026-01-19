<template>
  <div id="app">
    <TreeNode :node="treeData" />
  </div>
</template>

<script>
import TreeNode from './TreeNode.vue';

export default {
  name: 'App',
  components: {
    TreeNode
  },
  data() {
    return {
      treeData: {
        id: 1,
        name: '0',
        children: [
          {
            id: 2,
            name: '0-1',
            children: [
              {
                id: 4,
                name: '0-1-1',
                children: [
              {
                id: 4,
                name: '1-1-1'
              },
              {
                id: 5,
                name: '1-1-2'
              }
            ]
              },
              {
                id: 5,
                name: '0-1-2',
                children: [
              {
                id: 4,
                name: '1-1-1'
              },
              {
                id: 5,
                name: '1-1-2'
              }
            ]
              }
            ]
          },
          {
            id: 3,
            name: '0-2',
            children: [
              {
                id: 6,
                name: '0-2-1'
              },
              {
                id: 6,
                name: '0-2-2',
                children: [
                  {
                    id: 6,
                    name: '0-2-2-1'
                  },
                  {
                    id: 6,
                    name: '0-2-2-2'
                  }
                ]
              }
            ]
          }
        ]
      }
    };
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
