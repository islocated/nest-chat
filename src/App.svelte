<script>

	import {tick} from 'svelte'

	import io from 'socket.io-client'

	import MessageList from './MessageList.svelte'
	import MessageBar from './MessageBar.svelte'

	const socket = io("http://localhost:8000");

	let messages = [];
	let username = 'UserName';

</script>

<style>
	.messages {
        display: flex;
		flex-flow: column;
		height: 100vh;
    }
</style>



<main>
	<div class="messages">
		<MessageList {socket} {messages} />
		<MessageBar {socket} {username} />
	</div>
</main>