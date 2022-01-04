<template>
      <form class="search-form m-6 flex justify-center items-center">
      <input
        class="search-input rounded-l-2xl w-3/4 p-4 border-0 sm:p-2"
        type="text"
        placeholder="Search using any IP address"
        v-model="searchInput" @keyup.enter="takeIP"
      />
      <button class="p-4 rounded-r-2xl bg-black sm:p-2" type="submit" @click.prevent="takeIP"> <i class="fas fa-search text-white text-xl"></i></button>
    </form>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css'
import '@fortawesome/fontawesome-free/js/all.js'
export default {
  name: 'SearchBar',

  data() {
    return {
      searchInput: "",
    };
  },
  methods: {
    // search function
    takeIP() {
      this.$emit("trackIp", this.searchInput);
    },
  },
}
</script>
