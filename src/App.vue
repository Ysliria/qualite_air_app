<template>
  <div id="app">
    <div class="container">
      <h1>Mesure de la qualité de l'air</h1>
      <div class="row">
        <div v-for="city of cities" :key="city.index" class="col-sm-4">
          <City :city="city" @deleteCity="deleteCityAction"/>
        </div>
      </div>

      <CityForm @cityAddEvent="addCityAction" />
      <Alert v-if="showAlert" :type="typeAlert" :message="messageAlert" />
    </div>
  </div>
</template>

<script>
import City from '@/components/City';
import CityForm from '@/components/CiryForm';
import Alert from '@/components/Alert';

import {AirQualityService} from '@/services/AirQuality.service';

export default {
  name:       'App',
  components: {
    City,
    CityForm,
    Alert
  },
  data() {
    return {
      cities:       [
        {name: 'Lyon', iqa: null},
        {name: 'Paris', iqa: null},
        {name: 'Brest', iqa: null}
      ],
      typeAlert:    '',
      messageAlert: '',
      showAlert:    false
    };
  },
  methods:    {
    async addCityAction(cityName) {
      const dataForNewCity = await AirQualityService.getAirQuality(cityName);

      if (dataForNewCity !== 'Unknown station') {
        this.cities.push({
          name: cityName,
          iqa:  null
        });

        this.typeAlert    = 'success';
        this.messageAlert = 'Ville Ajoutée avec succès';
        this.showAlert    = true;
      } else {
        this.typeAlert    = 'warning';
        this.messageAlert = 'Ville non disponible !';
        this.showAlert    = true;
      }
    },
    deleteCityAction(city) {
      const indexToDelete = this.cities.findIndex(cityItem => cityItem.name ===city.name);

      this.cities.splice(indexToDelete);
    }
  },
};
</script>

<style>
</style>
