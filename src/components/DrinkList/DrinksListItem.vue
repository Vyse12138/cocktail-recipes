<template>
  <router-link :to="'/' + drink.strDrink" class="drink">
    <div class="drink-text">
      <h3 class="drink-text-title">{{ drink.strDrink }}</h3>
      <p>
        {{
          drink.strInstructions.length > 150
            ? drink.strInstructions.slice(0, 150).concat("...")
            : drink.strInstructions
        }}
      </p>
    </div>

    <img class="drink-img" :src="drink.strDrinkThumb" :alt="drink.strDrink" />
  </router-link>
</template>

<script lang="ts">
import { ref, defineComponent, toRefs, reactive, PropType } from "vue";
import Drink from "../../interfaces/Drink";

export default defineComponent({
  name: "DrinksListItem",
  props: {
    drink: {
      type: Object as PropType<Drink>,
      required: true
    }
  },
  setup(props) {
    const { drink } = toRefs(props); // destructure props
    
    return {
      drink
    };
  }
});
</script>

<style scoped>
a {
  color: black;
  text-decoration: none;
}

.drink {
  padding: 1.5rem 2rem;
  height: 100px;
  display: flex;
  flex-wrap: nowrap;
  flex-direction: row;
  cursor: pointer;
  border-bottom: 1px solid rgba(178, 186, 194, 0.15);
  background-color: #ffffff;
}
.drink-text {
  text-align: left;

  margin-top: -0.75em;
  flex: 1 1 auto;
  padding-right: 1rem;
}

.drink-img {
  flex: 0 0 auto;

  width: 100px;
  height: 100px;
}
</style>
