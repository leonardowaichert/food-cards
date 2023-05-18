<script setup>
import { reactive } from "vue";

const props = defineProps({
  imageUri: String,
  width: Number,
  height: Number,
  title: String,
  description: String,
  stars: Number,
  ranking: String,
  originalPrice: Number,
  discountPrice: Number,
  availableRooms: Number,
  stayDate: String,
  wifiIcon: Boolean,
  foodIcon: Boolean,
  swimIcon: Boolean,
});

const state = reactive({
  isFavorite: false,
});

const iconsPath = "./src/components/HotelCard/assets/icons";
const favoriteHotelIcon = `${iconsPath}/filled-heart.svg`;
const noFavoriteHotelIcon = `${iconsPath}/heart.svg`;

const calcSavedValue = () => {
  return props.originalPrice - props.discountPrice;
};

const getImgUrl = (imageUri) => {
  return "./src/components/HotelCard/assets/img/" + imageUri;
};

const setAsFavorite = () => {
  state.isFavorite = !state.isFavorite;
};
</script>

<template>
  <div
    :style="{ width: `${width}px`, height: `${height}px` }"
    class="hotel-card"
  >
    <div class="hotel-card__image-container">
      <div class="hotel-card__info-wrapper" @click="setAsFavorite">
        <img
          v-if="state.isFavorite"
          :src="favoriteHotelIcon"
          alt="Favorite icon"
        />
        <img v-else :src="noFavoriteHotelIcon" alt="Favorite icon" />
      </div>
      <img
        :src="getImgUrl(imageUri)"
        alt="hotel image"
        class="hotel-card__image"
      />
    </div>
    <div class="hotel-card__body-container">
      <div class="hotel-card__title-wrapper">
        <div class="hotel-card__title-wrapper--title">{{ title }}</div>
        <div class="hotel-card__title-wrapper__icons-container">
          <div v-if="swimIcon" class="icon-default">
            <img src="./assets/icons/swim.svg" alt="Swim indicator" />
          </div>
          <div v-if="wifiIcon" class="icon-default">
            <img src="./assets/icons/wifi.svg" alt="Wifi indicator" />
          </div>
          <div v-if="foodIcon" class="icon-default">
            <img src="./assets/icons/food.svg" alt="Food indicator" />
          </div>
        </div>
      </div>
      <div class="hotel-card__infos-wrapper">
        <div class="hotel-card__left-infos-wrapper">
          <div class="flex-row">
            <img
              v-for="(star, index) in 5"
              :key="index"
              :src="`${
                index < stars
                  ? './src/components/HotelCard/assets/icons/filled-star.svg'
                  : './src/components/HotelCard/assets/icons/star.svg'
              }`"
              alt="Stars indicator"
            />
            <div class="hotel-card__left-infos-wrapper--ranking">
              {{ ranking }}
            </div>
          </div>
          <div class="flex-row mt-20">
            <div class="hotel-card--label">{{ stayDate }}</div>
            <div class="hotel-card--label">{{ availableRooms }}</div>
          </div>
        </div>
        <div class="hotel-card__right-infos-wrapper">
          <div class="hotel-card__right-infos-wrapper--discount-price">
            ${{ discountPrice }}<span class="fs-18">/night</span>
          </div>
          <div class="hotel-card__right-infos-wrapper--original-price">
            <span class="line-through">${{ originalPrice }}</span>
            <span class="fs-14">/night</span>
          </div>
        </div>
      </div>
      <div class="hotel-card__description-wrapper body-text">
        {{ description }}
      </div>
      <div class="hotel-card__booking-wrapper">
        <div class="hotel-card__booking-wrapper--saving-text">
          You're saving <strong>${{ calcSavedValue() }}</strong>
        </div>
        <button class="hotel-card__booking-wrapper--booking-button">
          select rooms
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@use "../../globals/_globals.scss";
.hotel-card {
  margin: 20px;
  background-color: #ffffff;
  border-radius: 16px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  display: flex;
  flex-direction: column;
  min-width: 320px;

  &--label {
    display: flex;
    min-height: 32px;
    text-transform: uppercase;
    color: #007ae9;
    font-family: globals.$openSansFont;
    font-weight: 700;
    font-size: 0.625rem;
    text-align: center;
    letter-spacing: 0.2em;
    font-style: normal;
    border: 1px solid #d7d8d9;
    border-radius: 4px;
    align-items: center;
    padding: 0px 10px;
    margin-right: 10px;
  }

  &__image-container {
    max-height: 260px;
    position: relative;
    overflow: hidden;
  }

  &__info-wrapper {
    position: absolute;
    top: 15px;
    right: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }

  &__info-wrapper img {
    width: 32px;
    height: 32px;
  }

  &__image {
    width: 100%;
    height: 260px;
  }

  &__body-container {
    padding: 20px;
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  &__title-wrapper {
    font-family: globals.$dmSerifDisplay;
    font-size: 1.5rem;
    font-weight: 400px;
    line-height: 25px;
    display: flex;
    flex-direction: row;

    &--title {
      flex-grow: 1;
      color: #081f32;
    }

    &__icons-container {
      display: flex;
    }
  }

  &__infos-wrapper {
    display: flex;
    align-items: end;
    margin-top: 13px;

    img {
      margin-right: 7px;
      width: 16px;
      height: 16px;
    }
  }

  &__left-infos-wrapper {
    display: flex;
    flex-grow: 1;
    flex-direction: column;
    justify-content: center;

    &--ranking {
      text-transform: uppercase;
      color: #ffffff;
      border-radius: 4px;
      font-size: 0.625rem;
      font-family: globals.$openSansFont;
      background-color: #007ae9;
      padding: 0px 14px;
      margin-left: 10px;
      font-weight: 700;
      line-height: 22px;
      text-align: center;
      letter-spacing: 0.2em;
      font-style: normal;
    }
  }

  &__right-infos-wrapper {
    display: flex;
    flex-direction: column;
    font-family: globals.$dmSerifDisplay;

    &--discount-price {
      font-style: normal;
      font-weight: 400;
      font-size: 3rem;
      line-height: 25px;
      text-align: right;
      letter-spacing: 0.02em;
      color: #081f32;
    }

    &--original-price {
      margin-top: 2px;
      color: #b1b4b9;
      font-size: 1.375rem;
      line-height: 25px;
      text-align: right;
      letter-spacing: 0.02em;
    }
  }

  &__description-wrapper {
    color: #6e798c;
    display: flex;
    flex-grow: 1;
    max-height: 170px;
  }

  &__booking-wrapper {
    font-family: globals.$openSansFont;
    margin-top: 20px;

    &--saving-text {
      font-size: 0.875rem;
      font-style: normal;
      font-weight: 400;
      line-height: 25px;
      text-align: center;
      letter-spacing: 0.02em;
      color: #2ecc71;
    }

    &--booking-button {
      margin-top: 10px;
      width: 100%;
      text-align: center;
      border-radius: 8px;
      border: none;
      height: 80px;
      background-color: #2ecc71;
      font-weight: 700;
      font-size: 17px;
      line-height: 25px;
      text-align: center;
      letter-spacing: 0.2em;
      color: #ffffff;
      text-transform: uppercase;
      cursor: pointer;
    }
  }
}

.icon-default {
  width: 24px;
  height: 24px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0px 5px 0px 5px;
  background-color: #007ae9;
}

.flex-row {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.mt-20 {
  margin-top: 20px;
}

.fs-18 {
  font-size: 18px;
}

.fs-14 {
  font-size: 14px;
}

.line-through {
  text-decoration: line-through;
}

.body-text {
  font-size: 1rem;
  font-family: globals.$openSansFont;
  line-height: 25px;
  margin-top: 25px;
}
</style>
