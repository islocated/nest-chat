<script>
    import {onMount} from 'svelte'

    let localStream;

    onMount(async () => {
        const stream = await navigator.mediaDevices.getUserMedia({
            audio: true,
            video: true
        })

        localStream.srcObject = stream;
    })


</script>


<style>
    video {
        height: 100vh;
    }
</style>

<video bind:this={localStream} autoplay playsinline controls/>
