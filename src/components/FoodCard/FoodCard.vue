<script setup>
import { reactive } from "vue";

defineProps({
  imageUri: {
    type: String,
    default: "../../../../assets/no-image-available.png",
  },
  width: {
    type: Number,
    default: 360,
  },
  height: {
    type: Number,
    default: 530,
  },
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  calories: {
    type: Number,
    required: true,
  },
  pfc: {
    type: Number,
    required: true,
  },
  temperature: {
    type: Number,
    required: true,
  },
  priceWithDiscount: {
    type: Number,
    required: true,
  },
  originalPrice: {
    type: Number,
    required: true,
  },
  fireIcon: {
    type: Boolean,
    default: false,
  },
  leafIcon: {
    type: Boolean,
    default: false,
  },
  wheatIcon: {
    type: Boolean,
    default: false,
  },
});

const state = reactive({
  orderFood: false,
});

const getImgUrl = (imageUri) => {
  return "./src/components/FoodCard/assets/img/" + imageUri;
};

const orderFood = () => {
  state.orderFood = true;
};

const closeOrderFood = () => {
  state.orderFood = false;
};
</script>

<template>
  <div
    :style="{ width: `${width}px`, height: `${height}px` }"
    class="food-card"
  >
    <div v-show="!state.orderFood" class="display-flex-column">
      <div class="food-card__image-container">
        <div class="food-card__info-wrapper" title="Food infos">
          <img src="./assets/icons/info.svg" alt="Information icon" />
        </div>
        <img
          :src="getImgUrl(imageUri)"
          alt="Food image"
          class="food-card__image"
        />
      </div>
      <div class="food-card__body-container">
        <div class="food-card__title-wrapper">
          <div class="food-card__title-wrapper--title">{{ title }}</div>
          <div class="food-card__title-wrapper__icons-container">
            <div
              v-if="leafIcon"
              class="food-card__title-wrapper__icons-container--leaf icon-default"
              title="Organic"
            >
              <img src="./assets/icons/leaf.svg" alt="Leaf indicator" />
            </div>
            <div
              v-if="fireIcon"
              class="food-card__title-wrapper__icons-container--fire icon-default"
              title="Hot food"
            >
              <img src="./assets/icons/fire.svg" alt="Fire indicator" />
            </div>
            <div
              v-if="wheatIcon"
              class="food-card__title-wrapper__icons-container--wheat icon-default"
              title="Contains gluten"
            >
              <img src="./assets/icons/wheat.svg" alt="Wheat indicator" />
            </div>
          </div>
        </div>
        <div class="food-card__description-wrapper body-text">
          <span>{{ description }}</span>
        </div>
        <div class="food-card__infos-wrapper body-text">
          <span>{{ calories }} Cal</span>
          <span>P/F/C: {{ pfc }}</span>
          <span>{{ temperature }} ºC</span>
        </div>
        <div class="food-card__purchase-wrapper">
          <div>
            <span class="food-card__purchase-wrapper--discount-price"
              >${{ parseFloat(priceWithDiscount).toFixed(2) }}</span
            >
            <span class="food-card__purchase-wrapper--original-price"
              >${{ parseFloat(originalPrice).toFixed(2) }}</span
            >
          </div>
          <button
            class="food-card__purchase-wrapper--button"
            @click="orderFood"
          >
            ORDER
          </button>
        </div>
      </div>
    </div>
    <div v-if="state.orderFood" class="display-flex-column">
      <div class="food-card__order-food-container">
        <div class="food-card__order-food-container--close-icon">
          <img
            src="../../assets/close-icon.svg"
            alt="Close icon"
            @click="closeOrderFood"
          />
        </div>
        <div class="food-card__order-food-container--generic-text">
          <span
            >Any generic information about order food of
            <strong>{{ title }}</strong></span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@use "../../globals/_globals.scss";

.food-card {
  display: flex;
  flex-direction: column;
  background-color: #ffffff;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  margin: 20px;
  border-radius: 16px;
  min-width: 320px;
  max-width: 380px;

  &__image-container {
    position: relative;
    max-height: 215px;
  }

  &__info-wrapper {
    display: flex;
    position: absolute;
    align-items: center;
    justify-content: center;
    background-color: #ffffff;
    border-radius: 50%;
    height: 32px;
    width: 32px;
    top: 15px;
    right: 20px;
    cursor: pointer;
    transition: 0.2s;
  }

  &__info-wrapper:hover {
    transform: scale(1.1);
  }

  &__image {
    height: 100%;
    width: 100%;
  }

  &__body-container {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    padding: 20px;
  }

  &__title-wrapper {
    display: flex;
    flex-direction: row;
    font-family: globals.$dmSerifDisplay;
    font-size: 1.5rem;
    font-weight: 400px;
    line-height: 25px;

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
    display: flex;
    color: #6e798c;
  }

  &__infos-wrapper {
    display: flex;
    justify-content: space-between;
    color: #a5adbb;
  }

  &__purchase-wrapper {
    display: flex;
    flex-grow: 1;
    flex-direction: row;
    align-items: end;
    justify-content: space-between;
    font-family: globals.$dmSerifDisplay;
    font-weight: 400;
    margin-bottom: 20px;

    &--discount-price {
      font-size: 1.75rem;
      line-height: 25px;
      margin-right: 10px;
      color: #081f32;
    }

    &--original-price {
      text-decoration: line-through;
      font-size: 1.25rem;
      line-height: 25px;
      color: #f8593b;
    }

    &--button {
      border: none;
      text-align: center;
      background-color: globals.$buttonBackgroundColor;
      font-family: globals.$openSansFont;
      transition: 0.2s;
      line-height: 25px;
      font-weight: 600;
      letter-spacing: 0.18em;
      font-size: 0.875rem;
      width: 115px;
      height: 45px;
      border-radius: 4px;
      color: #ffffff;
      cursor: pointer;
    }

    &--button:hover {
      background-color: globals.$buttonHoverBackgroundColor;
    }
  }

  &__order-food-container {
    padding: 20px;
    display: flex;
    flex-direction: column;

    &--close-icon {
      text-align: right;
      cursor: pointer;
    }

    &--generic-text {
      display: flex;
      flex-grow: 1;
      font-family: globals.$openSansFont;
      font-size: 1.85rem;
      text-align: center;
      margin-top: 100px;
    }
  }
}

.icon-default {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 10px;
  border-radius: 50%;
  width: 24px;
  height: 24px;
}

.body-text {
  font-family: globals.$openSansFont;
  font-size: 1rem;
  line-height: 25px;
  margin-top: 25px;
}

.display-flex-column {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

@media (max-width: 420px) {
  .food-card {
    &__title-wrapper {
      flex-direction: column;

      &__icons-container {
        margin-top: 10px;
      }
    }

    &__purchase-wrapper {
      flex-direction: column;
      align-items: end;
      justify-content: flex-end;
      flex-grow: 1;
      margin-bottom: 10px;
      margin-bottom: 0;

      &--button {
        margin-top: 7px;
        width: 100%;
      }
    }
  }

  .body-text {
    margin-top: 5px;
  }
}
</style>
