<template>

<navbar  :alt="app_name"/>

<router-view />
<footer1 id="footer1"/>

</template>

<script>
import navbar from "./components/navbar.vue";
import Footer1 from "./components/footer.vue";
export default {
  components: {
    navbar,
    Footer1
},
  data(){
    return {
       logo_src: "public/img/logo.png",
      app_name: ""
    }
  }
}
</script>

<style>
* {
  font-family: Helvetica;
  padding: 0px;
  margin: 0px;
  box-sizing: border-box ;
}

.main-container{
  margin:50px;
  height: 250px;
  color: #97227e;

}
h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 40px;
  color: #97227e;
}
#footer{
    height: 200px;
    background-color: rgb(220, 189, 221);
    border-top: 4px solid white;
    color: rgb(220, 189, 221);
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    bottom:0%;
}
#footer1{
    height: 200px;
    background-color:rgb(220, 189, 221);
    border-top: 4px solid white;
    color: #97227e;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    bottom:0%;
}
</style>