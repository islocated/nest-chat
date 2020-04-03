<script>
    export let socket;
    export let username;

    let msg = '';

    function sendMessage() {
		const message = {
            text: msg,
            time: new Date().toLocaleString(),
            username: username
        }
        socket.emit('chat message', message); 
        msg = '';
	}

</script>


<style>
    .message-bar {
        display: flex;
        flex-flow: row;
        width: 100%;
    }

    .message-input {
        flex: 1;
        color: #ccc;
        border: none;
        border-right: 1px solid #26292f;
        padding: 10px;
        background-color: #40444b;
        font-family: "Tahoma";
        font-size: 16px;
        width: 100%;
    }

    .message-button {
        flex: 0;
        color: #ccc;
        border: none;
        padding: 10px;
        background-color: #40444b;
        font-family: "Tahoma";
        font-size: 16px;
        width: 100%;
    }

    .message-button:disabled{
        color: #777;
    }
</style>

<div class="message-bar">
	<form on:submit|preventDefault={sendMessage} class="message-bar">
		<input class="message-input" autocomplete="off" bind:value={msg} placeholder="Type message here"/>
		<button class="message-button">Send</button>
	</form>
</div>