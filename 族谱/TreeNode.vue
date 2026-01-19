<script setup>
import { ref } from 'vue'

const msg = ref('Hello World!')
</script>

<template>
   <div class="container">
      <div class="tree-container">
        <div class="tree">
          <!-- 第一层 -->
          <div class="tree-level">
            <div class="node">
              <h3>{{node.name}}</h3>
              <p>顶层父节点</p>
            </div>
          </div>
          <div v-if="node.children && node.children.length" class="tree-level">
            <div  v-for="child in node.children" :key="child.id" :node="child">
              <div class="children">
                 <TreeNode :node="child" />
              </div>
            </div>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'TreeNode',
  props: {
    node: {
      type: Object,
      required: true
    }
  }
}
</script>

<style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    .container {
      max-width: auto;
      width: 100%;
      background: rgba(0, 20, 40, 0.85);
      border-radius: 15px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
      padding: 10px;
      backdrop-filter: blur(10px);
    }

    header {
      text-align: center;
      margin-bottom: 30px;
    }
      
    .subtitle {
      color: #a0d2ff;
      font-size: 1.1rem;
      max-width: 600px;
      margin: 0 auto;
      line-height: 1.6;
    }

    h1 {
      font-size: 2.5rem;
      margin-bottom: 10px;
      background: linear-gradient(45deg, #00c6ff, #0072ff);
      background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    }

    .tree-container {
      display: flex;
      justify-content: center;
    }

    .tree {
      display: flex;
      flex-direction: column;
      align-items: center;
      position: relative;
       border: solid  green;
      padding: 10px 0;
    }
    
    .tree-level {
      display: flex;
      justify-content: center;
      position: relative;
      width: 100%;
      border: solid  red;
    }

      .tree-level:not(:last-child) {
      margin-bottom: 60px;
    }
    
    .node::before {
      content: '';
      position: absolute;
      top: -45px;
      bottom: 0px;
      left: 50%;
      width: 3px;
      height: 45px;
      transform: translateX(-50%);
       background: linear-gradient(10deg,yellow);
      z-index: -1;
    }

    .children::before {
      content: '';
      position: absolute;
      top: -20px;
      bottom: 0px;
      width: 100%;
      height: 3px;
       background: linear-gradient(10deg,yellow);
      z-index: 6;
    }



    
    .tree-level:first-child::before {
      top: 0;
      height: calc(50% + 30px);
    }
    
    .tree-level:last-child::before {
      bottom: 0;
      height: calc(50% + 30px);
    }

    .node {
      background: linear-gradient(135deg, #0072ff, #00c6ff);
      color: white;
      padding: 15px 25px;
      border-radius: 10px;
      text-align: center;
      min-width: 180px;
      box-shadow: 0 5px 15px rgba(0, 114, 255, 0.4);
      position: relative;
      z-index: 2;
      transition: all 0.3s ease;
      border: 2px solid rgba(255, 255, 255, 0.2);
    }
    
    .node:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 20px rgba(0, 114, 255, 0.6);
    }
    
    .node h3 {
      font-size: 1.3rem;
      margin-bottom: 5px;
    }
    
    .node p {
      font-size: 0.9rem;
      opacity: 0.9;
    }

    .children {
      display: flex;
      justify-content: center;
      position: relative;
      width: 100%;
    }
    



</style>
