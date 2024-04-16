<template>
  <div>
    <input v-model="newSkill" @keyup.enter="addSkill" placeholder="Add a skill and press enter">
    <ul>
      <li v-for="(skill, index) in skills" :key="index">{{ skill }}</li>
    </ul>
    <button @click="saveSkills">Save My Profile</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const supabase = useSupabaseClient()
const skills = ref([])
const newSkill = ref('')

function addSkill() {
  if (newSkill.value.trim()) {
    skills.value.push(newSkill.value.trim())
    newSkill.value = ''
  }
}

async function saveSkills() {
  // const { data, error } = await supabase
  //   .from('contacts')
  //   .insert([
  //     { skills: skills.value }
  //   ]);
  // if (error) console.log('Error:', error);
  // else console.log('Data saved:', data);
}
</script>