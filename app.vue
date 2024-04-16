<script setup>
import SkillInput from './components/skillInput.vue'
const supabase = useSupabaseClient()
const learningExperiences = ref([])

async function getLearingExperiences() {
  const { data } = await supabase.from('LearningExperiences').select()
  learningExperiences.value = data
}

onMounted(() => {
  getLearingExperiences()
})
</script>

<template>
  <div>
    <SkillInput />
    <li v-for="experience in learningExperiences" :key="experience.id">{{ experience.subject }}</li> 
  </div>
</template>
