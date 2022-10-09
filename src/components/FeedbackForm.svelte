<script>
  import Card from "./Card.svelte";
  import Button from "./Button.svelte";
  import RatingSelect from "./RatingSelect.svelte";

  let text = "";
  let rating = 10;
  let btnDisabled = true;
  let min = 10;
  let message;

  const handleInput = () => {
    if (text.trim().length <= min) {
      message = `Text must be at least ${min} characters`;
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  };

  const handleSelect = event => (rating = event.detail);
</script>

<form>
  <Card>
    <header>
      <h2>How would you rate your service with us?</h2>
    </header>
    <form>
      <RatingSelect on:rating-select={handleSelect} />
      <div class="input-group">
        <input
          type="text"
          bind:value={text}
          on:input={handleInput}
          placeholder="Tell us something that keeps you coming back"
        />
        <Button type="submit" disabled={btnDisabled}>Send</Button>
      </div>
      {#if message}
        <div class="message">
          {message}
        </div>
      {/if}
    </form>
  </Card>
</form>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }

  .input-group {
    display: flex;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    padding-right: 18px;
    border: none;
    font-size: 16px;
  }

  input:focus {
    outline: none;
  }

  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
