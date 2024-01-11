<script>
export default {
    name: 'AppLoader'
}
</script>
<template lang="">
    <div class="loader-container">
        <span class="loader"></span>
    </div>
</template>
<style lang="scss" scoped>
    .loader-container {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        .loader {
            width: 48px;
            height: 48px;
            border: 5px solid #fff;
            border-bottom-color: #ff3d00;
            border-radius: 50%;
            display: inline-block;
            box-sizing: border-box;
            animation: rotation 1s linear infinite;
        }
}
</style>