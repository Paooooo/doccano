<template>
  <v-card>
    <v-expansion-panels v-model="panel">
      <v-expansion-panel
          v-model="panel"
      expand>
        <v-expansion-panel-header>
          <v-icon>
            large
            mdi-file-eye-outline
          </v-icon>
          <div>Preview panel</div>
        </v-expansion-panel-header>
        <v-expansion-panel-content>
          <iframe :src="pdf_path" type="application/pdf"></iframe>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  </v-card>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({

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

  data() {
    return{
      panel: 0
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
iframe {
  height: 100%;
  width: 100%;
}

.preview {
  height: 50%;
}
</style>