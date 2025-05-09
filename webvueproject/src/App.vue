<template>

  <MyHeader placeName="Tourist Travel Guide" authorName="By Anitha Kona"/>
  <PlaceBox :places="places[0].places"/>
  

</template>

<script>

import MyHeader from './components/MyHeader.vue'
import PlaceBox from './components/PlaceBox.vue'

export default {
  name: 'App',
  components:{
    MyHeader,
    PlaceBox
  },

  data(){
  return {
    places: []
  }
  },
  methods: {
     async fetchplace(){
      const res = await fetch("https://travelguide-y24n.onrender.com/api")
      const data = await res.json()
      console.log(data)
      return data
     }

  },
  async created(){
    this.places = await this.fetchplace()
  },

}
  






</script>


<style>


@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Montserrat', sans-serif;
}
.container {
  max-width: 400px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 0.3em solid black;
  padding: 30px;
  border-radius: 5px;
}

div{
  margin-bottom: 0.5em;
  text-align: center;
}


</style>
