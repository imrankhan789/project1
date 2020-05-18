<template>
    <div class="calc">
    <div class="display">{{ current }}</div>
    <div class="btn" @click="append(7)">7</div>
    <div class="btn" @click="append(8)">8</div>
    <div class="btn" @click="append(9)">9</div>
    <div class="btn operator" @click="add">+</div>
    <div class="btn" @click="append(4)">4</div>
    <div class="btn" @click="append(5)">5</div>
    <div class="btn" @click="append(6)">6</div>
    <div class="btn operator" @click="division">/</div>
    <div class="btn" @click="append(1)">1</div>
    <div class="btn" @click="append(2)">2</div>
    <div class="btn" @click="append(3)">3</div>
    <div class="btn operator" @click="mul">x</div>
    <div class="btn" @click="append(0)">0</div>
    <div class="btn" @click="dot()">.</div>
    <div class="btn" @click="percentage">%</div>
    <div class="btn operator" @click="sub">-</div>
    <div class="btn operator" @click="equal">=</div>
    <div class="btn operator" @click="clear">C</div>
</div>
</template>
<script>
    export default{
        name:'Calculator',
        data(){
            return{
                current:'',
                operator:null,
                previous:null,
                operatorclicked:false,
                
            }

        },
        methods:{
            clear() {
                this.current='0';
            },
            percentage() { 
                this.current=(this.current)/100;
            },
            append(number) {
                if(this.operatorclicked)
                {
                    this.current = '';
                    this.operatorclicked = false;
                }
                //this.current=this.current+number;
                this.current= `${this.current}${number}`;
            },
            dot() {
                if(this.current.indexof('.') === -1){
                    this.append('.');
                }
            },
            setprevious() {
                this.previous = this.current;
                this.operatorclicked = true;

            },
            add() {
                this.operator= (a,b) => a+b;
                this.setprevious();
             },
            sub() {
                this.operator= (a,b) => a-b;
                this.setprevious();
            },
            division() {
                this.operator= (a,b) => a/b;
                this.setprevious();
            },
            mul() {
                this.operator= (a,b) => a*b;
                this.setprevious();
            },
            equal(){
                this.current = `${this.operator(parseFloat(this.previous),parseFloat(this.current))}`;

            },

        }
    }
</script>

<style scoped>
    .calc{
        display: grid;
        width: 400px;
        margin: auto;
        font-size: 40px;
        grid-template-columns: 4;
        grid-auto-rows: minmax(25px,auto);
        


    }
    .display{
        grid-column: 1/5;
        background-color: rgb(128, 107, 81);
    }
    .btn{
        background-color: #eee;
        border: 1px solid #333;
    }
    .operator{
        background-color: royalblue;
        color: white;
    }
</style>