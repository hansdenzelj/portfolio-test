<template>
<dialog ref="dialog">
    <p ref="dialog_content">Content</p>
    <button @click="this.isOpen = false">Close</button>
</dialog>
</template>

<script>
export default {
    props: ['trigger', 'foreground', 'background'],
    data() {
        return {
            isOpen: false,
            content: "lolololol",
        }
    },
    methods: {
        openArticle() {
            this.$refs.dialog.showModal()
        },
        closeArticle() {
            this.$refs.dialog.close()
        }
    },
    watch: {
        trigger: function() {
            this.isOpen = true
        },
        isOpen(state) {
            state ? this.openArticle() : this.closeArticle()
        }
    }
}
</script>