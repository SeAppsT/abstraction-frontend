<template>
  <div class="content">
    <div class="bookmark"><router-link style="
    text-decoration: none;
    display: block;
    width: 100%;
    height: 100%;
    color: black;" to="/">O</router-link></div>
    <div class="workspace"><grid></grid></div>
  </div>
</template>

<script>
import Grid from '@/components/Grid'

export default {
  name: 'GridPage',
  components: {
    Grid
  }
}
</script>

<style scoped>

.workspace{
  width: 90%;
  height: 90%;
  margin: 40px;
  padding: 10px;
  border: 2px solid black;
  overflow: scroll;
  border-radius: 4px;
  box-shadow: 0px 0px 4px 2px #a1a1a1 inset;
}

.bookmark{
  width: 20px;
  height: 80px;
  top: 20%;
  left: 0;
  font-size: 30px;
  text-align: center;
  line-height: 80px;
  background-color: black;
  position: absolute;
  border-radius: 0 5px 5px 0;
  overflow: hidden;
  cursor: pointer;
  transition: 0.2s;
}

.bookmark:hover{
  width: 50px;
  color: white;
}

</style>
