<script setup>
import PaymentsModal from "@/components/payment-modal.vue";

const paymentModalOpened = ref(false);
const amount = "1.99";

useHead({
  title: "Awesome Vue Sticker",
  script: [{ src: "https://sdk.paymentshub.com/pay-now.min.js" }],
});
</script>

<template>
  <div class="container">
    <div class="image-container">
      <img src="../assets/vue.svg" class="image" alt="Vue logo" />
    </div>
    <div class="description-container">
      <div class="description">
        <h1 class="heading">Awesome Vue Sticker</h1>
        <h2 class="heading">${{ amount }} USD</h2>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. In placerat
          magna enim, vel blandit lacus elementum quis. Etiam elementum ligula
          venenatis consequat gravida. Phasellus orci nibh, elementum sit amet
          pharetra in, elementum sit amet ipsum.
        </p>
        <button @click="paymentModalOpened = true">Purchase</button>
      </div>
    </div>
  </div>
  <PaymentsModal
    :opened="paymentModalOpened"
    :amount="amount"
    @close-modal="paymentModalOpened = false"
  />
</template>

<style scoped>
.container {
  display: flex;
  height: 100vh;
  width: 100vw;
  padding: 2rem;
  flex-direction: column;
  box-sizing: border-box;
}
.image-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  flex: 1;
}
.description-container {
  flex: 1;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  text-align: start;
}
.heading {
  margin: 0;
}
.description {
  max-width: 28rem;
}
.image {
  flex: 2;
  padding: 1.5rem;
  will-change: filter;
  transition: filter 300ms;
  height: 100%;
  box-sizing: border-box;
  object-fit: contain;
}
.image:hover {
  filter: drop-shadow(0 0 2rem #42b883aa);
}
@media (min-width: 768px) {
  .container {
    flex-direction: row;
    gap: 4rem;
    padding: 4rem;
  }
  .image-container {
    flex: 2;
  }
}
</style>
