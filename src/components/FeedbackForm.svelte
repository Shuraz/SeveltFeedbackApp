<script>
    import Button from "./Button.svelte";
    import RatingSelect from "./RatingSelect.svelte"
    import Card from "../components/ui/Card.svelte"
    import {createEventDispatcher} from 'svelte'
    import {v4 as uuidv4} from 'uuid'

    const dispatch = createEventDispatcher();
    let text=''
    let rating=10;
    let btnDisabled=true
    let min=10;
    let message;
    const handleInput=()=>{
        if(text.trim().length<=min){
            message=`Text must be at least ${min} character.`
            btnDisabled=true;
        }
        else{
            message=null;
            btnDisabled=false
        }
    }
    const handleSelect=(e)=>{
        rating =e.detail;
        // console.log(rating)
    }
    const handleSubmit=()=>{
        if(text.trim().length>min){
          const  newFeedback={
                id: uuidv4,
                rating:+rating,
                text
            }
            // console.log(newFeedback)
            dispatch('create-newfeedback',newFeedback)
            text=''
        }
    }
</script>
<Card>
    <header>
        <h2>How would you rate your service with us?</h2>
    </header>
    <form on:submit|preventDefault={handleSubmit}>
        <div>
            <RatingSelect on:rating-select={handleSelect}/>
        </div>
        <div class="input-group">
            <input type="text" on:input={handleInput} bind:value={text} placeholder="Tell us something that keep you coming back !!!">
            <Button disabled={btnDisabled} type="submit">Send</Button>
        </div>
        {#if message}
        <div class="message">{message}</div>
        {/if}
    </form>
</Card>
<style>
    header{
        max-width: 400px;
        margin: auto;
    }
    .input-group{
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
    }
    input{
        flex-grow: 2;
        border: none;
        font-size: 16px;
    }
    input:focus{
        outline: none;
    }
    .message{
        text-align: center;
        color:red;
    }
</style>