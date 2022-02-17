<template>
    <div id="app">
        <div class="all" @mouseleave="flagOn = false">
            <transition name="fade"><p v-if="!flagOn" class="flag" style="width:50px" @mouseenter="flagOn = true">ФЛАГ</p></transition>
            <transition name="move">
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
                flagOn: false,
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
    .move-enter
    {
        transform: translateX(100px);
    }
    .move-enter-to
    {
        right:0;
    }
    .move-enter-active
    {
        transition: all 1s;
    }
    .move-leave-from
    {
        right:0;
    }
    .move-leave-to
    {
        transform: translateX(99px);
    }

    .move-leave-active
    {
        transition: all 1s;
    }


    .move-down-enter
    {
        transform: translateY(-10px);
    }
    .move-down-enter-to
    {
        right:0;
    }
    .move-down-enter-active
    {
        transition: ease .2s;
    }
    .move-down-leave-from
    {
        right:0;
    }
    .move-down-leave-to
    {
        transform: translateY(100px);
    }

    .move-down-leave-active
    {
        transition: ease .2s;
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
