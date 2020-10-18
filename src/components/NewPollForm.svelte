<script>
    import PollStore from '../stores/pollStore.js';
    import { createEventDispatcher } from 'svelte';
    import Button from '../shared/Button.svelte';

    const dispatch = createEventDispatcher();

    let fields = {question:'', answerA:'', answerB:''};
    let errors = {question:'', answerA:'', answerB:''};
    let valid = false;



    function handleSubmit() {
        valid = true
        // check question input
        if(fields.question.trim().length < 5) {
            valid = false;
            errors.question = 'Question must be at least 5 chars long'
        }else{
            errors.question = ''
        }
        // check answer A input
        if(fields.answerA.trim().length < 1) {
            valid = false;
            errors.answerA = 'Empty field'
        }else{
            errors.answerA = ''
        }
        // check answer B input
        if(fields.answerB.trim().length < 1) {
            valid = false;
            errors.answerB = 'Empty field'
        }else{
            errors.answerB = ''
        }
        // if no errors
        if(valid){
             let poll = {...fields, id: Math.random(), votesA: 0, votesB: 0}
             PollStore.update(currentPolls => {
                 return [poll, ...currentPolls]
             });
             dispatch('addPoll');
        }
    };


</script>


<form on:submit|preventDefault={handleSubmit}>
    <div class="input-field">
        <label for="question">Poll Question: </label>
        <input type="text" id="question" bind:value={fields.question}>
        <div class="error">{errors.question}</div>
    </div>
     <div class="input-field">
        <label for="answerA">Answer A value: </label>
        <input type="text" id="answerA" bind:value={fields.answerA}>
        <div class="error">{errors.answerA}</div>
    </div>
     <div class="input-field">
        <label for="answerB">Answer A value: </label>
        <input type="text" id="answerB" bind:value={fields.answerB}>
        <div class="error">{errors.answerB}</div>
    </div>
    <Button> Submit </Button>
</form>


<style>
    form {
        width: 400px;
        text-align: center;
        margin: 0 auto;
        padding: 15px;
        border-radius: 50px;
        background: linear-gradient(145deg, #d9dde0, #ffffff);
        box-shadow:  9px 9px 18px #cdd1d4, 
                    -9px -9px 18px #ffffff;
    }
    .input-field {
        margin: 18px auto;
    }
    input {
        width: 100%;
        border-radius: 10px;
    }
    label {
        margin: 10px auto;
        text-align: left;
    }
    .error {
        font-weight: bold;
        color: crimson;
    }
</style>