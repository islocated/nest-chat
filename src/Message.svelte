<script>
    export let message;
</script>

<style>
    .message {
        display: flex;
        flex-flow: row;
    }

    .message:hover {
        background-color: #2f3136;
    }

    .message-time {
        font-size: .70em;
        color: #aaa;
    }

    .message-user-name {
        font-size: .70em;
        color: #aaa;
    }

    .message-text {
        flex-grow: 1;
        padding-left: 10px;
    }

    img {
        width: 40px;
        height: 40px;
        margin-top: 7px;
    }
</style>

<div class="message">
    <img src="#" alt=""/>
    <div class="message-text">
        <span class="message-user-name">{message.username}</span> <span class="message-time">{message.time}</span><br/>
        {message.text}
    </div>
</div>