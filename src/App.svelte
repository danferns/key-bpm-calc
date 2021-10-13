<script>
    function round(value) {
        return Math.round(value * 100) / 100;
    }
    let inputBPM = 128;
    let outputBPM = 128;
    $: pitchShift = round(Math.log2(outputBPM / inputBPM) * 12);
</script>

<main>
    <input type="number" bind:value={inputBPM} placeholder="Original BPM" />
    <input type="number" bind:value={outputBPM} placeholder="Stretched BPM" />
    {#if pitchShift}
        <p>
            The pitch will shift {pitchShift > 0 ? "up" : "down"} by
            {Math.abs(pitchShift)}
            {Math.abs(pitchShift) === 1 ? "semitone" : "semitones"}.
        </p>
    {/if}
</main>

<style>
    main {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
</style>
