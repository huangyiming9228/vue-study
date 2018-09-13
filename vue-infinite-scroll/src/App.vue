<template>
    <div id="app">
        <infinite-scroll></infinite-scroll>
    </div>
</template>

<script>
import InfiniteScroll from "./components/InfiniteScroll";

export default {
    name: 'App',
    components: {
        InfiniteScroll
    }
}
</script>

<style lang="scss">
body {
    font-family: 'Archivo Narrow', sans-serif;
    background: #25859a;
}

.display {
    display: flex;
    justify-content: center;
    align-content: center;
}

#app {
    @extend .display;
    flex-direction: column;
}
</style>
