# Gamble_v2
# 발표자 뽑기 (Random Picker Wheel)

웹에서 실행되는 발표자 뽑기 휠 프로젝트입니다.
참가자 목록을 입력하고 휠을 돌려 랜덤으로 발표자를 뽑을 수 있는 기능을 제공합니다.
모바일 환경에서도 작동하며, 사운드 효과와 부드러운 애니메이션을 지원합니다.

⸻

✨ 주요 기능
	•	참가자 이름 입력
쉼표(,) 또는 줄바꿈으로 구분하여 참가자 목록을 입력할 수 있습니다.
	•	실시간 휠 생성
입력 즉시 캔버스 기반의 휠 UI가 생성됩니다.
	•	스핀 기능
	•	클릭으로 바로 회전
	•	홀드 기능: 버튼을 길게 누를수록 더 빠르게 회전
	•	사운드 효과
	•	회전 중 루프 사운드
	•	멈출 때 당첨 효과음
	•	모바일 터치 지원
touchstart, touchend 이벤트로 모바일에서도 홀드 동작 가능
	•	커스터마이징
포인터 위치 조정, 사운드 볼륨 조절 등 다양한 설정 가능

⸻

🖥️ 데모 화면

[직접 확인](https://snowman0919.site/roulette_wheel/)
	


⸻

🚀 설치 및 실행 방법

1. 저장소 클론

git clone https://github.com/your-username/random-picker-wheel.git
cd random-picker-wheel

2. 로컬 실행

브라우저에서 index.html 파일을 열기만 하면 됩니다.

⸻

📂 프로젝트 구조

📦 random-picker-wheel
├── index.html         # 메인 HTML 파일
├── style.css          # 스타일시트
├── script.js          # 주요 로직
├── sounds/            # 사운드 파일
│   ├── spin-loop.mp3
│   └── win-chime.mp3
└── screenshots/       # README 이미지


⸻

🔧 주요 코드 설명

휠 그리기

function drawWheel(){
  const n = participants.length;
  const arc = 2 * Math.PI / n;

  ctx.save();
  ctx.translate(cx, cy);
  ctx.rotate(angle);

  for(let i=0; i<n; i++){
    ctx.beginPath();
    ctx.moveTo(0,0);
    ctx.arc(0,0,r,i*arc,(i+1)*arc);
    ctx.closePath();
    ctx.fillStyle = colorFor(i,n);
    ctx.fill();

    ctx.save();
    ctx.rotate(i*arc + arc/2);
    ctx.textAlign = 'right';
    ctx.fillStyle = '#000';
    ctx.font = '16px Arial';
    ctx.fillText(participants[i], r-10, 5);
    ctx.restore();
  }
  ctx.restore();
}


⸻

📱 모바일 터치 이벤트

btnSpinHold.addEventListener('touchstart', (e) => {
  e.preventDefault();
  spinHoldStart();
}, { passive: false });

btnSpinHold.addEventListener('touchend', (e) => {
  e.preventDefault();
  spinHoldEnd();
}, { passive: false });


⸻

🔊 사운드 파일 교체

sounds/ 폴더 안의 파일을 교체하여 나만의 효과음을 적용할 수 있습니다.

const spinSound = new Audio('./sounds/spin-loop.mp3');  // 회전 사운드
const winSound  = new Audio('./sounds/win-chime.mp3');  // 당첨 사운드


⸻

📜 라이선스

MIT License
자세한 내용은 LICENSE 파일을 확인하세요.

⸻

💡 향후 개선 사항
	•	휠 색상 사용자 커스터마이징
	•	가중치 기반 발표자 선정 기능
	•	휠 디자인 고급화 (3D 효과)
	•	다국어 지원 (한국어/영어)

⸻

🙌 기여
	1.	저장소 Fork
	2.	새로운 브랜치 생성 (git checkout -b feature/새기능)
	3.	코드 작성 후 커밋 (git commit -m "Add new feature")
	4.	Pull Request 생성

⸻
