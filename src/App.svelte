<script>

	import {tick} from 'svelte'

	import io from 'socket.io-client'

	import Video from './Video.svelte'
	import MessageList from './MessageList.svelte'
	import MessageBar from './MessageBar.svelte'

	const socket = io("http://localhost:8000");

	let messages = [];
	let username = 'UserName';

</script>

<style>
	.app {
        display: flex;
		flex-flow: row;
		height: 100vh;
    }
	.video {
		display: flex;
		flex-flow: column;
		width: 50%;
		
        background-color: #282828;
	}
	.messages {
        display: flex;
		flex-flow: column;
		width: 50%;
    }
</style>



<main>
	<div class="app">
		<div class="video">
			<Video />
		</div>
		<div class="messages">
			<MessageList {socket} {messages} />
			<MessageBar {socket} {username} />
		</div>
	</div>
</main>