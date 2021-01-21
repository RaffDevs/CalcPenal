<template>
    <q-card style="width: 350px" bordered>
        <q-card-section class="row items-center">
            <q-card-section class="col-12">
                <q-input class="text-right" outlined disable v-model="answer" />
            </q-card-section>
            <q-card-section class="col-12 row justify-center" >
                <div class="row col-12 q-mt-sm justify-center  no-wrap" >

                    <div class="col-3" style="margin : 0 1px">
                        <q-btn @click="clear" color="dark" label="C" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="percent" label="%" color="dark" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="times" label="*" color="dark" style="width : 100%"/>
                        
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="divide" color="dark" label="/" style="width : 100%"/>
                        
                    </div>
                </div>
                <div class="row col-12 q-mt-sm justify-center  no-wrap" >

                    <div class="col-3" style="margin : 0 1px">
                        <q-btn @click="append('9')" color="dark" label="9" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="append('8')"  color="dark" label="8" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="append('7')" color="dark" label="7" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="minus" color="dark" label="-" style="width : 100%"/>
                        
                    </div>
                </div>
                <div class="row col-12 q-mt-sm justify-center  no-wrap" >
                    <div class="col-3" style="margin : 0 1px">
                        <q-btn @click="append('6')" color="dark" label="6" style="width : 100%"/>
                    </div>

                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="append('5')"  color="dark" label="5" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="append('4')"  color="dark" label="4" style="width : 100%"/>
                    </div>
                    <div class="col-3" style="margin : 0 1px;">
                        <q-btn @click="plus" color="dark" label="+" style="width : 100%"/>
                        
                    </div>
                </div>
                <div class="row col-12 q-mt-sm justify-center  no-wrap" >
                    <div class="col-3" style="margin : 0 1px">
                        <q-btn @click="append('3')"  color="dark" label="3" style="width : 100%"/>
                    </div>

                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="append('2')"  color="dark" label="2" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="append('1')"  color="dark" label="1" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="equal" color="dark" label="=" style="width : 100%; "/>
                    </div>
                </div>
                <div class="row col-12 q-mt-sm justify-center no-wrap" >
                    <div class="col-9 " style="margin : 0 1px">
                        <q-btn @click="append('0')"  color="dark" label="0" style="width : 100%"/>
                    </div>
                    <div class="col-3 " style="margin : 0 1px">
                        <q-btn @click="dot"  color="dark" label="." style="width : 100%"/>
                    </div>
                </div>
                
            </q-card-section>
        </q-card-section>
      </q-card>
</template>

<script>
export default {

    data() {

        return {

            logList: "",

            current: "",

            answer: "",

            reset : false,

            operatorClicked: true
        };
    },

    methods: {

        append(number) {

            if (this.operatorClicked) {

                this.current = "";

                this.operatorClicked = false;
            }

            this.current += `${number}`;

            this.answer += `${number}`;
        },

        addtoLog(operator) {

            if (this.operatorClicked == false) {

                // this.logList += `${this.answer} ${operator} `;

                this.answer += `${operator}`;

                this.current = "";

                this.operatorClicked = true;
            }
        },

    
        clear() {

            this.current = "";

            this.answer = "";

            this.logList = "";

            this.operatorClicked = false;

        },

        percent() {

            if (this.answer != "") {

                this.answer = `${parseFloat(this.answer) / 100}`;

            }
        },

        dot() {
            
            if (this.current.indexOf(".") === -1) {

                this.append(".");

            }
        },

        divide() {

            this.addtoLog("/");

        },

        times() {

            this.addtoLog("*");

        },
        minus() {

            this.addtoLog("-");

        },

        plus() {

            this.addtoLog("+");

        },

        equal() {

            if (this.operatorClicked == false) {

                    this.answer = eval(this.answer);

                    this.reset = true;

            }

            else {
                
                this.answer = "???";
            }
        }
}
    
}
</script>