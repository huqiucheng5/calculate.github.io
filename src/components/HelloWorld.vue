<script setup>
import { onMounted, ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)

const questions = ref([])

function generateQuestions(){
  console.info("generateQuestions");
  for(let i =0; i<100; i++){
    const operator = Math.random()>0.5 ? "+" : "-";
    const n1 = Math.floor(Math.random() * 100);
    const n2 = Math.floor(Math.random() * 100);
    let answer;
    if(operator==="+"){
      answer = n1 + n2;
    }else {
      answer = n1 - n2;
    }
    questions.value.push(
      {
        description: `${n1}${operator}${n2}`,
        answer: answer
      }
    )
  }
}

onMounted(()=>{
      console.info("onMounted");
      generateQuestions();
    }
  )



</script>

<template>
  <h1>Calculate</h1>
  <ul>
    <li v-for="(question, index) in questions" :key="index">
      {{ question.description }} ={{ question.answer }}
    </li>
  </ul>

  
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
