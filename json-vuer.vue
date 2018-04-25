<template>
    <div class="json-vuer" v-if="this.json">
        <div class="json-vuer__switch">
            <div class="json-vuer__switch-collapse" v-if="allExpanded" @click="collapseAll">Alle einklappen</div>
            <div class="json-vuer__switch-expand" v-else @click="expandAll">Alle ausklappen</div>
        </div>
        <div class="json-vuer__level1__container json-vuer__container">

            <!--FIRST LEVEL-->
            <div v-for="(object1, key1, index1) in this.dataset"
                 class="json-vuer__container-sub json-vuer__level1__container-sub"
                 :class="{'json-vuer__is-expanded': allExpanded,
                          'json-vuer__is-collapsed': allCollapsed}">
                <div class="json-vuer__key json-vuer__level1__key" @click.prevent="toggleShow($event)">
                    <button class="json-vuer__btn-expand"></button>
                    <span class="json-vuer__key-title">{{reformat(key1)}}</span>
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
                            <span class="json-vuer__key-title">{{reformat(key2)}}</span>
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
                                    <span class="json-vuer__key-title">{{reformat(key3)}}</span>
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
                                            <span class="json-vuer__key-title">{{reformat(key4)}}</span>
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
                                                    <span class="json-vuer__key-title">{{reformat(key5)}}</span>
                                                </div>

                                                <!--SIXTH LEVEL-->
                                                <div v-if="isObject(object5)"
                                                     class="json-vuer__level6__container json-vuer__container">
                                                    <div v-for="(object6, key6, index6) in object5"
                                                         class="json-vuer__container-sub json-vuer__level6__container-sub"
                                                         :class="{'json-vuer__is-expanded': allExpanded,
                                                         'json-vuer__is-collapsed': allCollapsed,
                                                         'json-vuer__key-value-pair': isKeyValuePair(object6)}">
                                                        <div class="json-vuer__key json-vuer__level6__key"
                                                             @click.prevent="toggleShow($event)">
                                                            <button v-show="!isKeyValuePair(object6)"
                                                                    class="json-vuer__btn-expand"></button>
                                                            <span class="json-vuer__key-title">{{reformat(key6)}}</span>
                                                        </div>


                                                        <!--SEVENTH LEVEL-->
                                                        <div v-if="isObject(object6)"
                                                             class="json-vuer__level7__container json-vuer__container">

                                                            <div v-for="(object7, key7, index7) in object6"
                                                                 class="json-vuer__container-sub json-vuer__level7__container-sub"
                                                                 :class="{'json-vuer__is-expanded': allExpanded,
                                                                 'json-vuer__is-collapsed': allCollapsed,
                                                                 'json-vuer__key-value-pair': isKeyValuePair(object7)}">
                                                                <div class="json-vuer__key json-vuer__level7__key"
                                                                     @click.prevent="toggleShow($event)">
                                                                    <button v-show="!isKeyValuePair(object7)"
                                                                            class="json-vuer__btn-expand"></button>
                                                                    <span class="json-vuer__key-title">{{reformat(key7)}}</span>
                                                                </div>
                                                            </div>
                                                        </div>
                                                        <div v-else
                                                             class="json-vuer__value json-vuer__level7__value"
                                                             :class="{'json-vuer__is-expanded': allExpanded,
                                                             'json-vuer__is-collapsed': allCollapsed,
                                                             'json-vuer__key-value-pair': isKeyValuePair(object6)}">
                                                            {{reformat(object6)}}
                                                        </div>


                                                    </div>
                                                </div>
                                                <div v-else
                                                     class="json-vuer__value json-vuer__level6__value"
                                                     :class="{'json-vuer__is-expanded': allExpanded,
                                                     'json-vuer__is-collapsed': allCollapsed,
                                                     'json-vuer__key-value-pair': isKeyValuePair(object5)}">
                                                    {{reformat(object5)}}
                                                </div>


                                            </div>
                                        </div>
                                        <div v-else
                                             class="json-vuer__value json-vuer__level5__value"
                                             :class="{'json-vuer__is-expanded': allExpanded,
                                             'json-vuer__is-collapsed': allCollapsed,
                                             'json-vuer__key-value-pair': isKeyValuePair(object4)}">
                                            {{reformat(object4)}}
                                        </div>
                                    </div>
                                </div>
                                <div v-else
                                     class="json-vuer__value json-vuer__level4__value"
                                     :class="{'json-vuer__is-expanded': allExpanded,
                                     'json-vuer__is-collapsed': allCollapsed,
                                     'json-vuer__key-value-pair': isKeyValuePair(object3)}">
                                    {{reformat(object3)}}
                                </div>
                            </div>
                        </div>
                        <div v-else
                             class="json-vuer__value json-vuer__level3__value"
                             :class="{'json-vuer__is-expanded': allExpanded,
                             'json-vuer__is-collapsed': allCollapsed,
                             'json-vuer__key-value-pair': isKeyValuePair(object2)}">
                            {{reformat(object2)}}
                        </div>
                    </div>
                </div>
                <div v-else
                     class="json-vuer__value json-vuer__level2__value"
                     :class="{'json-vuer__is-expanded': allExpanded,
                     'json-vuer__is-collapsed': allCollapsed,
                     'json-vuer__key-value-pair': isKeyValuePair(object1)}">
                    {{reformat(object1)}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    /**
     * This is a custom imported function in order to reformat string-values
     * @param String
     * @returns {*}
     * @constructor
     */
    let ReformatFunction = function (String) {
        let ReformatJSON = require('./grammatik.json');
        if (ReformatJSON.hasOwnProperty(String)) {
            return ReformatJSON[String].long;
        }
        return String;
    };


    export default {
        name: "json-vuer",
        props: ['json'],
        data: function () {
            return {
                'data': this.json,
                'allExpanded': false,
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
            /**
             * Expand or collapse clicked sub-tree
             * @param event
             */
            toggleShow (event) {
                event.currentTarget.parentNode.classList.toggle('json-vuer__is-collapsed');
                event.currentTarget.parentNode.classList.toggle('json-vuer__is-expanded');

                /*        TODO: Async function: await toggle classes and check if element has class 'is-expanded'; If so,
                            set "allCollapsed" false;*/
            },
            /**
             * Expand entire tree
             */
            expandAll () {
                this.allExpanded = true;
            },
            /**
             * Collapse entire tree
             */
            collapseAll () {
                this.allExpanded = false;
            },
            /**
             * Custom imported reformatting function
             * @returns {string}
             */
            reformat (String) {
                return ReformatFunction(String);
            },
            /**
             * Determines, if {Entity} is an Object itself
             * @param Entity
             * @returns {boolean}
             */
            isObject (Entity) {
                return typeof(Entity) !== 'undefined' && typeof(Entity) === "object";
            },
            /**
             * Determines, if {Entity} is a key-value-pair (property-value)
             * @param Entity
             * @returns {boolean}
             */
            isKeyValuePair (Entity) {
                return !this.isObject(Entity);
            },

        }
    }
</script>

<style scoped>
    .json-vuer__switch {
        padding-top: 1rem;
        padding-bottom: 1rem;
        cursor: pointer;
    }

    .json-vuer__switch-collapse, .json-vuer__switch-expand {
        padding: 0.5rem;
        font-size: 1rem;
        text-align: center;
        border-radius: 3px;
    }

    .json-vuer__switch-collapse {
        border: 2px solid #326470;
        color: #326470;
    }

    .json-vuer__switch-expand {
        color: #fff;
        background: #326470;
    }

    .json-vuer__btn-expand {
        background: none;
        padding: 3px;
        border-radius: 5px;
    }

    .json-vuer__is-collapsed > .json-vuer__key > .json-vuer__btn-expand::before {
        Content: '▸';
        color: #fff;
    }

    .json-vuer__is-expanded > .json-vuer__key > .json-vuer__btn-expand::before {
        Content: '▼';
        font-size: small;
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
        /*border: 1px solid #ccc;*/
    }

    .json-vuer__container-sub {
        display: flex;
        flex-direction: column;
    }

    .json-vuer__is-expanded .json-vuer__container {
        max-height: 9999px;
    }

    .json-vuer__is-collapsed .json-vuer__container, .json-vuer__is-collapsed .json-vuer__value {
        max-height: 0px;
        padding: 0;
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
        min-width: 50%;
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
        min-width: 50%;
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
        border-bottom: 1px solid #fff;
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