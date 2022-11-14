<template>
  <div>
    <button @click="$emit('btnEvent')">
      NEXT
    </button>


    
  </div>
</template>

<script>
export default {
  name: "Botons",
  props: { currentSentence: { type: Number, required: true }},


};
</script>

<style lang="scss" scoped></style>
