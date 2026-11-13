# Hướng dẫn cho Agent – báo cáo & slide BTL số 2 (SGP bằng SAT)

## Bối cảnh
- Môn: Các vấn đề hiện đại KHMT, HK I 2026–2027. Đề tài: Social Golfer Problem (SGP).
- Tác giả: Mai Hải Thành (24021627), Bùi Đình Cảnh (24021392).
- Repo mã nguồn: https://github.com/thnhmai06/SAT-SGP (.NET 10: `src/Domain`, `src/Solvers/{Sat,Cp,Ilp}`, `src/Benchmarks`).
- Yêu cầu của thầy: `/Users/khach/Documents/HOBO/Các vấn đề hiện đại/Assignment 2 - requirements.pdf`
  và mẫu `Mau xay dung bao cao BTL so 1 và BTL so 2.pdf`.

## Yêu cầu bắt buộc của báo cáo
1. Trình bày như một bài báo khoa học, `\documentclass[a4paper,fleqn]{cas-sc}` (Elsevier).
2. Cấu trúc theo mẫu: Abstract, Keywords, Introduction, Background, phương pháp (SAT encoding),
   Computational Experiments, Conclusion, CRediT, Declaration of competing interest,
   **Data availability** (ghi link GitHub), Declaration of AI use, References.
3. So sánh SAT với **Cplex CP, Cplex MIP, Gurobi, CP-SAT**.
4. Thực nghiệm trên instance kích thước lớn; khuyến khích so sánh các encoding AMO/ALO
   (binary, commander, product, sequential counter, pairwise).
5. Hình vẽ kết quả dùng thư viện Python **cnsplots** (https://cnsplots.farid.one/latest/);
   đọc tài liệu của nó trước khi viết code vẽ, không đoán API.
6. SAT solver tham khảo: CaDiCaL, Glucose, Kissat, CryptoMiniSAT (PySAT hoặc gọi trực tiếp).
   Phương pháp encoding SGP lấy theo bài báo thầy chỉ định (chưa có trong repo – hỏi nhóm).

## Quy ước làm việc
- Không bịa số liệu, tên bài báo, DOI hay kết quả. Chưa có dữ liệu thì để `\TODO{...}`.
- Mọi con số trong báo cáo phải truy được về file CSV/log trong repo; bảng sinh ra đặt ở
  `report/generated/`, hình ở `report/figures/`.
- Ký hiệu nhất quán với mã nguồn: Player, Group, Round, Match; bộ ba $g$-$s$-$w$.
- Báo cáo viết tiếng Việt (giống BTL1); giữ thuật ngữ kỹ thuật tiếng Anh khi chuẩn.
- Biên dịch: XeLaTeX + BibTeX (trên Overleaf chọn compiler XeLaTeX). Máy local hiện chưa cài TeX.
- Khai báo AI trung thực ở mục cuối báo cáo.
- Chỉ sửa trong `docs/`; không đụng `src/` của repo nhóm nếu chưa được yêu cầu.

## Cấu trúc
- `report/main.tex`, `report/references.bib`, `report/figures/`, `report/generated/`
- `slides/main.tex` (Beamer 16:9), `slides/figures/`
- Tham khảo cách làm BTL1: `/Users/khach/Documents/HOBO/Các vấn đề hiện đại/NQueens_BTL1/report/`

## Việc còn lại (khi có code/kết quả)
1. Điền mọi `\TODO{}` trong `report/main.tex` và `slides/main.tex` (grep "TODO").
2. Viết script sinh bảng/hình từ CSV benchmark (cnsplots) → `generated/`, `figures/`.
3. Bổ sung email Thành, vai trò CRediT, tài liệu tham khảo bài báo SGP.
4. Biên dịch, kiểm tra không còn TODO, số trang, trích dẫn đủ.
