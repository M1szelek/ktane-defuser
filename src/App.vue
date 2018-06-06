<template>
    <div class="container">
        <div class="row">
            <div class="col-sm-12">
                <h3>KTANE Defuser</h3>
            </div>
        </div>
        <hr>
        <div class="row">
            <label>Serial No.</label>
            <input type="text" v-model="serialNo">
            <label>Amount of batteries </label>
            <input type="number" min="0" max="5" v-model="batteriesAmount">
            <label>Serial bus</label>
            <input type="checkbox" v-model="serialBus">
        </div>

        <hr>

        <div class="container">
            {{ parityOfLastNumber }}
        </div>

        <hr>

        <app-wires></app-wires>



    </div>
</template>

<script>
    import Wires from './components/Wires.vue';

    export default {
        data: function () {
            return {
                serialNo: '',
                batteriesAmount: 0,
                serialBus: false
            }
        },
        computed:{
            parityOfLastNumber(){
                return this.serialNo.slice(-1) % 2 == 0 ? 'even' : 'odd';
            }
        },
        methods: {

        },
        components: {
            appWires: Wires
        }
    }
</script>

<style>
</style>
