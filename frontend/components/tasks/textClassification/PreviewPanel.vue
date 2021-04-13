<template>
    <v-expansion-panels v-model="panel" class="mt-2">
      <v-expansion-panel
          v-model="panel"
          expand>
        <v-expansion-panel-header>
          <v-row>
          <v-btn
              text
              color="primary"
          >
            <v-icon left>
              mdi-file-eye-outline
            </v-icon>
            Preview Panel
          </v-btn>
            </v-row>
        </v-expansion-panel-header>
        <v-expansion-panel-content
        class="preview">
          <iframe :src="pdf_path" type="application/pdf"
                  height="100%"
                  width="100%"
          ></iframe>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
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
    return {
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

.preview {
  height: 40em;

}

</style>