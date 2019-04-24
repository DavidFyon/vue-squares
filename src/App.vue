<template>
<div id="app" class="container">
  <div class="row">
    <div class="col-6">
      <div class="col-12">
        <hr />
        <div class="form-group">
          <label>Vert : </label>
          <input class="form-control" v-model="green" type="number" />
        </div>
        <hr />
        <div class="form-group">
          <label>Bleu : </label>
          <input class="form-control" v-model="blue" type="number" />
        </div>
        <hr />
        <div class="form-group">
          <label>Rouge :</label>
          <input class="form-control" v-model="red" type="number" />
        </div>
        <hr />
        <div class="col-12">
          <button class="btn btn-primary" @click="saveSquare()">Sauvegarder</button>
          <button class="btn btn-secondary" @click="reset()">Annuler</button>
        </div>
        <hr />
        <h3> Nombre de carrés : {{ nbrOfSquares }} </h3>
        <hr />
        <div class="col-12" v-if="nbrOfSquares">
          <div class="prevsquare" v-for="square in squares" :style="{backgroundColor: square}"></div>
        </div>
        <h3 v-else> Ajouter des couleurs !</h3>
      </div>
    </div>
    <div class="col-6">
      <div class="square mx-auto"></div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
        green: 0,
        blue: 0,
        red: 0,
        squares: []
    }
  },
  methods: {
    resetColor() {
      this.red = this.green = this.blue = 0;
    },
    saveSquare() {
      this.squares.push(`rgb(${this.red}, ${this.green}, ${this.blue})`);
      this.resetColor();
    },
    reset() {
      this.resetColor();
      this.squares = [];
    }
  },
  computed: {
    nbrOfSquares() {
      return this.squares.length;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.square {
  width: 300px;
  height: 300px;
  margin-top: 50px;
  background-color: #ddd;
}

.prevsquare {
  width: 50px;
  height: 50px;
  display: inline-block;
  margin-left: 10px;
  margin-top: 10px;
  cursor: pointer;
}
</style>
