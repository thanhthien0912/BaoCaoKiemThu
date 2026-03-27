# Active Context: Deployment & Production Optimization

## Trạng thái hiện tại (02/12/2025)

### Công việc đang tập trung
1. **Deployment Stability**: Ổn định hóa môi trường production trên Railway (Backend) và Vercel (Frontend).
2. **Automation**: Tối ưu hóa các script setup và deployment (`setup-railway.ps1`, `generate-secrets.js`).
3. **Environment Configuration**: Đảm bảo đồng bộ biến môi trường giữa Backend, Frontend và Mobile App.
4. **Documentation**: Cập nhật hướng dẫn deployment chi tiết và xử lý sự cố (Crash Loop debug).

### Các thay đổi gần đây
- **02/12/2025**:
  - Cập nhật Mobile App (`app_config.dart`) sử dụng URL production mới: `https://deploy-production-dee9.up.railway.app/api`.
  - Đơn giản hóa tài liệu `DEPLOY.md` và thêm hướng dẫn tự động hóa.
  - Thêm `setup-railway.ps1` script để hỗ trợ setup environment variables và secrets.
  - Thêm `vercel.json` (hoặc config tương đương) để hỗ trợ SPA routing trên Vercel.
  - Thêm hướng dẫn fix lỗi Railway Root Directory và Crash Loop.
- **24/11/2025**:
  - Tích hợp AI Chat với Google Gemini API.
  - Hoàn thiện MoMo Payment Gateway integration.

### Milestones gần nhất
- ✅ **Deployment**: Backend deploy thành công lên Railway.
- ✅ **Deployment**: Frontend deploy thành công lên Vercel.
- ✅ **Mobile**: App build release trỏ về production server.
- ✅ **Automation**: Hoàn thành bộ script hỗ trợ deployment (secrets generation, env check).
- ✅ **Documentation**: Hoàn thiện `DEPLOY.md` và hướng dẫn debug.

## Ưu tiên hiện tại

### High Priority (Deployment & Operations)
1. **Monitor Stability**: Theo dõi stability của Backend trên Railway, đặc biệt là memory usage và crash loops.
2. **Env Var Sync**: Đảm bảo khi thay đổi URL backend/frontend, tất cả environment variables (CORS, Redirect URLs) được cập nhật đồng bộ.
3. **Mobile Release**: Test kỹ bản build release APK với server production.

### Medium Priority (Maintenance)
1. **Automated Tests**: Chạy suite test tự động trên environment production (sử dụng `test-railway-api.js`).
2. **Backup Strategy**: Thiết lập backup định kỳ cho MongoDB Atlas.

## Vấn đề cần giải quyết ngắn hạn
- Kiểm tra và xử lý các lỗi tiềm ẩn khi chuyển từ development (localhost) sang production (HTTPS/Railway).
- Đảm bảo CORS configuration trên Railway cho phép domain Vercel truy cập.
- Xác nhận MoMo IPN hoạt động đúng trên môi trường production (public URL).

## Dependencies & Tools
- **Railway**: Hosting Backend API.
- **Vercel**: Hosting Frontend Web App.
- **MongoDB Atlas**: Cloud Database.
- **PowerShell**: Chạy script setup trên Windows.
- **Node.js**: Runtime cho automation scripts.

## Blockers hiện tại
- Không có blockers nghiêm trọng.
- Lưu ý: Cần cập nhật thủ công IPN URL trong MoMo config nếu đổi domain Railway.

## Hành động cụ thể (Next Steps)
1. Chạy `test-railway-api.js` để verify backend health.
2. Kiểm tra kết nối từ Frontend (Vercel) tới Backend (Railway).
3. Thực hiện giao dịch thử nghiệm (MoMo) trên môi trường production.
4. Review logs trên Railway dashboard nếu có sự cố.

---
*Cập nhật lần cuối: 02/12/2025*