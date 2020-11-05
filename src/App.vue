<template>
  <div id="app">
   <button @click="$refs.dialog.show()">Open</button>

    <SimpleDialog ref="dialog" :initial-visible="true"/>
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
     // visible:false,
    }
  },
}
</script>

