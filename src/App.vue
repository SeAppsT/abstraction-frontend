<template>
  <router-view/>
</template>

<style>
:root {
  --violet: #890cc7;
}

input:focus, textarea:focus{
  outline:none;
}

*{
  margin: 0;
  padding: 0;
  font-family: 'Ubuntu', sans-serif;
}

.content{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.content{
  width: 100%;
  height: 100%;
}

.card{
  display: block;
}

.unvisible {
  border: 2px solid white;
  transition: 0.2s;
  border-radius: 4px;
  font-weight: bold;
}

.unvisible:focus {
  border: 2px dashed gray;
}

::-webkit-scrollbar-button {
  width:5px;
  height:5px;
}

::-webkit-scrollbar-track {
  border-radius: 10px;
  background-color: #CCCCCC;
}

::-webkit-scrollbar-thumb {
  border-radius: 10px;
  background-color: gray;
}

::-webkit-scrollbar-thumb:hover{
  background-color: black;
}

::-webkit-scrollbar{
  width: 5px;
  height: 5px;
}
</style>
