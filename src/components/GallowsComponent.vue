<template>
    <div class="gallows">
        <img :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${errors}.svg`" />
    </div>
</template>

<script>
export default {
    name: 'GallowsComponent',
    props: {
        errors: Number
    }
}
</script>

<style>
.gallows img {
    margin-top: 35px;
    height: 150px;
}
</style>