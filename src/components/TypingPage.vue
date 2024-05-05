<template>
  <div class="container">
    <div class="title">
      <h1>Typing Game</h1>
      <div class="marker"></div>
    </div>
    <button v-if="!startFlg" class="start-button mb-20" @click="gameStart">START</button>
    <div v-if="startFlg">
      <div class="question mb-20">{{ currentQuestion }}</div>
      <div v-if="currentQuestionCounts === questionCounts" class="clear">Clear!</div>
      <div class="type-form-wrapper mb-20">
        <input id="typeForm" v-model="typeBox" type="text" class="type-form">
      </div>

      <div class="gauge-wrapper mb-20">
        <div :style="styleObject" class="gauge"></div>
      </div>
      <div>{{ currentQuestionCounts }}/{{ questionCounts }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TypingPage',
  data() {
    return {
      startFlg: '',
      currentQuestion: '',
      questions: [
        'apple',
        'banana',
        'orange',
        'kiwi',
        'melon',
      ],
      typeBox: '',
      currentQuestionCounts: 0,
      questionCounts: 0
    }
  },
  computed: {
    styleObject: function() {
      let width = 20 * this.currentQuestionCounts + "%"
      let color;
      if (this.currentQuestionCounts === 5) {
        color = "#03a9f4"
      } else {
        color = "orange"
      }
      return {
        'width': width,
        'background-color': color
      }
    }
  },
  methods: {
    gameStart: function() {
      this.startFlg = true;
      this.$nextTick(function() {
        document.getElementById('typeForm').focus()
      })
    }
  },
  // 描画されたタイミング
  mounted: function() {
    this.currentQuestion = this.questions[0]
    this.questionCounts = this.questions.length
  },
  watch: {
    typeBox: function(e) {
      if (e == this.currentQuestion) {
        this.questions.splice(0,1)
        this.currentQuestion = this.questions[0]
        this.typeBox = ''
        this.currentQuestionCounts = this.currentQuestionCounts + 1
      }
    }
  }
}
</script>

<style src="../assets/style.css" scoped></style>
