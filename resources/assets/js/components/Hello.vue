<template>
    <div>
        <div>Hello {{name}}{{exclamationMarks}}</div>
        <button @click="decrement">-</button>
        <button @click="increment">+</button>
    </div>
</template>

<script lang="ts">
    import Vue, { ComponentOptions } from 'vue';

    interface HelloComponent extends Vue{
        name: string,
        initialEnthusiasm: number,
        enthusiasm: number,
        exclamationMarks: string
    }

    export default {
        props: {
            name: String,
            initialEnthusiasm: Number
        },
        data(){
            return {
                enthusiasm: this.initialEnthusiasm
            }
        },
        methods: {
            increment(){
                this.enthusiasm++;
            },
            decrement() {
                if (this.enthusiasm > 1) {
                    this.enthusiasm--;
                }
            }
        },
        computed: {
            exclamationMarks() : string {
                return Array(this.enthusiasm + 1).join('!');
            }
        }
    } as ComponentOptions<HelloComponent>;
</script>