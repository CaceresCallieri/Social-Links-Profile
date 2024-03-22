<script>
    export let href = '';
    export let text = '';

    import { onMount } from 'svelte'

    onMount(() => {
        setTimeout(() => {
            triggerHackerEffect(text)
        }, 100) // Delay effect until after the page is loaded and the animation completed
    })
    
    // HACKER EFFECT ANIMATION
    const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    let interval   
    let chars

    function triggerHackerEffect(string) {
        text = string
        chars = text.split('')
        let iterations = 0;

        if (interval) {
            clearInterval(interval);
        }

        const intervalTime = 200 / text.length; // Normalized time so that the effect is the same for all texts, no matter the length

        interval = setInterval(() => {
            chars = chars.map((char, index) => {
                if (index < iterations) {
                    return text[index];
                }

                return letters[Math.floor(Math.random() * 26)];
            });

            if (iterations >= text.length) clearInterval(interval);

            iterations += 1 / 4;
        }, intervalTime);
    }
</script>

<a on:mouseenter={() => triggerHackerEffect(text)} {href} target="_blank">
    {(chars) ? chars.join("") : text}
</a>