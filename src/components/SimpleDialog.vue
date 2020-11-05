<template>
  <div class="dialog-parent">

    <transition class="v-enter-active, v-enter" >
    <div class="dialog-backdrop" v-show="visible"></div>
    </transition>

    <transition class="v-leave-active, v-leave-to">
    <div class="dialog-window" v-show="visible">
      <header>
        <h1>{{titre}}</h1>
      </header>
      <div class="main">
        <slot/>
      </div>
      <footer>
        <button @click="visible = false">Close</button>
      </footer>
    </div>
    </transition>

  </div>
</template>
<script>
export default {
  name: 'SimpleDialog',
  props: {
    titre: {
      type: String,
      default: "Le titre par défaut",
    }
    //visible: {}
  },
  data: function () {
    return {
       visible:this.initialVisible,
    }
  },
  methods: {
    show() {
      this.visible = true;
    }
  }
}
</script>

<style scoped>
.dialog-window {
  position: relative;
  pointer-events: auto;
  animation: zoom 3s;
}
@keyframes zoom {
  from {transform: scale(0)}
  50% {transform: scale(2)}
  to {transform: scale(1)}
}
.dialog-parent {
  pointer-events: none;
  display: flex;
  justify-content: center;
  align-items: center;
}
.dialog-parent, .dialog-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
}
.dialog-backdrop {
  pointer-events: auto;
  background-color: rgba(255,30,80,0.5);
}

.v-enter-active {
  transition: opacity 2s;
}
.v-leave-active {
  transition: opacity 3s;
animation: dezoom 2s;
}
@keyframes dezoom {
  from {transform: scale(1)}
  50% {transform: scale(2)}
  to {transform: scale(0)}
}

.v-enter, .v-leave-to {
  opacity: 0;
}
</style>
