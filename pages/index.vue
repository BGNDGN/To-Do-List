<template>
<div id="container">
  <div id="inline">
    <input id="Input"
           type="text"
           placeholder="Please add a task to list" 
           v-model="GirilenDeger"
           maxlength="66">
    <button class="InputButon" @click="Ekle">Add to List</button>
  </div>
  <div id="Text">
    <ul id="Liste"> List
      <li class="Texts" v-for="(Degerler,index) in GirilenDegerler" :key="index">
        {{ index + 1 }}- {{ Degerler.text }}
        <button class="RemoveButon" @click="Kaldir">Remove</button>
      </li>
    </ul>
  </div>
</div>
</template>

<script>

import "@/pages/index.css"

export default {
  name: 'toDoList',
  data() {
    return {
      GirilenDeger: "",
      GirilenDegerler: [],
    }
  },

  methods: {
    Ekle() {
      if(this.GirilenDeger==="") {
        alert("Girdiğiniz değer boş!");
      }

      if(this.GirilenDeger.trim()) {
        this.GirilenDegerler.push({ text: this.GirilenDeger });
        this.GirilenDeger= ""
      }

    },

    Kaldir(index) {
      this.GirilenDegerler.splice(index, 1);
    }
  }
}
</script>
