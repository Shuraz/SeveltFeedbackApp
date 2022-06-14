<script>
    export let count;
    export let average;
</script>

<div class="feedback-stat">
    <h4>{count} Reviews</h4>
    <h4>Rating Average: {average}</h4>
</div>

<style>
    .feedback-stat{
        display: flex;
        justify-content: space-between;
        justify-items: center;
    }
</style>