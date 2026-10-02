---
date: 2026-10-02
type: review
period: 2026-W40 (2026-09-28 ~ 2026-10-04)
generated-by: AGENTS.md workflow run (executor simulation)
---

# Weekly Review — 2026-W40

> 由 AGENTS.md Executor 於 2026-10-02（週四）模擬執行。
> 注意：W40 至 10/4 才結束，本次 review 為「mid-week snapshot」。

---

## 📊 Projects 進度（2 個全部）

### [[projects/hw3-fluid-mechanics]] — `active` · due 2026-10-15

| 維度 | 狀態 |
|---|---|
| 完成度 | **0 / 10 題** |
| 距離 due | 13 天 |
| 已做 | 分頁標好（P1–P10）、notes.md 整理共通流程與各題公式、log.md 1 筆 |
| 參考資料 | [[raw/captures/2026-10-01-voice-memo-after-lecture]]、[[raw/captures/2026-10-02-screenshot-lecture-slide]] |
| 教授重點 | P6（壓力中心）、P10（能量+動量綜合）— per 10/1 語音 |
| 風險 | 🟡 **需每週 3–4 題才趕得上**；目前 next/ 只有「P3」單一 task，未對齊教授重點 |
| 行動 | 本週目標 P1–P5；建議把 next/ 拆分為 P1–P5 各自 task，或至少 P6 / P10 拆出 |

### [[projects/phd-application-2027]] — `active` · due 2027-01-15

| 維度 | 狀態 |
|---|---|
| 完成度 | 早期（粗版學校清單 + 文件 checklist） |
| 距離 due | 137 天 |
| 已做 | 學校清單 10 校、notes.md（領域定位、SOP 草）、README 時程 |
| 風險 | 🟡 12/15 大量截止，目前 advisor 寄信 0 封、推薦信未開口 |
| 行動 | 10 月內寄 2–3 封 advisor 信、產出 SOP outline；11 月前向教授要推薦信承諾 |

---

## 🌱 Areas 狀態（3 個全部）

### [[areas/career]] — `active`

- 近期重點：[[phd-application-2027]] 推動
- 本週進度：14:00 advisor meeting 將討論 SOP 主軸、PhD 選題
- 與 [[areas/ntu-esoe-2006]] 有重疊（指導教授相同）— 需注意區分（career = PhD 申請，ntu-esoe = 課業）
- 健康度：🟢 **有進度**

### [[areas/health]] — `active`

- 近期重點：每週 3 次慢跑、戒含糖飲料、23:30 睡、11 月健檢
- 🚨 **警訊**：
  - daily note：「連續 3 天沒運動」
  - 開學後運動頻率：3 → 1 / 週
  - 睡眠：6.5h（不夠）
- 行動：明日起每日排 30min 運動；強烈建議把「運動 N 天」做成 next/ task（或 recurring task）
- 健康度：🔴 **退化中，需立即處理**

### [[areas/ntu-esoe-2006]] — `active`

- 近期重點：[[hw3-fluid-mechanics]]、期中考（11 月初）、advisor meeting、選修 CFD
- 本週：HW#3 P1–P5 推進、PhD 討論
- 知識庫：已 wikilink 到 [[raw/captures/2026-10-01-voice-memo-after-lecture]] 與 [[raw/captures/2026-10-02-screenshot-lecture-slide]] — 串接良好
- 健康度：🟢 **學期初穩定**

---

## 🗄️ Archives 檢查

| 項目 | 狀態 |
|---|---|
| `archives/README.md` | 存在 |
| `archives/projects/` | 空資料夾，無內容 |
| `archives/tasks/` | 空資料夾，無內容 |
| 應歸檔未歸檔 | 無（10 月 done/ 尚為空，11/1 才需做 monthly 歸檔） |
| 滯留 done task | 0 |

> 月初歸檔機制（11/1 把 2026-10 done/ 移到 archives/tasks/2026-10/）尚未觸發，OK。

---

## 🎯 本週 OKR 建議（W40）

| Objective | Key Results | 截止 | 狀態 |
|---|---|---|---|
| HW#3 起步 | 寫完 P1–P5、自檢 | 2026-10-09 | 🟡 進行中 |
| PhD application kick-off | 寄 2 封 advisor 信、產出 SOP outline | 2026-10-09 | 🔴 未開始 |
| 重啟運動 | 至少 2 次慢跑 | 2026-10-09 | 🔴 連 3 天未動 |
| 完成 vault 結構驗證 | AGENTS.md workflow 跑過一輪 | 2026-10-02 | ✅ 此次執行 |

---

## 🚧 觀察到的問題（AGENTS.md 改進建議）

1. **🔴 資料來源單一性**：calendar/synced/ 與 calendar/daily/、daily/ 對同一事件（advisor meeting）時間不同（14:00 vs 11:30）。建議 AGENTS.md 規定 **synced 為 single source of truth**，daily/ 為鏡像（由 Dataview 生成），不手寫。

2. **🔴 raw/captures/ 內有「待分流」checkbox 清單**（如 10/01 voice-memo 末段），違反「raw 不可變 + 不可編輯」原則。應：
   - 在 AGENTS.md 明確禁止 capture 內放 actionable 清單
   - 「待分流」應轉成 `tasks/inbox/` 任務

3. **🟡 Triage 拆分過粗**：`tasks/next/2026-10-01-hw3-problem-3` 命名為「P3」，但教授強調 P6/P10。Triage 應主動依教授重點拆出多個 task。建議 AGENTS.md 在 Triage 段加「拆分原則」說明。

4. **🟡 健康警訊未結構化**：daily reflection 寫「連續 3 天沒運動」，但無 task 自動觸發。建議在 daily template 加「健康警訊」section + reflection 中顯著的紅旗自動 → next/ task。

5. **🟡 Recurring event 衝突未偵測**：09:00–10:30 流力課與 10:00 standup 衝突。AGENTS.md 可加「recurring event 衝突規則」（例如不允許時間重疊、警告）。

6. **🟡 缺乏自動化 trigger**：workflow 4 步全靠人記。建議在 `scripts/` 加：
   - `daily-brief.sh`（每日 7am 跑）
   - `weekly-review.sh`（週日 6pm 跑）
   - `triage-inbox.sh`（每 4h 檢查 inbox 是否有未分流）

7. **🟢 改進點小**：triage 後任務的 `due` 與 `project` / `area` 欄位應有必填檢查，目前 rules 未強調。

8. **🟢 觀察正面**：
   - 三層架構清晰
   - raw 不可變、wikilink 串接、area 不放知識內容 — 規範都落實
   - 模板齊全（task / project / area / daily / capture / event / recurring-event）
   - 範例資料（11 tasks / 7 events / 2 projects / 3 areas / 2 captures / 1 daily）足以驗證 workflow

---

## 🔄 本次 workflow 動作總結

- ✅ Step 1 Capture：盤點 raw/captures/ 現有 2 檔（10/01 voice memo、10/02 screenshot）
- ✅ Step 2 Triage：3 inbox tasks + 2 captures 全部決策（見 brief 末尾表）
- ✅ Step 3 Daily Brief：輸出 `dashboard/2026-10-02-brief.md`
- ✅ Step 4 Review：本檔
- 🔒 維持 raw/ 不可變、不刪除任何已存在檔案
