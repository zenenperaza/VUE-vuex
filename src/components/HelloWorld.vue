<template>
<div> 
  <h1>Contador</h1>
  <h3> {{ counter }} X 2 = {{ times2 }}</h3>
  <button v-on:click="increment">Increment</button>
</div>
</template>

<script lang="ts">
   import { defineComponent, Ref } from 'vue'
   import { mapMutations, mapState, mapGetters } from 'vuex'

   export default defineComponent({
    name: 'HelloWord',
    computed: {
      ...mapState(['counter']),
      ...mapGetters(['times2'])
    },
    methods: {      
      ...mapMutations(['setCounter']),
      increment(){
        this.setCounter(this.counter + 1)
      }
    }

   })
</script>

<style scoped>

</style>


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