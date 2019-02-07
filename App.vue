<template>
    <main>
        <div class="display">
            123
        </div>
        <div class="buttons">
            <div class="button-row" v-for="row in buttonRows">
                <div class="button" v-for="button in row">
                    {{ button.text }}
                </div>
            </div>
        </div>
    </main>
</template>

<script>
    export default {
        data: () => ({
            buttonRows: [
                [{
                    text: 'AC',
                    type: 'operator'
                }, {
                    text: '+/-',
                    type: 'operator'
                }, {
                    text: '%',
                    type: 'operator'
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
                    type: 'number'
                }, {
                    text: '=',
                    type: 'operator'
                }]
            ]
        })
    }
</script>

<style scoped>

</style>