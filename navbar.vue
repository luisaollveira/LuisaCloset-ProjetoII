<template>
  <div id="nav">
  

  <router-link to="/">Escolha de Roupas</router-link> |
  <router-link to="/pedidos">Pedidos</router-link>


  </div>  
</template>

<script>
export default {
name: "navbar",
props: [ "logo", "alt"]
}
</script>

<style scoped>
#nav {
  background-color: rgb(220, 189, 221);
  border-bottom: 4px rgb(220, 189, 221);
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
#nav #logo-url {
  margin: auto;
  margin-left: 0%;
}
#logo {
  width: 40px;
  height: 40px;
}

#nav a {
  color: #97227e;
  text-decoration: none;
  margin: 12px;
  transition: .5s;
}

#nav a:hover {
  color:rgb(0, 0, 0);
}

</style>