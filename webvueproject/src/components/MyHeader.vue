<template>


    <h2> {{ placeName }}</h2>
    <h2> {{ authorName }}</h2>
  </template>
  
  <script>
  
  
   
  
  export default {
    name: 'MyHeader',
    props: {
        placeName: String,
        authorName: String
    }
    
  }
  
  
  
  
  </script>
  
  
  <style>
  
  
  </style>