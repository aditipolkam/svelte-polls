<script>
    import Button from '../shared/Button.svelte';
    let fields = { question: '', answerA: '', answerB: ''};
    let error = { question: '', answerA: '', answerB: ''};
    let valid = false;

    const submitHandler = () =>{
        valid = true;

        //validate question
        if (fields.question.trim().length < 5){
            valid = false;
            error.question = 'Question must be atleast 5 charcters long.';
        }else{
            error.question = '';
        }

        //validate answerA
        if (fields.answerA.trim().length < 1){
            valid = false;
            error.answerA = 'Answer A cannot be empty.';
        }else{
            error.answerA = '';
        }

        //validate answerB
        if (fields.answerB.trim().length < 1){
            valid = false;
            error.answerB = 'Answer B cannot be empty.';
        }else{
            error.answerB = '';
        }
        //add new poll
    if(valid){
        console.log('valid', fields);
    }
}

    
</script>

<form on:submit|preventDefault = {submitHandler}>
    <div class="form-field">
        <label for="question">Poll Question</label>
        <input type="text" id="question" bind:value={fields.question}>
        <div class="error">{error.question}</div>
    </div>
    <div class="form-field">
        <label for="answer-a">Answer A</label>
        <input type="text" id="answer-a" bind:value={fields.answerA}>
        <div class="error">{error.answerA}</div>
    </div>
    <div class="form-field">
        <label for="answer-b">Answer b</label>
        <input type="text" id="answer-b" bind:value={fields.answerB}>
        <div class="error">{error.answerB}</div>
    </div>
    <Button type="primary" flat={true} inverse={true}>Add Poll</Button>
</form>

<style>
    form{
        width: 400px;
        margin : 0 auto;
        text-align: center;

    }
    .form-field{
        margin : 18px, auto;
    }
    input{
        width : 100%;
        border-radius: 6px;
    }
    label{
        margin: 18px auto;
        text-align: left;
    }
    .error{
        font-weight: bold;
        font-size: 12px;
        color: #d91b42;
    }
</style>