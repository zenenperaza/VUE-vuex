<template>
<div> 
  <h1>Contador</h1>
  <h3> {{ counter }} X 2 = {{ times2 }}</h3>
  <button v-on:click="increment">Increment</button>
</div>
</template>

<script lang="ts" setup>
   import { computed } from 'vue'
   import { useStore } from 'vuex';
      const store = useStore()
      const counter = computed(() => store.state.counter)
      const times2 = computed(() => store.getters.times2)
      const increment = () => store.commit('setCounter', counter.value + 1) 


</script>

<style scoped>

</style>

<!-- COMPOSITION API 
import { useStore } from 'vuex';

export default defineComponent({
 name: 'HelloWord',
 setup(){
   const store = useStore()
   const counter = computed(() => store.state.counter)
   const times2 = computed(() => store.getters.times2)
   const increment = () => store.commit('setCounter', counter.value + 1) 
   return {increment, counter, times2}
 }  

}) -->

<!-- OPTION API - 1ERA FORMA
export default defineComponent({
  name: 'HelloWord',
  computed: {
    counter(){
      return this.$store.state.counter
    },
    times2(){
      return this.$store.getters.times2
    }
  },
  methods: {
    increment(){
      this.$store.commit('setCounter', this.counter + 1)        
    }
  }

 }) -->