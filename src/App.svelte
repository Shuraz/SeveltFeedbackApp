<script>
import FeedbackForm from "./components/FeedbackForm.svelte";

	import FeedbackList from "./components/FeedbackList.svelte";
	import FeedbackStat from "./components/FeedbackStat.svelte"
let feedback =[
		{
			id:1,
			rating:10,
			text:'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit facere recusandae sit soluta tempora. Fuga libero dolorem aspernatur earum molestiae.'
		},
		{
			id:2,
			rating:8,
			text:'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit facere recusandae sit soluta tempora. Fuga libero dolorem aspernatur earum molestiae.'
		},
		{
			id:3,
			rating:9,
			text:'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Impedit facere recusandae sit soluta tempora. Fuga libero dolorem aspernatur earum molestiae.'
		}
	]
	$:count =feedback.length
	$:average= feedback.reduce((a,{rating})=>a+rating,0)/feedback.length
	
	const deleteFeedback=(e)=>{
		const itemId=e.detail;
		console.log(itemId)
		feedback=feedback.filter(item => item.id != itemId)
	}
	const handleNewFeedback=(e)=>{
		// console.log(e.detail)
		 const new_feedback=e.detail;
		feedback=[new_feedback,...feedback]
	}
</script>

<main class="container">
	<FeedbackForm on:create-newfeedback={handleNewFeedback}/>
<FeedbackStat {count} {average}/>
<FeedbackList feedback={feedback} on:delete-feedback={deleteFeedback}/>
</main>