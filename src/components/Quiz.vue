<template>
  <div>
    <h1>Quiz</h1>
    <div v-html="loading ? `Loading ...` : currentQuestion.question"></div>
    <!-- Only first question is displayed -->
    <form v-if="currentQuestion">
      <button
        v-for="answer in currentQuestion.answers"
        :key="answer"
        :questionIndex="currentQuestion.key"
        v-html="answer"
      >
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      questions: [],
      loading: false,
      questionIndex: 0,
    };
  },
  computed: {
    currentQuestion() {
      if (this.questions !== []) {
        return this.questions[this.questionIndex];
      }
      return null;
    },
  },
  methods: {
    async fetchQuestions() {
      this.loading = true;

      //fetching questions from api
      let response = await fetch(
        "https://opentdb.com/api.php?amount=20&category=21&type=multiple"
      );
      let data = await response.json();
      let questions = data.results.map((question) => {
        question.answers = [
          question.correct_answer,
          ...question.incorrect_answers,
        ];
        return question;
      });
      this.questions = questions;
      this.loading = false;
    },
  },
  mounted() {
    this.fetchQuestions();
  },
};
</script>

<style scoped>
button {
    margin-left: 10px;
    margin-top: 10px;
}
</style>