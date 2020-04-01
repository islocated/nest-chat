<script>
    import {onMount} from 'svelte'
    import {tick} from 'svelte'
    
    import Message from './Message.svelte'

    export let socket;
    export let messages;
    
    let div;

	function scrollToEnd() {
		div.scrollTop = div.scrollHeight;
    }

	onMount(async () => {
		socket.on('chat message', async (msg) => {
			messages = [...messages, msg];

			await tick();
			scrollToEnd();
		})
	})

</script>

<style>
    .message-main {
        flex-grow: 1;
        overflow-y: auto;
        background-color: #36393f;
    }

    .message-main ul {
        padding: 10px;
        list-style-type: none;
    }

    .message-main li {
        margin-bottom: 10px;
        color: #ccc;
    }
</style>

<div class="message-main" bind:this={div}>
    {#if messages}
    <ul>
        {#each messages as message}
        <li>
            <Message {message} />
        </li>
        {/each}
    </ul>
    {/if}
</div>