<script>
export default {
    name: 'AppCardYoGiOh',
    props: {
        url: String,
        title: String,
        type: String
    }
}
</script>

<template>
    <div class="container_fluid">
        <div class="card m-3">
            <img class="pb-3 card-img-top" :src="url" alt="#">
            <div class="card-body text-center">
                <h5 class="text-uppercase card-title">{{ title }}</h5>
                <h6 class="card-text">{{ type }}</h6>
            </div>
        </div>
    </div>


</template>

<style scoped lang="scss">
@use '../styles/partials/variables' as *;
@use '../styles/partials/mixins' as *;

.container_fluid {
    width: 100%;

}

.card {
    width: 500px;
    background-color: #ecae03;

    .card-body {

        .card-title {
            font-weight: bold;
            color: white;
        }

    }
}
</style>