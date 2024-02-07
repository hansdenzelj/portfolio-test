<template>
    <div 
    class="Card" 
    @click="showArticle = !showArticle"
    @mouseenter="active = true" 
    @mouseleave="active = false"
    :style="{'background-color': theme.background, 'color': theme.foreground}">
    <slot>
        Insert Content Here
    </slot>
    <!-- <Article :trigger="showArticle"></Article> -->
    </div>
</template>

<style scoped>
.Card {
    min-width: 100px;
    padding: 1em;
    border-radius: 0.25em;
    box-sizing: border-box;
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    transition: border 200ms;
    display: flex;
    flex-direction: column;
    font-size: clamp(1rem, 2.5vw, 2rem);
}

.Card:hover {
    border: 0.2em solid rgb(223, 223, 223)
}

</style>

<script>
import Article from './Article.vue'

export default {
    components: {
        Article,
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
            showArticle: false,
        }
    },
    emits: ['setColor', 'unsetColor'],
    methods: {
        emitSetBGColor() { //set background color
            this.$emit('setColor', this.theme.background)
        },
        emitUnsetBGColor() {
            this.$emit('unsetColor')
        }
    },
    watch: {
        active(state) {
            state ? this.emitSetBGColor() : this.emitUnsetBGColor()
        },
    },
}
</script>