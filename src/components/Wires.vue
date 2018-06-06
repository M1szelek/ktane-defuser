<template>
    <div>
        {{ currentQuestion }}
        <button v-for="(answer,key) in currentAnswers">{{ key }}</button>
    </div>
</template>

<script>
    export default {
        name: "Wires",
        data(){
            return {
                decisions: '3,no,yes',
                currentAnswers: [],
                decisionTree: {
                    question: 'How many wires?',
                    answers: {
                        '3': {
                            question: 'No red wires?',
                            answers: {
                                'yes': {
                                    question: 'Cut the second wire'
                                },
                                'no': {
                                    question: 'Last wire is white?',
                                    answers: {
                                        'yes': {
                                            question: 'Cut the last wire'
                                        },
                                        'no': {
                                            question: 'More than one blue wire?',
                                            answers: {
                                                'yes': {
                                                    question: 'Cut the last blue wire'
                                                },
                                                'no': {
                                                    question: 'Cut the last wire'
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        },
                        '4': {

                        },
                        '5': {

                        },
                        '6': {

                        }
                    }
                }
            }
        },
        computed:{
            currentQuestion(){
                if(!this.decisions.length){
                    return this.decisionTree.question;
                }else{
                    let decisions = this.decisions.split(',');
                    let currentAnswers = this.decisionTree.answers;
                    let result = currentAnswers[decisions[0]].question;
                    currentAnswers = currentAnswers[decisions[0]].answers;
                    this.currentAnswers = currentAnswers;
                    decisions.shift();
                    decisions.forEach((decision) => {
                            result = currentAnswers[decision].question;
                            currentAnswers = currentAnswers[decision].answers;
                            this.currentAnswers = currentAnswers;
                    });
                    return result;
                }

            }
        },
        methods:{
            fetchQuestion(){

            }
        }
    }
</script>

<style scoped>

</style>