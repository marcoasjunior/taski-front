<template>
  <v-card :loading="loading" class="" >
    <slot></slot>
  </v-card>
</template>

<script>
export default {
  name: "FormContainer",
  components: {},
  data() {
    return {
        loading: false,
    }
  }
}
</script>
