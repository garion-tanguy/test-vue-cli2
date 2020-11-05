<template>
  <div id="app">
   <button @click="visible = true">Open</button>

    <SimpleDialog :visible="visible"/>
  </div>
</template>

<script>

import SimpleDialog from "@/components/SimpleDialog";

export default {
  name: 'App',
  components: {
    SimpleDialog

  },
  data: function () {
    return {
      visible:false,
    }
  },
}
</script>

