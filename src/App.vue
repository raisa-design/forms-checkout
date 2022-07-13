
<template>
  <div class id="app"> 
    <div class="container">
    <form @submit.prevent="addTodo(todo)" class="formsBody">
      <div v-if="newScreen ===false">
        <div class="topForms">
          <img class="imgTop" src="@/assets/top3.png" alt="">
          <h1 class="titleForms">Formulário <br> para compra de <br>pacotes de adesivos </h1>
        </div>
          
        <div class="formBodyMain">
          <h2 class="subTitleForms">Quais adesivos:</h2>
           <div class="stickerList">
            <label for="" v-on:click="checkboxReact = !checkboxReact"><input type="checkbox"> React </label> 
            <label for="" v-on:click="checkboxVue = !checkboxVue" class="checkboxVue"><input type="checkbox"> Vue </label>
            <label for="" v-on:click="checkboxAngular= !checkboxAngular"><input type="checkbox"> Angular </label>     
           </div>
          
          
          <h2 class="subTitleForms">Quantos adesivos de cada?</h2>
          <div class="quantityStickers">
            <button class="buttonDecrease" v-on:click="qtde = qtde -1 "> - </button>
            <input v-on:click="amoutAdhesive= !amoutAdhesive" class="inputAmount" type="number" v-model="qtde">
            <button class="buttonIncrease" v-on:click="qtde =qtde +1"> + </button>
          </div>
        
          <h2 class="subTitleForms">Observações:</h2>
          <div class="input-group">
            <input
            type="text" 
            v-model="todo.description" 
            class="form-input" 
            placeholder="Alguma dúvida? Recado?"
            >
        </div>
        </div>
        <div class="footer">
            <button class="button" v-on:click="newScreen = true">Enviar</button>
        </div>
      </div>
          <div v-else>
             <div class="doubtMessage">
              <h1 class="titleCart">Lista de itens no carrinho</h1>
              <ul>
                <li v-if="checkboxReact===true">React</li>
                <li v-if="checkboxVue ===true">Vue</li>
                <li v-if="checkboxAngular===true">Angular</li>
              </ul>
              <ul>
                <li v-if="amoutAdhesive===true">Unidades</li>
              </ul>
              <div class="messageCustomer" v-for="t in todos" :key="t.id">
               {{t.description}}
              </div>
            </div>
            {{todo.description}}  
            <div>
              <h1 class="titlePayment">Formas de pagamento:</h1>
              <div class="formOfPaymentCard">
                <input 
                  name="payment"
                  class="inputCard" 
                  type="radio"
                >
              <img
              class="cardPayment"
              src="@/assets/cartao.png"
              alt="Imagem de um cartão de créditocom a cor principal azul claro e ícones amarelo e laranja "
              > 
              <p>Cartão de crédito</p>
            </div>
            <div class="dataCard">
              <p>Número do cartão</p>
              <input type="number">
              <p>Nome completo</p>
              <input type="text">
              <p>Validade</p>
              <input type="number">
              <p>Código de segurança</p>
              <input type="number">
              <label for=""><input type="checkbox">Salvar o cartão</label>
              
            </div>
            <div class="formOfPaymentPix">
               <input 
               name="payment"
               class="inputPix" 
               type="radio"
               >
              <img 
              class="pixPayment"
              src="@/assets/pix.png"
              alt="Imagem do nome Pix na cor cinza e ícone verde claro"
              > 
              <p>Pix</p>
            </div>
            <div class="formOfPaymentTicket">
               <input
              name="payment"
              class="inputTicket"
              type="radio"
              >
              <img 
              class="ticketPayment"
              src="@/assets/boleto.png"
              alt="Imagem do nome Pix na cor cinza e ícone verde claro"
              > 
              <p>Boleto</p>
            </div>
            <div class="finishingBuy">
               <button class="buttonFinishing">Finalizar</button>
            </div>
           
          </div>
          </div>   
     </form>     
    </div>
  </div>
</template>


<script>
  export default {
    name: "app",
    data(){
      return{todos:[],newScreen:false, todo: {checked:false}, checkboxReact:false,
       checkboxVue:false, checkboxAngular:false, qtde:1, amoutAdhesive:false };
    },

    methods:{
      addTodo(todo) {
      todo.id = Date.now()
      this.todos.push(todo)
      this.todo = {checked:false}
    },
      finishForm(newScreen){
        this.newScreen = true;
      },
    
      viewReact(checkboxReact){
        this.checkboxReact =true;
      },

      viewVue(checkboxVue){
        this.checkboxVue =true;
      },

      viewAngular(checkboxAngular){
        this.checkboxAngular=true;
      },
      viewAmount(amoutAdhesive){
        this.amoutAdhesive=true;
      }
    }
  };

</script>

<style>
@import "@/assets/base.css";

#app{
  width:55%;
  height: 400px;
  margin: 0 auto;
  margin-left: auto;
  padding-top: 10px;
  border-radius: 20px;

}
.imgTop{
  width: 100%;
  height: 150px;
  border-radius: 20px;
}
.img-logo{
  max-width: 20px;
  margin:0 auto;
  margin-top:10px;
}
body{
  background-color: #8A2BE2;
}
.topSvg{
  height: 150px;
}
.topForms{
  height: 100px;
  border-radius: 45px 45px 10px 220px;
}
.formsBody{
  border-radius: 22px;
  display:auto;
  background-color:#ffffff;
  box-shadow:5px 10px 18px #000000;

}
.titleForms{
  margin-left: 20px;
  color:#ffffff;
  display:flex;
  font-size:16px;
  bottom:125px;

}
.formBodyMain{
  padding: 50px;
}
.stickerList{
  display:flex;
  flex-direction: column;
}
.checkboxVue{
  margin-top: 10px;
}
.quantityStickers{
  display: flex;
  flex-direction: columns;
  margin-bottom: 10px;
}
.buttonDecrease{
  border: none;
  background-color:#2F3676;
  color: #ffffff;
  font-size: 14px;
  border-radius: 5px;
  font-size: 25px;
  width: 15%;
}
.inputAmount{
  width: 15%;
  margin-left: 5px;
  margin-right: 5px;
  border:none;
  border: solid 1px #8B91B2;
  border-radius: 5px;
  margin-top: 10px;
}
.buttonIncrease{
  border: none;
  background-color:#2F3676;
  color: #ffffff;
  border-radius: 5px;
  font-size: 25px;
  width: 15%;
}
h2{
  color:#000000;
  display:flex;
  font-size:18px;
  font-weight: 800;
}
.form-input{
  border-radius:05px;
}
.form-input{
  padding-bottom: 50px;
  padding-left: 10px;
  font-size: 12px;
  background-color:#DCE3E9;
  height: 90px;
  width: 100%;
  border: solid 1px #8B91B2;
}
.footer{
  display: flex;
  align-items: center;
  align-content: flex-end;
  width: 100%;
  height: 80px;
  background-color:#DCE3E9;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
}
.button{
  background-color: #2F3676;
  margin-left: 270px;
  border:none;
  border-radius: 5px;
  width: 90px;
  height: 30px;
  font-size: 18px;
  font-weight: 700;
  color: #ffffff;
  cursor: pointer;
}
.titleCart{
  font-size: 25px;
  padding-top:20px;
  padding-left: 20px
}
.titlePayment{
  padding-top:20px;
  padding-left: 20px;
  font-size: 25px;
}
.messageCustomer{
  margin-left: 25px;
}
.formOfPaymentCard{
  display:flex;
  padding-bottom: 10px;
}
.inputCard{
  top: 5px;
  margin-left:20px;
  margin-right:5px;
}
.dataCard{
  display: flex;
  flex-direction: column;
  width: 60%;
  margin-left:20px;
  margin-bottom: 30px;
}
.cardPayment{
  top: 2px;
  height: 20px;
  width: 30px;
  margin-left:5px;
  margin-right: 10px;
 }
.formOfPaymentPix{
  display:flex;
  padding-bottom: 20px;
}
.inputPix{
  top: 5px;
  margin-left:20px;
  margin-right:5px;
}
.pixPayment{
  top: 2px;
  height: 20px;
  width: 30px;
  margin-left:5px;
  margin-right: 10px;
}
.formOfPaymentTicket{
  display:flex;
  padding-bottom: 20px;
}
.inputTicket{
  top: 5px;
  margin-left:20px;
  margin-right:5px;
}
.ticketPayment{
  top: 2px;
  height: 20px;
  width: 30px;
  margin-left:5px;  
  margin-right: 10px;
}

.buttonFinishing{
  border: none;
  background-color:#2F3676;
  color: #ffffff;
  border-radius: 5px;
  font-size: 14px;
  width: 25%;
  padding:5px;
  margin-right: 20px;
  bottom:10px;
  margin: 10px;
  cursor: pointer;
}

.finishingBuy{
  display: flex;
  justify-content: flex-end;
}

</style>
