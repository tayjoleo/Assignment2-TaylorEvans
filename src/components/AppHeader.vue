<!-- When we set the background colour in AppHeader.vue
 it only affects the area around the component, not the whole page.
 Vue actively keeps component's styles separate so they don't 
 affect other parts of the app. -->

<template>
    <body>
        <h1>Hello world</h1>
    </body>
</template>

<script setup>
</script>

<style scoped>
    body {
        background-color: pink;
    }

    h1 {
        color:aqua;
    }
</style>
