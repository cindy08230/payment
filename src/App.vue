<template lang="pug">
  .payment
    router-view
    .payment__header
      p 12:22
      i.fas.fa-battery-full
    .payment__wrap
      .payment__wrap__bg
      .payment__wrap__top
        .payment__wrap__top__navi
          i.fas.fa-chevron-left
          h4.title 結帳
        .payment__wrap__top__step
          .step(:class="{ 'active' : !$route.params.type}") 1
          .line
          .step(:class="{ 'active' : $route.params.type === 'credit-card'}") 2
          .line
          .step(:class="{ 'active' : $route.params.type === 'comfirm-order'}") 3
          .line
          .step(:class="{ 'active' : $route.params.type === 'success'}")
            i.fas.fa-check
        h4.payment__wrap__top__text Step1 - 請選擇付款方式
      HomePage.payment__wrap__page(
        v-if="!$route.params.type"
        :payment-way="paymentWay"
      )
      InputInfo.payment__wrap__page(
        v-if="$route.params.type === 'credit-card'"
      )
      Confirm.payment__wrap__page(
        v-if="$route.params.type === 'comfirm-order'"
      )
      Success.payment__wrap__page(
        v-if="$route.params.type === 'success'"
      )
</template>


<script>
import HomePage from './components/HomePage'
import InputInfo from './components/InputInfo'
import Confirm from './components/Confirm'
import Success from './components/Success'
export default {
  name: 'App',
  components: {
    HomePage,
    InputInfo,
    Confirm,
    Success
  },
  data() {
    return {
      paymentWay:[
        {
          handle: "credit-card",
          title: "信用卡",
          subtitle: "(可接受VISA,Master,JCB)",
          image: require("../src/assets/credit_card.svg")
        },
        {
          handle: "super",
          title: "超商付款",
          subtitle: "(7-11,全家)",
          image: require("../src/assets/super.svg")
        },
        {
          handle: "pay-pal",
          title: "PayPal",
          subtitle: "(線上支付)",
          image: require("../src/assets/paypal.svg")
        },
        {
          handle: "ali-pay",
          title: "支付寶",
          subtitle: "(線上支付)",
          image: require("../src/assets/paypal.svg")
        },
        {
          handle: "atm-transfer",
          title: "ATM 轉帳",
          subtitle: "(台灣地區銀行發行之銀行金融卡)",
          image: require("../src/assets/atm-trans.svg")
        }
      ]
    }
  },
  methods: {}
}
</script>

<style lang="sass" scoped>
$width: calc(100vw - 20px)
$height: calc(100vh - 40px)

.payment
  width: 100vw
  height: 100vh
  &__header
    display: flex
    justify-content: space-between
    padding: 10px
    font-size: 15px
    position: fixed
    top: 0
    left: 50%
    transform: translateX(-50%)
    width: $width
    background-color: transparent
    z-index: 999999
    color: #fff
    .fas
      display: flex
      align-items: center

  &__wrap
    position: relative
    max-width: 414px
    width: $width
    height: $height
    margin: 0 auto
    overflow-x: hidden
    overflow-y: scroll
    padding: 40px 10px 0 10px

    &__bg
      position: absolute
      top: -180px
      left: -25%
      width: 150%
      height: 400px
      border-radius: 50%
      background: linear-gradient(to bottom,  #3a26af 0%,#8244bb 100%)
      z-index: -1
    
    &__top
      padding-top: 10px
      color: #fff

      &__navi
        display: flex
        justify-content: space-between
        align-items: center

        .title
          width: 100%
          text-align: center

      &__step
        display: flex
        justify-content: center
        align-items: center
        margin-top: 25px
        
        .step
          width: 30px
          height: 30px
          display: flex
          justify-content: center
          align-items: center
          border: 1px solid #fff
          border-radius: 50%
          font-weight: bold

        .active
          color: #8344bb
          background: #fff

        .line
          width: 40px
          height: 3px
          margin: 0 8px
          background-color: #fff

      &__text
        text-align: center
        margin-top: 25px

    &__page
      padding: 60px 30px 0
</style>
