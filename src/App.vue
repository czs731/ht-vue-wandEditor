<template>
  <div id="app">
    <w-editor edit-id="edit-1" v-model="content"></w-editor>
  </div>
</template>

<script>

import WEditor from '@/components/w-editor'
export default {
  name: 'App',
  components: {WEditor},
  data() {
    return {
      content: '311313131313'
    }
  },
}
</script>

<style>
#app {

}
</style>
