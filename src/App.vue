<template>
  <div v-for="rating in ratingUpto" :key=rating>
    <Rating :rating=rating @handleClick="handleClick"/>
  </div>
  <div>
      Selected stars: {{ JSON.stringify(selectedStars) }}
  </div>
  <div v-for="car in selectedCars" :key=car.name>
    <p>{{ car.name }} - {{ car.stars }}</p>
  </div>
</template>

<script>
import Rating from '@/components/Rating';
import Data from '@/data';

export default {
  name: 'App',
  components: {
    Rating
  },
  data() {
    return {
      ratingUpto: 5,
      carsData: Data,
      selectedStars: [5]
    }
  },
  computed: {
    selectedCars : function() {
       if ( this.selectedStars.length) {
         return this.carsData.filter((d) => this.selectedStars.includes(d.stars)).sort((a, b) => a.stars - b.stars);
       }
       return this.carsData;
    }
  },
  methods: {
    handleClick(rating) {
      const index = this.selectedStars.indexOf(rating);
      if(index >= 0) {
          this.selectedStars.splice(index, 1);
      } else {
        this.selectedStars.push(rating);
      }
     }
  }
}
</script>


<style scoped>
  div {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
