# Active Context: Deployment & Production Optimization

## Tráº¡ng thÃ¡i hiá»‡n táº¡i (02/12/2025)

### CÃ´ng viá»‡c Ä‘ang táº­p trung
1. **Deployment Stability**: á»”n Ä‘á»‹nh hÃ³a mÃ´i trÆ°á»ng production trÃªn Railway (Backend) vÃ  Vercel (Frontend).
2. **Automation**: Tá»‘i Æ°u hÃ³a cÃ¡c script setup vÃ  deployment (`setup-railway.ps1`, `generate-secrets.js`).
3. **Environment Configuration**: Äáº£m báº£o Ä‘á»“ng bá»™ biáº¿n mÃ´i trÆ°á»ng giá»¯a Backend, Frontend vÃ  Mobile App.
4. **Documentation**: Cáº­p nháº­t hÆ°á»›ng dáº«n deployment chi tiáº¿t vÃ  xá»­ lÃ½ sá»± cá»‘ (Crash Loop debug).

### CÃ¡c thay Ä‘á»•i gáº§n Ä‘Ã¢y
- **02/12/2025**:
  - Cáº­p nháº­t Mobile App (`app_config.dart`) sá»­ dá»¥ng URL production má»›i: `https://deploy-production-dee9.up.railway.app/api`.
  - ÄÆ¡n giáº£n hÃ³a tÃ i liá»‡u `DEPLOY.md` vÃ  thÃªm hÆ°á»›ng dáº«n tá»± Ä‘á»™ng hÃ³a.
  - ThÃªm `setup-railway.ps1` script Ä‘á»ƒ há»— trá»£ setup environment variables vÃ  secrets.
  - ThÃªm `vercel.json` (hoáº·c config tÆ°Æ¡ng Ä‘Æ°Æ¡ng) Ä‘á»ƒ há»— trá»£ SPA routing trÃªn Vercel.
  - ThÃªm hÆ°á»›ng dáº«n fix lá»—i Railway Root Directory vÃ  Crash Loop.
- **24/11/2025**:
  - TÃ­ch há»£p AI Chat vá»›i Google Gemini API.
  - HoÃ n thiá»‡n MoMo Payment Gateway integration.

### Milestones gáº§n nháº¥t
- âœ… **Deployment**: Backend deploy thÃ nh cÃ´ng lÃªn Railway.
- âœ… **Deployment**: Frontend deploy thÃ nh cÃ´ng lÃªn Vercel.
- âœ… **Mobile**: App build release trá» vá» production server.
- âœ… **Automation**: HoÃ n thÃ nh bá»™ script há»— trá»£ deployment (secrets generation, env check).
- âœ… **Documentation**: HoÃ n thiá»‡n `DEPLOY.md` vÃ  hÆ°á»›ng dáº«n debug.

## Æ¯u tiÃªn hiá»‡n táº¡i

### High Priority (Deployment & Operations)
1. **Monitor Stability**: Theo dÃµi stability cá»§a Backend trÃªn Railway, Ä‘áº·c biá»‡t lÃ  memory usage vÃ  crash loops.
2. **Env Var Sync**: Äáº£m báº£o khi thay Ä‘á»•i URL backend/frontend, táº¥t cáº£ environment variables (CORS, Redirect URLs) Ä‘Æ°á»£c cáº­p nháº­t Ä‘á»“ng bá»™.
3. **Mobile Release**: Test ká»¹ báº£n build release APK vá»›i server production.

### Medium Priority (Maintenance)
1. **Automated Tests**: Cháº¡y suite test tá»± Ä‘á»™ng trÃªn environment production (sá»­ dá»¥ng `test-railway-api.js`).
2. **Backup Strategy**: Thiáº¿t láº­p backup Ä‘á»‹nh ká»³ cho MongoDB Atlas.

## Váº¥n Ä‘á» cáº§n giáº£i quyáº¿t ngáº¯n háº¡n
- Kiá»ƒm tra vÃ  xá»­ lÃ½ cÃ¡c lá»—i tiá»m áº©n khi chuyá»ƒn tá»« development (localhost) sang production (HTTPS/Railway).
- Äáº£m báº£o CORS configuration trÃªn Railway cho phÃ©p domain Vercel truy cáº­p.
- XÃ¡c nháº­n MoMo IPN hoáº¡t Ä‘á»™ng Ä‘Ãºng trÃªn mÃ´i trÆ°á»ng production (public URL).

## Dependencies & Tools
- **Railway**: Hosting Backend API.
- **Vercel**: Hosting Frontend Web App.
- **MongoDB Atlas**: Cloud Database.
- **PowerShell**: Cháº¡y script setup trÃªn Windows.
- **Node.js**: Runtime cho automation scripts.

## Blockers hiá»‡n táº¡i
- KhÃ´ng cÃ³ blockers nghiÃªm trá»ng.
- LÆ°u Ã½: Cáº§n cáº­p nháº­t thá»§ cÃ´ng IPN URL trong MoMo config náº¿u Ä‘á»•i domain Railway.

## HÃ nh Ä‘á»™ng cá»¥ thá»ƒ (Next Steps)
1. Cháº¡y `test-railway-api.js` Ä‘á»ƒ verify backend health.
2. Kiá»ƒm tra káº¿t ná»‘i tá»« Frontend (Vercel) tá»›i Backend (Railway).
3. Thá»±c hiá»‡n giao dá»‹ch thá»­ nghiá»‡m (MoMo) trÃªn mÃ´i trÆ°á»ng production.
4. Review logs trÃªn Railway dashboard náº¿u cÃ³ sá»± cá»‘.

---
*Cáº­p nháº­t láº§n cuá»‘i: 02/12/2025*

## Boi canh hien tai: Bao cao Do an Mon KTPM

### Luu y nguoi dung da chot cho bao cao
- Gioi han bao cao duoi 35 trang.
- Hinh thuc trinh bay theo quy trinh trinh bay bao cao do an.
- Cau truc bao cao gom: Bia, lot bia, nhan xet GVHD, danh muc hinh, cac chuong noi dung, tai lieu tham khao.
- Chuong 1 chi gioi thieu ngan gon ve san pham va cac chuc nang se dung cho cac chuong ben duoi.
- Chuong 2 chi mo ta thiet ke test case cho cac chuc nang o Chuong 1; khong dua toan bo test case vao Word/PDF, luu trong file Excel.
- Moi chuc nang o Chuong 2 phai co it nhat 10 test case va dung template chung.
- Quy uoc phan cong o Chuong 2: 2 nguoi la mot chuc nang.
- Chuong 3 ap dung thiet ke test case black box cho 4 chuc nang khac nhau.
- Chuong 3 phai dung it nhat 3 ky thuat black box.
- Chuong 3 phai co mo ta yeu cau truoc khi phan tich va khong gop phan phan tich vao bang test case.
- Chuong 4 ap dung white box cho 4 chuc nang khac nhau.
- Chuong 4 phai co du 4 tieu chi: 1 chuc nang phu duong, 1 chuc nang phu nhanh, 1 chuc nang phu dieu kien, 1 chuc nang phu nhanh va dieu kien.
- Chuong 5 la unit test cho cac chuc nang da phan tich; trong bao cao chi chup ket qua sau khi chay, phan demo thuc hien truc tiep khi cham.
- Chuong 6 hien thuc: mo ta ngan viec tim hieu cong cu/tool va cai dat.
- Phan demo test tu dong voi cac chuc nang da viet test case khong dua vao Word/PDF, chi demo truc tiep khi cham.
- Chuong ket luan la chuong cuoi truoc tai lieu tham khao.

### He qua khi chinh bao cao
- Moi noi dung bao cao phai uu tien ngan gon, dung khung mon hoc, tranh dua chi tiet code/test case day du vao PDF.
- Khi sua cac chuong, phai kiem tra tinh nhat quan giua so chuc nang o Chuong 1, Chuong 2, Black Box, White Box va Unit Test.
- Neu co noi dung cu trong repo mau thuan voi khung tren, uu tien khung nguoi dung vua cung cap.

## Chuan bi Chuong 3: Black Box

### Nguon tai lieu da doc
- Folder tai lieu: `C:\Users\Admin\Desktop\BaoCaoKiemThu\BAITAPKIEMTHU`
- Tep lien quan truc tiep cho Chuong 3:
- `04.Bai04.ThietkeTestCaseBackBox (1).pptx`
- `TemplateTest.xlsx`

### Dinh huong noi dung Chuong 3
- Chuong 3 phai ap dung thiet ke test case black box cho 4 chuc nang khac nhau.
- Phai co mo ta yeu cau truoc khi phan tich.
- Khong gop phan phan tich ky thuat vao bang test case.
- Phai dung it nhat 3 ky thuat black box trong cac ky thuat giang vien da day.

### Cac ky thuat Black Box giang vien day
- Phan vung tuong duong (Equivalence Partitioning).
- Phan tich gia tri bien (Boundary Value Analysis).
- Bang quyet dinh (Decision Table).
- Dich chuyen trang thai (State Transition).

### Ghi nho cach ap dung tung ky thuat
- Phan vung tuong duong: chia input thanh nhom hop le va khong hop le; moi nhom can co it nhat 1 test case dai dien.
- Gia tri bien: uu tien cac moc min, min+1, gia tri binh thuong, max-1, max va cac gia tri vuot bien neu co rang buoc.
- Bang quyet dinh: dung cho logic nghiep vu co nhieu dieu kien lien quan nhau; liet ke dieu kien, gia tri cua dieu kien, hanh dong/ket qua mong doi va rut gon cac quy tac trung ket qua.
- Dich chuyen trang thai: dung cho chuc nang ma ket qua phu thuoc trang thai hien tai hoac lich su thao tac truoc do.

### Cach trinh bay nen dung trong bao cao
- Bat dau moi chuc nang bang mo ta yeu cau/nghiep vu ngan gon.
- Sau do trinh bay phan tich black box theo ky thuat da chon.
- Cuoi cung moi anh xa sang danh sach test case tong hop neu can.
- Khong dua full bang test case Excel vao Word/PDF; trong bao cao chi nen tom tat cach phan tich va ket qua thiet ke.

### Mau TemplateTest.xlsx dang goi y
- Cac cot cot loi gom: ID, Items, Sub-items, Description, PreCondition, Steps to Execute, Expected output.
- Co them cac cot theo doi thuc thi/bao loi nhu: Passed, Failed, Date, BugID, Note.
- Co cac cot moi truong/thiet bi trinh duyet de danh dau khi chay test.

### Huong chuan bi noi dung tiep theo
- Khi viet Chuong 3, uu tien chon 4 chuc nang co nghiep vu ro rang de de tach yeu cau va ap dung ky thuat.
- Nen phan bo ky thuat sao cho toan chuong co it nhat 3 ky thuat khac nhau; co the dung 1 ky thuat cho 1 chuc nang hoac ket hop nhieu ky thuat trong cung 1 chuc nang.
- Neu chuc nang co luat nghiep vu nhieu nhanh, uu tien Bang quyet dinh.
- Neu chuc nang co input theo khoang gia tri, uu tien Gia tri bien va Phan vung tuong duong.
- Neu chuc nang phu thuoc buoc truoc-sau hay trang thai tai khoan/don hang, uu tien Dich chuyen trang thai.
