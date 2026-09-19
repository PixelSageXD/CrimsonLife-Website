<script>
    let currentBlock = $state(1);
    let displayedText = $state('');
    let isTyping = $state(false);

    const blocks = {
        1: `You have reached the first contact. Welcome!
        To introduce what's happening here:

        This is an Alternate Reality Game (ARG). If you're aware of what that is, good! You'll understand a bit about what's going on here.
        If not, don't worry - this is beginner friendly, and you are urged to take part either way.

        To put it simply, you'll be using this website along with other aspects of the series to find clues to where you have to go next.
        Usually, they'll be hidden by a sort of extra puzzle, such as binary characters or a YouTube video link.
        (These examples may or may not be a part of this ARG, no confirmation.)`,

        2: `Some guidelines for taking part:
        
        Keep everything you find inside the Crimson Life Discord server or within DMs with Pix. You are encouraged to share your findings, though!
        Once this page is first reported, a channel will be created for everyone taking part to share what they find.

        Much of the information given as a reward in this puzzle will be limited to a certain number of people.
        This means that if you find any information about the series in a secret page, DM Pix to let them know, with a screenshot if possible.
        Once the DM is acknowledged, you can share info to do with how to find the page, but not what you learned there.
        
        Regardless: have fun!`,

        3: `'Ah, so you've found us.'
        
        'Don't worry if you don't know who we are, you'll be seeing much more of us very soon.'
        'We're incredibly grateful for your interest in this little game.'
        
        'We're almost ready to finally unravel all that we've been planning...'
        
        '...so we thought it's about time you learn a little more.'
        
        'But we're not just going to tell you.. it won't be THAT easy.'
        'That would be boring. We at least want to have a little fun too.'`,

        4: `'So, onto your assignment:'
        
        'We've scattered a few clues around as to where we'll be hiding next.'
        'We won't leave you completely in the dark, but you'll need to do a little searching.'

        'Once you find what you're looking for, there's an extra step - you need to find out what it means.
        After that, come back here. Not exactly here, but.. relatively close.'
        
        'Because we're so kind, here's another hint:
        Which elements and places are the most important to Crimson Life?'
        
        'This will be enough to get you started.'
        'We're looking forward to seeing you again soon...!'`,

        5: `Got a hint?
        
        This isn't the page where you need to be.
        Think about it again: 'not exactly here, but relatively close'.
        
        Good luck.`
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
    {#if currentBlock === 3 || currentBlock === 4}
        <div class="text-container-forgotten">
            <p>{displayedText}</p>
        </div>
    {:else}
        <div class="text-container">
            <p>{displayedText}</p>    
        </div>
    {/if}

    {#if !isTyping && currentBlock < 5}
        <button type="button" class="btn" onclick={nextBlock}>
            {currentBlock === 1 ? 'ACCEPT' : 'CONTINUE'}
        </button>
    {/if}
</div>

<style>
    .text-block {
        max-width: 600px;
        margin: 75px auto;
        text-align: center;
    }

    .text-container {
        min-height: 400px;
        white-space: pre-line;
        font-family: 'Minecraft-Regular', sans-serif;
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