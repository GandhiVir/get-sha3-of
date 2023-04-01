<script setup lang="ts">
import { SHA3 } from 'sha3'
</script>

<script lang="ts">
export default {
  data: () => ({
    SHA3String: '',
  }),
  methods: {
    getSHA3of: function() {
      let textString = '';
      const textInput = <HTMLInputElement>document.getElementById("textInput");
      if(textInput){
        textString = textInput.value;
      }
      const SHA3_BIT = 256;
      const SHA3_DIGEST = 'hex';
      const sha3 = new SHA3(SHA3_BIT);
      this.SHA3String = sha3.update(textString).digest(SHA3_DIGEST);
      sha3.reset();
    }
  }
}
</script>

<template>
  <h1>Get SHA3 for your string</h1>
  <p>Enter your string:</p>
  <input type="text" id="textInput" placeholder="Type your string here..." />
  <div id="example">
    <button v-on:click="getSHA3of">Get SHA3</button>
  </div>
  <br/>
  <p>{{ SHA3String }}</p>
</template>
