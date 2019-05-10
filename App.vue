<template>
    <main class="calculator">
        <div class="display">
            {{display}}
        </div>
        <div class="buttons">
            <div class="button-row" v-for="row in buttonRows" :key="row.index">
                <div 
                    @click="buttonClick(button)"
                    :style="button.style"
                    :class="{ operator: button.type == 'operator'}"
                    class="button" 
                    v-for="button in row" 
                    :key="button.text">
                        {{ button.text }}
                </div>
            </div>
        </div>
    </main>
</template>

<script>
    export default {
        methods: {
            buttonClick(button) {
                if(button.type == 'number') {
                    if(this.previousValue === null) {
                        this.previousValue = Number(this.display)
                        this.display = ''
                    }
                    if(button.text == '.' && this.display.includes('.')) return
                    this.display += button.text
                } else if(button.text == 'AC') {
                    this.display = ''
                } else if(button.text == '+/-') {
                    this.display *= -1
                } else if(button.text == '=') {
                    this.display = this.operations[this.currentOperator](+this.previousValue, +this.display)
                } else if(button.type == 'operator') {
                    this.previousValue = null
                    this.currentOperator = button.text
                }
            }
        },
        data: () => ({
            display: '',
            previousValue: null,
            currentOperator: '',
            operations: {
                '÷' : (a,b) => a / b,
                '×' : (a,b) => a * b,
                '-' : (a,b) => a - b,
                '+' : (a,b) => a + b
            },
            buttonRows: [
                [{
                    text: 'AC',
                    type: 'special'
                }, {
                    text: '+/-',
                    type: 'special'
                }, {
                    text: '%',
                    type: 'special'
                }, {
                    text: '÷',
                    type: 'operator'
                }],
                [{
                    text: '7',
                    type: 'number'
                }, {
                    text: '8',
                    type: 'number'
                }, {
                    text: '9',
                    type: 'number'
                }, {
                    text: '×',
                    type: 'operator'
                }],
                [{
                    text: '4',
                    type: 'number'
                }, {
                    text: '5',
                    type: 'number'
                }, {
                    text: '6',
                    type: 'number'
                }, {
                    text: '-',
                    type: 'operator'
                }],
                [{
                    text: '1',
                    type: 'number'
                }, {
                    text: '2',
                    type: 'number'
                }, {
                    text: '3',
                    type: 'number'
                }, {
                    text: '+',
                    type: 'operator'
                }],
                [{
                    text: '0',
                    type: 'number'
                }, {
                    text: '.',
                    type: 'number',
                    style: 'flex-basis: calc(100%/2)'
                }, {
                    text: '=',
                    type: 'operator',
                    style: 'flex-basis: calc(100%/2)'
                }]
            ]
        })
    }
</script>

<style  lang='css'>
body {
    width: 100vw;
    height: 100vh;
    font-size: 4vw;
    display: flex;
    justify-content: center;
    align-items: center;
}
    .calculator {
        width: 50vw;
        height: 70vh;
        font-family: sans-serif;
        border-radius: 5px;
        overflow: hidden;
        border: 0.5px solid #5D5B5D;
    }
    .display {
        height: 10vh;;
        background: #5D5B5D;
        text-align: right;
        font-size: 1.5em;
        color: white;
    }
    .buttons {
        height: 60vh;
        text-align: center;
    }
    .button-row {
        height: 20%;
        width: 100%;
        display: flex;
        justify-content: space-around;
    }
    .button {
        display: inline-block;
        outline: 0.5px solid #5D5B5D;
        width: 100%;
        /* padding: 0.4em; */
        background: #838183;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .operator {
        color: white;
        background: #FF9A00;
    }
    .button:active {
        background: #CDCCCD
    }
</style>