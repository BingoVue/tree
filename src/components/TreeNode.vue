<template>
  <li @click.stop="toggle">
    <h3>{{data.title}}</h3>
    <span v-if="isFolder">[{{open ? '-' : '+'}}]</span>
    <ul v-show="open" v-if="isFolder">
      <TreeNode v-for="(item, index) in data.children" :key="index" :data="item"/>
    </ul>
  </li>
</template>

<script>
export default {
  name: 'TreeNode',
  props: {
    data: {
      type: Object,
      require: true
    }
  },
  data: function() {
    return {
      open: false
    };
  },
  computed: {
    isFolder(){
      return this.data.children && this.data.children.length>0
    }
  },
  methods: {
    toggle() {
      if (this.isFolder) {
        this.open = !this.open;
      }
    }
  }
}
</script>