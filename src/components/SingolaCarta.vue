<script>

export default{
    name:'SingolaCarta',
    props: ['nomeCard']
}
</script>

<template>
    <div class="my-card col-12 col-md-4 col-lg-2">
        <div class="col-12">
            <img :src="nomeCard.card_images[0].image_url" alt="">
        </div>
        <h5>{{ nomeCard.name }}</h5>
        <span>{{ nomeCard.archetype }}</span>
    </div>
</template>

<style lang="scss" scoped>
.my-card{
    background-color: #d48f38;
    border: 1px solid red;
    color: black;
    text-align: center;
    div{
        
        img{
            width: 100%;
            margin-bottom: 5px;
        }
    }
}
</style>