# Session 09 - Bài 02

Config Server chạy ở `8888`, Pharmacy-Service ở `8090`. Cấu hình dùng trong bài nằm tại `pharmacy-config-repo/pharmacy-service.properties` và được Config Server đọc từ Git của repo này. PostgreSQL chạy ở cổng `5433`.

## Chạy

```bash
git status --short
git add pharmacy-config-repo/pharmacy-service.properties
git commit -m 'Update pharmacy config'
cd config-server && gradle bootRun
```

Terminal khác:

```bash
docker compose up -d
cd pharmacy-service && gradle bootRun
```

## Bài 02

BillController tính VAT từ `pharmacy.vat-rate`. Sửa giá trị trong Git, commit, sau đó gọi `POST http://localhost:8090/actuator/refresh`; lần tính hóa đơn kế tiếp dùng mức VAT mới.

Ví dụ: `curl -X POST localhost:8090/api/v1/bill -H 'Content-Type: application/json' -d '{"medicineTotal":100000}'`.
