<template>
  <div class="container">
    <div class="title">
      <h1>Typing Game</h1>
      <div class="marker"></div>
    </div>
    <button v-if="startFlg!=true" class="start-button mb-20" @click="gameStart">START</button>
    <div class="question mb-20">apple</div>
    <div class="clear">Clear!</div>
    <div class="type-form-wrapper mb-20">
      <input type="text" class="type-form">
    </div>

    <div class="gauge-wrapper mb-20">
      <div class="gauge"></div>
    </div>
    <div>1/5</div>
  </div>
</template>

<script>
export default {
  name: 'TypingPage',
  data() {
    return {
      startFlg: ''
    }
  },
  methods: {
    gameStart: function() {
      this.startFlg = true;
    }
  }
}
</script>

<style src="../assets/style.css" scoped></style>
