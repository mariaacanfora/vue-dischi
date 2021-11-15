<template>
    <div class="container">
        <div class="row row-cols-1 row-cols-md-5 gx-5 gy-4 py-5">
            <SingleCard v-for="(cd, i) in cdList" :key="i" :author="cd.author" :title="cd.title" :year="cd.year" :poster="cd.poster" ></SingleCard>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import SingleCard from './SingleCard.vue';
export default {
  components: { SingleCard },
  name: "CardContainer",
  data() {
      return{
          cdList: [],
      }
  },
  mounted() {
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((resp) => {
          //console.log(resp.data.response);
          this.cdList = resp.data.response
      })
  }
  
};
</script>

