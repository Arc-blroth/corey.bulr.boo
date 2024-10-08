<script>
  let bits = 32
  let num = 0
  $: output = num > (2 ** (bits - 1))
    ? "number too big"
    : Number((~-num & ((1 << bits) - 1)) + 1).toString(2).padStart(bits, "0")
</script>

<style>
  .calc {
    display: flex;
    flex-direction: column;
    width: min(600px, 80vw);
    height: 100%;
    place-content: center center;
    text-align: center;
    margin: auto;
    font-family: sans-serif;
    font-size: 24px;

    & input {
      font-size: 24px;
    }
  }
</style>

<div class="calc">
  <div>
    <label for="bits"># Bits: </label>
    <input type="number" id="bits" bind:value={bits}>
  </div>
  <div>
    <label for="num">Number: </label>
    <input type="number" id="num" bind:value={num}>
  </div>
  <p>Output: <code>{output}</code></p>
</div>
