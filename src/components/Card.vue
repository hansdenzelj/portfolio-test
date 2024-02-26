<template>
    <div 
    class="Card" 
    @click=openArticle()
    @mouseenter="active = true" 
    @mouseleave="active = false"
    :style="{'background-color': theme.background, 'color': theme.foreground}">
    <slot class="Card--Title" name="title">
        Insert Content Here
    </slot>
    <slot name="image">
        Insert Image Here
    </slot>
    </div>
</template>

<style scoped>
.Card {
    min-width: 100px;
    padding: 1em;
    border-radius: 0.75em;
    box-sizing: border-box;
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    transition: transform 200ms;
    display: flex;
    flex-direction: column;
    font-size: clamp(1rem, 2.5vw, 2rem);
}

.Card--Title {
    font-size: 2em;
}

.Card:hover {
    /* border: 0.2em solid rgb(223, 223, 223) */
    transform: scaleX(102%) scaleY(102%);
}

img {
    align-self:flex-start;
}

</style>

<script>

export default {
    components: {
    },
    props: {
        theme: {
            type: Object,
            default: () => ({
                foreground: '#000000',
                background: '#FFFFFF',
            }),
        },
    },
    data() {
        return {
            active: false,
        }
    },
    emits: ['setColor', 'unsetColor'],
    methods: {
        emitSetBGColor() { //set background color
            this.$emit('setColor', [this.theme.background, this.theme.foreground])
        },
        emitUnsetBGColor() {
            this.$emit('unsetColor')
        },
        openArticle(articleRef) {
            console.log("Hello")
        },
    },
    watch: {
        active(state) {
            state ? this.emitSetBGColor() : this.emitUnsetBGColor()
        },
    },
}
</script>