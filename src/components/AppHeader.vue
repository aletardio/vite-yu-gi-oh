<script>
export default {
    name: 'AppHeader'
}
</script>
<template lang="">
    <header>
        <div class="container-fluid">
            <div class='row'>
                <div class="col-12 d-flex flex-row align-items-center py-4">
                    <img src="/img/logo.png" alt="Yu-Gi-Oh" srcset="">
                    <h1 class="ps-4">
                        Yu-Gi-Oh Api
                    </h1>
                </div>
            </div>
        </div>
    </header>
</template>
<style lang="scss" scoped>
@use '../styles/generals.scss' as *;
@use '../styles/partials/variables' as *;

img {
    width: 8%;
}

</style>