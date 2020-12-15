<template>
  <div class="row form-group ajouterVille">
    <col-sm-2>
      Ajouter une ville :
    </col-sm-2>

    <b-col sm="3">
      <input type="text" id="cityField" class="form-control" v-model="newCity">
    </b-col>

    <b-col sm="2">
      <b-button @click="addCityAction" class="primary">Ajouter</b-button>
    </b-col>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newCity: null
    };
  },
  methods: {
    addCityAction() {
      if (this.newCity) {
        this.$emit("cityAddEvent", this.newCity);
      }
    }
  },
};
</script>

<style lang="scss" scoped>
.ajouterVille {
  margin-top: 2em;
}
</style>