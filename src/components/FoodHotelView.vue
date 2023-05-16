<script setup>
import FoodCard from "./FoodCard/FoodCard.vue";
import HotelCard from "./HotelCard/HotelCard.vue";
</script>

<template>
  <div class="food-cards">
    <FoodCard
      :width="360"
      :height="530"
      :imageUri="'pepperoni-pizza.jpg'"
      :title="'Pepperoni Pizza'"
      :fireIcon="true"
      :wheatIcon="true"
      :leafIcon="false"
      :description="'Premium pepperoni and cheese is made with real mozzarella on original hand-tossed crust.'"
      :temperature="53.8"
      :calories="265"
      :pfc="'12/10/31'"
      :originalPrice="29.9"
      :priceWithDiscount="23.9"
    />

    <FoodCard
      :width="360"
      :height="530"
      :imageUri="'tortellini.png'"
      :title="'Tortellini'"
      :fireIcon="true"
      :wheatIcon="true"
      :leafIcon="true"
      :description="'Pasta stuffed with beef and pork topped with your choice of cream sauce with bacon, bolognese or marinara sauce.'"
      :temperature="42.4"
      :calories="270"
      :pfc="'18/4/41'"
      :originalPrice="22.9"
      :priceWithDiscount="17.9"
    />

    <FoodCard
      :width="360"
      :height="530"
      :imageUri="'strawberry-cake.png'"
      :title="'Strawberry Cake'"
      :fireIcon="false"
      :wheatIcon="true"
      :leafIcon="false"
      :description="'Three layer strawberry dessert is not only beautiful looking, but also delicious! Perfect dessert for spring and summer.'"
      :temperature="13.9"
      :calories="346"
      :pfc="'6/14/49'"
      :originalPrice="18.9"
      :priceWithDiscount="13.9"
    />
  </div>
</template>

<style scoped lang="scss">
.food-cards {
  display: flex;
  flex-direction: row;
}
</style>
