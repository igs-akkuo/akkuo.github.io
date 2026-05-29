# Vita 麻將

麻將接龍休閒益智遊戲，基於 PixiJS v8 開發。

🎮 **遊玩網址：** https://igs-akkuo.github.io/akkuo.github.io/vita-mahjong/

---

## 更新記錄

### 2026-05-29

**核心邏輯修正**
- AutoPlay 重開時不改 localStorage（避免關卡被重設）
- 落單牌問題修正 — `ensureAllPaired` 強制確保所有圖案偶數張
- 冰凍牌、花牌、萬用牌納入配對驗證
- 洗牌開頭強制偶數，避免奇數牌死局
- 重複配對修正 — matchTiles 開始時立即標記 Removed 並更新自由狀態
- AutoPlay 配對前驗證 t2 狀態，防止配對已消除的牌
- AutoPlay 優先解凍冰凍牌，再找配對
- AutoPlay 配對優先最高層（從上往下清）
- AutoPlay 洗牌超過 10 次無解時停止
- 遮蔽牌改為相鄰牌消除時自動消失（符合規格書）
- 障礙物移除（100 關版本中無實際意義）
- HUD 重建後補上 updateLevel/updateScore/updatePowerups

**特殊機制時機調整**
- Lv1-40：純配對
- Lv41+：計時器（10 分鐘）
- Lv71+：冰凍牌、倒數牌、遮蔽牌

**視覺與特效**
- 得分飛行特效啟用（playScoreFly）
- 粒子拖尾（弧線飛行階段星星粒子）
- spawnTrailParticle 加入 destroyed 檢查防止 ticker crash
- 過關文字放大（84px）、分數漂浮放大（128px）
- Effects 容器設為 eventMode='none'，不攔截點擊
- 底部道具欄放大（按鈕 72px、欄高 110px）

**UI 修正**
- 時間到顯示「時間到 / 再來一局」面板
- 每局計時改為 10 分鐘
- 每步配對記錄 log
- 所有動作（選牌、洗牌、提示、撤銷、解凍）都有 console log
