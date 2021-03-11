<template>
  <div>
    <h1>Tokens Emitidos</h1>
    <div>
      <ul>
        <li v-for="(item, index) in tokenList" :key="index">
          <!-- <p>{{ item.dateTime }}</p> -->
          <p>
            {{ item.fromUser }} reconheceu {{ item.amount }} tokens E2C para
            {{ item.toUser }} {{ item.description }}
          </p>
          <p>
            <strong>Desejo de acessar de {{ item.toUser }}:</strong>
            {{ item.accessWish }}
          </p>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: "TokensEmitidos",
  data: function() {
    return {
      tokenList: []
    };
  },
  mounted() {
    this.getTokenList();
  },
  methods: {
    getTokenList() {
      let tokenList = JSON.parse(localStorage.getItem("TokensEmitidos"));
      this.tokenList = tokenList;
    }
  }
};
</script>
