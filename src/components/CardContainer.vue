<template>
<div class="Container">
    <slot>
        <p>Cards should be loaded here</p>
    </slot>
</div>
</template>

<style scoped>
.Container {
    display: grid;
    min-height: 600px;
    min-width: 600px;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 1.5em;
}

@media (max-width: 2000px) {
    .Container {
        grid-template-columns: 1fr 1fr;
    }
}

@media (max-width: 650px) {
    .Container {
        grid-template-columns: 1fr;
        min-width: 300px;
    }
}

</style>