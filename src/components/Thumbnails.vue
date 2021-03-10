<template>
 <ul class="thumbnails">
          <li class="thumbnail" :class="{'currentImage' : currentIndex == thumbnail.id}" v-for="thumbnail in thumbnails" :key="thumbnail.id">
            <img :src="thumbnail.src" :alt="thumbnail.alt" @click="changeMainImage" :data-num="thumbnail.id" />
          </li>
        </ul>

</template>

<script>
export default {

}
</script>

<style>

</style>
