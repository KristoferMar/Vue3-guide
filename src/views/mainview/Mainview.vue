<template>
  <div>
    <div class="center">
        <OfficeMap></OfficeMap>
    </div>
    <hr class="HorizontalSplit">
  </div>
</template>

<script>
import OfficeMap from './OfficeMap.vue';

export default {
  components: {
    OfficeMap,
  },
};
</script>

<style scoped>
    .center {
    padding: 20px;
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
    }

    .HorizontalSplit {
      width: 80%;
    }
</style>
