<template>
    <div class="Project-Wrapper">
        <div class="Project">
            <p>Contain details about the project here</p>
        </div>
    </div>
</template>

<script>
export default {
    props: [],
    data() {
        return {
           
        }
    },
    methods: {

    },
    watch: {
        
    }
}
</script>

<style scoped>
    .Project-Wrapper {
        position: fixed;
        z-index: 999;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        
        display: none;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .Project {
        width: 80%;
        height: 80%;
        background-color: white;
    }

    p {
        color: #000;
        margin: 0;
    }
</style>