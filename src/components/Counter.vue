<template>
    <h2> {{ isTitle }} </h2>
    <p> {{ counter }} <sup>2</sup> = {{ squareCounter }}</p>

    <div>
        <button @click="increase()" > +1 </button>
        <button @click="decrease()"> -1 </button>
    </div>
</template>

<script>
    export default {
        props: {
            title: String,
            start : {
                type: Number,
                require : true,
                default : 0,
                validator( value ){
                    return value >= 0
                }
            }
        }, 
        data(){
            return{
                counter: this.start
            }
        },
        methods:{
            increase(){
                this.counter++
            },
            decrease(){
                this.counter--
            },
            getSqueareValue(){
                return this.counter * this.counter
            }
        },
        computed: {
            squareCounter (){
                return this.counter * this.counter 
            },
            isTitle(){
                return this.title || 'counter'
            }
        },
        
    }
</script>

<style>

    button{
        background-color: #64bb87;
        border-radius: 5px;
        border: 1px solid white;
        color: azure;
        cursor:pointer;padding:5px 15px;
        margin:0 5px;
        transition: 0.3s ease-in-out;
    }
    button:hover{
        background-color: #5aa67b;
        transition: 0.3s ease-in-out;
    }

</style>