<script setup>
import { createClient } from '@supabase/supabase-js'
const supabase = createClient('https://wbqhbuxxzypoakzmslxi.supabase.co', 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6IndicWhidXh4enlwb2Frem1zbHhpIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MTMwNTA2NjAsImV4cCI6MjAyODYyNjY2MH0.T_LPqo5YvJlr9AdDCcv2l71ERZiuLYZq2NdBH3YOEXM')
const learningExperiences = ref([])

async function getLearingExperiences() {
  const { data } = await supabase.from('learningExperiences').select()
  learningExperiences.value = data
}

onMounted(() => {
  getLearingExperiences()
})
</script>


<template>
  <div>
    <li v-for="experience in learningExperiences" :key="experience.id">{{ experience.subject }}</li> 
  </div>
</template>
