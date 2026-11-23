
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BLUTING | 로또 번호 추천</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background: #090909;
    color: white;
    font-family: Arial, "Malgun Gothic", sans-serif;
    min-height: 100vh;
}

header {
    padding: 25px 8%;
    border-bottom: 1px solid #292929;
}

.logo {
    font-size: 25px;
    font-weight: 900;
    letter-spacing: 4px;
}

.container {
    max-width: 750px;
    margin: 80px auto;
    padding: 20px;
    text-align: center;
}

.tag {
    color: #ff3939;
    font-size: 13px;
    letter-spacing: 3px;
    margin-bottom: 20px;
}

h1 {
    font-size: 42px;
    margin-bottom: 15px;
    line-height: 1.3;
}

.description {
    color: #888;
    line-height: 1.7;
    margin-bottom: 45px;
}

#numbers {
    margin: 35px 0;
}

.number-set {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    flex-wrap: wrap;
    margin: 18px 0;
}

.set-label {
    color: #ff3939;
    font-size: 13px;
    width: 55px;
    text-align: left;
    font-weight: bold;
}

.ball {
    width: 52px;
    height: 52px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #111;
    font-size: 19px;
    font-weight: bold;
}

.ball.yellow {
    background: #f5c542;
}

.ball.blue {
    background: #4b9be8;
    color: white;
}

.ball.red {
    background: #ed5555;
    color: white;
}

.ball.gray {
    background: #aaa;
}

.ball.green {
    background: #65b875;
}

button {
    background: #ff3939;
    color: white;
    border: none;
    padding: 17px 45px;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
    transition: .2s;
    border-radius: 5px;
}

button:hover {
    background: #d92020;
    transform: translateY(-2px);
}

button:disabled {
    opacity: .6;
    cursor: wait;
}

.info {
    color: #666;
    font-size: 13px;
    margin-top: 30px;
    line-height: 1.7;
}

.history {
    margin-top: 65px;
    text-align: left;
    border-top: 1px solid #292929;
    padding-top: 30px;
}

.history h2 {
    font-size: 18px;
    margin-bottom: 20px;
}

.history-item {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 13px 0;
    border-bottom: 1px solid #222;
    flex-wrap: wrap;
}

.history-item span:first-child {
    color: #888;
    font-size: 12px;
    width: 65px;
}

.small-ball {
    width: 29px;
    height: 29px;
    border-radius: 50%;
    color: #111;
    font-size: 12px;
    font-weight: bold;
    display: flex;
    justify-content: center;
    align-items: center;
}

footer {
    text-align: center;
    color: #555;
    padding: 30px;
    font-size: 12px;
    border-top: 1px solid #222;
}

@media(max-width: 600px) {
    .container {
        margin: 55px auto;
    }

    h1 {
        font-size: 32px;
    }

    .ball {
        width: 39px;
        height: 39px;
        font-size: 15px;
    }

    .number-set {
        gap: 7px;
    }

    .set-label {
        width: 45px;
        font-size: 11px;
    }

    button {
        padding: 15px 30px;
    }
}
</style>
</head>

<body>

<header>
    <div class="logo">BLUTING.</div>
</header>

<main class="container">

    <div class="tag">LOTTO NUMBER GENERATOR</div>

    <h1>
        오늘의 행운을<br>
        만들어 보세요.
    </h1>

    <p class="description">
        버튼을 누르면 1부터 45까지의 숫자 중<br>
        중복되지 않는 6개의 번호를 5세트 추천합니다.
    </p>

    <!-- 추천 번호 출력 영역 -->
    <div id="numbers">

        <div class="number-set">
            <div class="set-label">SET 1</div>
            <div class="ball">?</div>
            <div class="ball">?</div>
            <div class="ball">?</div>
            <div class="ball">?</div>
            <div class="ball">?</div>
            <div class="ball">?</div>
        </div>

    </div>

    <button id="generateBtn" onclick="generateNumbers()">
        로또 번호 5세트 추천받기
    </button>

    <p class="info">
        ※ 추천 번호는 무작위 생성 결과이며 당첨을 보장하지 않습니다.<br>
        ※ 각 세트 내부에서는 번호가 중복되지 않습니다.
    </p>

    <!-- 최근 추천 내역 -->
    <div class="history">

        <h2>최근 추천 번호</h2>

        <div id="historyList">
            <p style="color:#666; font-size:13px;">
                아직 추천한 번호가 없습니다.
            </p>
        </div>

    </div>

</main>

<footer>
    BLUTING. © 2026 ALL RIGHTS RESERVED.
</footer>

<script>

let historyCount = 0;

// 번호 생성 함수
function generateNumbers() {

    const button = document.getElementById("generateBtn");

    button.disabled = true;
    button.textContent = "번호 생성 중...";

    setTimeout(() => {

        const numberBox = document.getElementById("numbers");

        numberBox.innerHTML = "";

        const generatedSets = [];

        // 총 5세트 생성
        for (let set = 0; set < 5; set++) {

            const pool = Array.from(
                { length: 45 },
                (_, index) => index + 1
            );

            // Fisher-Yates 무작위 셔플
            for (let i = pool.length - 1; i > 0; i--) {

                const j = Math.floor(Math.random() * (i + 1));

                [pool[i], pool[j]] = [pool[j], pool[i]];

            }

            // 숫자 6개 선택 및 오름차순 정렬
            const selected = pool.slice(0, 6)
                .sort((a, b) => a - b);

            generatedSets.push(selected);

            // 화면 출력
            const row = document.createElement("div");

            row.className = "number-set";

            const label = document.createElement("span");

            label.className = "set-label";

            label.textContent = "SET " + (set + 1);

            row.appendChild(label);

            selected.forEach(number => {

                const ball = document.createElement("div");

                ball.className = "ball " + getColor(number);

                ball.textContent = number;

                row.appendChild(ball);

            });

            numberBox.appendChild(row);

        }

        // 5세트 추천 내역 저장
        generatedSets.forEach(numbers => {

            addHistory(numbers);

        });

        button.disabled = false;

        button.textContent = "5세트 다시 추천받기";

    }, 400);

}


// 로또 번호 색상 설정
function getColor(number) {

    if (number <= 10) return "yellow";

    if (number <= 20) return "blue";

    if (number <= 30) return "red";

    if (number <= 40) return "gray";

    return "green";

}


// 추천 내역 추가
function addHistory(numbers) {

    historyCount++;

    const historyList = document.getElementById("historyList");

    if (historyCount === 1) {

        historyList.innerHTML = "";

    }

    const item = document.createElement("div");

    item.className = "history-item";

    const label = document.createElement("span");

    label.textContent = "추천 " + historyCount;

    item.appendChild(label);

    numbers.forEach(number => {

        const ball = document.createElement("div");

        ball.className = "small-ball " + getColor(number);

        ball.textContent = number;

        item.appendChild(ball);

    });

    historyList.prepend(item);

}

</script>

</body>
</html>
