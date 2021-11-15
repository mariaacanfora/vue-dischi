<template>
  <div class="col">
    <div class="card bg-header border-0 px-4 pt-4 pb-card rounded-0">
      <img :src="poster" class="card-img-top" :alt="title"/>
      <div class="card-body text-center ">
        <h4 class="text-light mb-3">{{title.toUpperCase()}}</h4>
        <h5 class="text-card m-0">{{author}}</h5>
        <h6 class="text-card">{{year}}</h6>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleCard",
  props: {
      "poster" : String ,
      "title": String, 
      "author": String,
      "genre": String,
      "year": Number
  }
};
</script>
