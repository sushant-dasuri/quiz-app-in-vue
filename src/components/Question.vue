<script setup>
import {defineProps, defineEmits} from "vue";

const {question, quiz} = defineProps(['question','quiz']);
const quizType = parseInt(quiz.id) === 1 ? true : false;
const emit = defineEmits(["selectOption"]);
const emitSelectedOption = (isCorrect) => {
    emit("selectOption", isCorrect);
}
</script>

<template>
    <div class="question-container">
            <img v-if="quizType" :src="question.text" />
            <h1 v-else class="question">
               {{question.text}}
            </h1>
        </div>
        <div class="options-container">
            <div v-for="option in question.options" :key="option.id" @click="emitSelectedOption(option.isCorrect)" class="option">
                <p class="option-label">{{option.label}}</p>
                <div class="option-value">
                    <p>{{option.text}}</p>
                </div>
            </div>
        </div>
        
</template>
<style scoped>
.question-container {
    margin-top: 20px;
}

.question-container img {
    width: 200px;
    height: 200px;
    object-fit: cover;
    padding: 15px;
    border: 1px solid #a0a0a0;
    margin: 0px 15px 15px 15px;
}

.question {
    font-size: 40px;
    margin-bottom: 20px;
}

.option {
    display: flex;
    margin-bottom: 20px;
    cursor: pointer;
}

.option-label {
    background-color: bisque;
    width: 50px;
    height: 50px;
    font-size: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.option-value {
    background-color: rgb(244, 239, 239);
    width: 100%;
    font-size: 30px;
    padding: 0px 20px;
}
</style>