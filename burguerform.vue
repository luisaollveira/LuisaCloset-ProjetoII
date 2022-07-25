<template>
  <Message :msg="msg" v-show="msg" />
  <div>
    <form id="burger-form" method="POST" @submit="createBurger">
      <div class="input-container">
        <label for="nome">Nome do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
      </div>
      <div class="input-container">
        <label for="nome">Email do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="email" placeholder="Digite o seu email">
      </div>
      <div class="input-container">
        <label for="pao">Escolha o modelo de blusa:</label>
        <select name="pao" id="pao" v-model="pao">
          
          <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
        </select>
      </div>
      <div class="input-container">
        <label for="carne">Escolha o modelo de calça:</label>
        <select name="carne" id="carne" v-model="carne">
          
          <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
        </select>
      </div>
      <div id="opcionais-container" class="input-container">
        <label id="opcionais-title" for="opcionais">Selecione os acessórios:</label>
        <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
          <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
          <span>{{ opcional.tipo }}</span>
        </div>
      </div>
      <div class="input-container">
        <label for="nome">Observações do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="email" placeholder="Suas observações">
      </div>
      <div class="input-container">
        <input class="submit-btn" type="submit" value="Criar meu look!">
      </div>
    </form>
  </div>
</template>

<script>
import Message from './Message.vue'
export default {
  name: "BurgerForm",
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisdata: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      status: "Solicitado",
      msg: null
    }
  },
  methods: {
    async getIngredientes() {
      const req = await fetch('http://localhost:3000/ingredientes')
      const data = await req.json()
      this.paes = data.paes
      this.carnes = data.carnes
      this.opcionaisdata = data.opcionais
    },
    async createBurger(e) {
      e.preventDefault()
      const data = {
        nome: this.nome,
        carne: this.carne,
        pao: this.pao,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado"
      }
      const dataJson = JSON.stringify(data)    
      const req = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: { "Content-Type" : "application/json" },
        body: dataJson
      });
      const res = await req.json()
      console.log(res)
      this.msg = "Look número " + res.id + " escolhido com sucesso!";
      // clear message
      setTimeout(() => this.msg = "", 3000)
      // limpar campos
      this.nome = ""
      this.carne = ""
      this.pao = ""
      this.opcionais = []
      
    }
  },
  mounted () {
    this.getIngredientes()
  },
  components: {
    Message
  }
}
</script>

<style scoped>
  #burger-form {
    max-width: 400px;
    margin: 0 auto;
    max-height: 5000px;
    display: block;
    float: left;
    color: #97227e;
  }
  .input-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 2px;
    padding: 5px;
    max-height: 60px;
    margin-top: 2px;
    width: auto;
  }
  label {
    font-weight: bold;
    margin-bottom: 10px;
    color: #97227e;
    padding: 0px 5px;
    border-left: 4px solid #97227e;
    max-width: 2000px;
    max-height: 50px;

  }
  input, select {
    padding: 5px 10px;
    width: 200px;
  }
 
  .checkbox-container {
    display: inline-block;
  margin-top: 5px;
    width: 500px;
    margin-bottom: 20px;
  }
  .checkbox-container span,
  .checkbox-container input {
    width: 10px;
  }
  .checkbox-container span {
    margin-left: 6px;
    font-weight: bold;
  }
  .submit-btn {
    background-color: rgb(220, 189, 221);
    color:#97227e;
    font-weight: bold;
    border: 2px solid white;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    margin-left: 0px;
  
  }
  .submit-btn:hover {
    background-color: transparent;
  
  }
  #opcionais-container{
     display: inline-block;
     justify-content: space-between;
  }

</style>