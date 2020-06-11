<template>
  <div id="app">
    <h1>Problema de Monty Hall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="doorAmount">Quantas portas?</label>
        <input type="text" id="doorAmount" size="3" v-model.number="doorAmount" />
      </div>
      <div v-if="!started">
        <label for="selectedDoor">Qual a porta premiada:</label>
        <input type="text" id="selectedDoor" size="3" v-model.number="selectedDoor" />
      </div>
      <button v-if="!started" @click="started=true">Iniciar</button>
      <button v-if="started" @click="started=false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">
        <div v-for="i in doorAmount" :key="i">
            <Door :hasGift="i === selectedDoor" :number="i" />
        </div>
    </div>
  </div>
</template>

<script>
import Door from "./components/Door";

export default {
  name: "App",
  components: { Door },
  data() {
    return {
      started: false,
      doorAmount: 3,
      selectedDoor: null
    };
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}

body {
  color: #fff;
  background: linear-gradient(
    to right,
    #67b26f,
    #4ca2cd
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app h1 {
  border: 1px solid #000;
  background-color: #0004;
  padding: 20px;
  margin-bottom: 60px;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}

.form div {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 300px;
}

.form button {
    margin-top: 20px;
    width: 100px;
    height: 40px;
    /* border-radius: 50px; */
}

.doors {
    align-self: stretch;

    display: flex;
    flex-direction: row;
    justify-content: space-around;
    flex-wrap: wrap;
}

</style>