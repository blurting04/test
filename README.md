
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BLUTING | 세상의 모든 궁금증</title>
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, "Malgun Gothic", sans-serif;
    background: #090909;
    color: #fff;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 28px 8%;
    border-bottom: 1px solid #252525;
}

.logo {
    font-size: 27px;
    font-weight: 900;
    letter-spacing: 4px;
}

nav a {
    color: #aaa;
    text-decoration: none;
    margin-left: 28px;
    font-size: 14px;
}

nav a:hover {
    color: white;
}

.hero {
    min-height: 550px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 80px 12%;
}

.tag {
    color: #999;
    letter-spacing: 3px;
    font-size: 12px;
    margin-bottom: 25px;
}

.hero h1 {
    font-size: clamp(42px, 7vw, 82px);
    line-height: 1.2;
    font-weight: 900;
    margin-bottom: 25px;
}

.hero h1 span {
    color: #ff3939;
}

.hero p {
    color: #aaa;
    font-size: 17px;
    line-height: 1.8;
}

.button {
    display: inline-block;
    width: fit-content;
    margin-top: 35px;
    padding: 15px 28px;
    border: 1px solid #555;
    color: white;
    text-decoration: none;
    transition: .3s;
}

.button:hover {
    background: white;
    color: black;
}

section {
    padding: 80px 12%;
}

.section-title {
    font-size: 30px;
    margin-bottom: 15px;
}

.section-desc {
    color: #888;
    margin-bottom: 40px;
}

.cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}

.card {
    background: #151515;
    padding: 35px 25px;
    border: 1px solid #292929;
    min-height: 180px;
}

.card h3 {
    font-size: 21px;
    margin-bottom: 15px;
}

.card p {
    color: #999;
    line-height: 1.7;
    font-size: 14px;
}

.about {
    background: #111;
    text-align: center;
}

.about p {
    color: #aaa;
    line-height: 2;
    max-width: 650px;
    margin: 20px auto 0;
}

footer {
    text-align: center;
    padding: 35px;
    border-top: 1px solid #252525;
    color: #666;
    font-size: 12px;
    letter-spacing: 2px;
}

@media(max-width: 700px) {
    header {
        padding: 22px 6%;
    }
    nav a {
        margin-left: 10px;
        font-size: 12px;
    }
    .hero {
        padding: 70px 7%;
        min-height: 480px;
    }
    section {
        padding: 65px 7%;
    }
    .cards {
        grid-template-columns: 1fr;
    }
}
</style>
</head>

<body>

<header>
    <div class="logo">BLUTING.</div>
    <nav>
        <a href="#home">HOME</a>
        <a href="#contents">CONTENTS</a>
        <a href="#about">ABOUT</a>
    </nav>
</header>

<main>
    <div class="hero" id="home">
        <div class="tag">DISCOVER · EXPLORE · KNOW</div>
        <h1>
            세상의 궁금증을<br>
            <span>새롭게 바라보다.</span>
        </h1>
        <p>
            몰랐던 이야기부터 흥미로운 이슈까지.<br>
            블러팅은 세상의 다양한 정보를 쉽고 재미있게 전달합니다.
        </p>
        <a href="#contents" class="button">블러팅 알아보기 →</a>
    </div>

    <section id="contents">
        <h2 class="section-title">WHAT WE DO.</h2>
        <p class="section-desc">블러팅이 전하는 세 가지 이야기</p>

        <div class="cards">
            <div class="card">
                <h3>01. TREND</h3>
                <p>지금 세상에서 주목받는 최신 이슈와 트렌드를 전달합니다.</p>
            </div>
            <div class="card">
                <h3>02. KNOWLEDGE</h3>
                <p>일상에서 지나쳤던 흥미로운 사실과 새로운 지식을 소개합니다.</p>
            </div>
            <div class="card">
                <h3>03. STORY</h3>
                <p>세상 곳곳에서 일어나는 특별하고 재미있는 이야기를 다룹니다.</p>
            </div>
        </div>
    </section>

    <section class="about" id="about">
        <h2 class="section-title">ABOUT BLUTING.</h2>
        <p>
            우리는 매일 수많은 정보를 마주합니다.<br>
            하지만 그중에는 아직 발견하지 못한 흥미로운 이야기가 많습니다.<br><br>
            BLUTING은 그 이야기들을 찾아내고,<br>
            누구나 쉽고 재미있게 이해할 수 있도록 전달하는 콘텐츠 브랜드입니다.
        </p>
    </section>
</main>

<footer>
    BLUTING. © 2026 ALL RIGHTS RESERVED.
</footer>

</body>
</html>
