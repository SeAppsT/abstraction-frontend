<template>
  <div v-bind:class="{block: isBlock}">
    <BlockMenu v-if="modalMode === 'pre'" v-bind:mode="modalMode"></BlockMenu>
    <div style="width: 100%; height: 100%;" v-if="component === null" v-on:click="callPreMenu()"></div>
    <div v-if="component" class="component" v-on:click="callComponentMenu()">
      <div v-bind:class="component.color"></div>
      <div style="font-weight: bold;">{{ component.title }}</div>
    </div>
    <BlockMenu v-if="modalMode === 'component'" v-bind:mode="modalMode" v-bind:title="component.title"></BlockMenu>
  </div>
</template>

<script>
import BlockMenu from '@/components/BlockMenu'

export default {
  name: 'Cell',
  components: {
    BlockMenu
  },
  data: function () {
    return {
      isBlock: false,
      component: null,
      name: null,
      modalMode: null
    }
  },
  props: {
    x: null,
    y: null,
    componentInfo: null
  },
  mounted () {
    if (this.componentInfo !== null) {
      this.isBlock = true
      this.component = this.componentInfo
    }
  },
  methods: {
    makeComponent: function () {
      this.component = {
        id: 5,
        title: 'Car',
        color: 'red'
      }
      this.isBlock = true
      this.modalMode = null
    },
    callPreMenu: function () {
      this.modalMode = 'pre'
      console.log(this.x, this.y)
    },
    callComponentMenu: function () {
      this.modalMode = 'component'
    },
    removeComponent: function () {
      this.component = null
      this.isBlock = false
      this.modalMode = null
    },
    cancelModal: function () {
      this.modalMode = null
    }
  }
}
</script>

<style scoped>
.red, .green, .gray{
  border: 1px solid black;
  width: 10px;
  height: 10px;
  margin-bottom: 10px;
  border-radius: 50px;
}

.red{
  background-color: red;
}

.green{
  background-color: green;
}

.gray{
  background-color: gray;
}

.component{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
