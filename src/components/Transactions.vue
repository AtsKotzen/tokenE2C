<template>
  <div>
    <h1>Reconhecer Tokens E2C</h1>
    <div id="create-e2c">
      <div>
        <label>Quem reconhece</label>
        <input type="text" placeholder="Nome" v-model="quemEmite" />
      </div>
      <br />
      <div>
        <label>Quem recebe</label>
        <input type="text" placeholder="Nome" v-model="quemRecebe" />
      </div>
      <br />
      <div>
        <label>Quantidade</label>
        <input type="number" v-model="amount" />
      </div>
      <br />
      <div>
        <label>Descrição</label>
        <textarea v-model="descricao"></textarea>
      </div>
      <br />
      <div>
        <label>A pessoa que recebe pode registrar o desejo de acessar</label>
        <textarea v-model="desejoAcessar"></textarea>
      </div>
      <br />
      <div>
        <button @click="emitirTokens()">Emitir tokens E2C</button>
      </div>
    </div>
  </div>
</template>
<script>
//import json from "../dummyData/users.json";
export default {
  name: "Transactions",
  data: function() {
    return {
      transactions: [],
      quemEmite: "",
      descricao: "",
      quemRecebe: "",
      amount: null,
      desejoAcessar: ""
    };
  },
  methods: {
    emitirTokens() {
      let payload = {
        dateTime: new Date(),
        fromUser: this.quemEmite,
        toUser: this.quemRecebe,
        amount: this.amount,
        description: this.descricao,
        accessWish: this.desejoAcessar
      };
      let deal = this.transactions;
      deal.push(payload);
      localStorage.setItem("TokensEmitidos", JSON.stringify(deal));
    }
  }
};
</script>
