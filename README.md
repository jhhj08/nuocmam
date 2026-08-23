<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ổ Bán Nước Mắm - Danh Sách Nhân Vật</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: #0f0e0c; color: #e0d8cc; padding: 24px 16px; min-height: 100vh; }
        header { text-align: center; margin-bottom: 24px; position: relative; }
        header h1 { color: #f59e0b; font-size: 2.2rem; margin-bottom: 8px; font-weight: 800; letter-spacing: -0.5px; }
        header p { color: #a8a29e; font-size: 0.95rem; }
        
        .container { max-width: 1100px; margin: 0 auto; }
        
        /* Notice Banner */
        .notice-banner {
            background: linear-gradient(135deg, rgba(69, 26, 3, 0.6), rgba(28, 25, 23, 0.9));
            border: 1px solid rgba(245, 158, 11, 0.4);
            border-radius: 16px;
            padding: 16px 20px;
            margin-bottom: 24px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        }
        .notice-header { display: flex; align-items: center; justify-content: space-between; gap: 12px; margin-bottom: 8px; flex-wrap: wrap; }
        .notice-tag { background: rgba(245, 158, 11, 0.2); color: #f59e0b; font-size: 11px; font-weight: 800; text-transform: uppercase; padding: 3px 8px; border-radius: 6px; }
        .notice-time { color: #a8a29e; font-size: 12px; }
        .notice-content { font-size: 14px; color: #f5f5f4; line-height: 1.6; }

        /* Tag Filter Bar */
        .filter-section { margin-bottom: 24px; background: #1c1917; padding: 16px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.08); }
        .filter-title { font-size: 0.85rem; color: #a8a29e; margin-bottom: 10px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.5px; }
        .tag-list { display: flex; flex-wrap: wrap; gap: 8px; max-height: 120px; overflow-y: auto; padding-right: 4px; }
        .tag-btn { background: #292524; color: #d6d3d1; border: 1px solid rgba(255,255,255,0.1); padding: 5px 12px; border-radius: 20px; font-size: 0.8rem; cursor: pointer; transition: all 0.2s; }
        .tag-btn:hover, .tag-btn.active { background: #f59e0b; color: #000; font-weight: 700; border-color: #f59e0b; }

        /* Search input */
        .search-box { margin-bottom: 16px; }
        .search-box input { width: 100%; background: #0f0e0c; border: 1px solid rgba(255,255,255,0.15); color: #fff; padding: 10px 16px; border-radius: 10px; font-size: 0.9rem; outline: none; }
        .search-box input:focus { border-color: #f59e0b; }

        .character-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 24px; }
        
        .card { 
            background: #1c1917; 
            border: 1px solid rgba(255, 255, 255, 0.1); 
            border-radius: 16px; 
            overflow: hidden; 
            box-shadow: 0 10px 25px rgba(0,0,0,0.5); 
            transition: transform 0.25s ease, box-shadow 0.25s ease, border-color 0.25s ease; 
            display: flex; 
            flex-direction: column; 
        }
        .card:hover { 
            transform: translateY(-5px); 
            box-shadow: 0 15px 30px rgba(217, 119, 6, 0.15); 
            border-color: rgba(245, 158, 11, 0.4); 
        }
        
        .img-container { width: 100%; height: 280px; overflow: hidden; position: relative; background: #000; }
        .card-img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.4s ease; }
        .card:hover .card-img { transform: scale(1.05); }
        
        .card-body { padding: 18px; display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between; }
        .card-title { font-size: 1.25rem; font-weight: 700; color: #ffffff; margin-bottom: 4px; }
        .card-creator { font-size: 0.75rem; color: #f59e0b; font-weight: 600; margin-bottom: 8px; text-transform: uppercase; letter-spacing: 0.5px; }
        .card-tags { display: flex; flex-wrap: wrap; gap: 4px; margin-bottom: 12px; }
        .badge-tag { background: rgba(245, 158, 11, 0.15); color: #fcd34d; font-size: 0.7rem; padding: 2px 8px; border-radius: 6px; border: 1px solid rgba(245, 158, 11, 0.2); }
        
        .card-desc { font-size: 0.85rem; color: #a8a29e; margin-bottom: 16px; line-height: 1.5; flex-grow: 1; }
        
        .card-actions { display: flex; align-items: center; justify-content: space-between; gap: 10px; margin-top: auto; }
        .btn-visit { 
            flex-grow: 1; 
            background: linear-gradient(135deg, #f59e0b, #d97706); 
            color: #000000; 
            text-decoration: none; 
            padding: 10px 14px; 
            border-radius: 10px; 
            text-align: center; 
            font-size: 0.85rem; 
            font-weight: 700; 
            text-transform: uppercase; 
            letter-spacing: 0.5px; 
            transition: opacity 0.2s, transform 0.1s; 
        }
        .btn-visit:hover { opacity: 0.92; }
        .btn-visit:active { transform: scale(0.97); }
        
        .like-btn { 
            background: rgba(244, 63, 94, 0.1); 
            border: 1px solid rgba(244, 63, 94, 0.3); 
            color: #fb7185; 
            padding: 8px 14px; 
            border-radius: 10px; 
            cursor: pointer; 
            display: flex; 
            align-items: center; 
            gap: 6px; 
            font-weight: 700; 
            font-size: 0.9rem; 
            transition: all 0.2s; 
        }
        .like-btn:hover { background: rgba(244, 63, 94, 0.2); border-color: rgba(244, 63, 94, 0.6); transform: scale(1.05); }
        .like-btn.liked { background: rgba(244, 63, 94, 0.3); border-color: rgba(244, 63, 94, 0.8); opacity: 0.75; cursor: default; }

        /* Carousel Navigation Buttons */
        .carousel-btn {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0, 0, 0, 0.65);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.2);
            width: 32px;
            height: 32px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.2s;
            z-index: 10;
        }
        .carousel-btn:hover { background: #f59e0b; color: black; }
        .carousel-btn.prev { left: 8px; }
        .carousel-btn.next { right: 8px; }
        .img-indicator {
            position: absolute;
            bottom: 8px;
            right: 8px;
            background: rgba(0,0,0,0.7);
            color: #f59e0b;
            font-size: 11px;
            font-weight: bold;
            padding: 2px 8px;
            border-radius: 12px;
            border: 1px solid rgba(245, 158, 11, 0.3);
            z-index: 10;
        }

        /* User Message Form */
        .mailbox-section { margin-top: 40px; background: #1c1917; border: 1px solid rgba(255,255,255,0.1); border-radius: 16px; padding: 24px; box-shadow: 0 10px 25px rgba(0,0,0,0.5); }
        .mailbox-section h2 { color: #f59e0b; font-size: 1.3rem; margin-bottom: 8px; }
        .mailbox-section p { color: #a8a29e; font-size: 0.85rem; margin-bottom: 16px; }
        .form-group { margin-bottom: 12px; }
        .form-group label { display: block; font-size: 0.8rem; color: #d6d3d1; margin-bottom: 4px; font-weight: 600; }
        .form-control { width: 100%; background: #0f0e0c; border: 1px solid rgba(255,255,255,0.15); color: #fff; padding: 10px 14px; border-radius: 8px; font-size: 0.9rem; outline: none; }
        .form-control:focus { border-color: #f59e0b; }
        textarea.form-control { resize: vertical; min-height: 90px; }
        .btn-submit { background: #f59e0b; color: #000; border: none; padding: 10px 20px; border-radius: 8px; font-weight: 700; cursor: pointer; transition: opacity 0.2s; }
        .btn-submit:hover { opacity: 0.9; }

        /* Admin Trigger & Modals */
        .admin-trigger { margin-top: 20px; text-align: center; }
        .btn-admin-open { background: transparent; color: #78716c; border: 1px dashed #78716c; padding: 6px 14px; border-radius: 8px; font-size: 0.8rem; cursor: pointer; transition: all 0.2s; }
        .btn-admin-open:hover { color: #f59e0b; border-color: #f59e0b; }

        .modal-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.85); backdrop-filter: blur(4px); display: none; justify-content: center; align-items: center; z-index: 1000; padding: 16px; }
        .modal-box { background: #1c1917; border: 1px solid rgba(245, 158, 11, 0.3); border-radius: 16px; width: 100%; max-width: 650px; max-height: 90vh; overflow-y: auto; padding: 24px; box-shadow: 0 20px 40px rgba(0,0,0,0.8); }
        .modal-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 12px; }
        .modal-header h3 { color: #f59e0b; font-size: 1.3rem; }
        .close-btn { background: none; border: none; color: #a8a29e; font-size: 1.5rem; cursor: pointer; }
        .close-btn:hover { color: #fff; }

        /* Admin Tabs */
        .admin-tabs { display: flex; gap: 8px; margin-bottom: 20px; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 8px; }
        .tab-btn { background: #292524; color: #a8a29e; border: none; padding: 8px 16px; border-radius: 8px; font-size: 0.85rem; font-weight: 600; cursor: pointer; }
        .tab-btn.active { background: #f59e0b; color: #000; }
        .tab-content { display: none; }
        .tab-content.active { display: block; }

        .tag-checkboxes { display: grid; grid-template-columns: repeat(auto-fill, minmax(110px, 1fr)); gap: 6px; max-height: 140px; overflow-y: auto; background: #0f0e0c; padding: 10px; border-radius: 8px; border: 1px solid rgba(255,255,255,0.1); margin-top: 6px; }
        .tag-checkboxes label { font-size: 0.75rem; color: #d6d3d1; display: flex; align-items: center; gap: 4px; cursor: pointer; }

        .msg-card { background: #0f0e0c; border: 1px solid rgba(255,255,255,0.08); border-radius: 10px; padding: 12px; margin-bottom: 10px; }
        .msg-head { display: flex; justify-content: space-between; margin-bottom: 6px; font-size: 0.8rem; }
        .msg-user { color: #f59e0b; font-weight: 700; }
        .msg-time { color: #78716c; }
        .msg-body { font-size: 0.85rem; color: #e0d8cc; white-space: pre-wrap; line-height: 1.4; }
        .btn-del-msg { background: rgba(244, 63, 94, 0.2); color: #fb7185; border: none; padding: 3px 8px; border-radius: 4px; font-size: 0.7rem; cursor: pointer; margin-top: 8px; }

        footer { text-align: center; margin-top: 40px; padding: 20px; font-size: 0.8rem; color: #78716c; border-top: 1px solid rgba(255, 255, 255, 0.05); }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>Ổ Bán Nước Mắm 🏺</h1>
        <p>Sáng lập bởi Bà Bán Nước Mắm (60°N Đạm) • Chọn nhân vật để khám phá</p>
    </header>

    <!-- Notice Banner -->
    <div class="notice-banner" id="noticeBanner">
        <div class="notice-header">
            <span class="notice-tag">📢 Thông Báo Quan Trọng Từ Admin</span>
            <span class="notice-time" id="noticeTime">Đăng lúc: 14:30 - 22/08/2026</span>
        </div>
        <div class="notice-content" id="noticeContent">Chào mừng bạn đến với Ổ Bán Nước Mắm (60°N Đạm)! Các nhân vật sẽ được cập nhật và làm mới thường xuyên trực tiếp trên web. Mọi góp ý hoặc yêu cầu thêm nhân vật xin vui lòng gửi thư cho Admin ở cuối trang.</div>
    </div>

    <!-- Filter & Search Section -->
    <div class="filter-section">
        <div class="search-box">
            <input type="text" id="searchInput" placeholder="🔍 Tìm kiếm nhân vật theo tên hoặc tag..." oninput="handleSearch()">
        </div>
        <div class="filter-title">Lọc theo thể loại / tag:</div>
        <div class="tag-list" id="tagFilterList"></div>
    </div>

    <!-- Character Cards Grid -->
    <div class="character-grid" id="characterApp"></div>

    <!-- User Mailbox Section -->
    <div class="mailbox-section">
        <h2>✉️ Gửi Thư Cho Admin</h2>
        <p>Gửi góp ý, yêu cầu thêm nhân vật hoặc lời nhắn nhủ cho Admin tại đây nhé!</p>
        <form id="userMailForm" onsubmit="handleSendMail(event)">
            <div class="form-group">
                <label>Tên / Biệt danh của bạn:</label>
                <input type="text" id="mailSender" class="form-control" placeholder="Nhập tên của bạn..." required>
            </div>
            <div class="form-group">
                <label>Nội dung thư / Lời nhắn:</label>
                <textarea id="mailContent" class="form-control" placeholder="Nhập nội dung lời nhắn tại đây..." required></textarea>
            </div>
            <button type="submit" class="btn-submit">Gửi Thư Ngay 📤</button>
        </form>
    </div>

    <!-- Admin Trigger Button -->
    <div class="admin-trigger">
        <button class="btn-admin-open" onclick="openAdminModal()">🔑 Quản Trị Admin</button>
    </div>

    <footer>
        <p>Bản quyền thuộc về Bà Bán Nước Mắm (60°N Đạm) • Chưng cất thủ công</p>
    </footer>
</div>

<!-- Password Modal -->
<div class="modal-overlay" id="passwordModal">
    <div class="modal-box" style="max-width: 400px;">
        <div class="modal-header">
            <h3>Xác Minh Admin</h3>
            <button class="close-btn" onclick="closeModal('passwordModal')">&times;</button>
        </div>
        <form onsubmit="verifyAdminPass(event)">
            <div class="form-group">
                <label>Mật khẩu Bảng Quản Trị:</label>
                <input type="password" id="adminPassInput" class="form-control" placeholder="Nhập mật khẩu..." required>
            </div>
            <button type="submit" class="btn-submit" style="width: 100%; margin-top: 10px;">Mở Khóa Bảng Admin</button>
        </form>
    </div>
</div>

<!-- Admin Panel Modal -->
<div class="modal-overlay" id="adminPanelModal">
    <div class="modal-box">
        <div class="modal-header">
            <h3>⚙️ Bảng Quản Trị Admin</h3>
            <button class="close-btn" onclick="closeModal('adminPanelModal')">&times;</button>
        </div>

        <div class="admin-tabs">
            <button class="tab-btn active" onclick="switchTab('tabChars')">Nhân Vật</button>
            <button class="tab-btn" onclick="switchTab('tabNotice')">Thông Báo</button>
            <button class="tab-btn" onclick="switchTab('tabMailbox')">Hộp Thư (<span id="unreadMailCount">0</span>)</button>
        </div>

        <!-- Tab 1: Quản lý nhân vật -->
        <div id="tabChars" class="tab-content active">
            <h4 style="color: #f59e0b; margin-bottom: 12px;" id="formCharTitle">Thêm Nhân Vật Mới</h4>
            <form id="charForm" onsubmit="handleSaveChar(event)">
                <input type="hidden" id="editCharId" value="">
                <div class="form-group">
                    <label>Tên nhân vật:</label>
                    <input type="text" id="charName" class="form-control" required>
                </div>
                <div class="form-group">
                    <label>Người tạo (Mặc định: Admin):</label>
                    <input type="text" id="charCreator" class="form-control" value="Admin" placeholder="Nhập tên người tạo...">
                </div>
                <div class="form-group">
                    <label>Trích dẫn / Mô tả ngắn:</label>
                    <input type="text" id="charDesc" class="form-control" required>
                </div>
                <div class="form-group">
                    <label>Link ảnh (Mỗi link một dòng hoặc cách nhau bằng dấu phẩy):</label>
                    <textarea id="charImages" class="form-control" required placeholder="https://link-anh-1.jpg&#10;https://link-anh-2.jpg"></textarea>
                </div>
                <div class="form-group">
                    <label>Link chuyển hướng (URL khi bấm Chọn nhân vật):</label>
                    <input type="url" id="charRedirect" class="form-control" required>
                </div>
                <div class="form-group">
                    <label>Chọn Tag / Thể loại có sẵn:</label>
                    <div class="tag-checkboxes" id="tagCheckboxContainer"></div>
                </div>
                <div class="form-group">
                    <label>Tự nhập thêm Tag (cách nhau bằng dấu phẩy):</label>
                    <input type="text" id="customTagsInput" class="form-control" placeholder="Ví dụ: Huyền huyễn, Sủng ngọt...">
                </div>
                <div style="display: flex; gap: 10px; margin-top: 16px;">
                    <button type="submit" class="btn-submit" style="flex: 1;">Lưu Nhân Vật</button>
                    <button type="button" class="btn-submit" onclick="resetCharForm()" style="background: #44403c; color: #fff;">Reset Form</button>
                </div>
            </form>

            <hr style="border-color: rgba(255,255,255,0.1); margin: 24px 0;">
            <h4 style="color: #a8a29e; margin-bottom: 12px;">Danh Sách Nhân Vật Hiện Có</h4>
            <div id="adminCharList"></div>
        </div>

        <!-- Tab 2: Quản lý thông báo -->
        <div id="tabNotice" class="tab-content">
            <h4 style="color: #f59e0b; margin-bottom: 12px;">Cập Nhật Thông Báo Trang Chủ</h4>
            <form onsubmit="handleSaveNotice(event)">
                <div class="form-group">
                    <label>Nội dung thông báo mới:</label>
                    <textarea id="noticeInput" class="form-control" style="min-height: 120px;" required></textarea>
                </div>
                <button type="submit" class="btn-submit">Đăng Thông Báo Mới 📢</button>
            </form>
        </div>

        <!-- Tab 3: Hộp thư admin -->
        <div id="tabMailbox" class="tab-content">
            <h4 style="color: #f59e0b; margin-bottom: 12px;">Danh Sách Thư Của User Send</h4>
            <div id="adminMailList"></div>
        </div>

    </div>
</div>

<script>
    // System Data & Configuration
    const ADMIN_PASS_HASH = "c82f0852613e36bdc9ec80fe5de10c4f295208544ed48031ebc5dc8418178a79"; // dmytbldeochovideotlenxuhuongtcaylamyoutubeadmm@221

    const PRESET_TAGS = [
        "BL", "GL", "Anygender", "Thanh xuân vườn trường", "Cổ trang", "Cổ xưa", "Hiện đại", 
        "Ma cà rồng", "18+", "NSFW", "Greenflag", "Redflag", "Ngược tâm", "SE", "HE", "Ngọt", 
        "Xuyên không", "Trùng sinh", "Tổng tài", "Hài hước", "Đô thị", "Lesbian", "Gay", "Đam mỹ", 
        "Lạnh lùng", "Trầm tính", "Năng động", "Ít nói", "Có vấn đề về tâm lý", "Côn trùng", 
        "Loạn luân", "Ngụy loạn luân", "NP", "Harem", "Niên hạ"
    ];

    const defaultCharacters = [
        {
            "id": "kinh-xuyen",
            "name": "Kình Xuyên",
            "creator": "Admin",
            "tags": ["Thanh xuân vườn trường", "Hiện đại", "Greenflag"],
            "desc": "”Ban đầu cứ tưởng trai hư, ai ngờ là thủ khoa trường mình.”",
            "avatar": "https://i.ibb.co/YBtjfjF3/IMG-20260822-184445.jpg",
            "images": ["https://i.ibb.co/YBtjfjF3/IMG-20260822-184445.jpg"],
            "redirectUrl": "https://aistudio.google.com/app/prompts?state=%7B%22ids%22:%5B%221C031lN-dga2kcD4nqKs1UvTwqQL2DJtQ%22%5D,%22action%22:%22open%22,%22userId%22:%22110303689433524750453%22,%22resourceKeys%22:%7B%7D%7D&usp=sharing"
        },
        {
            "id": "to-so-yen",
            "name": "Tô Sở Yên",
            "creator": "Admin",
            "tags": ["Thanh xuân vườn trường", "Hiện đại", "Ngọt"],
            "desc": "”...Chị có thể đóng giả làm chị gái em không?”",
            "avatar": "https://i.ibb.co/WW8CdQ0k/f14276cfda357e78ecf5cd12e4adad0b-1.jpg",
            "images": [
                "https://i.ibb.co/WW8CdQ0k/f14276cfda357e78ecf5cd12e4adad0b-1.jpg",
                "https://i.ibb.co/p6V085Hf/2056af053e7ef64528ce75db3a5dfe60.jpg",
                "https://i.ibb.co/MD2gQPTz/0ea3cd1dcb87b08f67d126019f6452bd.jpg",
                "https://i.ibb.co/ks1BJbft/10d03cf32f611e7e5b251d4d099cc9b7.jpg",
                "https://i.ibb.co/gZ06CSnX/75044e1e5f867daba212284b7e00a08a.jpg",
                "https://i.ibb.co/k635psqp/2a6fb4d5e05e6d9ffabe1e8a4e1903b0-1.jpg"
            ],
            "redirectUrl": "https://aistudio.google.com/app/prompts?state=%7B%22ids%22:%5B%221QPUgOCam-pShcWCJ8NmoeaUqtZeAR-QX%22%5D,%22action%22:%22open%22,%22userId%22:%22110303689433524750453%22,%22resourceKeys%22:%7B%7D%7D&usp=sharing"
        }
    ];

    // Local State Initialization
    let characterData = JSON.parse(localStorage.getItem('nuocmam_characters')) || defaultCharacters;
    let noticeData = JSON.parse(localStorage.getItem('nuocmam_notice')) || {
        content: "Chào mừng bạn đến với Ổ Bán Nước Mắm (60°N Đạm)! Các nhân vật sẽ được cập nhật và làm mới thường xuyên trực tiếp trên web. Mọi góp ý hoặc yêu cầu thêm nhân vật xin vui lòng gửi thư cho Admin ở cuối trang.",
        time: "Đăng lúc: 14:30 - 22/08/2026"
    };
    let userMails = JSON.parse(localStorage.getItem('nuocmam_user_mails')) || [];
    const likedChars = JSON.parse(localStorage.getItem('nuocmam_user_liked_chars') || '{}');
    const imageIndices = {};
    let selectedTag = "";

    // Helper SHA-256 Hash Function
    async function sha256(str) {
        const encoder = new TextEncoder();
        const data = encoder.encode(str);
        const buffer = await crypto.subtle.digest('SHA-256', data);
        return Array.from(new Uint8Array(buffer)).map(b => b.toString(16).padStart(2, '0')).join('');
    }

    // Render Tag Filter Buttons
    function renderTagFilters() {
        const container = document.getElementById('tagFilterList');
        container.innerHTML = `<button class="tag-btn ${selectedTag === '' ? 'active' : ''}" onclick="filterByTag('')">Tất cả</button>`;
        
        // Collect all active tags from preset + existing characters
        const allTagsSet = new Set(PRESET_TAGS);
        characterData.forEach(c => (c.tags || []).forEach(t => allTagsSet.add(t)));

        allTagsSet.forEach(tag => {
            const btn = document.createElement('button');
            btn.className = `tag-btn ${selectedTag === tag ? 'active' : ''}`;
            btn.innerText = tag;
            btn.onclick = () => filterByTag(tag);
            container.appendChild(btn);
        });
    }

    function filterByTag(tag) {
        selectedTag = tag;
        renderTagFilters();
        renderCharacters();
    }

    function handleSearch() {
        renderCharacters();
    }

    // Render Character Grid
    function renderCharacters() {
        const container = document.getElementById('characterApp');
        const searchKeyword = document.getElementById('searchInput').value.toLowerCase().trim();
        container.innerHTML = '';

        const filteredList = characterData.filter(char => {
            const matchesTag = !selectedTag || (char.tags && char.tags.includes(selectedTag));
            const matchesSearch = !searchKeyword || 
                char.name.toLowerCase().includes(searchKeyword) || 
                (char.tags && char.tags.some(t => t.toLowerCase().includes(searchKeyword))) ||
                (char.creator && char.creator.toLowerCase().includes(searchKeyword));
            return matchesTag && matchesSearch;
        });

        if (filteredList.length === 0) {
            container.innerHTML = `<div style="grid-column: 1/-1; text-align: center; color: #a8a29e; padding: 40px;">Không tìm thấy nhân vật phù hợp.</div>`;
            return;
        }

        filteredList.forEach((char) => {
            const charId = String(char.id);
            const isLiked = !!likedChars[charId];
            const imgs = (char.images && char.images.length > 0) ? char.images : [char.avatar];
            if (imageIndices[charId] === undefined) imageIndices[charId] = 0;
            const currentIdx = imageIndices[charId];
            const hasMultiple = imgs.length > 1;

            const tagsHtml = (char.tags || []).map(t => `<span class="badge-tag">${t}</span>`).join('');

            const card = document.createElement('div');
            card.className = 'card';
            card.innerHTML = `
                <div class="img-container" id="img-cont-${charId}">
                    <img src="${imgs[currentIdx]}" class="card-img" id="img-${charId}" alt="${char.name}" onerror="this.src='https://images.unsplash.com/photo-1544005313-94ddf0286df2?auto=format&fit=crop&w=600&q=80'" />
                    ${hasMultiple ? `
                        <button class="carousel-btn prev" onclick="prevImg('${charId}', event)">&#10094;</button>
                        <button class="carousel-btn next" onclick="nextImg('${charId}', event)">&#10095;</button>
                        <div class="img-indicator" id="ind-${charId}">${currentIdx + 1}/${imgs.length}</div>
                    ` : ''}
                </div>
                <div class="card-body">
                    <div>
                        <div class="card-creator">Người tạo: ${char.creator || 'Admin'}</div>
                        <h3 class="card-title">${char.name}</h3>
                        <div class="card-tags">${tagsHtml}</div>
                        <p class="card-desc">${char.desc}</p>
                    </div>
                    <div class="card-actions">
                        <a href="${char.redirectUrl}" target="_blank" rel="noopener noreferrer" class="btn-visit">Chọn nhân vật ↗</a>
                        <button class="like-btn ${isLiked ? 'liked' : ''}" onclick="toggleLike('${charId}', this)">
                            ❤️ <span id="like-count-${charId}">${isLiked ? 'Đã tim' : 'Tim'}</span>
                        </button>
                    </div>
                </div>
            `;
            container.appendChild(card);
        });
    }

    // Image Carousel Handlers
    window.prevImg = function(charId, e) {
        e.stopPropagation();
        const char = characterData.find(c => String(c.id) === String(charId));
        if (!char || !char.images || char.images.length <= 1) return;
        const total = char.images.length;
        imageIndices[charId] = (imageIndices[charId] - 1 + total) % total;
        document.getElementById('img-' + charId).src = char.images[imageIndices[charId]];
        document.getElementById('ind-' + charId).innerText = (imageIndices[charId] + 1) + '/' + total;
    };

    window.nextImg = function(charId, e) {
        e.stopPropagation();
        const char = characterData.find(c => String(c.id) === String(charId));
        if (!char || !char.images || char.images.length <= 1) return;
        const total = char.images.length;
        imageIndices[charId] = (imageIndices[charId] + 1) % total;
        document.getElementById('img-' + charId).src = char.images[imageIndices[charId]];
        document.getElementById('ind-' + charId).innerText = (imageIndices[charId] + 1) + '/' + total;
    };

    // Like Button Handler (1 per user)
    window.toggleLike = function(charId, btn) {
        if (likedChars[charId]) {
            alert('Bạn đã thả tim rồi!');
            return;
        }
        likedChars[charId] = true;
        localStorage.setItem('nuocmam_user_liked_chars', JSON.stringify(likedChars));
        btn.classList.add('liked');
        const countSpan = document.getElementById('like-count-' + charId);
        if (countSpan) countSpan.innerText = 'Đã tim';
    };

    // Render Notice Banner
    function renderNotice() {
        document.getElementById('noticeContent').innerText = noticeData.content;
        document.getElementById('noticeTime').innerText = noticeData.time;
    }

    // User Mail Handler
    function handleSendMail(e) {
        e.preventDefault();
        const sender = document.getElementById('mailSender').value.trim();
        const content = document.getElementById('mailContent').value.trim();
        if (!sender || !content) return;

        const now = new Date();
        const timeStr = `${now.getHours().toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')} - ${now.getDate().toString().padStart(2, '0')}/${(now.getMonth() + 1).toString().padStart(2, '0')}/${now.getFullYear()}`;

        userMails.unshift({ sender, content, time: timeStr });
        localStorage.setItem('nuocmam_user_mails', JSON.stringify(userMails));

        document.getElementById('userMailForm').reset();
        alert('Gửi thư thành công! Cảm ơn phản hồi của bạn.');
    }

    // Modal Control Functions
    function openAdminModal() {
        document.getElementById('adminPassInput').value = '';
        document.getElementById('passwordModal').style.display = 'flex';
    }

    function closeModal(modalId) {
        document.getElementById(modalId).style.display = 'none';
    }

    async function verifyAdminPass(e) {
        e.preventDefault();
        const inputPass = document.getElementById('adminPassInput').value;
        const hash = await sha256(inputPass);

        if (hash === ADMIN_PASS_HASH) {
            closeModal('passwordModal');
            document.getElementById('adminPanelModal').style.display = 'flex';
            loadAdminPanelData();
        } else {
            alert('Mật khẩu Admin không đúng!');
        }
    }

    // Admin Panel Tab Switcher
    function switchTab(tabId) {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
        
        event.target.classList.add('active');
        document.getElementById(tabId).classList.add('active');
    }

    // Load Data into Admin Panel
    function loadAdminPanelData() {
        // Tag Checkboxes
        const tagContainer = document.getElementById('tagCheckboxContainer');
        tagContainer.innerHTML = PRESET_TAGS.map(t => `<label><input type="checkbox" value="${t}"> ${t}</label>`).join('');

        // Notice Tab
        document.getElementById('noticeInput').value = noticeData.content;

        // Mailbox Tab
        renderAdminMailbox();

        // Character List
        renderAdminCharList();
    }

    // Admin Character Management
    function renderAdminCharList() {
        const container = document.getElementById('adminCharList');
        container.innerHTML = characterData.map(c => `
            <div style="background: #0f0e0c; padding: 10px; border-radius: 8px; margin-bottom: 8px; display: flex; justify-content: space-between; align-items: center;">
                <div>
                    <strong>${c.name}</strong> <span style="font-size: 0.75rem; color: #a8a29e;">(Tạo bởi: ${c.creator || 'Admin'})</span>
                </div>
                <div>
                    <button onclick="editChar('${c.id}')" style="background: #f59e0b; color: #000; border: none; padding: 4px 8px; border-radius: 4px; font-size: 0.75rem; cursor: pointer; margin-right: 4px;">Sửa</button>
                    <button onclick="deleteChar('${c.id}')" style="background: #ef4444; color: #fff; border: none; padding: 4px 8px; border-radius: 4px; font-size: 0.75rem; cursor: pointer;">Xóa</button>
                </div>
            </div>
        `).join('');
    }

    function handleSaveChar(e) {
        e.preventDefault();
        const editId = document.getElementById('editCharId').value;
        const name = document.getElementById('charName').value.trim();
        const creator = document.getElementById('charCreator').value.trim() || 'Admin';
        const desc = document.getElementById('charDesc').value.trim();
        const redirectUrl = document.getElementById('charRedirect').value.trim();
        const rawImgs = document.getElementById('charImages').value.trim().split(/[\n,]+/).map(s => s.trim()).filter(Boolean);
        
        // Collect checked tags + custom tags
        const selectedPresetTags = Array.from(document.querySelectorAll('#tagCheckboxContainer input:checked')).map(cb => cb.value);
        const customTags = document.getElementById('customTagsInput').value.split(',').map(s => s.trim()).filter(Boolean);
        const tags = Array.from(new Set([...selectedPresetTags, ...customTags]));

        if (editId) {
            // Update
            const idx = characterData.findIndex(c => String(c.id) === String(editId));
            if (idx !== -1) {
                characterData[idx] = { ...characterData[idx], name, creator, desc, redirectUrl, images: rawImgs, avatar: rawImgs[0] || '', tags };
            }
        } else {
            // Add New
            const newChar = {
                id: 'char-' + Date.now(),
                name, creator, desc, redirectUrl,
                images: rawImgs,
                avatar: rawImgs[0] || '',
                tags
            };
            characterData.unshift(newChar);
        }

        localStorage.setItem('nuocmam_characters', JSON.stringify(characterData));
        resetCharForm();
        renderAdminCharList();
        renderTagFilters();
        renderCharacters();
        alert('Lưu nhân vật thành công!');
    }

    function editChar(id) {
        const char = characterData.find(c => String(c.id) === String(id));
        if (!char) return;

        document.getElementById('editCharId').value = char.id;
        document.getElementById('charName').value = char.name;
        document.getElementById('charCreator').value = char.creator || 'Admin';
        document.getElementById('charDesc').value = char.desc;
        document.getElementById('charRedirect').value = char.redirectUrl;
        document.getElementById('charImages').value = (char.images || [char.avatar]).join('\n');
        document.getElementById('formCharTitle').innerText = 'Chỉnh Sửa Nhân Vật';

        // Check checkboxes
        const currentTags = char.tags || [];
        document.querySelectorAll('#tagCheckboxContainer input').forEach(cb => {
            cb.checked = currentTags.includes(cb.value);
        });

        const custom = currentTags.filter(t => !PRESET_TAGS.includes(t)).join(', ');
        document.getElementById('customTagsInput').value = custom;
    }

    function deleteChar(id) {
        if (!confirm('Bạn có chắc muốn xóa nhân vật này?')) return;
        characterData = characterData.filter(c => String(c.id) !== String(id));
        localStorage.setItem('nuocmam_characters', JSON.stringify(characterData));
        renderAdminCharList();
        renderTagFilters();
        renderCharacters();
    }

    function resetCharForm() {
        document.getElementById('charForm').reset();
        document.getElementById('editCharId').value = '';
        document.getElementById('charCreator').value = 'Admin';
        document.getElementById('formCharTitle').innerText = 'Thêm Nhân Vật Mới';
        document.querySelectorAll('#tagCheckboxContainer input').forEach(cb => cb.checked = false);
    }

    // Admin Notice Management
    function handleSaveNotice(e) {
        e.preventDefault();
        const content = document.getElementById('noticeInput').value.trim();
        if (!content) return;

        const now = new Date();
        const timeStr = `Đăng lúc: ${now.getHours().toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')} - ${now.getDate().toString().padStart(2, '0')}/${(now.getMonth() + 1).toString().padStart(2, '0')}/${now.getFullYear()}`;

        noticeData = { content, time: timeStr };
        localStorage.setItem('nuocmam_notice', JSON.stringify(noticeData));

        renderNotice();
        alert('Cập nhật thông báo thành công!');
    }

    // Admin Mailbox Management
    function renderAdminMailbox() {
        const container = document.getElementById('adminMailList');
        document.getElementById('unreadMailCount').innerText = userMails.length;

        if (userMails.length === 0) {
            container.innerHTML = `<div style="text-align: center; color: #a8a29e; padding: 20px;">Chưa có thư nào từ người dùng.</div>`;
            return;
        }

        container.innerHTML = userMails.map((m, idx) => `
            <div class="msg-card">
                <div class="msg-head">
                    <span class="msg-user">👤 ${m.sender}</span>
                    <span class="msg-time">🕒 ${m.time}</span>
                </div>
                <div class="msg-body">${m.content}</div>
                <button class="btn-del-msg" onclick="deleteMail(${idx})">Xóa thư</button>
            </div>
        `).join('');
    }

    function deleteMail(idx) {
        userMails.splice(idx, 1);
        localStorage.setItem('nuocmam_user_mails', JSON.stringify(userMails));
        renderAdminMailbox();
    }

    // App Initialization
    document.addEventListener('DOMContentLoaded', () => {
        renderNotice();
        renderTagFilters();
        renderCharacters();
    });
</script>
</body>
</html>
