<template>
    <div class="json-vuer">
        <div class="json-vuer__level1__container json-vuer__container">

            <!--FIRST LEVEL-->
            <div v-for="(object1, key1, index1) in this.dataset"
                 class="json-vuer__container-sub json-vuer__level1__container-sub"
                 :class="{'json-vuer__is-expanded': allExpanded,
                          'json-vuer__is-collapsed': allCollapsed}">
                <div class="json-vuer__key json-vuer__level1__key" @click.prevent="toggleShow($event)">
                    <button class="json-vuer__btn-expand"></button>
                    <span class="json-vuer__key-title">{{key1}}</span>
                </div>

                <!--SECOND LEVEL-->
                <div v-if="isObject(object1)"
                     class="json-vuer__level2__container json-vuer__container">
                    <div v-for="(object2, key2, index2) in object1"
                         class="json-vuer__container-sub json-vuer__level2__container-sub"
                         :class="{'json-vuer__is-expanded': allExpanded,
                                 'json-vuer__is-collapsed': allCollapsed,
                                 'json-vuer__key-value-pair': isKeyValuePair(object2)}">
                        <div class="json-vuer__key json-vuer__level2__key" @click.prevent="toggleShow($event)">
                            <button v-show="!isKeyValuePair(object2)"
                                    class="json-vuer__btn-expand"></button>
                            <span class="json-vuer__key-title">{{key2}}</span>
                        </div>

                        <!--THIRD LEVEL-->
                        <div v-if="isObject(object2)"
                             class="json-vuer__level3__container json-vuer__container">
                            <div v-for="(object3, key3, index3) in object2"
                                 class="json-vuer__container-sub json-vuer__level3__container-sub"
                                 :class="{'json-vuer__is-expanded': allExpanded,
                                 'json-vuer__is-collapsed': allCollapsed,
                                 'json-vuer__key-value-pair': isKeyValuePair(object3)}">
                                <div class="json-vuer__key json-vuer__level3__key" @click.prevent="toggleShow($event)">
                                    <button v-show="!isKeyValuePair(object3)"
                                            class="json-vuer__btn-expand"></button>
                                    <span class="json-vuer__key-title">{{key3}}</span>
                                </div>

                                <!--FOURTH LEVEL-->
                                <div v-if="isObject(object3)"
                                     class="json-vuer__level4__container json-vuer__container">
                                    <div v-for="(object4, key4, index4) in object3"
                                         class="json-vuer__container-sub json-vuer__level4__container-sub"
                                         :class="{'json-vuer__is-expanded': allExpanded,
                                         'json-vuer__is-collapsed': allCollapsed,
                                         'json-vuer__key-value-pair': isKeyValuePair(object4)}">

                                        <div class="json-vuer__key json-vuer__level4__key" @click.prevent="toggleShow($event)">
                                            <button v-show="!isKeyValuePair(object4)"
                                                    class="json-vuer__btn-expand"></button>
                                            <span class="json-vuer__key-title">{{key4}}</span>
                                        </div>

                                        <!--FIFTH LEVEL-->
                                        <div v-if="isObject(object4)"
                                             class="json-vuer__level5__container json-vuer__container">
                                            <div v-for="(object5, key5, index5) in object4"
                                                 class="json-vuer__container-sub json-vuer__level5__container-sub"
                                                 :class="{'json-vuer__is-expanded': allExpanded,
                                                 'json-vuer__is-collapsed': allCollapsed,
                                                 'json-vuer__key-value-pair': isKeyValuePair(object5)}">
                                                <div class="json-vuer__key json-vuer__level5__key" @click.prevent="toggleShow($event)">
                                                    <button v-show="!isKeyValuePair(object5)"
                                                            class="json-vuer__btn-expand"></button>
                                                    <span class="json-vuer__key-title">{{key5}}</span>
                                                </div>

                                                <!--SIXTH LEVEL-->
                                                <div v-if="isObject(object5)"
                                                     class="json-vuer__level6__container json-vuer__container">
                                                    <div v-for="(object6, key6, index6) in object5"
                                                         class="json-vuer__container-sub json-vuer__level6__container-sub"
                                                         :class="{'json-vuer__is-expanded': allExpanded,
                                                         'json-vuer__is-collapsed': allCollapsed,
                                                         'json-vuer__key-value-pair': isKeyValuePair(object6)}">
                                                        <div class="json-vuer__key json-vuer__level6__key" @click.prevent="toggleShow($event)">
                                                            <button v-show="!isKeyValuePair(object6)"
                                                                    class="json-vuer__btn-expand"></button>
                                                            <span class="json-vuer__key-title">{{key6}}</span>
                                                        </div>


                                                        <!--SEVENTH LEVEL-->
                                                        <div v-if="isObject(object6)"
                                                             class="json-vuer__level7__container json-vuer__container">

                                                            <div v-for="(object7, key7, index7) in object6"
                                                                 class="json-vuer__container-sub json-vuer__level7__container-sub"
                                                                 :class="{'json-vuer__is-expanded': allExpanded,
                                                                 'json-vuer__is-collapsed': allCollapsed,
                                                                 'json-vuer__key-value-pair': isKeyValuePair(object7)}">
                                                                <div class="json-vuer__key json-vuer__level7__key" @click.prevent="toggleShow($event)">
                                                                    <button v-show="!isKeyValuePair(object7)"
                                                                            class="json-vuer__btn-expand"></button>
                                                                    <span class="json-vuer__key-title">{{key7}}</span>
                                                                </div>
                                                            </div>
                                                        </div>
                                                        <div v-else
                                                             class="json-vuer__value json-vuer__level7__value">
                                                            {{object6}}
                                                        </div>


                                                    </div>
                                                </div>
                                                <div v-else
                                                     class="json-vuer__value json-vuer__level6__value">
                                                    {{object5}}
                                                </div>


                                            </div>
                                        </div>
                                        <div v-else
                                             class="json-vuer__value json-vuer__level5__value">
                                            {{object4}}
                                        </div>
                                    </div>
                                </div>
                                <div v-else
                                     class="json-vuer__value json-vuer__level4__value">
                                    {{object3}}
                                </div>
                            </div>
                        </div>
                        <div v-else
                             class="json-vuer__value json-vuer__level3__value">
                            {{object2}}
                        </div>
                    </div>
                </div>
                <div v-else
                     class="json-vuer__value json-vuer__level2__value">
                    {{object1}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "json-vuer",
        props: ['json'],
        data: function () {
            return {
                'data': this.json,
                'allExpanded': true,
            };
        },
        computed: {
            dataset: function () {
                return this.data;
            },
            allCollapsed: function () {
                return !this.allExpanded
            },
        },
        methods: {
            toggleShow (event) {
                event.currentTarget.parentNode.classList.toggle('json-vuer__is-collapsed');
                event.currentTarget.parentNode.classList.toggle('slide-up');
                event.currentTarget.parentNode.classList.toggle('json-vuer__is-expanded');
            },
            isUltimate () {
            },
            isObject (Entity) {
                return typeof(Entity) !== 'undefined' && typeof(Entity) === "object";
            },
            isKeyValuePair (Entity) {
                return !this.isObject(Entity);
            },
            Keys (object) {
                return Object.keys(object);
            }
        }
    }
</script>

<style scoped>
    .json-vuer__btn-expand {
        background: none;
        padding: 3px;
        border-radius: 5px;
    }

    .json-vuer__is-collapsed > .json-vuer__key > .json-vuer__btn-expand::before {
        Content: '+';
        color: #fff;
    }

    .json-vuer__is-expanded > .json-vuer__key > .json-vuer__btn-expand::before {
        Content: '-';
        color: #888;
    }

    .json-vuer__is-collapsed > .json-vuer__key {
        background: #326470;
        color: #fff;
    }

    .json-vuer__is-expanded > .json-vuer__key:hover {
        color: #326470;
    }

    .json-vuer {
        background: #fff;
        border: 1px solid #ccc;
    }

    .json-vuer__container-sub {
        display: flex;
        flex-direction: column;
    }

    .json-vuer__is-expanded .json-vuer__container {
        max-height: 9999px;
    }

    .json-vuer__is-collapsed .json-vuer__container {
        max-height: 0px;

    }

    .json-vuer__container {
        display: block;
        overflow: hidden;
        -webkit-transition: max-height 400ms ease-in-out;
        -moz-transition: max-height 400ms ease-in-out;
        -o-transition: max-height 400ms ease-in-out;
        transition: max-height 400ms ease-in-out;
    }

    .json-vuer__key-value-pair {
        flex-direction: row;
    }

    .json-vuer__key-value-pair .json-vuer__key {
        font-style: italic;
    }

    .json-vuer__key-value-pair .json-vuer__key:hover {
        color: #888;
    }

    .json-vuer__is-collapsed.json-vuer__key-value-pair > .json-vuer__key {
        background: #eee;
        color: #888;
    }

    .json-vuer__key {
        overflow: hidden;
        padding-left: 2px;
        min-width: 25%;
        background: #eee;
        color: #888;
        transition: background 400ms ease-in-out;
        cursor: pointer;
        -webkit-touch-callout: none;
        -webkit-user-select: none;
        -khtml-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
    }

    .json-vuer__value {
        overflow: visible;
        margin-left: 5px;
        padding: 5px;
        background: #fff;
        font-family: "Merriweather";
    }

    .json-vuer__level1__key,
    .json-vuer__level2__key,
    .json-vuer__level3__key,
    .json-vuer__level4__key,
    .json-vuer__level5__key,
    .json-vuer__level6__key,
    .json-vuer__level7__key {
        background: #eee;
        padding: 5px;
        font-weight: bold;
    }

    .json-vuer__level1__key {
        font-size: 1.5rem;
    }

    .json-vuer__level2__key {
        font-size: 1.25rem;
        padding-left: 1rem;

    }

    .json-vuer__level3__key {
        font-size: 1rem;
        padding-left: 2rem;

    }

    .json-vuer__level4__key {
        padding-left: 3rem;

    }

    .json-vuer__level5__key {
        padding-left: 4rem;

    }

    .json-vuer__level6__key {
        padding-left: 5rem;

    }

    .json-vuer__level7__key {
        padding-left: 6rem;
    }

</style>