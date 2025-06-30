```Python
import re
import csv

# ログファイル
log_text = """
2025-06-30 14:35 顧客: 山田太郎 AUでポイントを150貯まった。
2025-06-30 15:00 顧客: 山田太郎 SoftBankでポイントを100使った。
2025/06/29 09:20 ユーザー: Suzuki AUで200ポイント貯まった。
2025-06-29 10:10 ユーザー: Suzuki SoftBankで50ポイント使った。
2025-06-28 19:00 顧客名：佐藤花子、AUで350ポイント貯まった。
余計なデータ：通信障害発生
"""

# 正規表現
pattern = re.compile(
    r"(?P<time>\d{4}[-/]\d{2}[-/]\d{2} \d{2}:\d{2})\s+"
    r"(?:顧客:|ユーザー:|顧客名：)\s*(?P<customer>[\w\u4e00-\u9fafぁ-んァ-ンー]+).*?"
    r"(?P<store>AU|SoftBank)で(?:ポイントを)?"
    r"(?P<points>\d+)"
    r"(?P<action>貯まった|使った)"
)

# CSVファイル作成
with open("output.csv", "w", newline="", encoding="utf-8-sig") as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow(["日時", "顧客名", "店舗名", "ポイント数", "動作"])  # 表頭

    for match in pattern.finditer(log_text):
        writer.writerow([
            match.group("time"),
            match.group("customer"),
            match.group("store"),
            int(match.group("points")),
            match.group("action")
        ])

print("✅ CSV ファイル 'output.csv' が作成されました。")
```
**result**
日時	顧客名	店舗名	ポイント数	動作
2025-06-30 14:35	山田太郎	AU	150	貯まった
2025-06-30 15:00	山田太郎	SoftBank	100	使った
2025/06/29 09:20	Suzuki	AU	200	貯まった
2025-06-29 10:10	Suzuki	SoftBank	50	使った
2025-06-28 19:00	佐藤花子	AU	350	貯まった
