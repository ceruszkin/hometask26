<script>
import { useRouter } from 'vue-router'
import axios from "axios";

export default {

  beforeMount: function(el) {
    
    const router = useRouter()
    
    console.log("beforeMount router", router)
    console.log("route.query id", router.currentRoute.value.params.id)
    
    const ID = router.currentRoute.value.params.id
    console.log('axios', axios);
    axios.get("https://fakestoreapi.com/products/1")
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
  }
}
</script>

<template>
    <h1>{{data?.title}}</h1>

</template>

<style scoped></style>