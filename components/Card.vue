<!--
    Card to display information in the list page.
    This component could be achieved with the SmallCard component by using a <slot> to insert the div with the image. The solution used here allows for better control of the layout.
    Since the information shown can be categorized into title and subtitle, it was preferred to use only one component for both dogs and location.

    PROPS:
    - title: main information to display
    - subtitle: second information to display
    - link: link to the page description
-->
<template>
    <div class="card">
        <div class="image-container">
            <img class="img" src='~/assets/img/robert.jpg' />
        </div>
        <span class="title">{{ title }}</span>
        <span class="subtitle">{{ subtitle }}</span>
        <NuxtLink :to = "link" class="linkstyle" >see more information</NuxtLink>
    </div>
</template>

<script setup>
    const props = defineProps(['title', 'subtitle', 'link'])
</script>

<style>
    .image-container
    {
        display: flex;
        justify-content: center;
        padding: 2px;
        width: 100px;
        height: 100px;
    }

    .img
    {
        vertical-align: middle;
        max-width: 100%;
        max-height: 100%;
        height: auto;
        width: auto;
        margin: auto;
    }

    .card
    {
        display: flex;
        flex-flow: column;
        padding: 10px;
        border: solid blue;
        width: fit-content;
        height: fit-content;
    }

    .title
    {
        font-size: 2em;
        font-weight: bold;
        color: rgb(27, 103, 202);
    }
    .subtitle{
        font-size: 1em;
        color: rgb(14, 144, 161);
    }
    .linkstyle:hover{
        color:rgb(142, 205, 226);

        
    }
    .linkstyle{
        color: rgb(235, 134, 98);
        text-decoration: none;
    }
</style>