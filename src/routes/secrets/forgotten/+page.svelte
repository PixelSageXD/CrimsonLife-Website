<script>
    let currentBlock = $state(1);
    let displayedText = $state('');
    let isTyping = $state(false);

    const blocks = {
        1: `'Well done - you've made it to the end!'
        
        'The select few who got to our secrets the earliest learned the most about our plans.'
        'If you were a little after them, you didn't get the full picture, but you still know more than most.'
        'Anyone after that: tough luck. You'll just have to wait and see.'
        
        'All we can do is thank you again for your attention.'
        'This has helped greatly towards our progress.'`,

        2: `'Now that our preparations are almost complete...'
        
        'We're almost ready to show you who we've chosen as our subjects.'
        
        'Let's say... September 28th.'
        'Maybe earlier if our progress continues at this rate.'
        
        'Good luck. We'll see you in Crimson Life.'`,
    };

    async function typeText(text) {
        isTyping = true;
        let result = '';

        for (let index = 0; index < text.length; index++) {
            result += text[index];
            displayedText = result;
            await new Promise(resolve => setTimeout(resolve, 40));
        }

        isTyping = false;
    }

    function nextBlock() {
        if (isTyping) return;

        currentBlock++;
        typeText(blocks[currentBlock]);
    }

    $effect(() => {
        typeText(blocks[currentBlock]);
    });
</script>

<div class="text-block">
    <div class="text-container-forgotten">
        <p>{displayedText}</p>
    </div>

    {#if !isTyping && currentBlock === 1}
        <button type="button" class="btn" onclick={nextBlock}>
            CONTINUE
        </button>
    {/if}
</div>

<style>
    .text-block {
        max-width: 600px;
        margin: 75px auto;
        text-align: center;
    }

    .text-container-forgotten {
        min-height: 400px;
        white-space: pre-line;
        font-family: 'Minecraft-Italic', sans-serif;
        color: #ff5555
    }

    .btn {
        font-family: 'Minecraft-Bold', sans-serif;
    }
</style>