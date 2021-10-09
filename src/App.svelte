<script>
    function calculatePitchShift(ratio) {
        return Math.log2(ratio) * 12;
    }
    let inputBPM = 128;
    let outputBPM = 128;
    $: pitchShift = Math.round(calculatePitchShift(outputBPM / inputBPM) * 100) / 100;
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
