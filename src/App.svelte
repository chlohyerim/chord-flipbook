<script>
  // 데이터 리스트 정의
  const roots = [
    "C",
    "Db",
    "D",
    "Eb",
    "E",
    "F",
    "Gb",
    "G",
    "Ab",
    "A",
    "Bb",
    "B",
  ];
  const extensions = [
    "",
    "m",
    "sus4",
    "add9",
    "dim",
    "aug", // 3화음
    "maj7",
    "7",
    "m7",
    "m7-5",
    "mM7",
    "7-5",
    "7sus4",
    "6",
    "m6",
    "dim7",
    "aug7", // 4화음
    "maj7(9)",
    "7(9)",
    "7(b9)",
    "7(#9)",
    "7(#11)",
    "7(13)",
    "7(b13)",
    "7(9,13)",
    "7(b9,13)",
    "m7(9)",
    "m7(9,11)",
    "6(9)",
    "m6(9)", // 5화음
  ];
  const answers = [
    // C root
    [
      "도미솔",
      "도미b솔",
      "도파솔",
      "도레솔",
      "도미b솔b",
      "도미라b",
      "도미솔시",
      "도미솔시b",
      "도미b솔시b",
      "도미b솔b시b",
      "도미b솔시",
      "도미솔b시b",
      "도파솔시b",
      "도미솔라",
      "도미b솔라",
      "도미b솔b라",
      "도미라b시b",
      "도미솔시레",
      "도미솔시b레",
      "도미솔시b레b",
      "도미솔시b미b",
      "도미솔시b솔b",
      "도미솔시b라",
      "도미솔시b라b",
      "도미솔시레라",
      "도미솔시b레b라",
      "도미b솔시b레",
      "도미b솔시b레파",
      "도미솔라레",
      "도미b솔라레",
    ],
    // Db root
    [
      "레b파라b",
      "레b미라b",
      "레b솔b라b",
      "레b미b라b",
      "레b미솔",
      "레b파라",
      "레b파라b도",
      "레b파라b시",
      "레b미라b시",
      "레b미솔시",
      "레b미라b도",
      "레b파솔시",
      "레b솔b라b시",
      "레b파라b시b",
      "레b미라b시b",
      "레b미솔시b",
      "레b파라시",
      "레b파라b도미b",
      "레b파라b시미b",
      "레b파라b시레",
      "레b파라b시미",
      "레b파라b시솔",
      "레b파라b시시b",
      "레b파라b시라",
      "레b파라b도미b시b",
      "레b파라b시레시b",
      "레b미라b시미b",
      "레b미라b시미b솔b",
      "레b파라b시b미b",
      "레b미라b시b미b",
    ],
    // D root
    [
      "레솔b라",
      "레파라",
      "레솔라",
      "레미라",
      "레파라b",
      "레솔b시b",
      "레솔b라레b",
      "레솔b라도",
      "레파라도",
      "레파라b도",
      "레파라레b",
      "레솔b라b도",
      "레솔라도",
      "레솔b라시",
      "레파라시",
      "레파라b시",
      "레솔b시b도",
      "레솔b라레b미",
      "레솔b라도미",
      "레솔b라도미b",
      "레솔b라도파",
      "레솔b라도라b",
      "레솔b라도시",
      "레솔b라도시b",
      "레솔b라레b미시",
      "레솔b라도미b시",
      "레파라도미",
      "레파라도미솔",
      "레솔b라시미",
      "레파라시미",
    ],
    // Eb root
    [
      "미b솔시b",
      "미b솔b시b",
      "미b라b시b",
      "미b파시b",
      "미b솔b라",
      "미b솔시",
      "미b솔시b레",
      "미b솔시b레b",
      "미b솔b시b레b",
      "미b솔b라레b",
      "미b솔b시b레",
      "미b솔라레b",
      "미b라b시b레b",
      "미b솔시b도",
      "미b솔b시b도",
      "미b솔b라도",
      "미b솔시레b",
      "미b솔시b레파",
      "미b솔시b레b파",
      "미b솔시b레b미",
      "미b솔시b레b솔b",
      "미b솔시b레b라",
      "미b솔시b레b도",
      "미b솔시b레b시",
      "미b솔시b레파도",
      "미b솔시b레b미도",
      "미b솔b시b레b파",
      "미b솔b시b레b파라b",
      "미b솔시b도파",
      "미b솔b시b도파",
    ],
    // E root
    [
      "미라b시",
      "미솔시",
      "미라시",
      "미솔b시",
      "미솔시b",
      "미라b도",
      "미라b시미b",
      "미라b시레",
      "미솔시레",
      "미솔시b레",
      "미솔시미b",
      "미라b시b레",
      "미라시레",
      "미라b시레b",
      "미솔시레b",
      "미솔시b레b",
      "미라b도레",
      "미라b시미b솔b",
      "미라b시레솔b",
      "미라b시레파",
      "미라b시레솔",
      "미라b시레시b",
      "미라b시레레b",
      "미라b시레도",
      "미라b시미b솔b레b",
      "미라b시레파레b",
      "미솔시레솔b",
      "미솔시레솔b라",
      "미라b시레b솔b",
      "미솔시레b솔b",
    ],
    // F root
    [
      "파라도",
      "파라b도",
      "파시b도",
      "파솔도",
      "파라b시",
      "파라레b",
      "파라도미",
      "파라도미b",
      "파라b도미b",
      "파라b시미b",
      "파라b도미",
      "파라시미b",
      "파시b도미b",
      "파라도레",
      "파라b도레",
      "파라b시레",
      "파라레b미b",
      "파라도미솔",
      "파라도미b솔",
      "파라도미b솔b",
      "파라도미b라b",
      "파라도미b시",
      "파라도미b레",
      "파라도미b레b",
      "파라도미레",
      "파라도미b솔b레",
      "파라b도미b솔",
      "파라b도미b솔시b",
      "파라도레솔",
      "파라b도레솔",
    ],
    // Gb root
    [
      "솔b시b레b",
      "솔b라레b",
      "솔b시레b",
      "솔b라b레b",
      "솔b라도",
      "솔b시b레",
      "솔b시b레b파",
      "솔b시b레b미",
      "솔b라레b미",
      "솔b라도미",
      "솔b라레b파",
      "솔b시b도미",
      "솔b시레b미",
      "솔b시b레b미b",
      "솔b라레b미b",
      "솔b라도미b",
      "솔b시b레미",
      "솔b시b레b파라b",
      "솔b시b레b미라b",
      "솔b시b레b미솔",
      "솔b시b레b미라",
      "솔b시b레b미도",
      "솔b시b레b미미b",
      "솔b시b레b미레",
      "솔b시b레b파라b미b",
      "솔b시b레b미솔미b",
      "솔b라레b미라b",
      "솔b라레b미라b시",
      "솔b시b레b미b라b",
      "솔b라레b미b라b",
    ],
    // G root
    [
      "솔시레",
      "솔시b레",
      "솔도레",
      "솔라레",
      "솔시b레b",
      "솔시미b",
      "솔시레솔b",
      "솔시레파",
      "솔시b레파",
      "솔시b레b파",
      "솔시b레솔b",
      "솔시레b파",
      "솔도레파",
      "솔시레미",
      "솔시b레미",
      "솔시b레b미",
      "솔시미b파",
      "솔시레솔b라",
      "솔시레파라",
      "솔시레파시b라b",
      "솔시레파시b",
      "솔시레파레b",
      "솔시레파미",
      "솔시레파미b",
      "솔시레솔b라미",
      "솔시레파시b라b미",
      "솔시b레파라",
      "솔시b레파라도",
      "솔시레미라",
      "솔시b레미라",
    ],
    // Ab root
    [
      "라b도미b",
      "라b시미b",
      "라b레b미b",
      "라b시b미b",
      "라b시레",
      "라b도미",
      "라b도미b솔",
      "라b도미b솔b",
      "라b시미b솔b",
      "라b시레솔b",
      "라b시미b솔",
      "라b도레솔b",
      "라b레b미b솔b",
      "라b도미b파",
      "라b시미b파",
      "라b시레파",
      "라b도미솔b",
      "라b도미b솔시b",
      "라b도미b솔b시b",
      "라b도미b솔b라",
      "라b도미b솔b시",
      "라b도미b솔b레",
      "라b도미b솔b솔",
      "라b도미b솔b미",
      "라b도미b솔시b파",
      "라b도미b솔b라파",
      "라b시미b솔b시b",
      "라b시미b솔b시b레b",
      "라b도미b파시b",
      "라b시미b파시b",
    ],
    // A root
    [
      "라레b미",
      "라도미",
      "라레미",
      "라시미",
      "라도미b",
      "라레b파",
      "라레b미라b",
      "라레b미솔",
      "라도미솔",
      "라도미b솔",
      "라도미라b",
      "라레b미b솔",
      "라레미솔",
      "라레b미솔b",
      "라도미솔b",
      "라도미b솔b",
      "라레b파솔",
      "라레b미라b시",
      "라레b미솔시",
      "라레b미솔시b",
      "라레b미솔도",
      "라레b미솔미b",
      "라레b미솔솔b",
      "라레b미솔파",
      "라레b미라b시솔b",
      "라레b미솔시b솔b",
      "라도미솔시",
      "라도미솔시레",
      "라레b미솔b시",
      "라도미솔b시",
    ],
    // Bb root
    [
      "시b레파",
      "시b레b파",
      "시b미b파",
      "시b도파",
      "시b레b미",
      "시b레솔b",
      "시b레파라",
      "시b레파라b",
      "시b레b파라b",
      "시b레b미라b",
      "시b레b파라",
      "시b레미라b",
      "시b미b파라b",
      "시b레파솔",
      "시b레b파솔",
      "시b레b미솔",
      "시b레솔b라b",
      "시b레파라도",
      "시b레파라b도",
      "시b레파라b시",
      "시b레파라b레b",
      "시b레파라b미",
      "시b레파라b솔",
      "시b레파라b솔b",
      "시b레파라도솔",
      "시b레파라b시솔",
      "시b레b파라b도",
      "시b레b파라b도미b",
      "시b레파솔도",
      "시b레b파솔도",
    ],
    // B root
    [
      "시미b솔b",
      "시레솔b",
      "시미솔b",
      "시레b솔b",
      "시레파",
      "시미b솔",
      "시미b솔b시b",
      "시미b솔b라",
      "시레솔b라",
      "시레파라",
      "시레솔b시b",
      "시미b파라",
      "시미솔b라",
      "시미b솔b라",
      "시레솔b라b",
      "시레파라b",
      "시미b솔라",
      "시미b솔b시b레b",
      "시미b솔b라레b",
      "시미b솔b라도",
      "시미b솔b라레",
      "시미b솔b라파",
      "시미b솔b라솔b",
      "시미b솔b라솔",
      "시미b솔b시b레b라b",
      "시미b솔b라도라b",
      "시레솔b라레b",
      "시레솔b라레b미",
      "시미b솔b라레b",
      "시레솔b라b레b",
    ],
  ];

  let currentChord = "%";
  let startTime = null; // 첫 클릭 시점 (누적 시간용)
  let lastClickTime = null; // 직전 클릭 시점 (간격 측정용)
  let timeDiff = null; // 직전 클릭과의 차이
  let totalElapsedRaw = 0;
  let count = 0;

  let prevRootIndex = null;
  let prevExtIndex = null;
  let prevAnswer = null;

  // 밀리초를 {m}분 {s}초 {ms}로 변환하는 함수
  function formatTime(ms) {
    if (ms <= 0) return "0분 0초 000";
    const minutes = Math.floor(ms / 60000);
    const seconds = Math.floor((ms % 60000) / 1000);
    const milliseconds = ms % 1000;

    // 초와 밀리초가 한 자릿수일 때 0을 채우는 처리는 취향에 따라 조절 가능합니다.
    return `${minutes}분 ${seconds}초 ${milliseconds.toString().padStart(3, "0")}`;
  }

  function generateChord() {
    const now = Date.now();

    if (!startTime) {
      startTime = now;
    } else {
      // 간격 (초 단위 소수점 2자리)
      timeDiff = ((now - lastClickTime) / 1000).toFixed(2);
      // 전체 누적 밀리초 저장
      totalElapsedRaw = now - startTime;
    }

    if (prevRootIndex !== null && prevExtIndex !== null) {
      prevAnswer = answers[prevRootIndex][prevExtIndex];
    }

    // 랜덤 코드 생성
    const rootIndex = Math.floor(Math.random() * roots.length);
    const extIndex = Math.floor(Math.random() * extensions.length);
    const randomRoot = roots[rootIndex];
    const randomExt = extensions[extIndex];
    currentChord = randomRoot + randomExt;

    prevRootIndex = rootIndex;
    prevExtIndex = extIndex;

    lastClickTime = now;
    count = count + 1;
  }

  function reset() {
    startTime = null;
    lastClickTime = null;
    timeDiff = null;
    currentChord = "%";
    count = 0;
    prevRootIndex = null;
    prevExtIndex = null;
    prevAnswer = null;
  }
</script>

<main>
  <div class="container">
    <h3 class="title">Chord Flipbook</h3>

    <h1 class="chord-display">{currentChord}</h1>

    {#if prevAnswer}
      <p class="prev-answer">이전 정답: {prevAnswer}</p>
    {/if}

    {#if timeDiff}
      <p class="timer-counter">
        <span>{count}</span>번째 코드 / 이전 코드로부터
        <span>{timeDiff}</span>초 경과 / 총 시간
        <span>{formatTime(totalElapsedRaw)}</span>
      </p>
    {:else}
      <p class="timer-counter"><span>{count}</span>번째 코드</p>
    {/if}

    <div class="button-group">
      <button class="generate-btn" on:click={generateChord}>생성</button>
      <button class="reset-btn" on:click={reset}>리셋</button>
    </div>
  </div>
</main>

<style>
  :global(body) {
    margin: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f2f5;
    font-family: "Pretendard", sans-serif;
  }

  .container {
    text-align: center;
    padding: 5rem;
    background: white;
    border-radius: 20px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
    min-width: 300px;
  }

  .title {
    font-size: 2rem;
    margin: 1rem 0;
    color: #2f3542;
    font-weight: 800;
  }

  .prev-answer {
    font-size: 2rem;
    margin: 0 0 1.5rem 0;
    color: #2f35427f;
    font-weight: bold;
  }

  .chord-display {
    font-size: 7.5rem;
    margin: 1.5rem 0;
    color: #2f3542;
    font-weight: 800;
  }

  .timer-counter {
    color: #666;
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }

  .timer-counter span {
    color: #ff4757;
    font-weight: bold;
  }

  button {
    padding: 1rem 2.5rem;
    margin: 0.25rem;
    font-size: 1.5rem;
    background-color: #2ed573;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition:
      transform 0.1s,
      background-color 0.2s;
  }

  .generate-btn {
    background: #37b24d;
    color: white;
  }

  .reset-btn {
    background: #e9ecef;
    color: #495057;
  }

  button:hover {
    opacity: 0.85;
    transition: all 0.25s ease-out;
  }

  button:active {
    transform: scale(0.96);
    transition: all 0.02s ease-out;
  }

  @media (max-width: 600px) {
    .container {
      padding: 2rem;
      min-width: unset;
      width: 90%;
      box-sizing: border-box;
    }

    .title {
      font-size: 1.5rem;
    }

    .chord-display {
      font-size: 4.5rem;
    }

    .prev-answer {
      font-size: 1.25rem;
    }

    .timer-counter {
      font-size: 1rem;
    }

    button {
      padding: 0.8rem 1.5rem;
      font-size: 1.2rem;
      width: 100%;
      margin: 0.5rem 0;
      box-sizing: border-box;
    }

    .button-group {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }
  }
</style>
