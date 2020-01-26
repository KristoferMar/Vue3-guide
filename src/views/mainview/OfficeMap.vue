<template>
    <div>
        <img alt="Vue logo" src="../../assets/images/office.png">
    </div>
</template>

<script>
export default {
  setup() {
    // Could be done the following way
    const uri = '../../assets/images/office.png';
    return {
      uri,
    };
  },
};
</script>
