<template>
  <div class="card">
    <div class="card-inner" :class="{ isComplated: isComplate }">
      <div class="card-front">
        <div class="card-item pa-15 tw">
          <div class="d-flex justify-content-space-between">
            <span>DEBIT CARD</span>
            <span>BANK NAME</span>
          </div>
        </div>
        <div class="card-item pa-15">
          <div class="chip"></div>
        </div>
        <div class="card-item pa-15 tw">
          <div class="item-description">card number</div>
          <div class="item-card-number">
            <input
              @focus="handleFocus"
              @blur="handleBlur"
              v-model="form.cardNumber"
              type="text"
              class="item-card-number"
              placeholder="1234 5678 9012 3456"
            />
          </div>
        </div>
        <div class="card-item pa-15 d-flex justify-content-space-between tw">
          <div class="card-holder">
            <div class="item-description">cardholder name</div>
            <div class="item-card-holder">
              <input
                @focus="handleFocus"
                @blur="handleBlur"
                v-model="form.cardHolder"
                type="text"
                class="item-card-holder"
                placeholder="ATAKAN COSKUNDERE"
              />
            </div>
          </div>
          <div class="card-expiration">
            <div class="item-description">expiration date</div>
            <div class="item-card-expiration">
              <input
                @focus="handleFocus"
                @blur="handleBlur"
                v-model="form.expiryDay"
                type="text"
                class="item-card-expiration-input"
                placeholder="01"
              />
              <span class="tw date-divider"> / </span>
              <input
                @focus="handleFocus"
                @blur="handleBlur"
                v-model="form.expiryMonth"
                type="text"
                class="item-card-expiration-input"
                placeholder="21"
              />
            </div>
          </div>
        </div>
      </div>
      <div class="card-back tw">
        <div class="card-item strip"></div>
        <div class="card-item pa-15">
          <div class="card-item-cvc">
            <span class="pa-15">
              {{ form.cardHolder }}
            </span>

            <input
              v-model="form.cvc"
              type="text"
              class="item-card-cvc-input"
              placeholder="212"
            />
          </div>
          <div class="item-description text-right">security number</div>
        </div>
        <div class="card-item pa-15">
          <div
            style="background-color:white; height:10px; border-radius:3px; width:250px; margin:5px 0px"
          ></div>
          <div
            style="background-color:white; height:10px; border-radius:3px; width:200px; margin:5px 0px"
          ></div>
        </div>
        <div class="card-item pa-15">
          <button @click="isComplate = false">back</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isComplate: false,
      isAnyFocused: false,
      form: {
        cardNumber: "",
        expiryDay: "",
        expiryMonth: "",
        cardHolder: "",
        cvc: "",
      },
    };
  },
  watch: {
    isAnyFocused(val) {
      if (
        this.form.cardNumber.length == 16 &&
        this.form.expiryDay != "" &&
        this.form.expiryMonth != "" &&
        this.form.cardHolder != "" &&
        val == false
      ) {
        this.isComplate = true;
      }
    },
  },
  methods: {
    goFront() {
      this.isComplate = false;
    },
    handleBlur() {
      this.isAnyFocused = false;
      if (this.form.cardNumber.length != 16)
        alert("Card number must be 16 character");
    },
    handleFocus() {
      this.isAnyFocused = true;
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.justify-content-center {
  justify-content: center !important;
}
.justify-content-space-between {
  justify-content: space-between;
}
.text-center {
  text-align: center;
}
.text-right {
  text-align: right !important;
}
.w-100 {
  width: 100% !important;
}
.w-75 {
  width: 75% !important;
}
.h-100 {
  height: 100% !important;
}
.d-flex {
  display: flex;
}
.pa-15 {
  padding: 0px 15px !important;
}
.tw {
  color: white;
}
.strip {
  background-color: #b1b1b1;
  height: 40px;
  margin: 20px 0px;
}
input[type="text"] {
  width: 100%;
  border: none;
  background-color: transparent;
  border-radius: 5px;
  color: white;
}
input[type="text"]:focus {
  outline: none;
}
.isComplated {
  transform: rotateY(180deg);
}
.card {
  max-height: 250px;
  height: 55vw;
}
.card-inner {
  position: relative;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  background: rgb(31, 31, 31);

  box-shadow: 0 4px 8px 0 rgb(0 0 0 / 20%);
  background: linear-gradient(
    225deg,
    rgba(31, 31, 31, 1) 50%,
    rgba(0, 0, 0, 1) 50%
  );
  height: 100%;
  width: 100%;
  max-width: 400px;
  border-radius: 5px;
}
.isComplated {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  background-color: transparent;
  height: 100%;
  width: 100%;
}
.card-front {
  background-color: transparent;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}
.card-back {
  transform: rotateY(180deg);
}

.chip {
  width: 60px;
  height: 50px;
  background-color: grey;
  border-radius: 3px;
}
.item-description {
  font-size: 12px;
  color: grey;
  font-weight: bold;
}
.item-card-number {
  font-size: 30px;
}
.item-card-holder,
.item-card-expiration-input {
  font-weight: 600;
  font-size: 16px;
  padding: 5px 0px;
}
.item-card-expiration-input {
  width: 25px !important;
}
.item-card-expiration {
  padding: 5px 0px;
}
.item-card-cvc-input {
  width: 80px !important;
  font-weight: 600;
  font-size: 16px;
  padding: 5px 0px;
  background-color: #f0f0f0 !important;
  padding: 10px;
  text-align: center;
  color: black !important;
}
.date-divider {
  font-size: 20px;
  font-weight: 600;
  margin: 0px 5px;
}
.card-item {
  width: 100%;
}
.card-item-cvc {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #b1b1b1;
  border-radius: 3px;
}
</style>
