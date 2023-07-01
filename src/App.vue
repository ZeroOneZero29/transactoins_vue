<template>
    <div class="section-container">
            <h1 class="main_title">Пополнение счета</h1>
            <div class="subtitle-container">
                <img src='require("@/assets/img/icon/walet-ligth.png")' alt="walet" class="subtitle_img">
                <h2 class="subtitle">Выбирете платежную систему:</h2>
            </div>
        </div>
</template>
<script>
export default {
    
}
</script>
<style>
    @import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&display=swap");
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
}

.subtitle_img {
  -o-object-fit: contain;
     object-fit: contain;
}

.subtitle {
  color: #0F2D97;
  font-size: clamp(1.5rem, 0.853rem + 2.76vw, 2.25rem);
  font-weight: 600;
}/*# sourceMappingURL=main.css.map */
</style>
