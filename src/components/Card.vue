<template>
  <div class="card">
    <div class="card__content">
      <div class="card__content-pageview">
        <h5>
          <p>{{ range }} K</p>
          Pageview
        </h5>
      </div>

      <div class="card__content-range">
        <div class="range-slider">
          <input
            v-model="range"
            class="range-slider__range"
            type="range"
            min="1"
            max="5"
            value="3"
          />
        </div>
      </div>

      <div class="card__content-price">
        <p class="input-price">$ {{ printPrice }} /month</p>
        <p>{{ discount }}</p>
      </div>
    </div>

    <div class="card__content-options">
      <p>Monthly Billing</p>
      <div class="card__content-options-checkbox">
        <div class="toggle toggle--daynight">
          <input
            v-model="discount"
            type="checkbox"
            id="toggle--daynight"
            class="toggle--checkbox"
          />
          <label class="toggle--btn" for="toggle--daynight">
            <span class="toggle--feature"></span>
          </label>
        </div>
      </div>
      <p>Yearly Billing</p>
      <p class="btn btn--discount">25%<span> discount</span></p>
    </div>

    <div class="card__footer">
      <div class="card__footer-list">
        <ul>
          <li v-for="cardListItem in cardListItems" :key="cardListItem.listId">
            <p>{{ cardListItem.message }}</p>
          </li>
        </ul>
      </div>

      <div class="card__footer-button">
        <button class="btn">Start my trial</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    return {
      page: 10,
      range: 2,
      price: 12,
      discount: false,
      cardListItems: [
        { listId: 1, message: "Unlimited websites" },
        { listId: 2, message: "100% data ownership" },
        { listId: 3, message: "Email reports" },
      ],
    };
  },
  methods: {
    getDiscount() {
      this.price = this.discount ? this.price - this.price * 0.25 : this.price;
    },
  },

  mounted() {
    this.getDiscount();
  },

  watch: {
    discount: function () {
      this.getDiscount;
    },
  },

  computed: {
    printPrice() {
      return this.price;
    },

    getRange() {
      return this.range;
    },
  },
};
</script>

<style lang="scss">
@import "../assets/sass/_base.scss";
@import "../assets/sass/_button.scss";

// Card
.card {
  max-width: 545px;
  margin: 0 auto;
  background: $white;
  color: $grayish-blue;
  padding: 0 16px;
  border-radius: 6px;
  box-shadow: 0px 4px 8px 1px rgba(41, 51, 86, 0.19);
  -webkit-box-shadow: 0px 4px 8px 1px rgba(41, 51, 86, 0.19);
  -moz-box-shadow: 0px 4px 8px 1px rgba(41, 51, 86, 0.19);
}

.card__content {
  text-align: center;
}

.card__footer {
  text-align: center;
  padding: 40px 0;
}

.card__content-pageview {
  padding-top: 40px;
}

.card__content-range {
  padding-top: 40px;
}

// Range Slider
$range-width: 100% !default;

$range-handle-color: #8de4db !default;
$range-handle-color-focus: $strong-cyan !default;
$range-handle-size: 40px !default;

$range-track-color: $light-grayish-blue !default;
$range-track-height: 10px !default;

range-slider {
  width: $range-width;
}

.range-slider__range {
  -webkit-appearance: none;
  width: $range-width;
  height: $range-track-height;
  border-radius: 5px;
  background: $range-track-color;
  outline: none;
  padding: 0;
  margin: 0;

  .slider-25 {
    background-image: linear-gradient(
      to right,
      #10d5c2 0%,
      #10d5c2 24%,
      #cdd7ee 25%,
      #cdd7ee 100%
    );
  }

  // Range Handle
  &::-webkit-slider-thumb {
    appearance: none;
    width: $range-handle-size;
    height: $range-handle-size;
    border-radius: 50%;
    background-color: $range-handle-color;
    background-image: url("/home/pi/Documents/sites/interactive-pricing-component-app/src/assets/images/icon-slider.svg ");
    box-shadow: 0px 7px 20px rgba(0, 255, 231, 0.6);
    cursor: pointer;
    transition: background 0.15s ease-in-out;

    &:focus {
      background: $range-handle-color-focus;
    }
  }

  &:active::-webkit-slider-thumb {
    background-color: $range-handle-color-focus;
  }

  &::-moz-range-thumb {
    width: $range-handle-size;
    height: $range-handle-size;
    border: 0;
    border-radius: 50%;
    box-shadow: 0px 7px 20px rgba(0, 255, 231, 0.6);
    background-color: $range-handle-color;
    background-image: url("/home/pi/Documents/sites/interactive-pricing-component-app/src/assets/images/icon-slider.svg ");
    background-repeat: no-repeat;
    background-position: center;
    cursor: pointer;
    transition: background-color 0.15s ease-in-out;

    &:focus {
      background-color: $range-handle-color-focus;
    }
  }

  &:active::-moz-range-thumb {
    background-color: $range-handle-color-focus;
  }
}

.card__content-price {
  padding-top: 40px;
}

.card__content-options {
  padding: 50px 0;
  display: flex;
  justify-content: space-around;

  p {
    display: inline;
  }

  span {
    display: none;
  }
}

.card__footer-list {
  padding-bottom: 60px;

  ul {
    list-style-image: url("/assets/images/icon-check.svg");
  }

  li {
    padding-bottom: 15px;
  }

  p {
    display: inline;
    padding-left: 15px;
  }
}

/* Medium devices (tablets, 768px and up) */
@media (min-width: 992px) {
  .card__content {
    height: 170px;
    position: relative;
  }

  .card__content-pageview {
    position: absolute;
    top: 50px;
    left: 50px;
    padding-top: 0;
  }

  .card__content-range {
    position: absolute;
    top: 110px;
    width: 100%;
  }

  .card__content-price {
    position: absolute;
    top: 50px;
    right: 50px;
    padding-top: 0;
  }

  .card__content-options {
    padding: 50px 32px;
    display: flex;
    justify-content: flex-end;

    p {
      padding: 0 16px;

      span {
        display: inline;
      }
    }
  }

  .card__footer {
    display: flex;
    justify-content: space-around;
    border-top: 1px solid $light-grayish-blue;
  }

  .card__footer-list {
    text-align: left;
    padding-bottom: 0 !important;
  }

  .card__footer-button {
    padding-top: 20px;
  }
}
</style>