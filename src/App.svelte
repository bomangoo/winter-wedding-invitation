<script lang="ts">
    import Hero from './components/Hero.svelte'
    import Snow from './components/Snow.svelte'
    import Introduce from './components/Introduce.svelte'
    import Calendar from './components/Calendar.svelte';
    import Gallery from './components/Gallery.svelte';
    import Map from './components/Map.svelte';
    import Bank from './components/Bank.svelte';

    let volumeOn = false;

    function handleVolume() {
        const music = document.getElementById('main-bg') as HTMLAudioElement;
        if (!music) return;
        if (!volumeOn) {
            music.play();
            console.log('play');
            volumeOn = true;
        } else {
            music.pause();
            volumeOn = false;
        }
    }
</script>

<main>
    <button type="button" on:click={handleVolume}>
        <img src="/public/img/volume-on.png" style="opacity: {volumeOn ? 1 : 0}; transition: opacity 0.5s ease;" alt="배경 음악 켜기" />
        <img src="/public/img/volume-off.png" style="opacity: {volumeOn ? 0 : 1}; transition: opacity 0.5s ease;" alt="배경 음악 끄기" />
    </button>
    <Snow />
    <Hero />
    <Introduce />
    <Calendar />
    <Gallery />
    <Map />
    <Bank />
    <div>
        <h2>미리 감사드립니다</h2>
        <p>소중한 인연 모시기 위해 정성으로 자리를 마련했습니다.</p>
    </div>

    <audio id="main-bg" preload="none" loop src="/public/music/christmas-bg.mp3" />
</main>
<div id='snowArea'></div>

<style>
    button {
        position: fixed;
        width: 100%;
        z-index: 10;
    }
    button > img {
        position: absolute;
        top: 1rem;
        right: 1rem;
        width: 2rem;
        height: 2rem;
    }
    main {
        width: 100%;
        max-width: 36rem;
        margin: 0 auto;
        background-color: #fff;
    }

    #snowArea {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
    }
</style>
