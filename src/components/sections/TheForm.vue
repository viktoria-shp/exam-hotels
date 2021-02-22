<template>
  <div class="form-container container" id="app">
    <div class="add-product" :class="{'open': formOpen}">
        <div class="button-copy" v-show="!formOpen" @click="formOpen = true">find hotel</div>
        <form @submit="cancel()">
        <div class="form__field">
            <input type="text" class="form__element" name="title" v-model="productData.title" placeholder="Enter hotel name *" required="">
        </div>
        <div class="form__container form__container--inline">
            <div class="form__field form__field--short">
                <input type="number" class="form--element" name="rating" v-model="productData.rating" placeholder="Adults" required="" min="0" max="5" step="1">
            </div>
            <div class="form__field form__field--short">
                <input type="number" class="form--element" name="rating" v-model="productData.rating" placeholder="Children" required="" min="0" max="5" step="1">
            </div>
            <div class="form__field form__field--short">
                <datepicker monday-first="true" v-model="from" :disabled-dates="disabledDatesFrom" @selected="updateDDT"></datepicker>
            </div>
            <div class="form__field form__field--short">
                <datepicker monday-first="true" v-model="to" :disabled-dates="disabledDatesTo" @selected="updateDDF"></datepicker>
            </div>
            <div class="form__field form__field--short">
                <button type="submit" class="submit-button">Add Product</button>
            </div>
        </div>
        <div class="form__cancel" @click="cancel()">
            <img class="form__cancel-img" :src=iconSrc alt="">
        </div>
        </form>
    </div>
    </div>
</template>

<script>
import Datepicker from 'vuejs-datepicker';
export default {
    components: {
        Datepicker
    },
  data() {
    return {
        iconSrc: require("@/assets/close.svg"),
        formOpen: false,
        productData: {
        title: '',
        rating: '',
        price: '',
        list_price: '',
        is_featured: false
        },
        from: new Date(),
        to: new Date(),
        disabledDatesFrom: {
            to: new Date(),
            from: null
        },
        disabledDatesTo: {
            to: new Date(),
        }
    }},
  methods: {
    resetForm: function () {
      this.productData = {
        title: '',
        rating: '',
        price: '',
        list_price: '',
        is_featured: false
      }
    },
    cancel: function() {
      this.formOpen = false;
      this.resetForm();
    },
    updateDDT(selected) {
      this.disabledDatesTo.to = selected;
      if (this.to < this.disabledDatesTo.to) {
        this.to = this.disabledDatesTo.to;
      }
    },
    updateDDF(selected) {
      this.disabledDatesFrom.from = selected;
      if (this.from < this.disabledDatesTo.from) {
        this.from = this.disabledDatesTo.from;
      }
    }
  }
};
</script>

<style lang="scss">
    .form-container {
        display: flex;
        max-width: 100%;
        justify-content: center;
        align-items: center;
        position: absolute;
        bottom: -15%;
    }
    .add-product {
        &.open {  
            border-radius: 5px;
            position: absolute;
            top: 0;
            cursor: default;
            form {
                opacity: 1;
                transition: opacity 0.1s ease;
                transition-delay: 0.3s;
                min-height: 300px;
                width: max-content;
            }
        }
    transition: all 0.3s ease;
    box-shadow: 0 4px 16px 0 rgba(0, 0, 0, .07);
    cursor: pointer;
    .button-copy {
        text-align: center;
        line-height: 90px;
        text-transform: uppercase;
        font-weight: bold;
        color: $white;
        background: $main_color;
    }
    form {
        transition: none;
        opacity: 0;
        height: 0;
        overflow: hidden;
    }
    .form__cancel {
        text-align: center;
        margin-top: 1em; 
        span {
            cursor: pointer;
        &:hover {
            text-decoration: underline;
        }
        }
        &-img {
            top: -11%;
            position: absolute;
            max-width: 25px;
        }
    }
    }
    .submit-button {
        display: block;
        background-color: $main_color;
        width: 100%;
        height: 100%;
        color: #fff;
        text-transform: uppercase;
        font-size: 0.875em;
        border: none;
        font-weight: 700;
    &:hover {
        background-color: darken($main_color, 10%);
        cursor: pointer;
    }
    }

    .featured-note {
        color: #949494;
        font-size: 12px;
        margin: 4px 0px;
        line-height: 18px;
        font-style: italic;
    }

    form * {
        outline: none;
    }

    label {
    display: block;
    font-size: 14px;
    font-weight: bold;
    user-select: none;
    }

    .form__field {
        width: 100%;
            &--short {
                width: 20%;
                border: 2px solid #cb8670;
                &:focus {
                    border: 2px solid $white;
                }
            }
    }

    .form__container {
        &--inline {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            margin-bottom: -12px;
        }
        .vdp-datepicker__calendar {
            position: absolute;
            z-index: 100;
            background: $main_color;
            bottom: -50%;
        }
        .vdp-datepicker__calendar .cell.selected {
            background: #383737;
        }
    }

    .form__element {
        background-color: $main_bg;
        border: 2px solid $main_color;
        border-radius: 3px;
        font-size: 14px;
        line-height: 28px;
        padding: 0 4px;
        width: 100%;
        margin: 4px 0;
        box-sizing: border-box;
    &:focus {
        border: 2px solid $white;
        border-radius: 2px;
    }
    &:not(.texteare) {
        height: 100px;
    }
    &.textarea {
        height: 80px;
        resize: none;
    }
    }


    html,
    body {
    height: 100%;
    margin: 0;
    }

    body {
    font-family: 'Open Sans', sans-serif;
    font-size: 16px;
    background-color: #F3F4F5;
    cursor: default;
    }

    a {
    text-decoration: none;
    cursor: pointer;
    }

    ::selection {
    background-color: #F5617A;
    color: #fff;
    }

    ::-moz-selection {
    background-color: #F5617A;
    color: #fff;
    }
    input:not([type='range']), label, select, summary, textarea,
    input::placeholder {
        touch-action: manipulation;
        width: 100%;
        height: 100%;
        padding: 50px;
        background: rgba(54, 54, 54, 0.5);
        color: #cb8670;
        border: none;
        &:hover {
            border: 2px solid $white;
        }
    }
</style>
