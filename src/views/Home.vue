<template>
  <div class="home">
    <div class="drink">
      <Search v-model:name="name" />
      <DrinksList :name="name" />
    </div>

    <Side class="side" />
  </div>
</template>

<script lang="ts">
import { reactive, computed, ref, defineComponent, toRef, Ref } from "vue";
import { key } from "../store";
import { useStore } from "vuex";
import fetchDrinks from "../composables/fetchDrinks";
import DrinksList from "../components/DrinkList/DrinksList.vue";
import Search from "../components/Search.vue";
import Side from "../components/Side/Side.vue";

export default defineComponent({
  name: "Home",
  components: {
    DrinksList,
    Search,
    Side
  },
  setup() {
    const name = ref("ma");

    return {
      name
    };
  }
});
</script>

<style scoped>
.home {
  display: flex;
  max-width: 960px;
  margin: 0 auto;
}
.drink {
  flex: 1 0 700px;
}
.side {
  flex: 0 0 auto;
}
</style>
