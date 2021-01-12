<template>
  <div class="modalWrapper">
    <div class="modal" v-if="mode === 'pre'">
      <ul>
        <li v-on:click="relation()">Связь</li>
        <li v-on:click="component()">Компонент</li>
        <li style="color: red;" v-on:click="cancel()">Отмена</li>
      </ul>
    </div>
    <div class="modal" v-if="mode === 'component'">
      <textarea class="unvisible" v-model="$parent.component.title"></textarea>
      <ul>
        <li v-on:click="showComponent()">Показать</li>
        <li v-on:click="addRelation()">Добавить связь</li>
        <li v-on:click="move()">Переместить</li>
        <li style="color: red;" v-on:click="remove()">Удалить</li>
        <li style="color: red;" v-on:click="cancel()">Отмена</li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  name: 'BlockMenu',
  data: function () {
    return {

    }
  },
  methods: {
    component: function () {
      this.$parent.makeComponent()
    },
    cancel: function () {
      this.$parent.cancelModal()
    },
    remove: function () {
      this.$parent.removeComponent()
    },
    showComponent: function () {
      this.$router.push('component/' + this.$parent.component.id)
    }
  },
  props: {
    mode: null
  }
}
</script>

<style scoped>

.modal > textarea{
  font-size: 20px;
  padding: 3px;
  width: 100%;
  text-align: center;
}

.modalWrapper{
  top: 0;
  left: 0;
  position: absolute;
  width: 100%;
  height: 100%;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.modal{
  position: absolute;
  left: 27%;
  top: 15%;
  width: 40%;
  padding: 50px;
  overflow: hidden;
  background-color: white;
  font-weight: bold;
  box-shadow: 0px 0px 6px 0px #a1a1a1;
  transition: 0.2s;
}

h2{
  text-align: center;
  margin-bottom: 20px;
}

.modal > ul > li{
  list-style: none;
  border-bottom: 2px solid black;
  cursor: pointer;
  padding: 20px;
}

.modal > ul > li:last-child{
  border: 0;
}

.modal > ul > li:hover{
  background-color: #EEEEEE;
}
</style>
