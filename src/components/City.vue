<template>
  <div>
    <b-card :title="city.name" :class="color">
      <b-card-text>
        Qualité de l'air {{ city.iqa }}
      </b-card-text>
    </b-card>
  </div>
</template>

<script>
import { AirQualityService } from "@/services/AirQuality.service";
export default {
  props: {
    city: {
      type:    Object,
      default: null
    },
  },
  data() {
    return {
      color: ''
    };
  },
  mounted() {
    AirQualityService.getAirQuality(this.city.name);

    if (this.city.iqa <= 30) {
      this.color = 'pollution-faible';
    }

    if (this.city.iqa > 30 && this.city.iqa <= 50) {
      this.color = 'pollution-medium';
    }

    if (this.city.iqa > 50) {
      this.color = 'pollution-forte';
    }
  }
};
</script>

<style lang="scss" scoped>
  .pollution-faible {
    background: green;
    color: white;
  }

  .pollution-medium {
    background: orange;
    color: white;
  }

  .pollution-forte {
    background: red;
    color: white;
  }
</style>