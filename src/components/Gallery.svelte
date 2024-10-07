<script lang="ts">
    import { photos } from '../contents/photos';
    let currentSlide = 0;

    const imageLength = photos.length;
    let positionLeft = 0;

    const move = () => {
        positionLeft = currentSlide * 100;
    };

    const prev = () => {
        if (currentSlide === 0) return;
        currentSlide = currentSlide - 1;
        move();
    };

    const next = () => {
        if (currentSlide === imageLength - 1) return;
        currentSlide = currentSlide + 1;
        move();
    };

    const getIndex = (index: number) => {
        currentSlide = index;
        move();
    };
</script>

<div class="gallery-area">
    <h2>우리의 사계절</h2>

    <div class="gallery-container">
        <div class="slider" style="left: -{positionLeft}%;">
            {#each photos as img}
                <img src={img.src} alt={img.alt} />
            {/each}
        </div>
        <div class="arrow">
            <button on:click={prev} class={`prev ${currentSlide === 0 ? 'hide' : ''}`}>
                <img src="/public/img/prev.png" alt="이전 이미지" />
            </button>
            <button
                on:click={next}
                class={`next ${currentSlide === imageLength - 1 ? 'hide' : ''}`}
            >
                <img src="/public/img/next.png" alt="다음 이미지" />
            </button>
        </div>
        <div class="dot-pagination">
            {#each photos as img, i}
                <button
                    class={`${currentSlide === i ? 'active' : ''} ${img.alt}`}
                    on:click={() => getIndex(i)}
                />
            {/each}
        </div>
    </div>
</div>

<style>
    .gallery-area {
        padding: 4rem 0;
    }
    .gallery-area > h2 {
        padding: 0 1.5rem 0.8rem;
        font-size: 1.3rem;
        color: #555;
    }
    .gallery-container {
        position: relative;
        width: 100%;
        max-width: 640px;
        margin: 0 auto;
        overflow: hidden;
    }
    .slider {
        display: flex;
        position: relative;
        transition: left 0.5s;
        background-color: #eee;
    }
    .slider img {
        width: 100%;
        height: auto;
        object-fit: cover;
        flex-shrink: 0;
    }
    .prev,
    .next {
        transition: all 0.4s linear;
    }
    .prev.hide,
    .next.hide {
        opacity: 0;
        z-index: -1;
    }
    .arrow {
        display: flex;
        justify-content: space-between;
        align-items: center;
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
    }
    .arrow button {
        margin-bottom: 3rem;
        padding: 0.4rem 0.2rem;
        border: 0;
        cursor: pointer;
        background-color: #e5e5e569;
    }
    .arrow button img {
        width: 2.2rem;
    }
    .dot-pagination {
        position: relative;
        width: 100%;
        padding: 0.4rem 0;
        z-index: 10;
    }
    .dot-pagination button {
        width: 15px;
        height: 15px;
        margin: 0.2rem 0.4rem;
        padding: 0.2rem 0.4rem;
        border: 0;
        border-radius: 10px;
        background-color: #eee;
        text-align: center;
        cursor: pointer;
        opacity: 0.3;
        border: 1px solid transparent;
    }
    .dot-pagination .active {
        opacity: 1;
        border-color: #888;
    }
    .dot-pagination button.spring {
        background-color: #f3588e;
    }
    .dot-pagination button.summer {
        background-color: green;
    }
    .dot-pagination button.autumn {
        background-color: brown;
    }
    .dot-pagination button.winter {
        background-color: navy;
    }
</style>
