<template>
    <div class="controls">
        <button id="profile-button"  class="pill active">Profile</button>
        <button id="courses-button" v-on:click:="changeClass" class="pill">Courses</button>
    </div>
</template>

<script>
    export default {
        name: "Controls",
        methods: {
            changeClass: function () {

            }
        }
    }

</script>

<style scoped>

</style>