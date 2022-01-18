<template>
  <div
    class="floating-bar slide-active"
    :class="isScrolling ? 'slide-from' : 'slide-to'"
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

<script>

export default {
  data() {
    return {
      scrollY: 0
    }
  },
  created() {
    document.onscroll = (y) => {
      this.scrollY = y.path[1].scrollY
    }
    document.ontouchmove = (y) => {
      this.scrollY = y.view.scrollY
    }
  },
  computed: {
    isScrolling() {
      return this.scrollY === 0 ? true : false
    }
  }
}

</script>


<style scoped>
a {
  color: #42b983;
}

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
}

.bar-item > div {
  font-size: 0.7em;
  margin-top: 0.2rem;
}

.bar-item:not(:last-child) {
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
}
.slide-to {
  -webkit-transform: translateY(115px); /* WebKit */
  -moz-transform: translateY(115px); /* Mozilla */
  -o-transform: translateY(115px); /* Opera */
  -ms-transform: translateY(115px); /* Internet Explorer */
  transform: translateY(115px); /* CSS3 */
}
</style>
