<template>
  <div class="container">
    <div class="title">
      <h1>Typing Game</h1>
      <div class="marker"></div>
    </div>
    <button v-if="startFlg!=true" class="start-button mb-20" @click="gameStart">START</button>
    <div v-if="startFlg">
      <div class="question mb-20">{{ current_question }}</div>
      <div v-if="current_question_counts == question_counts" class="clear">Clear!</div>
      <div class="type-form-wrapper mb-20">
        <input v-model="typeBox" type="text" class="type-form">
      </div>

      <div class="gauge-wrapper mb-20">
        <div class="gauge"></div>
      </div>
      <div>{{ current_question_counts }}/{{ question_counts }}</div>
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
      typeBox: '',
      current_question_counts: 0,
      question_counts: 0
    }
  },
  methods: {
    gameStart: function() {
      this.startFlg = true;
    }
  },
  // 描画されたタイミング
  mounted: function() {
    this.current_question = this.questions[0]
    this.question_counts = this.questions.length
  },
  watch: {
    typeBox: function(e) {
      if (e == this.current_question) {
        this.questions.splice(0,1)
        this.current_question = this.questions[0]
        this.typeBox = ''
        this.current_question_counts = this.current_question_counts + 1
      }
    }
  }
}
</script>

<style src="../assets/style.css" scoped></style>
