<template>
<img class="mainImage"
:src="mainImage.src"
:alt="mainImage.alt"
/>

</template>

<script>
export default {
  name: 'MainImage',
  props:{
    mainImage:{
      require: true
    }
  }
}
</script>

<style>

</style>
