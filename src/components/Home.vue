<template>
  <div id="starter" v-if="!seen">
    <button @click="seen = !seen">START</button>
  </div>

  <div v-if="seen" id="hide">
    <div class="myDiv" id="box">
      <img :src="PICS[currentSentence].src" />
    </div>
    <div>
      <Botons @btnEvent="btnEvent" :currentSentence="currentSentence" />
      
      <h1>{{ currentSentence + 1 }}</h1>

      <Scene :currentSentence="currentSentence" :PICS="PICS" />
    </div>
  </div>
</template>

<script>
let pic1 = {
  txt: "El nostre heroi estava surant per l'espai sideral quan a la llunyania va albirar una nau espacial",
  src: "public/1.jpg",
  bkg: "tomato",
};
let pic2 = {
  txt: "Sentia curiositat per l'interior de la nau i es va posar a inspeccionar-la. Va arribar a una sala amb dues portes.",
  src: "../src/assets/2.jpg",
  bkg: "blue",
};
let pic3 = {
  txt: "L'heroi va decidir travessar la porta que el portava a casa",
  src: "../src/assets/3.jpg",
  bkg: "orange",
};
let pic4 = {
  txt: "Mentrestant, altres herois no van tenir tanta sort en la seva elecció ...",
  src: "../src/assets/4.jpg",
  bkg: "aquamarine",
};

const PICS = [];
PICS.push(pic1, pic2, pic3, pic4);

let currentSentence = 0;
let bkg = document.getElementById("box");

import Botons from "./Botons.vue";
import Scene from "./Scene.vue";

export default {
  name: "Home",
  components: { Botons, Scene },
  data() {
    return { currentSentence, PICS, seen: false };
  },
  methods: {
   
    btnEvent() {
      if (this.currentSentence >= 4) {
        this.currentSentence = 0;
        document.getElementById("box").style.backgroundColor = PICS[3].bkg;
      } else {
        document.getElementById("box").style.backgroundColor =
          PICS[this.currentSentence].bkg;
        this.currentSentence++;

        document.getElementById("box").style.backgroundImage =
          PICS[this.currentSentence].src;
      }
    },
  },
};
</script>

<style lang="css" scoped>
#starter {
  background-color: red;
  margin: 100px;
  margin-top: 200px;
  padding: 50px;
  border: dashed 10px orange;
  border-radius: 25px;
  place-items: center;
}
.myDiv {
  margin: 0px;
  padding: 0px;
  width: 100%;

  position: absolute;
  z-index: -1;
}
.p {
  background-color: blue;
  height: 150px;
}
img {
  width: 100%;
}
</style>
