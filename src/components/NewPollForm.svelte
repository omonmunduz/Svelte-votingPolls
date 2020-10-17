<script>
    import Button from '../shared/Button.svelte';
    let fields = {question:'', answerA:'', answerB:''}

    function handleSubmit() {
        console.log(fields)
    }
</script>


<form on:submit|preventDefault={handleSubmit}>
    <div class="input-field">
        <label for="question">Poll Question: </label>
        <input type="text" id="question" bind:value={fields.question}>
    </div>
     <div class="input-field">
        <label for="answerA">Answer A value: </label>
        <input type="text" id="answerA" bind:value={fields.answerA}>
    </div>
     <div class="input-field">
        <label for="answerB">Answer A value: </label>
        <input type="text" id="answerB" bind:value={fields.answerB}>
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
</style>