<!--
    Page description for a single dog.
    As described in the SmallCard component, the same component was used for both Dog and Location since they have the same structure.
-->
<template>
    <main>
        <div class = "info-group">
            <img id = "main-img" src = "~/assets/img/peter.jpg" />
            <div id = "data-container">
                <p class = "data">Name: <span>{{ dog.name }}</span></p>
                <p class = "data">Role: <span>{{ dog.breed }}</span></p>
                <p class = "data">Age: <span>{{ dog.age }}</span></p>
            </div>
        </div>
        
        <!--
            v-html allows us to change the structure of a HTML element.
            It used because of the 'newLineOnFullStop' function that returns a string with the <br> tags.
            This function is a composable that is available anywhere, without requiring to be imported.
        -->

        <p id = "description" v-html = "newLineOnFullStop(dog.description)"></p>
      
         <h1 id="proj">projects supervised:</h1>

        <SmallCard :title = "dog.location.name" :subtitle = "dog.location.city" :link = "'/locations/' + dog.location.id" />
    </main>
</template>

<script setup>
    const route = useRoute()
    const id = route.params.id
    // useRuntimeConfig provide us with environment variables set up in the nuxtconfig file
    const { data: dog } = await useFetch(useRuntimeConfig().public.serverURL + '/dogs/' + id)
</script>

<style>
    #main-img {
    width: 30%;
    height: auto;
    }

    main {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .info-group {
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        gap: 40px;
    }

    .data {
        font-weight: bolder;
        font-size: 20pt;
        color:rgb(27, 103, 202);
    }

    .data span {
        font-weight: 100;
        font-size: 15pt;
        color:  rgb(11, 139, 182);
    }

    #description {
        padding: 0 20px 0 20px;
        font-size: 15pt;
        color: rgb(14, 144, 161);
    }
    #proj{
        color:  rgb(235, 134, 98);
        font-size: 20pt;
    }
</style>