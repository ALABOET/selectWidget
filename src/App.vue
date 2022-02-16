<template>
    <div id="app">
        <div class="all" @mouseleave="flagOn = false">
            <transition name="fade"><p v-if="!flagOn" class="flag" style="width:50px" @mouseenter="flagOn = true">ФЛАГ</p></transition>
            <transition name="fade">
            <vue-select class="vueSelect" v-if="flagOn" :options="languages"
                        @select="optionSelect"
                        :selected="selected"></vue-select>
            </transition>
        </div>
    </div>
</template>

<script>

    import vueSelect from "@/components/vueSelect";
    export default {
        name: 'App',
        data() {
            return {
                flagOn: true,
                selected: 'select it',
                languages: [
                    {

                        text: 'English',
                        value: 'en|en'
                    },
                    {

                        text: 'French',
                        value: 'en|fr'
                    },
                    {

                        text: 'German',
                        value: 'en|de'
                    },
                    {

                        text: 'Italian',
                        value: 'en|it'
                    },
                    {

                        text: 'Japanese',
                        value: 'en|ja'
                    },
                    {

                        text: 'Polish',
                        value: 'en|pl'
                    },
                    {

                        text: 'Portuguese',
                        value: 'en|pt'
                    },
                    {

                        text: 'Spanish',
                        value: 'en|es'
                    }]
            }
        },
        methods: {
            optionSelect(option) {
                ///сюда добавить перевод и прочую дичь
                this.selected = option.text
                this.flagOn = false
            }
        },
        components: {
            vueSelect
        }
    }
</script>

<style>
    .all {
        position: absolute;
        width: 200px;
        height: 70px;
        right: 0px;
    }

    .vueSelect, .flag {
        position: absolute;
    }

    .flag {
        right: 0;
        top: -13px;
    }

    .fade-enter {
        opacity: 0;
    }

    .fade-enter-to {
        opacity: 1;
    }

    .fade-enter-active {
        transition: all .3s;
    }

    .fade-leave-from {
        opacity: 1;
    }

    .fade-leave-to {
        opacity: 0;
    }

    .fade-leave-active {
transition: all .3s;
    }
</style>
