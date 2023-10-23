<script setup>
import { ref } from 'vue'
import CardsItem from './cards-item/index.vue'

const cards = [
  { value: '12', suit: 'crosses' },
  { value: '12', suit: 'crosses' },
  { value: '12', suit: 'crosses' }
]
let isCenterCardOpened = ref(false)
function toggleCenterCard () {
  isCenterCardOpened.value = !isCenterCardOpened.value
}
</script>

<template>
  <div class="cards">
    <div
      class="cards__wr"
    >
      <cards-item
        v-for="({ value, suit }, index) in cards"
        :value="value"
        :suit="suit"
        :opened="isCenterCardOpened && index === 1"
      />
    </div>

    <button
      class="cards__button"
      @click="toggleCenterCard"
    >
      Play
    </button>
  </div>
</template>

<style>
.cards {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.cards__wr {
  display: flex;
  gap: 20px;
  margin-bottom: 50px;
}

@media screen and (max-width: 768px) {
  .cards__wr {
    gap: 2vw;
    margin-bottom: 4vw;
  }
}

.cards__button {
  display: flex;
  width: 100%;
  height: 15vw;
  max-width: 345px;
  max-height: 73px;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
  color: #FFF;
  text-align: center;
  font-size: 16px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
  border-radius: 12px;
  border: 1px solid #4456FE;
  background: linear-gradient(180deg, #4457FF 0%, #3C4DE1 100%);
  cursor: pointer;
}
</style>
