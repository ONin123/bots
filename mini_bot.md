# 🧠 Auto Trade Enterprise – Hệ thống giao dịch AI tự vận hành

Hệ thống này là nền tảng giao dịch thông minh, không chỉ tự động hoá việc vào lệnh mà còn có khả năng **tự giám sát, tự sửa lỗi, tự học từ các lần fix trước** như một doanh nghiệp AI thực thụ.

---

# AutoTrade Enterprise - Tổng Quan Hệ Thống

## 🎯 Mục tiêu hệ thống
Xây dựng hệ thống giao dịch tự động đa coin (10-100 cặp tiền) trên OKX futures, có khả năng:
- Tự phân tích tín hiệu đa khung thời gian bằng AI
- Đặt lệnh limit với TP/SL tùy chỉnh
- Giám sát và bảo vệ lệnh bằng Guard AI và Closer AI
- Tự học từ kết quả giao dịch, tối ưu chiến lược và quản lý vốn
- Giao diện dashboard tổng hợp trạng thái bot và kết quả học
- Tự động sửa lỗi code bằng AI (Ollama + Watcher)

# 🧠 Strategy Engine v1.0 – Auto Trade Enterprise

Hệ thống chiến lược giao dịch thông minh, có khả năng:
- Phân tích đa chiều: sóng, nến, volume, macro
- Gọi chiến lược phù hợp theo thị trường
- Ghi nhận hiệu suất, học từ lệnh sai
- Tự điều chỉnh chiến lược kém hiệu quả
- Có dashboard KPI và hệ thống kiểm thử định kỳ
---

## 📁 Cấu trúc thư mục chính

.\venv\Scripts\activate

---

## 📁 CẤU TRÚC THƯ MỤC TOÀN HỆ THỐNG

```bash
auto_trade_enterprise/
├── run_all.py                    # Khởi động toàn hệ thống
├── supervisor_ai.py             # Shortcut trung tâm gọi supervisor
│
├── 1. presentation/             # Giao diện người dùng & dashboard
│   ├── telegram_bot/
│   └── web_dashboard/
│
├── 2. orchestration/            # Bộ não điều phối trung tâm
│   ├── ceo.py                   # Tổng quản lý logic hệ thống
│   ├── portfolio_manager.py     # Quản lý danh mục tài sản
│   ├── risk_controller.py       # Quản trị rủi ro chung
│   ├── bot_coordinator.py       # Giao tiếp bot chiến lược
│   └── intelligence/            # 🌐 Supervisor AI Core
│       ├── supervisor_ai.py     # Điều phối lỗi và AI agents
│       ├── error_router.py      # Phân loại lỗi
│       ├── priority_scoring.py  # Chấm điểm độ nghiêm trọng
│       ├── fix_selector.py      # Chọn agent phù hợp để sửa lỗi
│       └── self_improve.py      # Ghi log và tự học từ fix
│
├──3.strategy/
├── ├strategies/                        # ✅ Chiến lược vào lệnh chuẩn hoá
│   ├── breakout_strategy/ ✅
│   ├── pullback_strategy/ ✅
│   └── ...
│
├── controller/
│   └── strategy_controller.py ✅       # Gọi chiến lược theo context
│
├── analyst/
│   ├── analyst_ai.py ✅
│   ├── bots/
│   │   └── analyst_btc.py ✅
│   └── frameworks/ ✅
│       ├── wave_analysis.py ✅
│       ├── volume_spike.py ✅
│       ├── candle_patterns.py ✅
│       └── macro_filter.py ✅
│
├── guard/
│   ├── guard_ai.py ✅
│   ├── bots/
│   │   └── guard_btc.py ✅
│   └── strategies/
│       ├── trend_reversal_detector.py ✅
│       └── volatility_kill.py ✅
│
├── closer/
│   ├── closer_ai.py ✅
│   ├── bots/
│   │   └── closer_btc.py ✅
│   └── rules/
│       ├── tp_optimizer.py ✅
│       └── exit_on_loss_reversal.py ✅
│
├── learner/
│   ├── learner_ai.py ✅
│   ├── bots/
│   │   └── learner_btc.py ✅
│   └── modules/
│       ├── review_log_analyzer.py ✅
│       └── self_adjustment.py ✅
│
├── strategy_tester.py ✅              # Kiểm thử chiến lược 7 ngày gần nhất
├── weekly_kpi_logger.py ✅            # Ghi log hiệu suất
├── run_weekly_jobs.py ✅              # Gọi tester + ghi log định kỳ
├── strategy_dashboard.py ✅           # Giao diện xem KPI bằng Streamlit
│
├── 4. execution/                # Thực hiện lệnh trên sàn
│   ├── trader.py
│   ├── order_manager.py
│   └── sl_tp_handler.py
│
├── 5. infrastructure/          # Hạ tầng, tiện ích, giám sát
│   ├── api_clients/             # Kết nối OKX, Exness, Binance...
│   │   └── okx_client.py
│   ├── monitoring/              # Theo dõi & báo lỗi
│   │   ├── watcher.py           # Gửi lỗi đến Supervisor AI
│   │   ├── heartbeat.py
│   │   └── alert_manager.py
│   ├── logging/
│   │   ├── trade_logger.py
│   │   ├── error_logger.py
│   │   └── learning_logger.py
│   └── utils/                   # Hàm phụ trợ chung
│       ├── formatter.py
│       └── validators.py
│
├── 6. ai_agents/                # 🤖 Các AI sửa lỗi (client của Supervisor)
│   ├── ollama_brain.py          # Agent gửi lỗi đến Ollama API
│   ├── gpt_patcher.py           # Backup GPT agent (nếu cần)
│   ├── backup_fixer.py          # Sửa lỗi thủ công bằng template
│   └── syntax_validator.py      # Kiểm tra cú pháp sau fix
│
├── 7. data_config/              # Dữ liệu & cấu hình
│   ├── config/
│   │   ├── coins.yaml
│   │   └── settings.yaml
│   ├── credentials/
│   │   └── api_keys.yaml
│   ├── logs/
│   │   ├── error.log                # Log lỗi cho watcher
│   │   ├── processed_errors.log     # Lỗi đã xử lý
│   │   └── system_diagnostic.json  # Tình trạng tổng quát
│   ├── kpi_logs/
│   │   ├── kpi_btc.csv
│   │   ├── award_log.csv
│   │   └── fix_history.csv         # Nhật ký sửa lỗi AI
│   └── ai_learn/
│       └── system_memory.json      # Bộ nhớ học tập của AI
```

---

## 🔧 CÁC TỆP QUAN TRỌNG KHÁC

- `smart_updater.py` → Áp dụng code fix vào dòng cụ thể
- `award_center.py` → Ghi nhận thành tích AI hoạt động tốt
- `kpi_tracker.py` → Tổng hợp KPI bot chiến lược
- `deploy.sh` → Script triển khai nhanh hệ thống

---


---

## 🚀 Tình trạng triển khai

| Module                     | Trạng thái         | Ghi chú                               |
|----------------------------|--------------------|-------------------------------------|
| AI Phân tích & học (Strategy) | Hoàn chỉnh         | analyst, guard, closer, learner AI  |
| Đặt lệnh (Execution)          | Hoàn chỉnh         | Gửi lệnh limit futures OKX          |
| Bộ điều phối (Orchestration)  | Hoàn chỉnh         | Portfolio, capital, bot coordinator |
| Monitoring & Fix lỗi (Infra)  | Hoàn chỉnh         | Watcher + Ollama, log, order track  |
| Dashboard (Presentation)      | Hoàn chỉnh         | Dashboard gộp với 4 tab chính       |
| Cấu hình & dữ liệu            | Hoàn chỉnh         | coins.yaml, system_memory.json, logs|

| Chiến lược chuẩn hoá | ✅ Full | breakout + pullback đã chuẩn hoá interface & logic |
| Framework phân tích | ✅ Full | đã có sóng, volume, candle, macro |
| Analyst AI | ✅ | Phân tích theo coin, đã có analyst_btc |
| Guard AI | ✅ | Có logic đảo chiều & volatility, đã hoạt động |
| Closer AI | ✅ | Có logic TP tối ưu & cảnh báo đảo chiều khi đang lãi |
| Learner AI | ✅ | Ghi nhận thất bại, tự đánh giá, tự điều chỉnh chiến lược |
| Kiểm thử chiến lược | ✅ | Test toàn bộ chiến lược trên 7 ngày gần nhất |
| Dashboard hiệu suất | ✅ | Xem % vào lệnh, số lượng test, biểu đồ tiến độ |
| Cảnh báo Telegram | ⏳ Chờ cập nhật cuối | Sẽ tích hợp sau khi hệ thống ổn định |
## 🧠 Tự học – tự sửa – tự chọn chiến lược tốt nhất
Hệ thống Strategy Engine v1.0 đã có khả năng:
- Gọi đúng chiến lược theo thị trường
- Phân tích kỹ thuật chuyên sâu (volume, nến, sóng, vĩ mô)
- Ghi log học máy + đánh giá hiệu quả
- Tự điều chỉnh chiến lược nếu thua liên tiếp
- Dashboard theo dõi hiệu suất & tester định kỳ

📌 Sẵn sàng tích hợp cảnh báo, mô hình AI nâng cao, và mở rộng thêm các coin khác.


---

## 🛠 Hướng phát triển tiếp theo

- Tích hợp Telegram cảnh báo tự động
- Tối ưu đa luồng, async để tăng hiệu suất bot
- Tạo mô-đun `trainer_ai.py` nâng cao cho tự động cải tiến chiến lược
- Thêm hệ thống cảnh báo rủi ro tức thời (Risk Management)
- Mở rộng giao diện dashboard đa kênh (mobile, email)

---

## 🔖 Cách chạy hệ thống

1. Kích hoạt môi trường Python:
```bash
.\venv\Scripts\activate
---

## ✅ READY TO BUILD
Bạn có thể chạy `run_all.py` để khởi động toàn bộ hệ thống.
Các file chính đã kết nối chuẩn. Hãy bắt đầu nâng cấp từng module để hoàn thiện doanh nghiệp AI tự động!

openai:
  api_key: sk-xxxxx-your-real-api-key-here


đã cập nhật
 HỆ THỐNG PHÂN TÍCH TÍN HIỆU – CHUẨN V5 (ANALYST + STRATEGY)
📌 Luồng xử lý chuẩn:
text
Sao chép
Chỉnh sửa
main.py
  → SignalHub.analyze(symbol)
      → analyst_ai.analyze(symbol, candles, context)
          → analyst_<coin>.analyze(candles, context)
              → strategy_controller.select_best_strategy(context)
                  → breakout_strategy.should_enter(candles, context)
                      → method: volume_confirm, ema_crossover, ...
              → return signal dict (raw_signal)
🧩 Vai trò từng tệp:
Tệp	Vai trò duy nhất
main.py	Chạy vòng lặp chính, gọi SignalHub
signal_hub.py	Gọi analyst_ai → kiểm tra tín hiệu → return should_enter
analyst_ai.py	Dispatcher theo symbol (vd: btc_usdt → analyst_btc.py)
analyst_<coin>.py	Gọi controller, nhận strategy → trả raw_signal chuẩn
strategy_controller.py	Chọn chiến lược phù hợp từ context
strategies/*.py	Mỗi file 1 chiến lược, có hàm should_enter(candles, context)
methods/*.py	Tập hợp các xác nhận kỹ thuật như EMA, RSI, Volume...
analyst_core.py	(Tùy chọn) Xử lý điểm số, merge signal, filter noise

✅ Định dạng raw_signal chuẩn:
python
Sao chép
Chỉnh sửa
{
  "side": "buy",
  "entry_price": 1.234,
  "score": 1.6,
  "reason": "breakout + volume + ema",
  "timeframe": "M15",
  "should_enter": True
}
⚙ Nguyên tắc hệ thống:
Thành phần	Chức năng
Method	Xử lý kỹ thuật nhỏ, không dùng context
Strategy	Gom các method, quyết định logic vào lệnh
Controller	Chọn chiến lược tối ưu cho từng context
Analyst_<coin>	Đại diện logic riêng từng coin
Analyst AI	Dispatcher đa coin
Signal Hub	Gateway quyết định có gửi lệnh không

🎯 Lợi ích chuẩn V5:
Mỗi AI độc lập → dễ mở rộng 10–50 coin

Không vòng lặp chéo → dễ sửa lỗi

Log rõ ràng → dễ gỡ bug

Có thể thêm chiến lược mới không ảnh hưởng hệ thống cũ
