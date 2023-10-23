<script setup>
defineProps({
  value: {
    type: String,
    required: true
  },
  suit: {
    type: String,
    required: true
  },
  opened: {
    type: Boolean,
    default: false
  }
})

function getIconSrc (icon) {
  return new URL(`/src/assets/icons/${icon}.svg`, import.meta.url)
}
</script>

<template>
  <div
    :class="['cards-item', {
      'cards-item--opened': opened
    }]"
  >
    <div class="cards-item__inner">
      <div class="cards-item__front">
        <div class="cards-item__value">
          {{ value }}
        </div>

        <img
            class="cards-item__suit"
            :src="getIconSrc(suit)"
            :alt="suit"
        />
      </div>

      <div class="cards-item__back" />
    </div>
  </div>
</template>

<style>
.cards-item {
  width: 30vw;
  height: 45vw;
  max-width: 185px;
  max-height: 277px;
  perspective: 1000px;
  background-color: transparent;
}

.cards-item--opened .cards-item__inner {
  transform: translate(0, -297px) rotateY(180deg);
}

@media screen and (max-width: 768px) {
  .cards-item--opened .cards-item__inner {
    transform: translate(0, -47vw) rotateY(180deg);
  }
}

.cards-item__inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.cards-item__front,
.cards-item__back {
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 20px;
  backface-visibility: hidden;
}

.cards-item__front {
  padding: 10px 20px;
  background-color: #FFF;
  transform: rotateY(180deg);
}

.cards-item__value {
  font-size: 48px;
  font-weight: 600;
  color: #000;
  line-height: 1;
  margin-bottom: 8px;
}

.cards-item__back {
  background: url('@/assets/icons/back.svg') no-repeat center / cover, linear-gradient(180deg, #3085E8 0%, #1660B6 100%);
  border: 9px solid grey;
}
</style>
