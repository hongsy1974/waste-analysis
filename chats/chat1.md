# 폐기물 실적 분석 대시보드

_Started 2026-06-30 01:27 UTC_

---

## User

# Claude Design 프롬프트 — 폐기물 실적 분석 도구

> 아래 내용을 Claude Design 채팅창에 그대로 붙여넣으세요.

---

## 만들고 싶은 것
폐기물 담당자가 매월 말 폐기물 실적을 정리·분석하는 **웹 기반 대시보드 도구**의 UI를 디자인해줘. 정부 폐기물 시스템에서 내려받은 엑셀을 매월 업로드하면 누적 데이터로 쌓이고, 여러 기준으로 위탁량을 조회·분석할 수 있는 사내 업무용 도구야.

## 사용 환경 (중요)
- **담당자는 컴퓨터 모니터(데스크톱)를 주로 사용한다.** 와이드 화면(최소 1440px 폭) 기준으로, 좌측 사이드 내비게이션 + 우측 콘텐츠 영역의 데스크톱 레이아웃으로 설계해줘.
- 정보 밀도가 높아도 좋지만, 한 화면에서 핵심 지표 → 추이 → 상세 순으로 시선이 흐르도록 정리해줘.
- 모바일 대응은 이번 범위가 아니다. 데스크톱 최적화에 집중.

## 디자인 원칙 (첨부 이미지의 사내 포털 'Cleverse' 스타일을 따른다)
첨부한 한화솔루션 사내 포털 화면의 룩앤필을 기준으로 일관된 디자인 시스템을 만들어줘.

1. **컬러**
   - 메인 액센트: **한화 오렌지(약 #F37021 / 비비드 오렌지)**. 주요 버튼, 강조 수치, 활성 탭, 차트 포인트 컬러에 사용.
   - 베이스: **깨끗한 화이트 배경 + 아주 옅은 그레이(#F5F6F8) 면 분리**.
   - 상단/내비 영역은 **딥 차콜~블랙** 계열로 대비.
   - 보조 강조(알림·증가/감소): 레드 계열 뱃지, 증감은 상승=레드, 하락=블루/그레이 등 명확히 구분.
2. **레이아웃**
   - **카드/모듈 기반** 구성. 위젯마다 라운드 코너(약 12px)와 옅은 보더/그림자로 분리.
   - 카드 우상단에 액션 버튼(예: '+', 내보내기) 배치하는 패턴.
   - 넉넉한 여백과 정돈된 그리드.
3. **타이포그래피**
   - 한글 산세리프(맑은 고딕/Pretendard 계열), 깔끔하고 가독성 높게.
   - 핵심 수치는 크고 굵게(예: 92% 게이지처럼), 라벨은 작고 그레이 톤.
4. **컴포넌트**
   - 알약(pill) 형태 버튼·뱃지, 라운드 입력 필드.
   - 원형 게이지/도넛, 라인·막대 차트 등 대시보드형 데이터 시각화.
   - 탭(예: WORK/INFO처럼) 전환 UI.
   - 전반적으로 **차분하고 전문적인 기업용 톤**. 화려한 장식 대신 절제된 깔끔함.

## 디자인할 화면
아래 화면들을 위 디자인 시스템으로 일관되게 만들어줘. **요약 대시보드와 부서 배분 입력 화면이 가장 중요(★)하다.**

### 1) 데이터 업로드 화면 (월별 업로드)
- 엑셀 드래그&드롭 / 파일 선택 영역.
- 대상 월 자동 인식 + 확정, 유효성 검사 결과(인식 행 수·매핑 상태·경고).
- 누적 반영 미리보기(신규 추가 행 수, 누적 후 총 건수), 동일 월 재업로드 시 '덮어쓰기/취소' 안내.

### 2) 누적 데이터 관리 화면
- 월별 업로드 이력 테이블(대상 월·업로드 일시·행 수·상태), 특정 월 삭제/재업로드.
- 전체 누적 건수·기간 범위(예: 2026-01 ~ 2026-06) 요약.

### 3) ★요약 대시보드 (가장 핵심 화면)
- **상단 조회 필터 바**: 기간(월/분기/연간/사용자 지정) · 폐기물 종류 · 처리업체명 · 발생 부서명 — 각 항목 단독·다중 선택 가능.
- **조회 결과 카드**: 선택 조건의 **총 위탁량**(크게 강조) + 보조 지표(처리업체 수, 폐기물 종류 수).
- **증감 비교 카드 3개**: 전월 대비 / 전분기 대비 / 전년(동기) 대비 — 증감량과 증감률을 각각, 상승/하락을 컬러로 구분.
- **월별 발생(위탁)량 추이 차트**: 선택 기간을 월 단위로 분해한 라인 또는 막대.
- 보조 차트: 폐기물 종류별·처리업체별·부서별 비중(도넛/막대).

### 4) 업체별 분석 화면
- 처리업체별 위탁량·비중 표 + 차트, 정렬·검색, 폐기물 종류 2차 필터, 전월/전년 동월 비교.

### 5) 폐기물 종류별 분석 화면
- 종류별 위탁량·비중, 처리업체 분포, 기간 추이, 지정/일반 등 분류 그룹핑.

### 6) ★발생 부서 배분 비율 입력 화면
- 행=폐기물 종류, 열=부서(팀)인 입력 표. 각 셀에 배분 비율(%) 입력.
- 행 합계가 100%가 되도록 실시간 검증·경고 표시.
- 비율 프리셋 저장/불러오기(매월 동일 비율 재사용). 발생 부서명은 이 화면에서 별도 입력·관리.

### 7) 부서별 발생 분석 결과 화면
- 입력 비율을 적용해 산출된 부서별 위탁량/비율을 종류별·합계로 표시. 부서 간 비교 차트.

### 8) 리포트/내보내기 화면
- 현재 필터 결과를 엑셀/PDF로 내보내기. 월간 보고용 표준 템플릿(요약+업체별+종류별+부서별) 일괄 출력.

## 산출물 요청
- 먼저 **컬러·타이포·컴포넌트가 정리된 디자인 시스템 한 장**을 보여주고,
- 그다음 **요약 대시보드(화면 3)를 가장 완성도 높게** 디자인해줘.
- 좌측 사이드 내비게이션에 위 8개 화면이 메뉴로 들어가는 구조로, 전체 화면 간 일관성을 유지해줘.

## Assistant

첨부하신 'Cleverse' 포털 이미지가 제 쪽에 전달되지 않았습니다(현재 프로젝트가 비어 있어요). 다만 색·타이포·레이아웃·컴포넌트 방향을 글로 매우 상세히 적어주셔서, 이미지 없이도 그 설명을 기준으로 진행할 수 있습니다. 시작 전 몇 가지만 빠르게 확정하겠습니다.

참고로 한화/Cleverse의 고유 UI를 그대로 복제하진 않고, 말씀해주신 디자인 원칙(오렌지 액센트, 차콜 내비, 카드형 레이아웃)을 바탕으로 **이 도구만의 오리지널 디자인 시스템**으로 만들어 드립니다.

_[tool: set_project_title]_

_[tool: questions_v2]_

## User

Questions answered:
- reference_image: Decide for me
- scope: 위 두 개 + ★발생 부서 배분 입력(화면6)까지
- variations: Decide for me
- sample_data: 사실적인 가상 데이터를 만들어줘 (지정/일반 폐기물, 톤 단위)
- font: Decide for me
- chart_style: 1
- unit_period: 위탁량은 톤(t), 기간은 2026-01 ~ 2026-06 형식

## Assistant

Detailed brief — I'll build a single Design Component with a charcoal sidebar (8 menus + 디자인 가이드), and fully design the **디자인 시스템 시트**, **요약 대시보드**, and **발생 부서 배분 입력** screens with realistic fabricated data (지정/일반 폐기물, 톤 단위, 2026-01~06).

_[tool: update_todos]_

Now building the Design Component.

_[tool: dc_write]_

Let me check the three main screens.

_[tool: show_html]_

_[tool: show_html]_

_[tool: get_webview_logs]_

_[tool: eval_js]_

Content is present (timing on first capture). Let me navigate to the dashboard and re-capture.

_[tool: eval_js]_

_[tool: save_screenshot]_

_[tool: save_screenshot]_

_[tool: eval_js]_

_[tool: eval_js]_

The entrance animation is leaving content stuck at `opacity:0`. Removing it.

_[tool: dc_html_str_replace]_

_[tool: eval_js]_

_[tool: save_screenshot]_

_[tool: eval_js]_

_[tool: eval_js]_

Live DOM is stale — my edit removed it from the template but the preview didn't re-render that node. Reloading.

_[tool: show_html]_

Design system sheet renders cleanly now. Let me verify the dashboard and allocation screens.

_[tool: eval_js]_

_[tool: save_screenshot]_

_[tool: eval_js]_

_[tool: save_screenshot]_

_[tool: eval_js]_

_[tool: save_screenshot]_

All three core screens render correctly — design system sheet, dashboard (filters, KPI 807.3t, comparison cards, charts), and the allocation matrix with live 100% validation.

_[tool: update_todos]_

_[tool: delete_file]_

_[tool: ready_for_verification]_

완성했습니다. 좌측 차콜 내비(8개 메뉴 + 디자인 가이드)에 오렌지 액센트·화이트 카드 시스템을 적용한 단일 도구로, 세 화면을 완성도 높게 구현했습니다.

- **디자인 시스템 시트** (첫 화면): 컬러 팔레트, Pretendard 타이포 스케일, 컴포넌트(알약 버튼·뱃지·세그먼트 탭·게이지)와 증감 표기 규칙(상승=레드▲ / 하락=블루▼).
- **요약 대시보드**: 조회 필터 바(기간 세그먼트 + 종류·업체·부서 다중선택 팝오버), 총 위탁량 807.3t 강조 카드, 전월/전분기/전년 증감 3카드, 월별 추이 라인 차트, 종류별·업체별(도넛)·부서별 보조 차트. 필터를 바꾸면 수치·차트가 실제로 갱신됩니다.
- **발생 부서 배분 입력**: 종류(행)×부서(열) % 입력표, 행 합계 100% 실시간 검증, 프리셋 저장/불러오기, 부서 추가·삭제.

데이터는 지정/일반 폐기물 10종·처리업체 6곳·6개 부서의 2026 상반기 가상 실적(톤 단위)으로 채웠습니다. 나머지 5개 메뉴(업로드·누적관리·업체별·종류별·부서별·리포트)는 설명이 담긴 안내 화면으로 연결해 두었고, 우상단 테마 패널에서 액센트 컬러·밀도·보조차트 표시를 조정할 수 있습니다.

데스크톱(1440px+) 기준 설계라 미리보기 폭이 좁으면 일부 텍스트가 줄바꿈됩니다 — 넓은 화면에서 가장 잘 보입니다. 다음으로 업로드 화면이나 부서별 분석 결과 화면을 이어서 디자인할까요?

## User

데이터 기간을 2024년부터로 관리할 수 있도록 해줘

## Assistant

_[tool: read_file]_

_[tool: read_file]_

Now I understand the structure. The user changed density default to 컴팩트 (preserved). Let me read the filter bar section of the template.

_[tool: read_file]_

Two changes — extend data to 2024+ with a year selector, and rename departments. Let me see the period segment area of the filter bar.

_[tool: read_file]_

I have everything I need. Applying all changes — extending the dataset to 2024-01~2026-06, adding a year selector, multi-year period logic, dense-chart handling, and the department rename.

_[tool: dc_js_str_replace]_

Given the scope (multi-year data + monthly allocation), let me first check for any user in-place edit overrides so I don't clobber them, then continue with targeted edits.

_[tool: grep]_

No user style-overrides — only the density default. I'll continue with targeted edits. Let me read the allocation screen's top controls to edit them precisely.

_[tool: read_file]_

Now I'll apply all remaining changes as a batch — data generation, multi-year period logic, dense charts, department rename, and the monthly allocation model.

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

Now the renderVals computations and the template.

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

All logic edits applied. Now the template edits — year selector, dynamic trend range, sidebar footer, and the allocation month-selector controls.

_[tool: dc_html_str_replace]_

_[tool: dc_html_str_replace]_

_[tool: dc_html_str_replace]_

_[tool: dc_html_str_replace]_

_[tool: dc_html_str_replace]_

All edits applied. Let me verify the dashboard (year selector + dense chart) and the monthly allocation screen render correctly.

_[tool: show_html]_

_[tool: eval_js]_

_[tool: get_webview_logs]_

_[tool: save_screenshot]_

Year selector works — total switches from 796.9t (2026) to 3,665t (전체 2024–2026). But the select shows "전체 기간" at default when it should show "2026년". Let me diagnose.

_[tool: eval_js]_

That was after my test set it to 'all'. Let me reset and check the default binding.

_[tool: eval_js]_

_[tool: grep]_

_[tool: eval_js]_

State is correct (chip shows 2026년) but the framework isn't applying the controlled `value` to the `<select>` — it defaults to the first option. Let me check whether the allocation month select has the same problem.

_[tool: eval_js]_

_[tool: eval_js]_

The month select works correctly (shows 2026-06 at index 29), so the control mechanism is fine. Let me reload fresh and inspect the year select default cleanly.

_[tool: show_html]_

_[tool: eval_js]_

Fresh load is correct — year defaults to 2026년 (index 1); my earlier reading was a stale-state artifact. Let me verify the allocation screen and the dense 30-month trend chart.

_[tool: save_screenshot]_

Both work — allocation has the 대상 월 selector, "30개월 중 30개월 100% 정합" summary, "현재 비율 전체 월 적용" button, and renamed departments (PE생산팀, VCM생산팀, 품질보증팀, 정비팀…). Dashboard 전체 기간 shows 3,665t across 2024–2026. Let me confirm the dense 30-month trend chart renders cleanly.

_[tool: save_screenshot]_

_[tool: eval_js]_

Everything works — 30-month dense trend (labels every 3rd month: 24.01, 24.04…), year selector driving all KPIs, renamed departments, and per-month allocation. Cleaning up and handing off.

_[tool: delete_file]_

_[tool: ready_for_verification]_

세 가지를 모두 반영했습니다.

**데이터 기간 2024년부터 관리** — 데이터셋을 2024-01 ~ 2026-06(30개월)로 확장했습니다. 조회 필터에 **연도 선택(전체 기간 / 2024 / 2025 / 2026)** 을 추가해, 선택에 따라 총 위탁량·증감 카드·추이 차트가 모두 갱신됩니다. 전월/전분기/전년 동기 비교도 실제 누적 데이터 기준으로 계산되며(이제 전년 동월 비교가 실데이터로 가능), 추이 차트는 30개월일 때 자동으로 조밀 모드(3개월 간격 라벨)로 표시됩니다.

**부서명 변경** — PE생산팀 · VCM생산팀 · 품질보증팀 · 정비팀 · 물류팀 · 총무팀으로 교체했습니다(배분표·부서별 차트·필터에 일괄 반영).

**부서 배분 비율 월별 입력** — 배분 비율을 **월 단위로 따로 관리**하도록 바꿨습니다. 상단에 대상 월 선택(◀ ▶ + 드롭다운)이 생기고, 선택한 월의 표를 편집하면 그 월에만 저장됩니다. "현재 비율 전체 월 적용" 버튼으로 한 번에 복사할 수 있고, "전체 30개월 중 N개월 100% 정합" 요약으로 미완성 월을 추적합니다. 대시보드의 부서별 위탁량도 이제 월별 배분 비율 × 선택 기간으로 산출됩니다.

참고로 미리보기 폭이 좁아 배분 화면 상단 카드 문구가 줄바꿈되어 보이는데, 실제 사용 환경(1440px+)에서는 한 줄로 정돈됩니다. 다음으로 부서별 분석 결과 화면이나 업로드 화면을 이어서 만들까요?

## User

요약 대시보드에서 조회조건에 연도만 선택할 수 있는데, 선택한 기간의 데이터를 조회할 수 있도록 수정해줘. 연도를 선택하고 시작월 선택하고 종료월 선택하는 형태면 좋겠어. 사진의 월별, 분기, 연간, 사용자 지정은 삭제해도 돼

## Assistant

I'll replace the year-only selector and the 월별/분기/연간/사용자지정 segment with a 시작월 ~ 종료월 range picker spanning the full 2024–2026 dataset.

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

Now the template — replace the year select + period segment with the range pickers.

_[tool: dc_html_str_replace]_

_[tool: show_html]_

_[tool: eval_js]_

Range picker works — selecting 2025-03 ~ 2026-02 updates the chip to "(12개월)". Let me capture the final look.

_[tool: save_screenshot]_

Verified via the live DOM: the range picker works — selecting 2025-03 ~ 2026-02 correctly updates the chip to "(12개월)", total to 1,504t, and the trend. (The native `<select>` showing "2024-01" in the screenshot is just a static-capture limitation — `html-to-image` doesn't serialize a select's live value; the real browser shows the chosen month, as the eval confirms.)

Let me reset to default and confirm it's clean.

_[tool: eval_js]_

Default correctly resets to 2026-01 ~ 2026-06 (6개월) with all 30 months selectable. Cleaning up and handing off.

_[tool: delete_file]_

The 조회 기간 selector is in. 월별/분기/연간/사용자지정 세그먼트와 연도 단독 선택을 없애고, **시작월 ~ 종료월** 드롭다운으로 교체했습니다.

- 두 드롭다운 모두 2024-01부터 2026-06까지 30개월을 담고 있어, 연·월을 합친 형태로 시작·종료 시점을 고르면 됩니다.
- 선택한 구간의 데이터가 총 위탁량·증감 카드·추이 차트·종류/업체/부서 분석에 모두 반영되고, 상단 칩에 "2026-01 ~ 2026-06 (6개월)"처럼 기간과 개월 수가 표시됩니다.
- 시작월을 종료월보다 뒤로 고르면 자동으로 보정되고, 초기화 버튼은 기본값(2026-01 ~ 2026-06)으로 되돌립니다.

ready_for_verification은 호출하지 않았는데, 바로 확인하시겠어요? 원하시면 검증까지 돌리겠습니다.

## User

매월 업데이트 하는 데이터가 누적되면 누적된 데이터 기준으로 기간조회 등 할 수 있도록 해줘

## Assistant



## User

다시 얘기할께 매월 엑셀로 데이터 파일을 업로드 하면 누적 데이터로 관리될 건데, 이 누적된 데이터에 있는 기간을 기준으로 자료나 기간이 업데이트되어 조회될 수 있도록 해줘

## Assistant

This is a meaningful one: the queryable period should be driven by whatever months exist in the accumulated data, and update as data is uploaded/removed. That means making the 데이터 업로드 and 누적 데이터 관리 screens functional (they're currently placeholders) so accumulated coverage can actually change, then binding the dashboard's period range to that coverage. Let me read the current logic to refactor precisely.

_[tool: read_file]_

_[tool: read_file]_

I have the complete picture. I'll model the accumulated data as a `loaded` set of months (extending the data universe to 2027 so new months can be added), make 데이터 업로드 and 누적 데이터 관리 functional, and bind the dashboard's period range + selectable months to the accumulated coverage. Applying the logic changes:

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

Now the renderVals updates — placeholder/meta/built, loaded-aware sums, monthOptions, coverage, and the upload/history compute + return.

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

Now the templates — coverage hint in the filter bar, and the two new screens.

_[tool: dc_html_str_replace]_

_[tool: dc_html_str_replace]_

Let me verify the new screens and the data-binding behavior (upload a month → dashboard period extends).

_[tool: show_html]_

_[tool: eval_js]_

_[tool: save_screenshot]_

Both screens render well. Now the key test — upload a new month and confirm the dashboard's coverage and selectable months update.

_[tool: eval_js]_

_[tool: eval_js]_

The data-binding works exactly as intended: after uploading 2026-07, the dashboard coverage updates to "2024-01 ~ 2026-07", the chip shows "(31개월)", and 2026-07 becomes selectable (31 month options). Deletion uses the same clamp logic to shrink the range. Cleaning up and handing off.

_[tool: delete_file]_

The accumulated-data binding is done.

_[tool: ready_for_verification]_

조회 기간이 누적 데이터를 기준으로 동작하도록 바꿨고, 그걸 검증할 수 있게 **데이터 업로드**와 **누적 데이터 관리** 화면도 실제로 작동하게 만들었습니다.

**누적 데이터 모델** — 월별 엑셀 업로드를 시뮬레이션해 데이터가 "누적"되는 구조로 바꿨습니다. 현재 2024-01 ~ 2026-06(30개월)이 누적되어 있고, 데이터 보유 기간(최소~최대 월)이 요약 대시보드의 조회 가능 범위를 결정합니다.

**데이터 업로드 화면** — 드래그&드롭 영역 + 대상 월 선택 → "누적 반영". 인식 행 수·매핑 상태·경고, 신규 추가 건수와 누적 후 총 건수 미리보기, 동일 월은 덮어쓰기 안내가 표시됩니다. 새 월을 반영하면 즉시 누적에 추가됩니다.

**누적 데이터 관리 화면** — 전체 누적 건수·기간 범위·업로드 월 수 요약과, 월별 이력 테이블(대상 월·업로드 일시·행 수·상태·재업로드/삭제).

**조회 기간 ↔ 데이터 연동** — 대시보드의 시작월~종료월 드롭다운은 *누적된 월만* 나열하고, 필터 바에 "누적 데이터 2024-01 ~ 2026-06"이 표시됩니다. 검증 결과 2026-07을 업로드하니 곧바로 범위가 "2024-01 ~ 2026-07 (31개월)"로 확장되고 새 월이 선택지에 추가됐으며, 월을 삭제하면 범위가 자동으로 줄어듭니다. 전월/전년 동월 비교도 누적된 데이터가 있을 때만 계산하고, 없으면 "비교 불가"로 표시합니다.

데이터 모델을 2027년까지 확장해 두어 향후 월도 계속 누적·조회할 수 있습니다. 다음으로 업체별/종류별/부서별 분석 화면을 이어서 만들까요?

## User

에코레저를 지우고 폐기물 실적 분석을 에코레저 형태로 수정해줘(사진 참조)

## Assistant

Simple, targeted change — make "폐기물 실적 분석" the bold wordmark and drop the "에코레저" name (and its now-duplicate subtitle), keeping the same logo block format.

_[tool: dc_html_str_replace]_

The 에코레저 wordmark is now replaced — the orange mark sits next to "폐기물 실적 분석" as the bold title (the duplicate subtitle removed).

## User

누적데이터 2024-01~2026-06은 삭제해주고, 선택창인 종류, 처리업체, 발생부서는 발생부서, 종류, 처리업체 순으로 재정렬해줘

## Assistant

Two filter-bar tweaks — remove the coverage label and reorder the dropdowns to 발생부서 → 종류 → 처리업체. Let me read the current filter blocks.

_[tool: read_file]_

Two targeted edits — remove the coverage label and reorder the dropdowns to 발생부서 → 종류 → 처리업체.

_[tool: dc_html_str_replace]_

_[tool: dc_html_str_replace]_

Done. The "누적 데이터 2024-01 ~ 2026-06" label is removed, and the dropdowns now read 발생부서 → 종류 → 처리업체.

## User

요약 대시보드를 맨 위쪽으로 옮겨줘

## Assistant

_[tool: dc_js_str_replace]_

요약 대시보드를 메뉴 맨 위로 옮겼습니다. 이제 요약 대시보드 → 데이터 업로드 → 누적 데이터 관리 → 업체별 → 종류별 → 발생 부서 배분 → 부서별 → 리포트 순입니다.

## User

요약대시보드, 부서별 분석, 종류별 분석, 업체별 분석, 데이터 업로드, 누적 데이터 관리, 발생 부서 배분, 리포트/내보내기 순으로 수정해줘

## Assistant

_[tool: dc_js_str_replace]_

메뉴 순서를 요약 대시보드 → 부서별 분석 → 종류별 분석 → 업체별 분석 → 데이터 업로드 → 누적 데이터 관리 → 발생 부서 배분 → 리포트/내보내기로 변경했습니다.

