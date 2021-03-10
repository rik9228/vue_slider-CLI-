<template>
 <ul class="locations">
          <li
            class="location"
            v-for="location in locations"
            :key="location.id"
            :data-num="location.id"
            :class="{'currentLocation' : currentIndex == location.id}"
            @click="locationChange"
          ></li>
        </ul>

</template>

<script>
export default {

}
</script>

<style>

</style>
