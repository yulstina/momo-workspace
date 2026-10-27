# MOMO Workspace

1인 크리에이터를 위한 **크리에이티브 프로젝트 · 콘텐츠 워크플로 SaaS 대시보드**의 디자인 명세와 토큰입니다.
딱딱한 관리자 콘솔이 아니라 기분 좋은 개인 작업실처럼 느껴지되, 카드·차트·필터·일정·작업 관리는 바로 읽히는 것을 목표로 합니다.

포트폴리오용 자체 기획이며, 실존하는 회사나 실제 데이터를 나타내지 않습니다. 데모의 모든 수치는 예시 데이터입니다.

## 저장소 구성

| 경로 | 내용 |
|---|---|
| `DESIGN.md` | 디자인 명세 원본 (v1.0). 컬러, 타이포, 그리드, 모션, 상태, 반응형, 수용 기준 |
| `tokens/tokens.css` | CSS 커스텀 프로퍼티. 바닐라 HTML/CSS 또는 런타임 테마 전환용 |
| `tokens/_tokens.scss` | SCSS 변수 + 타입/브레이크포인트/모션 믹스인. Vue 3 + Vite 등에서 `@use` |
| `tokens/tokens.json` | 디자인 도구·에이전트가 읽는 토큰 데이터. 토큰마다 usage 주석 포함 |
| `tokens/fonts.css` | `@font-face` 선언. `tokens.css` 보다 먼저 불러온다 |
| `fonts/` | 웹폰트 파일(woff2)과 라이선스 |

세 토큰 파일은 같은 값을 담고 있습니다. 값을 바꿀 때는 `DESIGN.md`를 먼저 고치고 세 파일에 함께 반영합니다.

## 사용 방법

바닐라:

```html
<link rel="stylesheet" href="tokens/fonts.css">
<link rel="stylesheet" href="tokens/tokens.css">
```

```css
.card {
  background: var(--bg-card);
  border: 1px solid var(--border-soft);
  border-radius: var(--radius-card);
  padding: var(--space-5);
  box-shadow: var(--shadow-card);
}
```

SCSS:

```scss
@use "tokens/tokens" as t;

.card {
  background: t.$bg-card;
  border-radius: t.$radius-card;
  padding: t.$space-5;
  @include t.type(card);
}
```

## 사용 규칙

**컬러**

- 본문과 수치는 `--text-primary`, 보조 레이블은 `--text-secondary`를 씁니다. 파스텔 위에 옅은 글자를 올리지 않습니다.
- `--accent-lavender`, `--accent-peach`, `--accent-butter`, `--accent-blue`는 묶음을 나타내는 면 색입니다. 글자색으로 쓰지 않고, 그 위의 글자는 `--on-accent`를 씁니다.
- `--action-mint` 버튼의 글자는 항상 `--on-action-mint`입니다. 흰 글자는 대비가 모자랍니다.
- `--border-soft`는 카드 가장자리를 긋는 장식선입니다. 입력창 테두리, 토글 트랙, 차트 축, 체크되지 않은 체크박스처럼 **보여야 의미가 전달되는 선**에는 `--border-strong`을 씁니다.
- `--error`와 `--success`는 항상 아이콘이나 단어를 함께 씁니다. 색만으로 상태를 전하지 않습니다.
- 배경 70%, 흰 카드 20%, 파스텔과 강조 10%가 기준 비율입니다. 진한 채도는 중요한 동작과 차트 강조에만 씁니다.

**타이포그래피**

- 제목은 `--font-heading`(LINE Seed Sans KR), 본문·표·필터·차트 레이블은 `--font-body`(Pretendard Variable)를 씁니다.
- `--font-display`(Fredoka)는 영문 브랜드 표기에만 씁니다. 한글에는 쓰지 않습니다.
- KPI 수치에는 `--font-number`와 `font-variant-numeric: tabular-nums`를 함께 적용해 자리수가 흔들리지 않게 합니다.

**간격과 모서리**

- 간격은 8px 리듬(`--space-1` ~ `--space-7`)만 씁니다. 카드 안쪽 여백은 `--space-4`에서 `--space-5` 사이입니다.
- 모서리는 카드 `--radius-card`, 버튼·입력 `--radius-input`, 태그·칩 `--radius-pill` 세 가지입니다.
- 체크박스, 아이콘 버튼, 캘린더 칸은 `--tap-target`(44px) 이상으로 잡습니다.
- 비대칭 벤토 그리드를 쓰되 그리드 선 자체는 예측 가능하게 둡니다. 표의 행과 차트의 축은 일부러 어긋내지 않습니다.

**모션**

- 애니메이션은 상태를 알리는 데에만 씁니다. 진행, 완료, 전환, 피드백이 대상이고, 가만히 있는 요소를 계속 움직이지 않습니다.
- 한 화면에서 쉬지 않고 도는 루프는 되도록 하나 이하로 둡니다.
- `transform`과 `opacity`만 움직입니다. `top`과 `left`는 쓰지 않습니다.
- 이징은 `--ease-out`을 씁니다. 숫자가 빽빽한 표에는 바운스를 넣지 않습니다.
- hover로만 알 수 있는 표시는 반드시 `:focus-visible` 상태로도 보이게 합니다. 포커스 링은 `--action-dark`입니다.
- `prefers-reduced-motion: reduce`에서는 `tokens.css`의 모든 duration이 0이 됩니다. 패럴랙스, 진입 스태거, 마스코트 루프, 카운터는 이때 꺼야 하고, 끈 상태에서도 모든 기능이 그대로 동작해야 합니다.

**상태**

- 주요 컴포넌트마다 Default, Hover, Active/Selected, Focus-visible, Disabled, Loading, Empty, Error를 준비합니다.
- 로딩은 조용한 스켈레톤과 읽어줄 수 있는 상태 텍스트로 처리합니다. 번쩍이는 시머는 쓰지 않습니다.
- 토스트는 오른쪽 아래에 4~6초, 직접 닫기 가능. 심각한 오류는 자동으로 사라지지 않게 둡니다.

## 아이콘과 일러스트

아이콘 세트와 마스코트는 아직 저장소에 없습니다. 참고 사이트의 로고, 일러스트, 마스코트는 가져오지 않고 직접 만든 것만 씁니다. 마스코트는 데스크톱에서 96~140px, 인사 영역과 빈 상태·목표 달성에만 등장시키고 카드마다 올리지 않습니다.

## 폰트

웹용 `woff2` 파일을 `fonts/`에 넣었고, `tokens/fonts.css`가 `@font-face`로 연결합니다.
Pretendard, Fredoka, Plus Jakarta Sans는 가변 폰트라 파일 하나가 모든 굵기를 담당합니다.

| 파일 | 역할 | 굵기 | 크기 |
|---|---|---|---|
| `LINESeedKR-Regular.woff2` | 제목 `--font-heading` | 400 | 512 KB |
| `LINESeedKR-Bold.woff2` | 제목 `--font-heading` | 600–700 | 453 KB |
| `PretendardVariable.woff2` | 본문 `--font-body` | 45–920 | 2.0 MB |
| `Fredoka-Variable.woff2` | 영문 브랜드 `--font-display` | 300–700 | 84 KB |
| `PlusJakartaSans-Variable.woff2` | KPI 수치 `--font-number` | 200–800 | 58 KB |

LINE Seed는 정적 폰트라 Regular와 Bold만 넣었습니다. Bold 파일이 600과 700을 함께 받도록
선언해, 600을 쓸 때 브라우저가 Regular를 굵게 흉내 내 획이 뭉개지는 일을 막았습니다.
Thin(300)은 대시보드에서 쓰지 않아 뺐습니다.

Fredoka와 Plus Jakarta Sans는 배포본이 `ttf`뿐이라 `woff2`로 변환했습니다. Fredoka는
한글 글립이 없으니 로고와 영문 헤드라인에만 쓰고, 한글에는 절대 걸지 않습니다.

첫 화면 전환(FOUT)을 줄이려면 본문 폰트 하나만 미리 받으면 됩니다.

```html
<link rel="preload" href="fonts/PretendardVariable.woff2" as="font" type="font/woff2" crossorigin>
```

### 라이선스

- **LINE Seed Sans KR** — LINE Seed 폰트 라이선스. 배포 zip에 라이선스 파일이 없어
  `fonts/`에도 넣지 못했습니다. 납품 전에 https://seed.line.me/ 에서 조건을 확인하세요.
- **Pretendard** — SIL Open Font License 1.1 (`fonts/LICENSE-Pretendard.txt`)
- **Fredoka** — SIL Open Font License 1.1 (`fonts/OFL-Fredoka.txt`)
- **Plus Jakarta Sans** — SIL Open Font License 1.1 (`fonts/OFL-PlusJakartaSans.txt`)

OFL 세 폰트는 웹 임베딩과 재배포가 허용되므로 저장소에 파일을 함께 둘 수 있습니다.
