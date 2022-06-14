<template>
  <v-row justify="center mb-12">
    <div class="mx-3 mt-5 box-1">
      <FormContainer class="">
        <v-form v-model="valid" class="">
          <v-container class="justify-center">
            <div class='d-flex justify-center'>
              <p class="headline">Criar Tarefa</p>
            </div>
            <v-row align="end">
              <v-col cols="12" md="12" class="input">
                <v-text-field dense
                  v-model="title"
                  :rules="titleRules"
                  :counter="50"
                  label="Título"
                  outlined
                  required
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12" md="12">
                <v-text-field dense
                  v-model="description"
                  :rules="descriptionRules"
                  :counter="100"
                  label="Descrição"
                  outlined
                  required
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12" md="12">
                <v-select dense
                  v-model="chosenDays"
                  :items="daysOfWeek"
                  attach
                  chips
                  label="Dias da Semana"
                  outlined
                  multiple
                  class=""
                ></v-select>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12" md="12">
                <v-text-field dense
                  v-model="location"
                  label="Local"
                  outlined
                  required
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12" md="12">
                <v-time-picker 
                  v-model="time"
                  label="Hora"
                  format="24hr"
                  outlined
                  full-width
                  required
                ></v-time-picker>
              </v-col>
            </v-row>
            <v-row justify="center">
              <v-btn
                class="ma-2"
                :loading="loading"
                :disabled="loading"
                color="primary"
                @click="loader = 'loading'"
              >
                Criar tarefa
              </v-btn>
            </v-row>
          </v-container>
        </v-form>
      </FormContainer>
    </div>
  </v-row>
</template>

<script>
import FormContainer from "./FormContainer.vue";
export default {
  name: "CreateTaskForm",
  components: {
    FormContainer,
  },
  data() {
    return {
      description: "",
      tags: "",
      daysOfWeek: [
        "Segunda-feira",
        "Terça-feira",
        "Quarta-feira",
        "Quinta-feira",
        "Sexta-feira",
        "Sábado",
        "Domingo",
      ],
      time: "",
      chosenDays: [],
      loader: null,
      loading: false,

      valid: false,
      titleRules: [
        (v) => !!v || "Obrigatório",
        (v) => v.length <= 50 || "Mais de 50 caracteres",
      ],
      descriptionRules: [
        (v) => !!v || "Obrigatório",
        (v) => v.length <= 100 || "Mais de 100 caracteres",
      ],
      emailRules: [
        (v) => !!v || "E-mail é obrigatório",
        (v) => /^\w+@[a-zA-Z_]+?\.[a-zA-Z]{2,3}$/.test(v) || "E-mail precisa ser válido",
      ],
    };
  },
  watch: {
    loader() {
      const l = this.loader;
      this[l] = !this[l];

      setTimeout(() => (this[l] = false), 3000);

      this.loader = null;
    },
  },
};
</script>
<style>
.box-1 {
  width: 90%;
  max-width: 500px;
}
.box-2 {
  width: 100%;
}

.input {
  width: 100%;
}
</style>
