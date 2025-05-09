<template>
    <SinglePlace :places="places" />
  </template>
  
  <script>
  import SinglePlace from './SinglePlace.vue'
  
  export default {
    name: 'PlaceBox',
    components: {
      SinglePlace
    },
    props: {
      places: {
        type: Array,
        required: true
      }
    }
  }
  </script>
  