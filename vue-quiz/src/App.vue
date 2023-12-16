<script>
export default{
  data(){
    return{
      questions: [
          {
            text: "Вопрос 1",
            responses: [
              {text: 'Неправильно, очень плохо.'}, 
              {text: 'Правильно!', correct: true}, 
            ],
            userAnswer: null
          }, {
            text: "Вопрос 2",
            responses: [
              {text: 'Правильный ответ', correct: true}, 
              {text: 'Неправильный ответ'}, 
            ],
            userAnswer: null
          },
          {
            text: "Вопрос 3",
            responses: [
              {text: 'Правильный ответ', correct: true}, 
              {text: 'Неправильный ответ'}, 
            ],
            userAnswer: null
          },
          {
            text: "Вопрос 4",
            responses: [
              {text: 'Правильный ответ', correct: true}, 
              {text: 'Неправильный ответ'}, 
            ],
            userAnswer: null
          }
        ],
        questionIndex: 0,
        correctAnswers: 0,
        showResults: false
    }
  },
  methods:{
    next(){
      this.questionIndex++;
    },
    prev(){
      this.questionIndex--; 
    },
    checkAnswers() {
      this.correctAnswers = this.questions.filter(question => {
        return question.responses.find(responses => responses.text === question.userAnswer && responses.correct)
      }).length
      this.showResults = true
    }
  }
  }
</script>
<template>
  <div v-for="(question, index) in questions">
    <div v-show="index === questionIndex">
      <h2>{{ question.text }}</h2>
      <ol>
        <li v-for="response in question.responses">
          <label>
            <input type="radio"
            :value="response.text" v-model="question.userAnswer"
            > {{response.text}}
          </label>
        </li>
      </ol>

      <button v-if="questionIndex > 0" v-on:click="prev">
        Предыдущий
      </button>
      <button v-on:click="next">
        Следующий
      </button>
    </div>
  </div>
  <div v-if="questionIndex === questions.length">
      <button @click="checkAnswers">Check Answers</button>
    </div>
    <p v-if="showResults">You got {{ correctAnswers }} out of {{ questions.length }} correct.</p>
</template>

<style scoped>

</style>
