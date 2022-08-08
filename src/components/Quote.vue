<template>
<div class="quote">
    <!-- {{ handleApi() }} -->
    <h1>{{ quoteTxt }}</h1> 
    <p>{{ writer }}</p>
</div>
</template>

<script>
export default {
    name: 'myQ',
    props: ['quoteTxt', 'writer']
}
</script>

<style lang="scss">
    .quote {
        position: relative;
        // left: 25px;
        padding: 40px 20px;
        font-family: 'Montserrat', sans-serif;
        // margin: 25px 10px;
        color: white;
        border: 6px solid #198754;
        border-top: none;
        border-right: none;
        width: 80%;
        // box-shadow: -10px 10px 20px rgb(89, 255, 0);
        background-color: rgb(72, 72, 72);
        border-radius: 10px;

        h1 {
            margin-bottom: 25px;
        }
    }
</style>