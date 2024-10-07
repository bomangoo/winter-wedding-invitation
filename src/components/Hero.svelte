<script lang="ts">
    import { onMount } from 'svelte';
    import TreeAnimation from './TreeAnimation.svelte';

    let dDayMessage = '';

    function dDayCount() {
        const targetDate = new Date('2025-01-18');
        const now = new Date();
        const timeDiff = targetDate.getTime() - now.getTime();
        const dayDiff = Math.ceil(timeDiff / (1000 * 60 * 60 * 24));

        if (dayDiff > 0) {
            dDayMessage = `D-${dayDiff}`;
        } else if (dayDiff === 0) {
            dDayMessage = '오늘이 D-Day입니다!';
        } else {
            dDayMessage = `D+${Math.abs(dayDiff)}`;
        }
    }

    onMount(() => {
        dDayCount();
    });
</script>

<div class="hero-area">
    <section class="wrapper">
        <div class="hero-top">
            <TreeAnimation />
            <h1>WEDDING DAY</h1>
            {#if dDayMessage}
                <p>{dDayMessage}</p>
            {/if}
            <a
                class="calendar_link"
                href="https://www.google.com/calendar/render?action=TEMPLATE&text=%EC%9A%A9%EC%97%B0%EB%B3%B4%EB%AF%B8%EA%B2%B0%ED%98%BC%EC%8B%9D&dates=20250118T030000Z/20250118T040000Z&details=%EA%B9%80%EC%9B%90%EC%A2%85%20%EA%B9%80%EB%82%A8%ED%9D%AC%20%EC%95%84%EB%93%A4%20%EA%B9%80%EC%9A%A9%EC%97%B0,%20%EC%84%B1%EC%9E%84%EC%8B%9D%20%EB%B0%95%EB%B3%91%EC%9D%B8%20%EB%94%B8%20%EC%84%B1%EB%B3%B4%EB%AF%B8%20%EA%B2%B0%ED%98%BC%EC%8B%9D&location=%EA%B6%8C%EC%84%A0%EB%8F%99%EC%84%B1%EB%8B%B9&sf=true&output=xml"
                >캘린더에 저장하기</a
            >
        </div>
        <div class="hero-image">
            <img src="/public/img/main-hero.webp" alt="용연이와 보미" loading="lazy" />
        </div>

        <div class="hero-info">
            <h2>김용연 <img src="/public/img/couple-cookie.png" alt="커플 쿠키" /> 성보미</h2>
            <p>2025년 1월 18일 토요일 12시</p>
            <p>수원 권선동 성당</p>
        </div>
    </section>
</div>

<style>
    .hero-area {
        padding: 1.5rem;
    }
    .hero-top {
        padding: 0.5rem 0;
        text-align: center;
    }
    .hero-top h1 {
        font-size: 0.7rem;
        letter-spacing: 3px;
        color: red;
        opacity: 0.5;
    }
    .hero-top p {
        padding-bottom: 0.3rem;
        font-size: 1.3rem;
        color: #666;
    }
    .calendar_link {
        font-size: 0.8rem;
        color: #888;
    }
    .hero-image {
        position: relative;
        padding-top: calc(525 / 350 * 100%);
        background-color: #999;
    }
    .hero-image img {
        position: absolute;
        top: 0;
        left: 0;
    }
    .hero-info {
        padding: 1rem 0;
    }
    .hero-info > h2 {
        padding: 0 0 0.3rem 0.2rem;
        letter-spacing: 0.4rem;
        font-size: 1.4rem;
        color: #958585;
        text-align: center;
    }
    .hero-info > h2 img {
        display: inline-block;
        width: 15%;
        margin-bottom: -0.5rem;
    }
    .hero-info p {
        padding-bottom: 0.2rem;
        font-size: 1.1rem;
        font-weight: 500;
        color: #656565;
    }
</style>
