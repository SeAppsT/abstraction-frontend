<template>
  <div class="content">
    <div class="topMenu">
      <div>Текст
        <ul>
          <li>Текст</li>
          <li>Изображение</li>
          <li>Текст + изображение</li>
        </ul>
      </div>
      <div></div>
      <div></div>
    </div>
    <input class="unvisible" type="text">
    <textarea class="unvisible" v-if="viewType === 'text'"></textarea>
    <div v-if="viewType === 'image'"></div>
  </div>
</template>

<script>
export default {
  name: 'Component',
  data: function () {
    return {
      viewType: 'text'
    }
  }
}
</script>

<style scoped>

input{
  width: 95%;
  margin: 40px;
  font-size: 35px;
}

.topMenu{
  background-color: black;
  height: 50px;
  width: 100%;
  display: flex;
  justify-content: space-around;
}

.topMenu > div{
  height: 50px;
  color: white;
  text-align: center;
  line-height: 50px;
  overflow: hidden;
}

.topMenu > div > ul{
  opacity: 0;
  transition: 0.2s;
}

.topMenu > div:hover > ul{
  opacity: 1;
}
</style>
