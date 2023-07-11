<template>
  <div>
    <div class="title">
        <div class="section-container">
            <h1 class="main_title">Пополнение счета</h1>
            <div class="subtitle-container">
              <img class="subtitle_img" :src="require('./assets/img/icon/wallet-light.png')" alt="">
              <h2 class="subtitle">Выбирете платежную систему:</h2>
            </div>
        </div>
    </div>
    <div class="pay">
        <div class="pay-container">
            <div class="pay_card_first pay_card"
            :class="{ 'isActive': activeEl===1 }"
            @click="activeEl = 1, showElOne = 1, showElTwo = 0, showElTree = 0"
            >
              <img class="card_first_img" :src="require('./assets/img/pay/mobile-banking.png')" alt="">
              <p class="card_first_text">Перевод по номеру телефона</p>
            </div>
            <div class="pay_card_second pay_card"
            :class="{ 'isActive': activeEl===2 }"
            @click="activeEl = 2, showElOne = 0, showElTwo = 1"
            >
              <img class="card_second_img" :src="require('./assets/img/pay/webmoney.png')" alt="">
            </div>
            <div class="pay_card_third pay_card"
            :class="{ 'isActive': activeEl===3 }"
            @click="activeEl = 3, showElOne = 0, showElTwo = 1">
              <img class="card_third_img" :src="require('./assets/img/pay/qiwi.png')" alt="">
            </div>
        </div>
    </div>
    <div class="payment" :class="{ 'paymentActive': showElTwo===1}">
        <div class="payment-main-container">
            <div class="payment-container">
                <form action="#" v-on:submit.prevent="submit">
                    <div class="text-field">
                        <input class="payment_input"  
                        id="payment" 
                        type="number" 
                        autocomplete="off"
                        v-model="paymentData"
                        required="required">
                        <span class="payment__input_text">Введите сумму:</span></div>
                    <button 
                    class="payment_btn" 
                    type="submit" 
                    id="payment_btn"
                    @click="submitForm">
                    Пополнить
                    </button>
                </form>
            </div>
            <div class="notification-container">
                <div class="circle">
                    <div class="point">!</div>
                </div>
                <p class="text_notification">Сумма перевода не <br> должна превышать <br> 100 000₽</p>
            </div>
        </div>
	  </div> 
    <div class="ticket" :class="{ 'ticketActive': showElOne===1 }">
        <div class="ticket-container">
            <div class="ticket-flex-container">
                <img class="ticket_img" :src="require('./assets/img/icon/receipt.png')" alt="">
                <p class="ticket_text">Загрузите квитанцию об оплате</p>
            </div>
            <div class="input__wrapper">
                <input name="file" type="file" id="input__file" class="input input__file">
                <label for="input__file" class="input__file-button">
                   <span class="input__file-button-text">Прикрепить файл</span>
                </label>
             </div>
        </div>
        <div class="notification-container-2">
            <div class="circle">
                <div class="point">!</div>
            </div>
            <p class="text_notification">Сумма перевода не <br> должна превышать <br> 100 000₽</p>
        </div>
    </div>
  </div>
</template>


<script>
import { useVuelidate } from '@vuelidate/core'
import { required } from '@vuelidate/validators'

export default {
  setup () {
    return { v$: useVuelidate() }
  },
  data () {
    return {
      paymentData: '',
      activeEl: 0,
      showElOne: 0,
      showElTwo: 0,
    }
  },
  
  validations () {
    return {
      paymentData: { required },
    }
  },

  methods: {
    submitForm() {
      console.log(this.v$);
    },
    /*testActive () {
      if (isActive = true) {
        isActive2 = true;
        isActive3 = false
      }
    }
    */
  },

}
</script>


<style lang="css">
  @import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&display=swap");
  html, body, div, span, applet, object, iframe,
  h1, h2, h3, h4, h5, h6, p, blockquote, pre,
  a, abbr, acronym, address, big, cite, code,
  del, dfn, em, img, ins, kbd, q, s, samp,
  small, strike, strong, sub, sup, tt, var,
  b, u, i, center,
  dl, dt, dd, ol, ul, li,
  fieldset, form, label, legend,
  table, caption, tbody, tfoot, thead, tr, th, td,
  article, aside, canvas, details, embed,
  figure, figcaption, footer, header, hgroup,
  menu, nav, output, ruby, section, summary,
  time, mark, audio, video {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
  }

  article, aside, details, figcaption, figure,
  footer, header, hgroup, menu, nav, section {
    display: block;
  }

  html {
    height: 100%;
  }

  body {
    line-height: 1;
  }

  ol, ul {
    list-style: none;
  }

  blockquote, q {
    quotes: none;
  }

  blockquote:before, blockquote:after,
  q:before, q:after {
    content: "";
    content: none;
  }

  table {
    border-collapse: collapse;
    border-spacing: 0;
  }

  body {
    background-color: #ffffff;
  }

  body {
    font-family: Montserrat;
    font-style: normal;
    background-color: #F0FAFE;
    padding: 0 15px;
  }

  .section-container {
    max-width: 840px;
    margin: 0 auto;
    margin-top: clamp(3.75rem, 2.134rem + 6.9vw, 5.625rem);
    padding: 0 20px;
  }

  .main_title {
    color: #0F2D97;
    font-size: clamp(2.25rem, 1.172rem + 4.6vw, 3.5rem);
    font-weight: 700;
    margin-bottom: clamp(2.5rem, 1.422rem + 4.6vw, 3.75rem);
  }

  .subtitle-container {
    display: flex;
    gap: clamp(0.875rem, 0.336rem + 2.3vw, 1.5rem);
    align-items: center;
  }

  .subtitle_img {
    -o-object-fit: contain;
      object-fit: contain;
  }

  .subtitle {
    color: #0F2D97;
    font-size: clamp(1.5rem, 0.853rem + 2.76vw, 2.25rem);
    font-weight: 600;
  }

  .pay {
    margin-top: clamp(2.5rem, 1.548rem + 4.76vw, 3.75rem);
  }

  .pay-container {
    max-width: 740px;
    margin: 0 auto;
    display: flex;
    gap: clamp(2.5rem, 1.071rem + 7.14vw, 4.375rem);
    padding: 0 10px;
  }

  @media (max-width: 768px) {
    .pay-container {
      flex-wrap: wrap;
      align-items: center;
      justify-content: center;
    }
  }
  .pay_card {
    border-radius: 8px;
    border: 2px solid #0F2D97;
    width: 200px;
    padding: 2px 10px;
    height: 90px;
    transition: all 0.8s;
    cursor: pointer;
  }

  .pay_card:hover {
   background-color: rgba(0, 133, 255, 0.15);
  }

  .isActive {
    /*background-color: rgba(0, 133, 255, 0.15);*/
    box-shadow: 0px 0px 4px 2px rgba(15, 45, 151, 0.50) inset, 0px 0px 4px 1px rgba(0, 0, 0, 0.25);
  }
  .card_first_img {
    -o-object-fit: contain;
      object-fit: contain;
  }

  .pay_card_first {
    display: flex;
    gap: 7px;
    justify-content: center;
    align-items: center;
  }

  .card_first_text {
    font-weight: 600;
    text-align: center;
    font-size: 18px;
    color: #0F2D97;
  }

  .pay_card_second {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .card_second_img {
    -o-object-fit: contain;
      object-fit: contain;
  }

  .pay_card_third {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .card_third_img {
    -o-object-fit: contain;
      object-fit: contain;
  }

  input[type=number]::-webkit-outer-spin-button,
  input[type=number]::-webkit-inner-spin-button {
    -webkit-appearance: none;
  }

  input[type=number],
  input[type=number]:hover,
  input[type=number]:focus {
    -webkit-appearance: none;
            appearance: none;
    -moz-appearance: textfield;
  }

  .payment {
    margin-top: clamp(1.875rem, 0.923rem + 4.76vw, 3.125rem);
    display: none;
  }
  .paymentActive {
    display: block;
  }

  .payment-container {
    max-width: 740px;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    justify-self: center;
  }

  .text-field {
    margin: 0 auto;
    width: clamp(11.875rem, 8.065rem + 19.05vw, 16.875rem);
    position: relative;
    display: flex;
  }

  .payment_input {
    width: 100%;
    height: 50px;
    padding: 6px 0 4px 20px;
    outline: none;
    font-size: 18px;
    background: #F0FAFE;
    border-radius: 8px;
    border: 2px solid rgba(15, 45, 151, 0.5);
    color: #0F2D97;
    transition: all 0.8s;
  }

  .payment_input:focus {
      border: 2px solid #0F2D97;
      box-shadow: 0px 0px 4px 2px rgba(0, 0, 0, 0.25);
  }
  .payment_input:valid,
  .payment_input:focus {
    border: 2px solid #0F2D97;
    box-shadow: 0px 0px 4px 2px rgba(0, 0, 0, 0.25);
  }
  
  .payment__input_text {
    display: block;
    position: absolute;
    left: 20px;
    top: 22px;
    color: rgba(15, 45, 151, 0.7);
    font-size: clamp(1rem, 0.905rem + 0.48vw, 1.125rem);
    font-weight: 500;
    pointer-events: none;
    transform-origin: left;
    transition: all 0.8s;
  }

  .text-field input:valid ~ span,
  .text-field input:focus ~ span {
    top: 4px;
    transform: scale(0.85);
    color: #0F2D97;
  }

  * button {
    padding: 0;
    border: none;
    font: inherit;
    color: inherit;
    background-color: transparent;
    cursor: pointer;
  }

  .payment_btn {
    color: #FFF;
    text-align: center;
    font-size: clamp(1.25rem, 1.06rem + 0.95vw, 1.5rem);
    font-weight: 500;
    border: none;
    outline: none;
    border-radius: 8px;
    background: #3C5ED4;
    width: clamp(11.875rem, 8.065rem + 19.05vw, 16.875rem);
    padding: 15px 0;
    margin-top: 20px;
    transition: all 0.8s;
  }

  .payment_btn:hover {
    box-shadow: 0px 0px 5px 2px rgba(0, 0, 0, 0.45);
  }

  .notification-container {
    width: clamp(14.688rem, 7.545rem + 35.71vw, 24.063rem);
    height: clamp(7.5rem, 6.548rem + 4.76vw, 8.75rem);
    background-color: #FF2626;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: clamp(1.25rem, 0.964rem + 1.43vw, 1.625rem);
    border-radius: 8px;
  }

  .point {
    color: #F0FAFE;
    text-align: center;
    font-size: clamp(2.25rem, 1.774rem + 2.38vw, 2.875rem);
    font-weight: 500;
    line-height: normal;
  }

  .text_notification {
    color: #F0FAFE;
    text-align: center;
    font-size: clamp(1rem, 0.81rem + 0.95vw, 1.25rem);
    font-weight: 500;
    font-style: normal;
    line-height: normal;
  }

  .circle {
    width: 46px;
    height: 46px;
    border: 2px solid #F0FAFE;
    border-radius: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .payment-main-container {
    max-width: 740px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
  }

  @media (max-width: 768px) {
    .payment-main-container {
      flex-direction: column;
      flex-wrap: wrap;
    }
    .notification-container {
      margin-top: 20px;
    }
    .payment_input {
      height: 44px;
      padding: 6px 0 0 20px;
    }
    .payment__input_text {
      top: 18px;
    }
  }
  @media (max-width: 425px) {
    .notification-container {
      padding: 0 20px;
    }
  }
  .ticket {
    display: none; 
    padding-bottom: 40px;
    max-width: 740px;
    margin: 0 auto;
    justify-content: space-between;
    align-items: center;
    margin-top: 20px;
  }

  .ticketActive {
    display: flex;
  }

  .ticket-container {
    padding: 20px 16px 0 16px;
    max-width: 220px;
    border-radius: 8px;
    border: 2px solid #153BC2;
    margin: 0 auto;
    margin-top: 30px;
  }

  .ticket-flex-container {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto;
    margin-bottom: 20px;
  }

  .notification-container-2 {
  width: clamp(14.688rem, 7.545rem + 35.71vw, 24.063rem);
  height: clamp(7.5rem, 6.548rem + 4.76vw, 8.75rem);
  background-color: #FF2626;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: clamp(1.25rem, 0.964rem + 1.43vw, 1.625rem);
  border-radius: 8px;
}

  .ticket_text {
    color: #153BC2;
    text-align: center;
    font-size: clamp(1.25rem, 1.406rem - 0.78vw, 1.125rem);
    font-style: normal;
    font-weight: 500;
    line-height: normal;
  }

  .input__wrapper {
    width: 100%;
    position: relative;
    margin-bottom: 20px;
    text-align: center;
  }

  .input__file {
    opacity: 0;
    visibility: hidden;
    position: absolute;
  }

  .input__file-button-text {
    line-height: 1;
    margin-top: 0px;
    text-align: center;
  }

  .input__file-button {
    width: 100%;
    max-width: 180px;
    height: 36px;
    background: #153BC2;
    color: #F0FAFE;
    font-size: 16px;
    font-weight: 400;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 8px;
    cursor: pointer;
    margin: 0 auto;
  }/*# sourceMappingURL=main.css.map */
</style>