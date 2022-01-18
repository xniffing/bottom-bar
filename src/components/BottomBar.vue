<template>
  <div
    class="floating-bar slide-active"
    :class="isTopScroll || isUpDirection || isBottomScroll ? 'slide-from' : 'slide-to'"
  >
    <div class="bar-items">
      <div class="bar-item active">
        <i class="fas fa-percent"></i>
        <div>Descontos</div>
      </div>
      <div class="bar-item">
        <i class="fas fa-users"></i>
        <div>Sugerir Parceiro</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, watch, ref } from 'vue'

let scrollY = ref(0)
let isUpDirection = ref(true)

watch(scrollY, (newY, oldY) => {
  newY > oldY ? isUpDirection.value = false : isUpDirection.value = true
})  

document.onscroll = (y) => {
  scrollY.value = y.path[1].scrollY
}
document.ontouchmove = (y) => {
  scrollY.value = y.view.scrollY
}

const isTopScroll = computed(() => {
  return scrollY.value <= 20 ? true : false
})

const isBottomScroll = computed(() => {
  return (window.innerHeight + scrollY.value ) >= document.body.offsetHeight ? true : false
})
</script>

<style scoped>
.floating-bar {
  position: fixed;
  bottom: 1.2rem;
  width: 100%;
  display: flex;
  justify-content: space-around;
}
.bar-items {
  padding: 0.7rem 2rem;
  border-radius: 2rem;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  background: rgb(0 0 0 / 60%);
  display: flex;
  box-shadow: 0px 0 13px #0000007a;
}
.bar-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;
}
.bar-item > div {
  font-size: 0.7em;
  margin-top: 0.2rem;
}
.bar-items > div:not(:last-child) {
  margin-right: 2rem;
}
.active {
  color: orange;
}
.slide-active {
  transition: all 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55);
}
.slide-from {
  -webkit-transform: translateY(0); /* WebKit */
  -moz-transform: translateY(0); /* Mozilla */
  -o-transform: translateY(0); /* Opera */
  -ms-transform: translateY(0); /* Internet Explorer */
  transform: translateY(0); /* CSS3 */
  opacity: 1;
}
.slide-to {
  -webkit-transform: translateY(115px); /* WebKit */
  -moz-transform: translateY(115px); /* Mozilla */
  -o-transform: translateY(115px); /* Opera */
  -ms-transform: translateY(115px); /* Internet Explorer */
  transform: translateY(115px); /* CSS3 */
  opacity: 0;
}
</style>
