<template>
  <div id="grid">
    <Cell
      v-bind:key="item.toString()"
      v-for="item in blocks"
      v-bind:x="item.x" v-bind:y="item.y"
      v-bind:componentInfo="item.component">
    </Cell>
  </div>
</template>

<script>
import axios from 'axios'
import Cell from '@/components/Cell'

export default {
  name: 'Grid',
  components: {
    Cell
  },
  data: function () {
    return {
      blocks: []
    }
  },
  mounted () {
    // eslint-disable-next-line no-unused-vars
    let components = []
    axios
      .get('http://81.177.6.174:8080/components/111')
      .then(response => (components = response.body))
      .catch(response => (console.log(response)))
    for (let i = 0; i < 900; i++) {
      const obj = {
        x: i % 30,
        y: Math.round(i / 30),
        component: null
      }
      this.blocks.push(obj)
    }
  }
}
</script>

<style scoped>

#grid{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  grid-gap: 5px;
}

#grid > div{
  border: 2px solid gray;
  display: block;
  width: 100px;
  height: 100px;
  border-radius: 4px;
  background-color: #303030;
  transition: 0.2s;
}

#grid > div:hover{
  border: 2px solid black;
  background-color: #909090;
}

#grid > div > ul{
  display: block;
  width: 100%;
  height: 100%;
  list-style: none;
}

#grid > div > ul > li{
  display: flex;
  height: 49%;
  justify-content: center;
  align-items: center;
}

#grid > div > ul > li:hover{
  background-color: #EEEEEE;
}

#grid > div > ul > li:first-child{
  border-bottom: 2px inset black;
}

.block{
  background-color: white!important;
  border: 2px solid white!important;
  border-radius: 2px!important;
  box-shadow: 0px 0px 4px 0px #a1a1a1;
  cursor: pointer;
}
</style>
