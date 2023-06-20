<script setup lang="ts">
import { onMounted } from 'vue';

// import { ref } from 'vue'
 // 扩展了节点、边的G6
import G6 from '@antv/g6'
// import * as G6Util from '@antv/util'
import { TREELIST } from '../data/treeList';
const props = defineProps<{ msg: string }>()
const initData = {
  // 点集
  nodes: [
    {
      id: 'node1', // 节点的唯一标识
      type: 'rect',
      size: [100, 40],
      x: 100, // 节点横坐标
      y: 200, // 节点纵坐标
      label: '起始点', // 节点文本
    },
    {
      id: 'node2',
      type: 'rect',
      size: [100, 40],
      x: 300,
      y: 400,
      label: '目标点',
    },
  ],
  // 边集
  edges: [
    // 表示一条从 node1 节点连接到 node2 节点的边
    {
      source: 'node1', // 起始点 id
      target: 'node2', // 目标点 id
      label: '我是连线', // 边的文本
      type: 'cubic'
    },
  ],
};
onMounted(() => {
  console.log('mounted')
  const data = {
  nodes: [
    {
        id: '11',
      x: 100,
      y: 100,
      type: 'rect',
      label: 'rect',
    },
  ],
};

const graph = new G6.Graph({
  container: 'mountNode',
  width: 500,
  height: 300,
  defaultNode: {
    type: 'rect', // 在数据中已经指定了 type，这里无需再次指定
    style: {
      fill: '#bae637',
      stroke: '#eaff8f',
      lineWidth: 5,
      radius: 10,
    },
  },
});
graph.data(data);
graph.render();
})
</script>

<template>
  <div id="mountNode"></div>
</template>

<style scoped>

</style>
