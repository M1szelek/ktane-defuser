<template>
    <div>
        {{ currentQuestion }}
    </div>
</template>

<script>
    export default {
        name: "Wires",
        data(){
            return {
                decisions: '3',
                decisionTree: {
                    question: 'How many wires?',
                    answers: {
                        '3': {
                            question: 'No red wires?',
                            answers: {
                                'yes': {
                                    solution: 'Cut the second wire'
                                },
                                'no': {
                                    question: 'Last wire is white?',
                                    answers: {
                                        'yes': {
                                            solution: 'Cut the last wire'
                                        },
                                        'no': {
                                            question: 'More than one blue wire?',
                                            answers: {
                                                'yes': {
                                                    solution: 'Cut the last blue wire'
                                                },
                                                'no': {
                                                    solution: 'Cut the last wire'
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
                    console.log(currentAnswers);
                    let result = currentAnswers[decisions[0]].question;

                    console.log(result);

                    decisions.forEach((decision) => {
                        if(currentAnswers.solution){
                            return currentAnswers.solution
                        }else{
                            currentAnswers = currentAnswers.answers[decision];
                            result = currentAnswers.question;
                        }
                    });

                    return result;
                }

            },
            answers(){
                return Object.keys(this.descisionTree.answers);
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