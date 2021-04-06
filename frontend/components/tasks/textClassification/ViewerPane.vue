<template>
    <div class="preview">
    <iframe :src="pdf_path" type="application/pdf"> </iframe>
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
    },
    metadata: {
      type: Object,
      default: () => ({}),
      required: true
    }
  },
  computed: {
    pdf_path() {
      const metapath = this.metadata.file_path
      return metapath.substr(15)
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