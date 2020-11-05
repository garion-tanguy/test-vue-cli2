<template>
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
