<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>عجلة الحظ - متجر سات مصر</title>
    <!-- الخطوط والأيقونات -->
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
    <!-- html2canvas للصور -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <style>
        /* متغيرات الألوان - خاصة بالعجلة */
        :root {
            --ink: #0f172a;
            --muted: #475569;
            --brand1: #00c2ff;
            --brand2: #6a5cff;
            --spin1: #1e90ff;
            --spin2: #0b5ed7;
            --shot1: #22c55e;
            --shot2: #16a34a;
            --line: rgba(15, 23, 42, 0.10);
        }

        /* إعادة تعيين بسيط */
        * {
            box-sizing: border-box;
        }
        body {
            margin: 0;
            padding: 0;
            font-family: 'Cairo', system-ui, Arial, sans-serif;
            background: #fff;
            color: var(--ink);
            -webkit-text-size-adjust: 100%;
            text-size-adjust: 100%;
        }

        /* حاوية العجلة – يمكن وضعها في أي مكان دون التأثير على باقي الصفحة */
        .page {
            width: 100%;
            max-width: 980px;
            margin: 0 auto;
            padding: 10px 12px 22px;
            background: #fff;
        }

        /* رأس العجلة */
        .head {
            text-align: center;
            margin: 6px 0 8px;
        }
        .title {
            font-weight: 900;
            font-size: clamp(18px, 5.5vw, 26px);
            margin: 0 0 6px;
            background: linear-gradient(135deg, var(--brand1), var(--brand2));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .hint {
            color: var(--muted);
            font-size: clamp(12px, 3.6vw, 14px);
            margin: 0 auto;
            max-width: 880px;
            line-height: 1.7;
        }

        /* محاذاة العجلة */
        .wheel-wrap {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 12px;
            margin-top: 12px;
        }
        .wheel-center {
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .wheel-stage {
            position: relative;
            width: min(420px, 92vw);
            aspect-ratio: 1/1;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0;
            background: #fff;
        }
        canvas {
            width: 100%;
            height: 100%;
            display: block;
            border-radius: 999px;
            box-shadow: none;
            background: transparent;
            touch-action: manipulation;
        }

        /* الأزرار */
        .btn {
            width: min(420px, 92vw);
            border: 0;
            border-radius: 14px;
            padding: 12px 14px;
            cursor: pointer;
            font-family: 'Cairo', sans-serif;
            font-weight: 900;
            font-size: 15px;
            color: #fff;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        .btn:disabled {
            opacity: 0.55;
            cursor: not-allowed;
        }
        .btn.spin {
            background: linear-gradient(135deg, var(--spin1), var(--spin2));
        }
        .btn.shot {
            background: linear-gradient(135deg, var(--shot1), var(--shot2));
        }

        /* صندوق النتيجة */
        .result {
            width: min(420px, 92vw);
            text-align: center;
            font-weight: 900;
            padding: 10px 12px;
            border-radius: 14px;
            border: 1px dashed rgba(15, 23, 42, 0.15);
            background: rgba(0, 194, 255, 0.05);
            color: #0b1220;
            display: none;
            line-height: 1.7;
            font-size: 14px;
        }
        .result.show {
            display: block;
        }

        /* معلومات إضافية */
        .meta {
            width: min(420px, 92vw);
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            color: var(--muted);
            font-size: 13px;
            flex-wrap: nowrap;
        }
        .pill {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 8px 12px;
            border-radius: 999px;
            font-weight: 900;
            font-size: 12px;
            color: #0b1220;
            background: linear-gradient(90deg, rgba(0, 194, 255, 0.14), rgba(106, 92, 255, 0.14));
            border: 1px solid rgba(0, 194, 255, 0.18);
            white-space: nowrap;
        }
        .pill i {
            background: linear-gradient(135deg, var(--brand1), var(--brand2));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            color: transparent;
        }
        .device-pill {
            border: 1px solid rgba(15, 23, 42, 0.12);
            background: #f8fafc;
            direction: ltr;
        }
        .device-pill .dv-label {
            font-weight: 900;
        }
        .device-pill .dv-code {
            font-weight: 900;
            letter-spacing: 0.6px;
        }

        /* بطاقات النسب المتغيرة */
        .prob-wrap {
            width: min(420px, 92vw);
            border: 1px solid var(--line);
            border-radius: 16px;
            padding: 12px;
            background: linear-gradient(180deg, rgba(0, 194, 255, 0.06), rgba(106, 92, 255, 0.04));
        }
        .prob-title {
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 900;
            margin: 0 0 10px;
            font-size: 14px;
            color: #0b1220;
        }
        .prob-title i {
            background: linear-gradient(135deg, var(--brand1), var(--brand2));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            color: transparent;
        }
        .cards {
            display: grid;
            grid-template-columns: 1fr;
            gap: 10px;
        }
        .card {
            border: 1px solid rgba(15, 23, 42, 0.10);
            background: #fff;
            border-radius: 14px;
            padding: 10px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 10px;
        }
        .card .left {
            display: flex;
            align-items: center;
            gap: 8px;
            min-width: 0;
            flex: 1;
        }
        .badge-icon {
            width: 30px;
            height: 30px;
            border-radius: 10px;
            display: grid;
            place-items: center;
            background: linear-gradient(135deg, var(--brand1), var(--brand2));
            color: #fff;
            flex: 0 0 auto;
            font-size: 14px;
        }
        .label {
            font-weight: 900;
            font-size: 13px;
            color: #0b1220;
            line-height: 1.3;
            white-space: normal;
            overflow: visible;
        }
        .pct {
            font-weight: 900;
            font-size: 12px;
            padding: 6px 10px;
            border-radius: 999px;
            background: linear-gradient(135deg, #1e90ff, #0b5ed7);
            color: #fff;
            border: 1px solid rgba(30, 144, 255, 0.25);
            white-space: nowrap;
            flex: 0 0 auto;
        }
        .prob-note {
            margin-top: 10px;
            color: #475569;
            font-size: 12px;
            line-height: 1.7;
            text-align: center;
        }

        @media (max-width: 420px) {
            .btn { font-size: 14px; }
            .result { font-size: 13px; }
            .meta { flex-wrap: wrap; }
        }

        /* ===== لم نخفي أي عناصر خارجية ===== */
        /* تم إزالة جميع قواعد الإخفاء التي كانت موجودة سابقاً */
    </style>
</head>
<body>
    <!-- اسم المنتج – يبقى ظاهراً كما هو -->
    <h1 id="details_name" class="details_name" style="direction: rtl; text-align: center; display: block; width: 100%;">
        <span class="product-name-single">عجلة الحظ</span>
    </h1>

    <!-- لعبة عجلة الحظ -->
    <div class="page">
        <div class="head">
            <div class="title">🎡 عجلة الحظ</div>
            <p class="hint">شارك معنا في تدوير عجلة الحظ للاستفادة من الخصومات والعروض 🎁</p>
        </div>

        <div class="wheel-wrap">
            <div class="wheel-center">
                <div class="wheel-stage" id="wheelOnly">
                    <canvas id="wheelCanvas"></canvas>
                </div>
            </div>

            <button class="btn spin" id="spinBtn" type="button">
                <i class="fa-solid fa-rotate-right"></i> تدوير العجلة
            </button>
            <button class="btn shot" id="shotBtn" type="button" disabled>
                <i class="fa-solid fa-camera"></i> إرسال سكرين شوت
            </button>

            <div class="result" id="resultBox">&mdash;</div>

            <div class="meta">
                <span id="spinsInfo" class="pill"><i class="fa-solid fa-circle-info"></i> المحاولات المتبقية: --</span>
                <span id="deviceInfo" class="pill device-pill">
                    <i class="fa-solid fa-fingerprint"></i>
                    <span class="dv-label">Device:</span>
                    <span class="dv-code">&mdash;</span>
                </span>
            </div>

            <div class="prob-wrap">
                <div class="prob-title"><i class="fa-solid fa-chart-pie"></i> نسب الفوز المعروضة (تقديرية)</div>
                <div class="cards" id="probCards"></div>
                <div class="prob-note" id="probNote"></div>
            </div>
        </div>
    </div>

    <!-- ===== عناصر المنتج والنموذج (تبقى ظاهرة تماماً) ===== -->
    <!-- سعر المنتج -->
    <div class="price-container" style="text-align: center; direction: rtl;">
        <span class="product-price">
            <span class="price-label">سعر المنتج :</span>
            <span class="product-price-current-number">0</span>
            <span>جنيه</span>
        </span>
    </div>

    <!-- الأزرار تحت السعر -->
    <div class="action-buttons">
        <div class="btn-box whatsapp-btn" onclick="sendWhatsAppMessage()"><i class="fab fa-whatsapp"></i> واتساب</div>
        <div class="btn-box share-btn" onclick="shareProduct()"><i class="fas fa-share-alt"></i> مشاركة</div>
    </div>

    <!-- viewers count -->
    <div class="viewers-container">
        <div>👁️ <span class="viewers-count">107</span> شخص يشاهد هذا المنتج الآن</div>
        <div class="discount-text">استفد من الخصم الآن قبل انتهاء العرض</div>
    </div>

    <h3>" تنفيذ الطلب الآن "</h3>

    <!-- إطار عرض الإجمالي -->
    <div class="shipping-info-frame active" id="shippingInfoFrame">
        <div class="shipping-row"><span class="shipping-label">سعر المنتج:</span> <span class="shipping-value" id="productPriceDisplay">0 جنيه</span></div>
        <div class="shipping-row"><span class="shipping-label">سعر الشحن:</span> <span class="shipping-value" id="shippingPriceDisplay">75 جنيه</span></div>
        <div class="shipping-row"><span class="shipping-label">الإجمالي:</span> <span class="shipping-value shipping-total" id="totalPriceDisplay">75 جنيه</span></div>
    </div>

    <!-- نموذج الطلب -->
    <form id="orderForm">
        <label for="name">الاسم الثلاثي</label>
        <input type="text" id="name" required>
        <label for="phone">الرقم الأساسي</label>
        <input type="tel" id="phone" required>
        <label for="altPhone">الرقم الاحتياطي (اختياري)</label>
        <input type="tel" id="altPhone">
        <label for="address">العنوان</label>
        <textarea id="address" required></textarea>
        <label for="governorate">المحافظة</label>
        <select id="governorate" required>
            <option value="القاهرة">القاهرة - 75 جنيه</option>
            <option value="الجيزة">الجيزة - 75 جنيه</option>
            <option value="القليوبية">القليوبية - 85 جنيه</option>
            <option value="الفيوم">الفيوم - 85 جنيه</option>
            <option value="المنوفية">المنوفية - 85 جنيه</option>
            <option value="البحيرة">البحيرة - 85 جنيه</option>
            <option value="بني سويف">بني سويف - 85 جنيه</option>
            <option value="الشرقية">الشرقية - 85 جنيه</option>
            <option value="الإسماعيلية">الإسماعيلية - 85 جنيه</option>
            <option value="الدقهلية">الدقهلية - 85 جنيه</option>
            <option value="السويس">السويس - 85 جنيه</option>
            <option value="الغربية">الغربية - 85 جنيه</option>
            <option value="كفر الشيخ">كفر الشيخ - 85 جنيه</option>
            <option value="دمياط">دمياط - 85 جنيه</option>
            <option value="بورسعيد">بورسعيد - 85 جنيه</option>
            <option value="الإسكندرية">الإسكندرية - 85 جنيه</option>
            <option value="مرسى مطروح">مرسى مطروح - 110 جنيه</option>
            <option value="البحر الأحمر">البحر الأحمر - 110 جنيه</option>
            <option value="المنيا">المنيا - 110 جنيه</option>
            <option value="أسيوط">أسيوط - 110 جنيه</option>
            <option value="سوهاج">سوهاج - 110 جنيه</option>
            <option value="قنا">قنا - 110 جنيه</option>
            <option value="الأقصر">الأقصر - 120 جنيه</option>
            <option value="أسوان">أسوان - 120 جنيه</option>
            <option value="الوادي الجديد">الوادي الجديد - 120 جنيه</option>
            <option value="شمال سيناء">شمال سيناء - 120 جنيه</option>
            <option value="جنوب سيناء">جنوب سيناء - 120 جنيه</option>
        </select>
        <div class="button-container"><button type="button" class="order-button" onclick="sendToWhatsApp()">تنفيذ الطلب</button></div>
    </form>

    <!-- الشريط السفلي -->
    <div class="bottom-bar">
        <div class="menu-toggle-btn" id="menuToggleBtn"><span></span><span></span><span></span></div>
        <button class="buy-now-btn" onclick="sendWhatsAppMessage()">شراء هذا المنتج الآن</button>
        <div class="cart-box" onclick="sendWhatsAppMessage()">
            <div class="cart-count">1</div>
            <img src="https://cdn-icons-png.flaticon.com/512/3737/3737372.png" alt="سلة التسوق">
        </div>
    </div>

    <script>
        (function() {
            // ---------- الإعدادات الثابتة ----------
            const WHATSAPP_NUMBER = "201126766088"; // رقم الواتساب
            const MAX_SPINS_PER_WINDOW = 2;          // أقصى عدد دورات كل 6 ساعات
            const SPIN_WINDOW_MS = 6 * 60 * 60 * 1000; // 6 ساعات

            // شرائح العجلة (6 شرائح)
            const SEGMENTS = [
                { key: "try",   label: "حظ سعيد المرة القادمة", short: "حظ سعيد",        icon: "fa-face-smile",        cardIcon: "fa-face-smile" },
                { key: "50",    label: "خصم 50 جنيه",           short: "خصم 50ج",         icon: "fa-tags",              cardIcon: "fa-tags" },
                { key: "ship",  label: "شحن مجاني",             short: "شحن مجاني",       icon: "fa-truck-fast",        cardIcon: "fa-truck-fast" },
                { key: "gift",  label: "اشتراك هدية للتليفون",  short: "اشتراك هدية",     icon: "fa-gift",              cardIcon: "fa-gift" },
                { key: "5p",    label: "خصم 5% عند شراء جهازين", short: "خصم 5% (جهازين)", icon: "fa-percent",           cardIcon: "fa-percent" },
                { key: "cash",  label: "كاش باك 100 جنيه عند شراء جهاز اخر", short: "كاش باك 100ج", icon: "fa-money-bill-wave", cardIcon: "fa-money-bill-wave" }
            ];

            // ألوان متدرجة للشرائح (6 ألوان)
            const GRADS = [
                ["#38bdf8", "#2563eb"],
                ["#22c55e", "#16a34a"],
                ["#f59e0b", "#f97316"],
                ["#a855f7", "#7c3aed"],
                ["#ef4444", "#fb7185"],
                ["#06b6d4", "#0ea5e9"]
            ];

            // الاحتمالات الحقيقية (مجموعها 100%)
            const PROB = {
                try: 79,          // حظ سعيد
                p5: 8,            // خصم 5% (جهازين)
                cash: 1,          // كاش باك 100ج
                eachOther: 4      // كل من الخيارات الثلاثة الأخرى (خصم 50، شحن مجاني، هدية)
            };

            // ---------- المتغيرات العامة ----------
            let currentRotation = 0;
            let isSpinning = false;
            let lastResult = null;
            let deviceCode = null;

            // عناصر DOM
            const canvas = document.getElementById("wheelCanvas");
            const ctx = canvas.getContext("2d");
            const spinBtn = document.getElementById("spinBtn");
            const shotBtn = document.getElementById("shotBtn");
            const spinsInfo = document.getElementById("spinsInfo");
            const deviceInfo = document.getElementById("deviceInfo");
            const deviceCodeEl = deviceInfo.querySelector(".dv-code");
            const resultBox = document.getElementById("resultBox");
            const wheelOnly = document.getElementById("wheelOnly");
            const probCards = document.getElementById("probCards");
            const probNote = document.getElementById("probNote");

            // ---------- دوال مساعدة للجهاز والتخزين ----------
            function makeDeviceCode12() {
                const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
                let out = "";
                const arr = new Uint8Array(12);
                // استخدام crypto إن أمكن، وإلا تعبئة عشوائية
                if (crypto && crypto.getRandomValues) {
                    crypto.getRandomValues(arr);
                } else {
                    for (let i = 0; i < 12; i++) arr[i] = Math.floor(Math.random() * 255);
                }
                for (let i = 0; i < 12; i++) out += chars[arr[i] % chars.length];
                return out;
            }

            function getDeviceCode() {
                const key = "mw_device_code_v1";
                let code = localStorage.getItem(key);
                if (code && /^[A-Z0-9]{12}$/.test(code)) return code;
                code = makeDeviceCode12();
                localStorage.setItem(key, code);
                try {
                    document.cookie = `${key}=${code}; max-age=${60 * 60 * 24 * 365}; path=/; SameSite=Lax`;
                } catch (e) {}
                return code;
            }

            // ---------- إدارة المحاولات ----------
            function getSpinTimestamps() {
                try {
                    const v = JSON.parse(localStorage.getItem("mw_spin_ts_v6h") || "[]");
                    return Array.isArray(v) ? v.filter(n => Number.isFinite(n)) : [];
                } catch {
                    return [];
                }
            }

            function setSpinTimestamps(list) {
                localStorage.setItem("mw_spin_ts_v6h", JSON.stringify(list));
            }

            function pruneOldSpins(list) {
                const now = Date.now();
                return list.filter(ts => (now - ts) < SPIN_WINDOW_MS);
            }

            function spinsLeft() {
                const list = pruneOldSpins(getSpinTimestamps());
                setSpinTimestamps(list);
                return Math.max(0, MAX_SPINS_PER_WINDOW - list.length);
            }

            function addSpinNow() {
                const list = pruneOldSpins(getSpinTimestamps());
                list.push(Date.now());
                setSpinTimestamps(list);
                return list.length;
            }

            function updateSpinUI() {
                const left = spinsLeft();
                spinsInfo.innerHTML = `<i class="fa-solid fa-circle-info"></i> المحاولات المتبقية (كل 6 ساعات): <b>${left}</b> / ${MAX_SPINS_PER_WINDOW}`;
                spinBtn.disabled = (left <= 0) || isSpinning;
            }

            // ---------- رسم العجلة ----------
            function resizeCanvasOnly() {
                const dpr = window.devicePixelRatio || 1;
                const rect = canvas.getBoundingClientRect();
                const size = Math.floor(Math.min(rect.width, rect.height));
                canvas.width = Math.floor(size * dpr);
                canvas.height = Math.floor(size * dpr);
                ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
            }

            function drawWheel(rotation) {
                const rect = canvas.getBoundingClientRect();
                const size = Math.min(rect.width, rect.height); // الحجم المنطقي (CSS)
                const cx = size / 2;
                const cy = size / 2;
                const radius = size / 2;

                ctx.clearRect(0, 0, size, size);
                ctx.direction = "rtl";

                const segCount = SEGMENTS.length; // 6
                const segAngle = (Math.PI * 2) / segCount;
                const startBase = -Math.PI / 2 + rotation; // نبدأ من الأعلى

                for (let i = 0; i < segCount; i++) {
                    const start = startBase + i * segAngle;
                    const end = start + segAngle;

                    // رسم القطاع
                    ctx.beginPath();
                    ctx.moveTo(cx, cy);
                    ctx.arc(cx, cy, radius, start, end);
                    ctx.closePath();

                    const grad = ctx.createLinearGradient(cx - radius, cy - radius, cx + radius, cy + radius);
                    grad.addColorStop(0, GRADS[i][0]);
                    grad.addColorStop(1, GRADS[i][1]);
                    ctx.fillStyle = grad;
                    ctx.fill();

                    ctx.strokeStyle = "rgba(255,255,255,0.92)";
                    ctx.lineWidth = 2;
                    ctx.stroke();

                    // النص المختصر
                    const mid = start + segAngle / 2;
                    const isLong = (SEGMENTS[i].key === "5p" || SEGMENTS[i].key === "cash");
                    const textRadius = radius * (isLong ? 0.62 : 0.70);
                    const x = cx + Math.cos(mid) * textRadius;
                    const y = cy + Math.sin(mid) * textRadius;

                    ctx.save();
                    ctx.textAlign = "center";
                    ctx.textBaseline = "middle";
                    ctx.fillStyle = "rgba(255,255,255,0.98)";
                    ctx.font = `900 ${Math.max(12, size * 0.033)}px Cairo`;
                    ctx.fillText(SEGMENTS[i].short, x, y);
                    ctx.restore();
                }

                // الدائرة الداخلية (المؤشر)
                const hubR = radius * 0.20;
                ctx.beginPath();
                ctx.arc(cx, cy, hubR, 0, Math.PI * 2);
                ctx.fillStyle = "#ffffff";
                ctx.fill();
                ctx.beginPath();
                ctx.arc(cx, cy, hubR, 0, Math.PI * 2);
                ctx.strokeStyle = "rgba(15,23,42,0.12)";
                ctx.lineWidth = 2;
                ctx.stroke();

                // رسم مثلث المؤشر
                const badgeR = hubR * 0.76;
                const cg = ctx.createLinearGradient(cx - badgeR, cy - badgeR, cx + badgeR, cy + badgeR);
                cg.addColorStop(0, "#1e90ff");
                cg.addColorStop(1, "#0b5ed7");
                ctx.beginPath();
                ctx.arc(cx, cy, badgeR, 0, Math.PI * 2);
                ctx.fillStyle = cg;
                ctx.fill();
                ctx.beginPath();
                ctx.arc(cx, cy, badgeR, 0, Math.PI * 2);
                ctx.strokeStyle = "#ffffff";
                ctx.lineWidth = 1.5;
                ctx.stroke();

                ctx.save();
                ctx.translate(cx, cy);
                const triTop = -badgeR * 0.62;
                const triLeftX = -badgeR * 0.38;
                const triRightX = badgeR * 0.38;
                const triBaseY = -badgeR * 0.10;
                ctx.beginPath();
                ctx.moveTo(0, triTop);
                ctx.lineTo(triLeftX, triBaseY);
                ctx.lineTo(triRightX, triBaseY);
                ctx.closePath();
                ctx.fillStyle = "#ffffff";
                ctx.fill();
                ctx.restore();

                ctx.beginPath();
                ctx.arc(cx, cy, badgeR * 0.11, 0, Math.PI * 2);
                ctx.fillStyle = "#ffffff";
                ctx.fill();
            }

            function resizeAndDraw() {
                resizeCanvasOnly();
                drawWheel(currentRotation);
            }

            // ---------- اختيار النتيجة حسب الاحتمالات ----------
            function pickIndex() {
                const r = Math.random() * 100;
                if (r < PROB.try) return 0;                 // 79% حظ سعيد
                const b1 = PROB.try + PROB.p5;               // 87%
                if (r < b1) return 4;                         // 8% خصم 5%
                const b2 = b1 + PROB.cash;                    // 88%
                if (r < b2) return 5;                          // 1% كاش باك
                // 12% المتبقية موزعة على 3 شرائح (خصم 50، شحن مجاني، هدية)
                const rr = r - b2; // 0..12
                if (rr < PROB.eachOther) return 1;            // خصم 50
                if (rr < PROB.eachOther * 2) return 2;        // شحن مجاني
                return 3;                                      // هدية
            }

            // ---------- دالة الدوران مع حركة سلسة ----------
            function easeOutCubic(t) {
                return 1 - Math.pow(1 - t, 3);
            }

            function spin() {
                if (isSpinning) return;
                const left = spinsLeft();
                if (left <= 0) {
                    updateSpinUI();
                    return;
                }
                addSpinNow();
                isSpinning = true;
                shotBtn.disabled = true;
                updateSpinUI();

                const pickedIndex = pickIndex();
                const segCount = SEGMENTS.length;
                const segAngle = (Math.PI * 2) / segCount;
                const offset = (0.18 + Math.random() * 0.64) * segAngle; // إزاحة عشوائية داخل القطاع
                const targetSegmentAngle = pickedIndex * segAngle + offset; // الزاوية المطلوبة داخل العجلة
                // نحول الزاوية إلى قيمة طبيعية (من 0 إلى 2PI) حيث تكون العقبة في الأعلى
                const targetNorm = (Math.PI * 2 - targetSegmentAngle) % (Math.PI * 2);
                const fullSpins = 6 + Math.floor(Math.random() * 3); // 6-8 لفات كاملة
                const currentNorm = ((currentRotation % (Math.PI * 2)) + (Math.PI * 2)) % (Math.PI * 2);
                const delta = (targetNorm - currentNorm + (Math.PI * 2)) % (Math.PI * 2);
                const targetRotation = currentRotation + fullSpins * (Math.PI * 2) + delta;

                const startRotation = currentRotation;
                const duration = 4200; // 4.2 ثانية
                const startTime = performance.now();

                function frame(now) {
                    const t = Math.min(1, (now - startTime) / duration);
                    const e = easeOutCubic(t);
                    currentRotation = startRotation + (targetRotation - startRotation) * e;
                    drawWheel(currentRotation);
                    if (t < 1) {
                        requestAnimationFrame(frame);
                    } else {
                        isSpinning = false;
                        updateSpinUI();
                        lastResult = SEGMENTS[pickedIndex];
                        resultBox.textContent = `✅ النتيجة: ${lastResult.label}`;
                        resultBox.classList.add("show");
                        addResult(lastResult.key);
                        renderProbCards(); // تحديث البطاقات (اختياري)
                        shotBtn.disabled = false;
                    }
                }
                requestAnimationFrame(frame);
            }

            // ---------- تخزين النتائج (اختياري) ----------
            const RESULTS_KEY = "mw_spin_results_v1";
            function getResults() {
                try {
                    const v = JSON.parse(localStorage.getItem(RESULTS_KEY) || "[]");
                    return Array.isArray(v) ? v : [];
                } catch {
                    return [];
                }
            }
            function setResults(list) {
                localStorage.setItem(RESULTS_KEY, JSON.stringify(list));
            }
            function pruneResults(list) {
                const now = Date.now();
                return list.filter(x => x && Number.isFinite(x.t) && typeof x.k === "string" && (now - x.t) < SPIN_WINDOW_MS).slice(-200);
            }
            function addResult(key) {
                const list = pruneResults(getResults());
                list.push({ t: Date.now(), k: key });
                setResults(list);
            }

            // ---------- تحديث بطاقات النسب المتغيرة (كل 15 ثانية) ----------
            function renderProbCards() {
                // توليد 6 أرقام عشوائية مجموعها 100
                let points = [0];
                for (let i = 0; i < 5; i++) points.push(Math.floor(Math.random() * 101));
                points.sort((a, b) => a - b);
                points.push(100);
                const pcts = [
                    points[1] - points[0],
                    points[2] - points[1],
                    points[3] - points[2],
                    points[4] - points[3],
                    points[5] - points[4],
                    points[6] - points[5]
                ];

                const items = [
                    { name: "خصم 50 جنيه", pct: pcts[0], icon: "fa-tags" },
                    { name: "شحن مجاني", pct: pcts[1], icon: "fa-truck-fast" },
                    { name: "اشتراك هدية للتليفون", pct: pcts[2], icon: "fa-gift" },
                    { name: "خصم 5% عند شراء جهازين", pct: pcts[3], icon: "fa-percent" },
                    { name: "كاش باك 100 جنيه عند شراء جهاز اخر", pct: pcts[4], icon: "fa-money-bill-wave" },
                    { name: "حظ سعيد المرة القادمة", pct: pcts[5], icon: "fa-face-smile" }
                ];

                probCards.innerHTML = items.map(it => `
                    <div class="card">
                        <div class="left">
                            <span class="badge-icon"><i class="fa-solid ${it.icon}"></i></span>
                            <div class="label">${it.name}</div>
                        </div>
                        <div class="pct">${it.pct}%</div>
                    </div>
                `).join("");

                const now = new Date();
                probNote.innerHTML = `Results of participation (${now.toLocaleDateString('en-US')} ${now.toLocaleTimeString('en-US')})`;
            }

            // ---------- التقاط الشاشة وإرسالها ----------
            async function createWheelShot1024() {
                // التأكد من تحميل الخطوط إن أمكن
                if (document.fonts && document.fonts.ready) {
                    try { await document.fonts.ready; } catch (e) {}
                }
                // التقاط صورة للعنصر wheelOnly
                const uiCanvas = await html2canvas(wheelOnly, {
                    scale: 3,
                    backgroundColor: "#ffffff",
                    useCORS: true
                });

                const out = document.createElement("canvas");
                out.width = 1024;
                out.height = 1024;
                const octx = out.getContext("2d");
                octx.fillStyle = "#ffffff";
                octx.fillRect(0, 0, 1024, 1024);

                const padding = 24;
                const barH = 170;
                const wheelSize = Math.min(1024 - padding * 2, (1024 - barH) - padding * 2);
                const wheelX = (1024 - wheelSize) / 2;
                const wheelY = 16;

                octx.imageSmoothingEnabled = true;
                octx.imageSmoothingQuality = "high";
                octx.drawImage(uiCanvas, wheelX, wheelY, wheelSize, wheelSize);

                const resultText = lastResult ? lastResult.label : "—";
                const codeText = deviceCode;
                const now = new Date();
                const dtText = now.toLocaleString("ar-EG", {
                    year: "numeric", month: "2-digit", day: "2-digit",
                    hour: "2-digit", minute: "2-digit", second: "2-digit"
                });

                const barY = 1024 - barH;
                octx.save();
                octx.fillStyle = "rgba(15,23,42,0.78)";
                octx.fillRect(0, barY, 1024, barH);
                octx.textAlign = "center";
                octx.textBaseline = "middle";
                octx.font = "900 34px Cairo";
                octx.fillStyle = "#ffffff";
                octx.fillText(`النتيجة: ${resultText}`, 512, barY + barH * 0.32);
                octx.font = "900 30px Cairo";
                octx.fillStyle = "#e2e8f0";
                octx.fillText(`Device: ${codeText}`, 512, barY + barH * 0.62);
                octx.font = "900 26px Cairo";
                octx.fillStyle = "#cbd5e1";
                octx.fillText(`التاريخ والوقت: ${dtText}`, 512, barY + barH * 0.86);
                octx.restore();

                return out;
            }

            async function sendScreenshot() {
                if (!lastResult) return;
                const shotCanvas = await createWheelShot1024();
                const blob = await new Promise(resolve => shotCanvas.toBlob(resolve, "image/png", 1.0));
                const localUrl = URL.createObjectURL(blob);

                // تحميل الصورة محلياً (اختياري)
                const a = document.createElement("a");
                a.href = localUrl;
                a.download = `wheel-${deviceCode}-${Date.now()}.png`;
                document.body.appendChild(a);
                a.click();
                a.remove();

                // فتح واتساب مع الرسالة
                const msg = `مرحباً متجر سات مصر 👋 نتيجة عجلة الحظ الخاصة بتجربتي: ${lastResult.label} ارسل سكرين شوت العجله اللي على موبايلك للاستفاده من الخصم عبر وتساب Device: ${deviceCode}`;
                const waUrl = "https://wa.me/" + WHATSAPP_NUMBER + "?text=" + encodeURIComponent(msg);
                window.open(waUrl, "_blank");

                // تنظيف الرابط
                setTimeout(() => URL.revokeObjectURL(localUrl), 1000);
            }

            // ---------- التهيئة ----------
            async function init() {
                deviceCode = getDeviceCode();
                deviceCodeEl.textContent = deviceCode;

                if (document.fonts && document.fonts.ready) {
                    try { await document.fonts.ready; } catch (e) {}
                }

                updateSpinUI();
                renderProbCards();
                // ضبط حجم اللوحة ورسم العجلة
                resizeAndDraw();

                window.addEventListener("resize", resizeAndDraw, { passive: true });

                // تحديث النسب كل 15 ثانية
                setInterval(renderProbCards, 15000);
            }

            // ربط الأحداث
            spinBtn.addEventListener("click", spin);
            shotBtn.addEventListener("click", sendScreenshot);

            // بدء التشغيل
            init();

            // دوال وهمية لتجنب أخطاء onclick (إذا لم تكن معرفة)
            window.sendWhatsAppMessage = function() { console.log("واتساب"); };
            window.shareProduct = function() { console.log("مشاركة"); };
            window.sendToWhatsApp = function() { console.log("طلب"); };
        })();
    </script>
</body>
</html>
