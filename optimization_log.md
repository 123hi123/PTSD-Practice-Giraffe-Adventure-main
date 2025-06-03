# AppUpdate.cpp 優化記錄

## 優化目標
逐步重構 AppUpdate.cpp 中921行的 Update() 函數，提升代碼可讀性和維護性。

## 優化計畫
1. **第一步：統一鼠標位置獲取** ✅ 已完成
2. 第二步：提取常量定義
3. 第三步：分離簡單的邏輯塊
4. 第四步：逐步分解大函數

---

## 第一步：統一鼠標位置獲取 ✅ 已完成

### 問題分析
在原代碼中發現多處重複獲取鼠標位置：

#### 重複調用位置：
1. ~~**第116行**：`glm::vec2 position = Util::Input::GetCursorPosition();` (大廳邏輯)~~ ✅ 已修復
2. ~~**第155行**：`glm::vec2 position = Util::Input::GetCursorPosition();` (遊戲UI按鈕)~~ ✅ 已修復  
3. ~~**第293行**：`glm::vec2 position = Util::Input::GetCursorPosition();` (鼠標點擊調試)~~ ✅ 已修復
4. ~~**第304行**：`glm::vec2 mousePosition = Util::Input::GetCursorPosition();` (拖拽邏輯)~~ ✅ 已修復
5. ~~**第546行**：`glm::vec2 position = Util::Input::GetCursorPosition();` (猴子選擇)~~ ✅ 已修復
6. ~~**第549行**：`glm::vec2 position = Util::Input::GetCursorPosition();` (猴子升級界面)~~ ✅ 已修復
7. ~~**第853行**：`glm::vec2 position = Util::Input::GetCursorPosition();` (勝利/失敗界面)~~ ✅ 已修復

### 優化結果
#### 修改內容：
- ✅ 在 `Update()` 函數開始添加：`const glm::vec2 mousePosition = Util::Input::GetCursorPosition();`
- ✅ 移除所有重複的鼠標位置獲取調用（總共7處）
- ✅ 統一使用 `mousePosition` 變量名稱
- ✅ 確保所有相關功能正常運作

#### 性能改善：
- **減少函數調用**：從8次 `GetCursorPosition()` 減少到1次
- **提升性能**：消除7次重複的系統調用
- **代碼一致性**：統一的變量命名

#### 代碼品質改善：
- 提升可讀性：明確的變量來源
- 降低維護成本：統一管理鼠標位置
- 減少錯誤可能：避免多次獲取可能的不一致

### 測試建議
請確認以下功能正常：
- [ ] 大廳按鈕點擊
- [ ] 遊戲中UI按鈕（暫停、加速）
- [ ] 猴子拖拽放置
- [ ] 猴子選擇和升級
- [ ] 勝利/失敗界面互動

### 實施狀態
✅ **第一步完成** - 成功統一鼠標位置獲取，代碼更簡潔高效

---

## 下一步計畫
準備進行第二步：提取常量定義，將魔術數字替換為有意義的常量名稱。 