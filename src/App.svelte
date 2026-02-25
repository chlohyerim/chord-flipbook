<script>
  // 데이터 리스트 정의
  const roots = ["C", "Db", "D", "Eb", "E", "F", "Gb", "G", "Ab", "A", "Bb", "B"];
  const extensions = [
    "", "m", "sus4", "add9", "dim", "aug",
    "maj7", "m7", "7", "m7-5", "mM7", "7-5", "7sus4", "6", "m6", "dim7", "aug7",
    "maj7(9)", "7(9)", "7(b9)", "7(#9)", "7(#11)", "7(13)", "7(b13)", "7(9,13)", "7(b9,13)", "6(9)", "m6(9)", "m7(9)", "m7(9,11)"
  ];

  let currentChord = "%";
  let startTime = null;      // 첫 클릭 시점 (누적 시간용)
  let lastClickTime = null;   // 직전 클릭 시점 (간격 측정용)
  let timeDiff = null;        // 직전 클릭과의 차이
  let totalElapsed = null;    // 누적 시간
  let totalElapsedRaw = 0;
  let count = 0;
  
  // 밀리초를 {m}분 {s}초 {ms}로 변환하는 함수
  function formatTime(ms) {
    if (ms <= 0) return "0분 0초 000";
    const minutes = Math.floor(ms / 60000);
    const seconds = Math.floor((ms % 60000) / 1000);
    const milliseconds = ms % 1000;
    
    // 초와 밀리초가 한 자릿수일 때 0을 채우는 처리는 취향에 따라 조절 가능합니다.
    return `${minutes}분 ${seconds}초 ${milliseconds.toString().padStart(3, '0')}`;
  }

  function generateChord() {
    const now = Date.now();
    
    if (!startTime) {
      startTime = now;
      currentChord = "시작!";
    } else {
      // 간격 (초 단위 소수점 2자리)
      timeDiff = ((now - lastClickTime) / 1000).toFixed(2);
      // 전체 누적 밀리초 저장
      totalElapsedRaw = now - startTime;
    }
    
    // 랜덤 코드 생성
    const randomRoot = roots[Math.floor(Math.random() * roots.length)];
    const randomExt = extensions[Math.floor(Math.random() * extensions.length)];
    currentChord = randomRoot + randomExt;

    lastClickTime = now;
    count = count + 1;
  }

  function reset() {
    startTime = null;
    lastClickTime = null;
    timeDiff = null;
    totalElapsed = null;
    currentChord = "%";
    count = 0;
  }
</script>

<main>
  <div class="container">
    <h3 class="title">Chord Flipbook</h3>
    <h1 class="chord-display">{currentChord}</h1>
    
    {#if timeDiff}
      <p class="timer-counter"><span>{count}</span>번째 코드 / 이전 코드로부터 <span>{timeDiff}</span>초 경과 / 총 시간 <span>{formatTime(totalElapsedRaw)}</span></p>
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
    font-family: 'Pretendard', sans-serif;
  }

  .container {
    text-align: center;
    padding: 5rem;
    background: white;
    border-radius: 20px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    min-width: 300px;
  }

  .title {
    font-size: 2rem;
    margin: 1rem 0;
    color: #2f3542;
    font-weight: 800;
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
    transition: transform 0.1s, background-color 0.2s;
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
</style>
