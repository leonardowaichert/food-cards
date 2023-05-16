<script setup>
defineProps({
  imageUri: String,
  width: Number,
  height: Number,
  shadow: Boolean,
  title: String,
  description: String,
  calories: Number,
  pfc: Number,
  temperature: Number,
  priceWithDiscount: Number,
  originalPrice: Number,
  fireIcon: Boolean,
  leafIcon: Boolean,
  wheatIcon: Boolean,
});

const getImgUrl = (imageUri) => {
  return "./src/components/FoodCard/assets/img/" + imageUri;
};
</script>

<template>
  <div :style="{ width: `${width}px`, height: `${height}px` }" class="card">
    <div class="card__image-container">
      <div class="card__info-wrapper">
        <img src="./assets/icons/info.svg" alt="Information icon" />
      </div>
      <img :src="getImgUrl(imageUri)" alt="Food image" class="card__image" />
    </div>
    <div class="card__body-container">
      <div class="card__title-wrapper">
        <div class="card__title-wrapper--title">{{ title }}</div>
        <div class="card__title-wrapper__icons-container">
          <div
            v-if="leafIcon"
            class="card__title-wrapper__icons-container--leaf icon-default"
          >
            <img src="./assets/icons/leaf.svg" alt="Leaf indicator" />
          </div>
          <div
            v-if="fireIcon"
            class="card__title-wrapper__icons-container--fire icon-default"
          >
            <img src="./assets/icons/fire.svg" alt="Fire indicator" />
          </div>
          <div
            v-if="wheatIcon"
            class="card__title-wrapper__icons-container--wheat icon-default"
          >
            <img src="./assets/icons/wheat.svg" alt="Wheat indicator" />
          </div>
        </div>
      </div>
      <div class="card__description-wrapper body-text">
        <span>{{ description }}</span>
      </div>
      <div class="card__infos-wrapper body-text">
        <span>{{ calories }} Cal</span>
        <span>P/F/C: {{ pfc }}</span>
        <span>{{ temperature }} ºC</span>
      </div>
      <div class="card__purchase-wrapper">
        <div>
          <span class="card__purchase-wrapper--discount-price"
            >${{ parseFloat(priceWithDiscount).toFixed(2) }}</span
          >
          <span class="card__purchase-wrapper--original-price"
            >${{ parseFloat(originalPrice).toFixed(2) }}</span
          >
        </div>
        <button class="card__purchase-wrapper--button">ORDER</button>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.card {
  margin: 20px;
  background-color: #ffffff;
  border-radius: 16px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;

  &__image-container {
    max-height: 215px;
    position: relative;
  }

  &__info-wrapper {
    position: absolute;
    background-color: #ffffff;
    border-radius: 50%;
    height: 32px;
    width: 32px;
    top: 15px;
    right: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }

  &__image {
    width: 100%;
  }

  &__body-container {
    padding: 20px;
  }

  &__title-wrapper {
    font-family: "DM Serif Display", serif;
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

      &--fire {
        background-color: #f8593b;
      }

      &--wheat {
        background-color: #ffc22b;
      }

      &--leaf {
        background-color: #2ecc71;
      }
    }
  }

  &__description-wrapper {
    color: #6e798c;
  }

  &__infos-wrapper {
    color: #a5adbb;
    display: flex;
    justify-content: space-between;
  }

  &__purchase-wrapper {
    margin-top: 40px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    font-family: "DM Serif Display", serif;
    font-weight: 400;

    &--discount-price {
      font-size: 1.75rem;
      line-height: 25px;
      margin-right: 10px;
      color: #081f32;
    }

    &--original-price {
      font-size: 1.25rem;
      line-height: 25px;
      color: #f8593b;
      text-decoration: line-through;
    }

    &--button {
      border: none;
      width: 115px;
      height: 45px;
      border-radius: 4px;
      background-color: #2ecc71;
      color: #ffffff;
      font-family: "Open Sans", sans-serif;
      font-size: 0.875rem;
      line-height: 25px;
      text-align: center;
      font-weight: 600;
      letter-spacing: 0.18em;
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
}

.body-text {
  font-size: 1rem;
  font-family: "Open Sans", sans-serif;
  line-height: 25px;
  margin-top: 25px;
}
</style>
