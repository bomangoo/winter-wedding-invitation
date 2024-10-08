<script lang="ts">
    import { onMount } from 'svelte';

    let mapElement: HTMLDivElement;

    const latitude = 37.253158;
    const longitude = 127.039522;
    const naverMapLink = 'https://naver.me/xFpoOwe1';
    const weddingAddress = '경기 수원시 권선구 권선로 830';
    const tMapKey = import.meta.env.VITE_TMAP_KEY;

    onMount(() => {
        // naver map
        const clientId = import.meta.env.VITE_NAVER_MAP_CLIENT_ID;
        if (!clientId) return;
        const naverMapScript = document.createElement('script');
        naverMapScript.src = `https://openapi.map.naver.com/openapi/v3/maps.js?ncpClientId=${clientId}`;
        naverMapScript.async = true;
        document.head.appendChild(naverMapScript);

        naverMapScript.onload = () => {
            const mapOptions = {
                center: new naver.maps.LatLng(latitude, longitude),
                zoom: 16,
                draggable: false,
            };

            const map = new naver.maps.Map(mapElement, mapOptions);

            const marker = new naver.maps.Marker({
                position: new naver.maps.LatLng(latitude, longitude),
                map: map,
            });
        };

        // kakao navigation
        const kakaoKey = import.meta.env.VITE_KAKAO_JAVASCRIPT_KEY;
        Kakao.init(kakaoKey);
    });

    function onClickMap() {
        window.open(naverMapLink);
    }

    function copyAddress() {
        window.navigator.clipboard.writeText(weddingAddress).then(() => {
            alert('주소 복사 완료!');
        });
    }

    function kakaonavi() {
        Kakao.Navi.start({
            name: '천주교 권선동 성당',
            x: longitude,
            y: latitude,
            coordType: 'wgs84',
        });
    }
</script>

<div class="map-area">
    <h2>오시는 길</h2>
    <div class="map-info-wrapper">
        <div class="map-address">
            <img src="./img/church.png" alt="성당 건물" />
            <div>
                <h3>수원 권선동 성당</h3>
                <p>{weddingAddress}</p>
                <button type="button" on:click={copyAddress}>
                    <img src="./img/copy-icon.png" alt="주소 복사하기" />
                </button>
                <a href="tel:0312378845">031-237-8845</a>
            </div>
        </div>
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div id="map" bind:this={mapElement} on:click={onClickMap}></div>
        <div class="map-app-link">
            <button on:click={kakaonavi}>
                <img src="./img/kakaonavi-icon.png" alt="" />
                <p>카카오 내비</p>
            </button>
            <a
                href={`https://apis.openapi.sk.com/tmap/app/routes?appKey=${tMapKey}&goalname=권선동성당&goalx=${longitude}&goaly=${latitude}`}
            >
                <img src="./img/tmap-icon.png" alt="" />
                <p>T맵</p>
            </a>
            <a href={naverMapLink}>
                <img src="./img/navermap-icon.png" alt="" />
                <p>네이버 맵</p>
            </a>
            <a href="https://kko.to/rrMPV4So5_">
                <img src="./img/kakaomap-icon.png" alt="" />
                <p>카카오 맵</p>
            </a>
        </div>
    </div>
    <ul class="detail-information">
        <li>
            <h3>지하철 안내</h3>
            <p>수인분당선 매탄권선역 3번 출구 도보 1분 거리</p>
        </li>
        <li>
            <h3>버스 안내</h3>
            <p>광역 버스: 3007, 8800</p>
            <p>지선 버스: 88, 92-1, 99, 62-1</p>
        </li>
        <li>
            <h3>주차 안내</h3>
            <p>성당 내 100여대 주차 가능</p>
        </li>
        <li>
            <h3>기타 안내</h3>
            <p class="red">화환 및 화분은 반입 금지입니다</p>
            <p>
                대신,
                <a
                    href="https://m.search.naver.com/search.naver?sm=mtp_hty.top&where=m&query=%EC%8C%80%ED%99%94%ED%99%98"
                    target="_blank"
                >
                    <b>"쌀 화환"</b></a
                >은 가능합니다.
            </p>
        </li>
    </ul>
</div>

<style>
    .map-area {
        padding: 4rem 0;
    }
    .map-area > h2 {
        padding: 0 0 0.8rem 1.5rem;
        font-size: 1.3rem;
        color: #555;
    }

    .map-info-wrapper {
        background-color: #fdf6f6;
    }
    .map-address {
        display: flex;
        gap: 1rem;
        padding: 1rem 1.5rem;
    }
    .map-address > img {
        width: 3rem;
        object-fit: contain;
        margin-bottom: 0.3rem;
    }
    .map-address h3 {
        font-size: 1.2rem;
        color: #666;
    }
    .map-address p {
        display: inline-block;
        color: #555;
    }
    .map-address button {
        display: inline-block;
        width: 1.8rem;
    }
    .map-address a {
        display: block;
        text-decoration: none;
    }
    #map {
        height: 300px;
    }
    .map-app-link {
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .map-app-link a,
    .map-app-link button {
        display: flex;
        align-items: center;
        flex-direction: column;
        gap: 0.5rem;
        width: 22%;
        padding: 0.6rem 0;
        text-decoration: none;
        text-align: center;
        color: #666;
        font-size: 0.9rem;
    }
    .map-app-link img {
        width: 50%;
    }
    .detail-information {
        padding: 1rem 1.5rem;
    }
    .detail-information li {
        padding: 0.5rem 0;
    }
    .detail-information li h3 {
        color: #333;
    }
    .detail-information li p {
        color: #666;
    }
    .detail-information li p.red {
        color: red;
        font-weight: bold;
    }
</style>
