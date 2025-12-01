{"id":"38216","variant":"standard","title":"웹용 30문제 시험지"}
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>웹용 30문제 시험지</title>
<style>
body { font-family: Arial, sans-serif; margin: 20px; background: #f0f8ff; }
h1 { text-align: center; margin-bottom: 30px; }
.question { margin-bottom: 20px; padding: 15px; background: #fff; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
.options { margin-left: 20px; }
input[type="text"] { width: 60%; padding: 5px; font-size: 16px; }
button { padding: 10px 20px; font-size: 16px; margin-top: 10px; cursor: pointer; display: block; margin-left: auto; margin-right: auto; }
.result { font-size: 20px; font-weight: bold; margin-top: 30px; text-align: center; color: #333; }
</style>
</head>
<body>
<h1>웹용 시험지 (30문제)</h1>
<form id="examForm">

<!-- 문제 1~30 예시 (단답형 + 객관식 섞음) -->
<div class="question">
<p>1. 대한민국의 수도는?</p>
<input type="text" name="q1">
</div>

<div class="question">
<p>2. 포유류를 고르세요.</p>
<div class="options">
<label><input type="radio" name="q2" value="개"> 개</label><br>
<label><input type="radio" name="q2" value="참새"> 참새</label><br>
<label><input type="radio" name="q2" value="독수리"> 독수리</label>
</div>
</div>

<div class="question">
<p>3. 5 + 7 = ?</p>
<input type="text" name="q3">
</div>

<!-- 4~30번 문제는 같은 구조로 추가 가능 -->
<!-- 예시로 4~30번까지 단답형/객관식 번갈아 추가 -->

<button type="button" onclick="checkAnswers()">제출</button>
</form>

<div class="result" id="result"></div>

<script>
function checkAnswers() {
    const answers = {
        q1: "서울",
        q2: "개",
        q3: "12"
        // q4~q30 문제 정답 추가
    };
    let score = 0;
    let total = Object.keys(answers).length;

    for (let q in answers) {
        const elements = document.getElementsByName(q);
        if (!elements) continue;

        if (elements[0].type === "text") {
            if (elements[0].value.trim() === answers[q]) score++;
        } else if (elements[0].type === "radio") {
            for (let el of elements) {
                if (el.checked && el.value === answers[q]) score++;
            }
        }
    }

    document.getElementById("result").innerText = `점수: ${score} / ${total}`;
}
</script>
</body>
</html>
