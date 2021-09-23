<template>
  <div id="gatificador">
    <div id="gatificador_title">Random Gif Cat</div>
    <form id="gatificador_options" @submit.prevent="gifCat()">
      <div class="gatificador_fields">Título del gif: 
        <input type="text" name="says" id="titulo-gif" v-model="says">
      </div>
      <div class="gatificador_fields">Filtro de color: 
        <select name="filtros-gif" id="filtros-gif" v-model="filter">
          <option value="">- </option>
          <option value="blur">blur</option>
          <option value="monotono">monotono</option>
          <option value="sepia">sepia</option>
          <option value="negative">negative</option>
          <option value="paint">paint</option>
        </select>
      </div>
      <div class="gatificador_fields">Color de título: 
        <select name="color-gif" id="color-gif" v-model="colorGif">
          <option value="">- </option>
          <option value="red">rojo</option>
          <option value="orange">anaranjado</option>
          <option value="yellow">amarillo</option>
          <option value="green">verde</option>
          <option value="blue">azul</option>
          <option value="purple">morado</option>
          <option value="white">blanco</option>
          <option value="black">negro</option>
        </select>
        <div id="gatificador_colorSample" :style="{ 'background-color': colorGif }"></div>
      </div>
      <div class="gatificador_fields">Tamaño de título: 
        <input type="number" name="sizeTitle" id="sizeTitle" min="0" max="500" step="50" v-model="sizeTitle">
      </div>
      <div class="gatificador_button">
        <button type="submit" style="width: 150px">Dame mi Gato!</button>
      </div>
    </form>
    <div id="gatificador_view">
      <img :src="urlGato" alt="GatoGif">
    </div>
  </div>
</template>

<script>
export default {
  name: "RandomGifCat",
  data:()=>({
    urlGato: `https://cataas.com/cat/gif`,
    says: ``,
    filter: ``,
    colorGif: ``,
    sizeTitle: ``,
  }),
  methods: {
    gifCat(){
      if (this.says == '') {
        this.urlGato = `https://cataas.com/cat/gif?filter=${this.filter}&color=${this.colorGif}&size=${this.sizeTitle}`
      } else {
        this.urlGato = `https://cataas.com/cat/gif/says/${this.says}?filter=${this.filter}&color=${this.colorGif}&size=${this.sizeTitle}`
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#gatificador{
  width: 100vw;
  margin: 0;
  padding: 0;
  
  &_title{
    background: lightblue;
    height: 15vh;
    color:rgb(23, 83, 83) ;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: Arial, Helvetica, sans-serif;
    font-size: x-large;
    font-weight: 700;
  }
  &_options{
    background: lightcoral;
    height: 250px;
    color: lightslategray;
    position: relative;
    padding-top: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .gatificador_fields{
    margin-left: auto;
    margin-right: auto;
    display: flex;
    align-items: center;
    width: 300px;
  }
  &_colorSample{
    width: 30px;
    height: 30px;
    border-radius: 50%;
    margin: 0px 10px;
  }
  &_view{
    background: lightblue;
    position: relative;
    text-align: center;
    padding-bottom: 4rem;
  }
  .gatificador_button{
    background: lightblue;
    height: 4rem;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

</style>
