<script>
  let text = "The book is on the table";
  let htmlText = text;

  let start = 5;
  let range = 3;
  $: end = start + range;
  $: rangeMax = text.length - range;

  $: {
    start = start < 0 ? 0 : start;
    start = start > text.length - range ? text.length - range : start;
    end = end > text.length ? text.length : start + range;

    htmlText = [
      text.slice(0, start),
      `<b>`,
      text.slice(start, end).toUpperCase(),
      `</b>`,
      text.slice(end)
    ].join("");
  }
</script>

<p style="font-size: 2rem;">
  {@html htmlText}
</p>
<input type="range" bind:value={range} min="1" max={text.length} />
<input type="range" bind:value={start} min="0" max={rangeMax} />
