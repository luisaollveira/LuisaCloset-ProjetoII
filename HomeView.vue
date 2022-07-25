<template>
 <banner/>
  <div class="main-container">
    <h1>MONTE O SEU LOOK:</h1>
  <burguerform/>
  </div>
 
</template>


<script>
import banner from "../components/banner.vue"
import burguerform from "../components/burguerform.vue"
export default{
components: {
banner,
burguerform
  }
}
</script>

<style scoped>
.main-container{
  color: #97227e;
}
</style>


