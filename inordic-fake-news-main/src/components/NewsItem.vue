<script>
  import { useRouter, useRoute } from 'vue-router'
  import axios from 'axios'

  import Loader from "./Loader.vue"

  export default {
  
    beforeMount: function(el) {
      
      const router = useRouter()
      
      console.log("beforeMount router", router)
      console.log("route.query id", router.currentRoute.value.params.id)
      
      const ID = router.currentRoute.value.params.id
      console.log('axios', axios);
      axios.get(`https://fakestoreapi.com/products/${ID}`)
      .then((response) => {
          this.data = response.data
      })
    },
    mounted: () => {
      console.log("mounted")
    },    
    data() {
      return {
        hello: "Привет",
        data: null
      };
    },
    setup() {
      return {
      }
    },
    components: {
      'loader': Loader
    }
  }
</script>

<template>
    <loader v-if="!data"></loader>
    <section v-if="data">
      <button>
        <router-link to='/news/'>
          Назад
        </router-link>
      </button>
      <img v-bind:src="data?.image" v-bind:alt="data?.title">
      <h1>{{data?.title}}</h1>
    </section>
    <comments :id="data.id"></comments>
</template>

<style scoped>
  img{
    max-width: 400px;
  }
  button{
    position: absolute;
    top: 0;
    left: 0;
  }
  button a{
    color: white;
    font-size: 20px;
  }
</style>