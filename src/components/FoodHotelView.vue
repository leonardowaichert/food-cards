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
  <div class="hotel-cards">
    <HotelCard
      :width="515"
      :height="715"
      :imageUri="'montreal.jpg'"
      :title="'DoubleTree Montreal Hotel'"
      :wifiIcon="true"
      :foodIcon="true"
      :swimIcon="false"
      :stars="4"
      :ranking="'#7 bugdet'"
      :stayDate="'sep 22-27'"
      :availableRooms="'2 rooms'"
      :discountPrice="99"
      :originalPrice="149"
      :description="'The Hotel DoubleTree Montréal Centre-Ville / Downtown is set in the heart of the city, a few steps away from the lovely cafés and boutiques. The Hotel offers warm hospitality in a wonderful relaxed atmosphere and many other services.'"
    />

    <HotelCard
      :width="515"
      :height="715"
      :imageUri="'bali.jpg'"
      :title="'Holiday Inn Resort Bali Benoa'"
      :wifiIcon="true"
      :foodIcon="true"
      :swimIcon="true"
      :stars="5"
      :ranking="'#3 spa'"
      :stayDate="'sep 25-30'"
      :availableRooms="'1 room'"
      :discountPrice="250"
      :originalPrice="400"
      :description="'Located on the sparkling waterfront of Tanjung Benoa Beach, the Holiday Inn Resort Bali Benoa offers beachfront activities, an exciting Kids Club, four pools, chilled-out lounge zones, free Wi-Fi and our signature Tea Tree Spa for optimum relaxation.'"
    />
  </div>
</template>

<style scoped lang="scss">
.food-cards,
.hotel-cards {
  display: flex;
  flex-direction: row;
}
</style>
