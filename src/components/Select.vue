<template>
  <select class="form-select-sm" aria-label="Default select example" @click="$emit('optionClick', $event.target.value)">
    <option value="">Seleziona un genere</option>
    <option
      v-for="(num, gen) in genresList"
      :key="gen"
      :value="gen">
      {{ gen }}
    </option>
  </select>
</template>

<script>
export default {
  name: "Select",
  props: {
    genresList: Object,
  },
};
</script>
