<script>
  import { FeedbackStore } from "../stores";
  import { fade, scale } from "svelte/transition";
  import FeedbackItem from "./FeedbackItem.svelte";
  import FeedbackForm from "./FeedbackForm.svelte";

  let feedback = [];

  FeedbackStore.subscribe(data => (feedback = data));
</script>

{#each feedback as fb}
  <div in:scale out:fade={{ duration: 500 }}>
    <FeedbackItem item={fb} on:delete-feedback />
  </div>
{/each}
