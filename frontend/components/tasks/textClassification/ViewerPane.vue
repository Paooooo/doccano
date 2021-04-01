<template>
  <v-card>
    <v-card-title> Viewer Pane </v-card-title>
    <div class="preview">
    <iframe :src="/pdf/ + doc.text" type="application/pdf"> </iframe>
    </div>
  </v-card>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend( {
  props: {
    doc: {
      type: Object,
      default: () => ({}),
      required: true
    }
  }
})
</script>

<style scoped>
.preview {
width: 100%;
height: 100%;
}
</style>