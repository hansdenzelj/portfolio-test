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
    grid-template-columns: repeat(1, 1fr);
    gap: 1.5em;
    margin: 0 2em 0 2em;
}

@media (min-width: 768px) {
    .Container {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (min-width: 1536px) {
    .Container {
        grid-template-columns: repeat(3, 1fr);
    }
}

@media (min-width: 1920px) {
    .Container {
        grid-template-columns: repeat(4, 1fr);
    }
}
</style>