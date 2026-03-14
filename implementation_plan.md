# Game Optimization Phase 2: Day 2-5 & Affection Events

這個計畫著重於將「欺騙性的戀愛校園感」延續至第2到第5天，並修復一些遺留的小問題，最後加入好感度解鎖的專屬劇情系統。

## User Review Required
> [!IMPORTANT]
> 關於「好感度事件 (Affection Events)」，預計設定為每個人有 3 個事件，會在好感度達標時，於當天的放學後 (Transition Home) 自動插入觸發。
> - **觸發條件構想**：
>   - 事件一：好感度 >= 15 (預計 Day 2 或 Day 3 可達成) -> 稍微透露他們的執念與對「失去事物」的空虛感。
>   - 事件二：好感度 >= 30 (預計 Day 3 或 Day 4 可達成) -> 隱約帶出白月光的影子（彼得的貓/林恩、蘭蘭的火/喬諾娜、奧拉的同僚/蜜拉思），但不打破校園 AU 的表象。
>   - 事件三：好感度 >= 45 (預計 Day 5 可達成) -> 觸及他們內心最深處的執著，為第二週的崩壞線做情感鋪墊。
> 請您確認這樣的觸發條件與劇情推進節奏是否符合您的期望？

## Proposed Changes

### Global Bug Fixes
*   #### [MODIFY] [js/scripts/day1.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/scripts/day1.js) & [js/core/game.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/core/game.js)
    *   將所有「斯特拉學園」替換為「紙校」。
    *   修復 `day1_break_prompt` 中彼得出現兩個選項的地圖 bug。

### Game Engine Updates
*   #### [MODIFY] [js/core/game.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/core/game.js)
    *   在 [handleSceneEnd](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/core/game.js#746-1130) 進入 `night_chat` 前，加入 `checkAffectionEvents()` 邏輯。
    *   當前最高好感度角色若達到閾值且該事件尚未觸發過（將記錄在 `game.state` 中），則攔截流程，跳轉至對應的好感度事件場景。
*   #### [MODIFY] [js/systems/minigame.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/systems/minigame.js) & [js/core/game.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/core/game.js)
    *   在白月光線中，於小遊戲合成對應男主的專屬句子也能增加 `GE` (Good End) 值。
    *   **設計準則**：每天的小遊戲詞彙庫必須符合「當天校園主題」，且每個男主一定有專屬的三個詞彙可供合成，確保每天能在小遊戲中獲得最高 3 次的好感/GE加分。

### Script Expansion (Day 2 - Day 5)
*   #### [MODIFY] [js/scripts/day2.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/scripts/day2.js) & [js/scripts/day3.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/scripts/day3.js)
    *   全面改寫這兩天的劇情。確保完全沒有「紅色污漬」、「雜訊」、「亂碼」等驚悚元素。
    *   加入更多的校園日常互動，如一起吃午餐、社團活動中的趣味對話，延續乙女遊戲的甜蜜氛圍。
*   #### [NEW] [js/scripts/day4.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/scripts/day4.js) & [js/scripts/day5.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/scripts/day5.js)
    *   新增第 4 天與第 5 天的獨立劇本檔案。
    *   包含每天的早晨、下課、午餐、社團與放學選項，並填入具有單元劇性質的校園事件（例如：校慶準備、考試讀書會等），讓每日都不會枯燥。
*   #### [MODIFY] White Moonlight Routes (Across all days)
    *   全面改寫進入「白月光線」（林恩、喬諾娜、蜜拉思）時的專屬劇情，使其符合現在細膩、有起承轉合的文風。男主們會毫不保留地將玩家視為**離去**的白月光（注意：白月光並未死去，只是離開了）。
    *   **GE 值系統**：在白月光線的對話中加入選項。這些選項會根據人物表上白月光的真實性格設計。若玩家選擇「語氣或行為最貼近原本白月光」的選項，將增加 `GE` (Good End) 值。
*   #### [MODIFY] [index.html](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/index.html)
    *   將新增的 [day4.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/scripts/day4.js) 與 [day5.js](file:///e:/Downloads/CD%E5%80%91/%E5%B0%8F%E9%81%8A%E6%88%B2/DOKIDOKI-main/js/scripts/day5.js) 引入遊戲中。

## Verification Plan

### Automated Tests
*   Run the browser agent to fast-forward through Day 1 to Day 5, verifying that no horror text appears and map navigation works smoothly.
*   Simulate clicking one specific character exclusively to verify that their 3 Affection Events trigger correctly on different days.
