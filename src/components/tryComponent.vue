<template>
  <div>
    <div>
      <span>This is an imported component</span>
    </div>
    <div>
      <div>and this is its prop:</div>
      <div>{{ prop }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TryImportVue",
  props: {
    prop: {
      type: String,
    },
  },
};
</script>
