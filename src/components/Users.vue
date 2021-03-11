<template>
  <div class="hello">
    <h1>Usuários</h1>
    <div id="users-list">
      <ul>
        <div v-for="(u, index) in users.users" :key="index">
          <li>{{ u.name }}</li>
          <li>{{ u.email }}</li>
        </div>
      </ul>
    </div>
  </div>
</template>

<script>
import json from "../dummyData/users.json";
export default {
  name: "Users",
  data: function() {
    return {
      users: []
    };
  },
  mounted() {
    this.listUsers();
  },
  methods: {
    listUsers() {
      let usr = json;
      this.users = usr;
    }
  }
};
</script>

<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
