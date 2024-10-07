<script lang="ts">
    const currentLink = window.location.href;

    function kakaoShare() {
        Kakao.Link.sendScrap({
            requestUrl: currentLink,
            templateId: 112935,
        });
    }

    function linkShare() {
        window.navigator.clipboard.writeText(currentLink).then(() => {
            alert('청첩장 링크가 복사되었습니다.');
        });
    }
</script>

<div class="share-area">
    <div>
        <button type="button" on:click={kakaoShare}>
            <img src="/public/img/kakao-icon.png" alt="카카오톡으로 공유하기" />
            <p>카카오톡 공유</p>
        </button>
        <button type="button" on:click={linkShare}>
            <img src="/public/img/link-share-icon.png" alt="링크 복사하기" />
            <p>링크 복사</p>
        </button>
    </div>
</div>

<style>
    .share-area {
        padding: 0.3rem 1.5rem 1.2rem;
        background-color: #fdf6f6;
    }
    .share-area > div {
        display: flex;
        justify-content: center;
        gap: 1rem;
    }
    .share-area > div > button {
        display: flex;
        flex-direction: column;
        width: 6rem;
    }
    .share-area > div > button img {
        padding: 1rem 1rem 0;
    }
    .share-area > div > button:last-of-type img {
        padding: 1.3rem 1.5rem 0.7rem;
    }
    .share-area > div > button > p {
        width: 100%;
        text-align: center;
        color: #666;
        font-size: 0.8rem;
    }
</style>
