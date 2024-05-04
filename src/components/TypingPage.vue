<template>
  <div class="container">
    <div class="title">
      <h1>Typing Game</h1>
      <div class="marker"></div>
    </div>
    <button v-if="startFlg!=true" class="start-button mb-20" @click="gameStart">START</button>
    <div v-if="startFlg">
      <div class="question mb-20">{{ current_question }}</div>
      <div class="clear">Clear!</div>
      <div class="type-form-wrapper mb-20">
        <input v-model="typeBox" type="text" class="type-form">
      </div>

      <div class="gauge-wrapper mb-20">
        <div class="gauge"></div>
      </div>
      <div>1/5</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TypingPage',
  data() {
    return {
      startFlg: '',
      current_question: '',
      questions: [
        'apple',
        'banana',
        'orange',
        'kiwi',
        'melon',
      ],
      typeBox: ''
    }
  },
  methods: {
    gameStart: function() {
      this.startFlg = true;
    }
  },
  mounted: function() {
    this.current_question = this.questions[0]
  },
  watch: {
    typeBox: function(e) {
      if (e == this.current_question) {
        this.questions.splice(0,1)
        this.current_question = this.questions[0]
        this.typeBox = ''
      }
    }
  }
}
</script>

<style src="../assets/style.css" scoped></style>
