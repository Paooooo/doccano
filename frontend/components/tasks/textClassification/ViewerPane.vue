<template>
    <div class="preview">
    <iframe :src="/pdf/ + doc.text" type="application/pdf"> </iframe>
    </div>
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
.preview, iframe {
width: 100%;
height: 100%;
}
</style>