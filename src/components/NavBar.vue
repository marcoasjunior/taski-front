<template>
  <v-bottom-navigation app v-model="value" grow>
    <v-btn @click="changePage('tasks')" value="table">
      <span>Tarefas</span>

      <v-icon>mdi-table</v-icon>
    </v-btn>
    <v-btn @click="changePage('add')" value="plus">
      <span>Adicionar</span>

      <v-icon>mdi-plus</v-icon>
    </v-btn>

    <v-btn @click="changePage('account')" value="account">
      <span>Perfil</span>

      <v-icon>mdi-account</v-icon>
    </v-btn>
  </v-bottom-navigation>
</template>

<script>
export default {
  name: "FormContainer",
  components: {},
  data() {
    return {
      loading: false,
      value: "recent",
    };
  },
  methods: {
    changePage(page) {
      if (page === "tasks") {
        this.$router.push("/tasks");
      } else if (page === "account") {
        this.$router.push("/account");
      } else if (page === "add") {
        this.$router.push("/add");
      }
    },
  },
};
</script>
