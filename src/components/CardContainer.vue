<template>
  <div>
    <div class="container text-center">
      <Select :genresList="genresList" @optionClick = "onChoosedOption"></Select>
      <div class="row row-cols-1 row-cols-md-5 gx-5 gy-4 py-5">
        <SingleCard
          v-for="(cd, i) in genresFilteredList"
          :key="i"
          :author="cd.author"
          :title="cd.title"
          :year="cd.year"
          :poster="cd.poster"
          :genre="cd.genre"
        ></SingleCard>
      </div>
    </div>

    <Loader v-if="loading === true"></Loader>
  </div>
</template>

<script>
import axios from "axios";
import SingleCard from "./SingleCard.vue";
import Loader from "./Loader.vue";
import Select from './Select.vue';
export default {
  components: { SingleCard, Loader, Select },
  name: "CardContainer",
  data() {
    return {
      cdList: [],
      loading: true,
      choosedGenre: "",
    };
  },
  methods:{
    onChoosedOption(option){
      console.log(option);
      this.choosedGenre = option  
    }
  },
  computed: {
    genresList () {
      const genreObj = {};

      this.cdList.forEach((cd) => {
        const {genre} = cd;

        if (!genreObj[genre]){
          genreObj[genre] = 0
        }

        genreObj[genre]++
      })
      console.log(genreObj);
      return genreObj;
    },  

    genresFilteredList () {
      if (!this.choosedGenre){
        return this.cdList
      }

      return this.cdList.filter((cd) => {
        return this.choosedGenre === cd.genre
      })
    }
  },
  mounted() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((resp) => {
        //console.log(resp.data.response);
        this.cdList = resp.data.response;
        setTimeout(() => {
            this.loading = false;
        }, 1000);
      });
  },
};
</script>

