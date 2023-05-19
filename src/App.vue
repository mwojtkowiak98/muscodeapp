<template>
	<div id="app">
		<h1 id="title">Muscode App</h1>
    <div id="container">
      <TodoList/>
      <ProductList/>
      <ProductTiles/>
    </div>
	</div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import ProductList from './components/ProductList.vue'
import ProductTiles from './components/ProductTiles.vue'

export default {
	components: {
		TodoList,
    ProductList,
    ProductTiles
	}
}
</script>

<style>
html {
  background-color: #f5f8fa;
  color: #384a5c;
  font-size: 14px;
  font-family: 'Roboto', sans-serif;
}
h2 {
  margin: 0px;
  font-size: 16px;
}
#title {
  margin: 42px auto;
  text-align: center;
  color: #333;
}
#app {
  max-width: 1180px;
  margin: auto;
}
#container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 15px;
}
#grid-item-1 {
  grid-column: 1/2;
  grid-row: 1/2;
}
#grid-item-2 {
  grid-column: 2/4;
  grid-row: 1/2;
}
#grid-item-3 {
  grid-column: 1/4;
  grid-row: auto;
}
#container > div, #grid-item-3 > div {
  box-shadow: 0px 0px 15px -5px #b2b2b2;
  border-radius: 10px;
  background-color: white;
  padding: 22px 18px 18px 18px;
}
#container > div:last-child {
  background-color: transparent;
  border-radius: 0px;
  box-shadow: none;
  padding: 0px;
}

@media only screen and (max-width: 768px) {
  #container, #grid-item-3 {
    display: flex !important;
    flex-direction: column;
  }
}
</style>