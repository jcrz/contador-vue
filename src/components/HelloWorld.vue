<template>
  <div class="container">
    <section class="contador-div">
      <b-row>
        <b-col cols="12" md="12">
          <h1>Counter Game!</h1>
        </b-col>
        <b-col cols="12" md="12">
          <h4>Clicks: {{ contador }}</h4>
          <br>
        </b-col>
        <b-col cols="12" md="12">
          <b-button @click="aumentarContador()" v-on:mouseover="mouseIn" v-on:mouseleave="mouseOut" class="btn">
            {{ btnNombre }}
          </b-button>
        </b-col>
      </b-row>
    </section>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function(){
    return {
      contador: 0,
      btnNombre: 'Contador'
    }
  },
  mounted() {
    if (localStorage.contador){
      this.contador = localStorage.contador;
    }
  },
  watch: {
    contador(valor) {
      localStorage.contador = valor;
    }
  },
  methods: {
    aumentarContador(){
      this.contador++;
    },
    mouseIn: function() {
      this.btnNombre = '+ 1'
    },
    mouseOut: function(){
      this.btnNombre = 'Contador'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 500px;
}
.contador-div {
  background-color: darkblue;
  color: white;
  border-radius: 10px;
  padding: 20px;
}
.btn {
  color: #212529;
  background-color: #ffc107;
  width: 300px;
}
.btn:hover {
  background-color: #ffc107;
  color: #212529;
}
</style>
