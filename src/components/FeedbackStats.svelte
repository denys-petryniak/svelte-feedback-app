<script>
  import { FeedbackStore } from "../stores";

  $: count = $FeedbackStore.length;
  $: average = $FeedbackStore.reduce((total, { rating }) => total + rating, 0) / count;
  $: getAverage = isNaN(average) ? 0 : average;
</script>

<div class="feedback-stats">
  <h4>{count} Reviews</h4>
  <h4>Rating Average: {getAverage}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
