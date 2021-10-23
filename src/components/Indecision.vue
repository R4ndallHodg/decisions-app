<template>
  <img v-if="image" :src="image" alt="Background image" />
  <div class="container"></div>
  <div class="indecision-container">
    <input v-model="question" class="question-input" type="text" />
    <p>Remember to end the sentence with an interrogation sign (?)</p>

    <div v-if="isValidQuestion" class="decision-container">
      <h2>{{ question }}</h2>
      <p>{{ answer }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: "",
      answer: null,
      image: null,
      isValidQuestion: false,
    };
  },

  methods: {
    async getAnswer() {
      this.answer = "Loading...";

      const response = await fetch("https://yesno.wtf/api");
      const { answer, image } = await response.json();

      this.answer = answer;
      this.image = image;
    },
  },

  watch: {
    question(value) {
      this.isValidQuestion = false;
      if (!value.includes("?")) return;
      this.isValidQuestion = true;
      this.getAnswer();
    },
  },
};
</script>

<style scoped>
img,
.container {
  position: fixed;
  top: 0;
  min-height: 100%;
  min-width: 100%;
  max-height: 100vh;
  max-width: 100vw;
  overflow: hidden;
  object-fit: cover;
}

.container {
  background-color: rgba(0, 0, 0, 0.7);
}

.indecision-container {
  transform: translate(50%, -450%);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 2;
}

.indecision-container {
  color: rgb(255, 255, 255);
}

.question-input {
  border: 1px solid rgb(83, 79, 79);
  width: 30rem;
  height: 2.5rem;
  border-radius: 10px;
  margin-bottom: 1rem;
  font-size: 1rem;
  color: rgb(87, 87, 87);
  outline: none;
  padding-left: 2rem;
}

.decision-container {
  color: rgb(255, 255, 255);
  transform: translateY(350%);
}

.decision-container p {
  font-size: 2.5rem;
  font-weight: 700;
}

.decision-container h2 {
  font-size: 1.5rem;
  font-weight: 700;
}
</style>
