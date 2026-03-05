


<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no"/>
<meta name="theme-color" content="#8b0000"/>
<meta name="mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>
<meta name="apple-mobile-web-app-title" content="고추직판장"/>
<meta name="application-name" content="고추직판장"/>
<meta name="description" content="고추농가 직판장 관리 앱"/>
<link rel="manifest" id="manifest-link"/>
<title>🌶️ 고추농가 직판장</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@400;600;700;900&display=swap');
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
:root{--red:#8b0000;--red2:#c0392b;--red3:#e74c3c;--bg:#fef9f9;--nav-h:58px;--hdr-h:54px}
html,body{height:100%;width:100%;overflow:hidden;font-family:'Noto Sans KR',sans-serif;background:#1a0000}
#app{position:fixed;inset:0;display:flex;flex-direction:column;height:100%;height:100dvh}
/* HEADER */
#header{flex-shrink:0;height:var(--hdr-h);background:linear-gradient(135deg,var(--red),var(--red2));padding:0 14px;display:flex;align-items:center;justify-content:space-between;gap:8px;box-shadow:0 2px 16px rgba(0,0,0,.45);z-index:10}
#logo{display:flex;align-items:center;gap:9px;flex:1;min-width:0}
#logo .le{font-size:22px;flex-shrink:0}
#logo-text h1{color:#fff;font-size:13px;font-weight:900;line-height:1;white-space:nowrap}
#logo-text p{color:#fca5a5;font-size:7px;letter-spacing:1.5px;margin-top:2px}
#back-btn{display:none;align-items:center;gap:6px;background:rgba(255,255,255,.15);border:1px solid rgba(255,255,255,.25);border-radius:10px;padding:6px 11px;color:#fff;font-size:12px;font-weight:700;cursor:pointer;font-family:inherit;flex-shrink:0}
#back-btn.show{display:flex}
#hdr-title{display:none;color:#fff;font-size:14px;font-weight:900;flex:1;text-align:center}
#hdr-title.show{display:block}
#hdr-btns{display:flex;gap:5px;flex-shrink:0}
.hbtn{border:none;border-radius:10px;padding:6px 9px;font-size:11px;font-weight:700;cursor:pointer;font-family:inherit;white-space:nowrap}
.hbtn-g{background:rgba(255,255,255,.15);color:#fff;border:1px solid rgba(255,255,255,.25)}
.hbtn-a{background:#fbbf24;color:#78350f}
/* MAIN */
#main{flex:1;overflow-y:auto;overflow-x:hidden;background:var(--bg);-webkit-overflow-scrolling:touch;position:relative}
/* NAV */
#nav{flex-shrink:0;height:var(--nav-h);display:flex;background:#fff;border-top:1px solid #fecaca;box-shadow:0 -2px 12px rgba(139,0,0,.08);padding-bottom:env(safe-area-inset-bottom,0px)}
.nb{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:2px;padding:6px 2px;border:none;background:none;cursor:pointer;font-family:inherit;color:#a8a29e;font-size:7px;font-weight:700;position:relative;transition:color .15s}
.nb.active{color:var(--red2)}
.nb .ni{font-size:18px;line-height:1}
.nb::after{content:'';position:absolute;top:0;left:25%;width:0;height:2.5px;background:var(--red2);border-radius:0 0 99px 99px;transition:width .2s}
.nb.active::after{width:50%}
/* PAGES */
.pg{display:none;padding:13px;padding-bottom:20px;min-height:100%}
.pg.active{display:block;animation:pgIn .2s ease}
@keyframes pgIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}
@keyframes fadeUp{from{opacity:0;transform:translateY(5px)}to{opacity:1;transform:none}}
#pg-detail{display:none;position:absolute;inset:0;background:var(--bg);z-index:20;overflow-y:auto;padding:13px;padding-bottom:20px}
#pg-detail.show{display:block;animation:slideIn .25s cubic-bezier(.32,1,.32,1)}
@keyframes slideIn{from{transform:translateX(100%);opacity:.5}to{transform:none;opacity:1}}
/* CARD */
.card{background:#fff;border-radius:16px;padding:14px;margin-bottom:10px;box-shadow:0 1px 6px rgba(139,0,0,.07);border:1px solid #ffe4e4}
.card-title{font-size:13px;font-weight:900;color:var(--red);margin-bottom:11px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:6px}
.card-title-edit{font-size:10px;background:#fef2f2;color:var(--red2);border:none;border-radius:7px;padding:3px 9px;font-weight:700;cursor:pointer;font-family:inherit}
/* STAT GRID */
.sgrid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:10px}
.sc{border-radius:14px;padding:12px;color:#fff;position:relative;overflow:hidden}
.sc .lbl{font-size:8.5px;font-weight:700;opacity:.75;letter-spacing:1px;text-transform:uppercase}
.sc .val{font-size:22px;font-weight:900;margin-top:3px;line-height:1}
.sc .sub{font-size:9px;opacity:.6;margin-top:2px}
.sc .ico{position:absolute;right:8px;top:8px;font-size:32px;opacity:.13}
/* BAR */
.bar-row{margin-bottom:8px}
.bar-meta{display:flex;justify-content:space-between;font-size:11px;margin-bottom:3px;color:#57534e}
.bar-meta b{color:var(--red)}
.bar-track{height:8px;background:#fef2f2;border-radius:99px;overflow:hidden}
.bar-fill{height:100%;border-radius:99px;transition:width .6s ease}
/* CHIPS */
.chips{display:flex;gap:5px;overflow-x:auto;padding-bottom:2px;margin-bottom:10px;scrollbar-width:none}
.chips::-webkit-scrollbar{display:none}
.chip{border:1.5px solid #fecaca;background:#fff;border-radius:99px;padding:5px 11px;font-size:11px;font-weight:700;color:#78716c;cursor:pointer;white-space:nowrap;font-family:inherit;transition:all .15s;flex-shrink:0}
.chip.active{background:var(--red2);border-color:var(--red2);color:#fff}
.tag{display:inline-block;padding:2px 7px;border-radius:99px;font-size:10px;font-weight:700}
.tg{background:#dcfce7;color:#16a34a}.ty{background:#fef9c3;color:#a16207}.tr{background:#fee2e2;color:#dc2626}
/* TABLE */
.tbl-wrap{overflow-x:auto;border-radius:12px;border:1px solid #fecaca}
table{width:100%;border-collapse:collapse;font-size:12px}
thead tr{background:#fef2f2}
th{padding:9px 11px;text-align:left;font-size:10px;font-weight:700;color:var(--red);letter-spacing:.5px}
td{padding:9px 11px;border-top:1px solid #fff5f5;color:#44403c}
tr:nth-child(even) td{background:#fffafa}
/* PEPPER BADGE */
.pb{display:inline-flex;align-items:center;gap:3px;padding:3px 8px;border-radius:99px;font-size:10px;font-weight:700}
.pb-r{background:#fef2f2;color:var(--red2)}.pb-g{background:#f0fdf4;color:#16a34a}
.pb-o{background:#fff7ed;color:#ea580c}.pb-d{background:#f5f5f4;color:#44403c}
/* EMPTY */
.empty{text-align:center;padding:36px 20px;color:#c4b5a5}
.empty .ei{font-size:44px;margin-bottom:10px}
.empty p{font-size:13px;font-weight:600}
/* NOTICE */
.notice-item{display:flex;gap:10px;padding:10px 12px;background:#fef9f9;border-radius:12px;border:1px solid #ffe4e4;border-left:3px solid var(--red2);margin-bottom:7px}
.nd{width:7px;height:7px;border-radius:50%;background:var(--red2);flex-shrink:0;margin-top:4px}
.nt{font-size:12px;font-weight:700;color:#1c1917}
.nb2{font-size:11px;color:#78716c;margin-top:2px;line-height:1.4}
.ntm{font-size:10px;color:#a8a29e;margin-top:3px}
/* FAB */
.fab{position:fixed;bottom:68px;right:14px;width:48px;height:48px;border-radius:99px;background:linear-gradient(135deg,var(--red),var(--red2));border:none;color:#fff;font-size:24px;cursor:pointer;box-shadow:0 4px 20px rgba(139,0,0,.45);display:none;align-items:center;justify-content:center;z-index:50;transition:transform .15s;line-height:1}
.fab:active{transform:scale(.9)}
.fab.show{display:flex}
/* OVERLAY / SHEET */
.overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.52);z-index:200;align-items:flex-end;justify-content:center}
.overlay.show{display:flex}
.sheet{background:#fff;border-radius:22px 22px 0 0;padding:20px 18px 34px;width:100%;max-width:480px;animation:shUp .28s cubic-bezier(.32,1,.32,1);max-height:92vh;overflow-y:auto}
@keyframes shUp{from{transform:translateY(100%)}to{transform:none}}
.sh{width:38px;height:4px;background:#e7e5e4;border-radius:99px;margin:0 auto 16px}
.stitle{font-size:15px;font-weight:900;color:var(--red);margin-bottom:15px;text-align:center}
.fg{margin-bottom:12px}
.fl{font-size:11px;font-weight:700;color:#57534e;margin-bottom:4px;display:block;letter-spacing:.5px}
.fi{width:100%;border:1.5px solid #fecaca;border-radius:11px;padding:10px 13px;font-size:14px;font-family:inherit;color:#1c1917;background:#fef9f9;outline:none;transition:border-color .15s}
.fi:focus{border-color:var(--red2)}
.fr{display:grid;grid-template-columns:1fr 1fr;gap:9px}
select.fi{-webkit-appearance:none;cursor:pointer}
textarea.fi{resize:vertical;min-height:80px;line-height:1.5}
.bsub{width:100%;background:linear-gradient(135deg,var(--red),var(--red2));color:#fff;border:none;border-radius:13px;padding:13px;font-size:14px;font-weight:900;font-family:inherit;cursor:pointer;margin-top:4px}
.bcan{width:100%;background:#f5f5f4;color:#78716c;border:none;border-radius:13px;padding:11px;font-size:13px;font-weight:700;font-family:inherit;cursor:pointer;margin-top:7px}
.bdel{width:100%;background:#fee2e2;color:#dc2626;border:none;border-radius:13px;padding:11px;font-size:13px;font-weight:700;font-family:inherit;cursor:pointer;margin-top:7px;display:flex;align-items:center;justify-content:center;gap:5px}
/* DATE BAR */
.date-bar{display:flex;align-items:center;justify-content:space-between;background:#fff;border-radius:13px;padding:10px 13px;margin-bottom:10px;border:1px solid #ffe4e4;box-shadow:0 1px 5px rgba(139,0,0,.06)}
.dnav{width:36px;height:36px;border:none;background:#fef2f2;border-radius:11px;font-size:20px;cursor:pointer;display:flex;align-items:center;justify-content:center;color:var(--red2);font-weight:900;flex-shrink:0;user-select:none}
.dnav:active{background:#fecaca}
.dmid{text-align:center;flex:1;padding:0 8px}
.dmain{font-size:14px;font-weight:900;color:#1c1917;line-height:1.3}
.dday{font-size:10px;color:#a8a29e;font-weight:600;margin-top:1px}
.dtbtn{font-size:9px;background:#fef2f2;color:var(--red2);border:none;border-radius:6px;padding:3px 8px;font-weight:700;cursor:pointer;font-family:inherit;margin-top:4px;display:inline-block}
/* 주문탭 저장 바 */
.order-save-bar{display:flex;gap:7px;margin-bottom:10px;background:#fff;border-radius:13px;padding:10px 13px;border:1px solid #ffe4e4;box-shadow:0 1px 5px rgba(139,0,0,.06)}
.osb-btn{flex:1;display:flex;flex-direction:column;align-items:center;gap:3px;padding:9px 4px;border:none;border-radius:11px;font-size:10px;font-weight:700;cursor:pointer;font-family:inherit}
.osb-btn span{font-size:18px}
.osb-excel{background:#e8f5e9;color:#2e7d32}
.osb-numbers{background:#e3f2fd;color:#1565c0}
.osb-all{background:linear-gradient(135deg,#fee2e2,#fecaca);color:var(--red2)}
/* SUM3 */
.sum3{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin-bottom:10px}
.s3{background:#fff;border-radius:11px;padding:10px;border:1px solid #ffe4e4;text-align:center}
.s3v{font-size:17px;font-weight:900;color:var(--red2);line-height:1}
.s3l{font-size:9px;color:#a8a29e;font-weight:600;margin-top:2px}
/* ORDER LIST */
.ol-head{display:grid;grid-template-columns:2fr 1.3fr 0.8fr 76px;gap:5px;padding:7px 10px;background:#fef2f2;border-radius:9px;margin-bottom:5px;font-size:9.5px;font-weight:700;color:var(--red)}
.oi{display:grid;grid-template-columns:2fr 1.3fr 0.8fr 76px;gap:5px;padding:9px 10px;background:#fff;border-radius:11px;border:1px solid #ffe4e4;margin-bottom:5px;align-items:center;animation:fadeUp .2s ease;cursor:pointer;transition:box-shadow .12s}
.oi:active{box-shadow:0 2px 10px rgba(139,0,0,.12)}
.oi-n{font-size:13px;font-weight:700;color:#1c1917}
.oi-p{font-size:9.5px;color:#a8a29e;margin-top:1px}
.oi-m{font-size:9.5px;color:#b8b0aa;margin-top:2px}
.abts{display:flex;gap:3px;flex-wrap:wrap}
.ab{border:none;border-radius:7px;padding:4px 7px;font-size:9.5px;font-weight:700;cursor:pointer;font-family:inherit}
.ab-ok{background:#dcfce7;color:#16a34a}.ab-del{background:#fee2e2;color:#ef4444}.ab-undo{background:#e0f2fe;color:#0369a1}
.sdot{width:7px;height:7px;border-radius:50%;display:inline-block;margin-right:3px}
.sp{background:#fbbf24}.sd{background:#10b981}
/* INVENTORY */
.iitem{display:flex;align-items:center;justify-content:space-between;padding:10px 12px;background:#fff;border-radius:11px;border:1px solid #ffe4e4;margin-bottom:7px;cursor:pointer}
.ileft{display:flex;align-items:center;gap:9px}
.iico{width:34px;height:34px;border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:18px}
.iname{font-size:13px;font-weight:700;color:#1c1917}
.istk{font-size:10px;color:#a8a29e;margin-top:1px}
.ipr{font-size:13px;font-weight:900;color:var(--red2)}
.ipu{font-size:10px;color:#a8a29e}
.sbar{width:72px;height:5px;background:#fef2f2;border-radius:99px;overflow:hidden;margin-top:4px}
.sbarf{height:100%;border-radius:99px;transition:width .5s}
/* CUSTOMER */
.csw{position:relative;margin-bottom:10px}
.csi{width:100%;border:1.5px solid #fecaca;border-radius:13px;padding:10px 13px 10px 38px;font-size:14px;font-family:inherit;color:#1c1917;background:#fff;outline:none}
.csi:focus{border-color:var(--red2)}
.csic{position:absolute;left:12px;top:50%;transform:translateY(-50%);font-size:15px;pointer-events:none}
.cc{background:#fff;border-radius:13px;border:1px solid #ffe4e4;margin-bottom:7px;overflow:hidden;cursor:pointer;animation:fadeUp .2s ease}
.cct{display:flex;align-items:center;gap:11px;padding:12px}
.cav{width:40px;height:40px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:16px;font-weight:900;color:#fff;flex-shrink:0}
.cinf{flex:1;min-width:0}
.cnam{font-size:13px;font-weight:900;color:#1c1917}
.cpho{font-size:10px;color:#6b7280;margin-top:1px}
.cpbs{display:flex;gap:3px;margin-top:4px;flex-wrap:wrap}
.crgt{text-align:right;flex-shrink:0}
.ctot{font-size:13px;font-weight:900;color:var(--red2)}
.ccnt{font-size:9.5px;color:#a8a29e;margin-top:2px}
.cgrd{font-size:10px;font-weight:700;margin-top:3px}
.gv{color:#f59e0b}.gr{color:#3b82f6}.gn{color:#10b981}
/* DETAIL */
.det-hero{background:linear-gradient(135deg,var(--red),var(--red2));border-radius:16px;padding:18px;margin-bottom:10px;display:flex;align-items:center;gap:13px;position:relative;overflow:hidden}
.det-hero::before{content:'';position:absolute;right:-20px;top:-20px;width:100px;height:100px;border-radius:50%;background:rgba(255,255,255,.06)}
.det-avatar{width:52px;height:52px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:20px;font-weight:900;color:#fff;flex-shrink:0;border:2.5px solid rgba(255,255,255,.4)}
.det-info{flex:1}
.det-name{font-size:17px;font-weight:900;color:#fff;line-height:1}
.det-phone{font-size:11px;color:#fca5a5;margin-top:3px}
.det-phone a{color:#fcd34d;text-decoration:none;font-weight:700}
.det-grade{font-size:11px;font-weight:700;margin-top:5px;background:rgba(255,255,255,.18);border-radius:99px;padding:2px 10px;display:inline-block;color:#fff}
.det-btns{display:flex;gap:6px;margin-bottom:10px;flex-wrap:wrap}
.det-btn{flex:1;min-width:52px;border:none;border-radius:11px;padding:10px 4px;font-size:9.5px;font-weight:700;cursor:pointer;font-family:inherit;display:flex;flex-direction:column;align-items:center;gap:3px}
.det-btn span{font-size:17px}
.det-btn-sms{background:#eff6ff;color:#1d4ed8}
.det-btn-kakao{background:#fef9c3;color:#78350f}
.det-btn-order{background:#fff0f0;color:var(--red2)}
.det-btn-parcel{background:#f0fdf4;color:#16a34a}
.det-btn-edit{background:#fefce8;color:#a16207}
.det-btn-del{background:#fee2e2;color:#dc2626}
.det-stat-row{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin-bottom:10px}
.dsd{background:#fff;border-radius:11px;padding:11px;border:1px solid #ffe4e4;text-align:center}
.dsdv{font-size:15px;font-weight:900;color:var(--red2)}
.dsdl{font-size:9px;color:#a8a29e;margin-top:2px;font-weight:600}
.det-order-row{display:flex;align-items:center;gap:8px;padding:9px 10px;background:#fff;border-radius:11px;border:1px solid #ffe4e4;margin-bottom:5px;cursor:pointer}
.dor-date{font-size:10px;color:#a8a29e;width:70px;flex-shrink:0}
.dor-p{flex:1}
.dor-q{font-size:12px;font-weight:700;color:#1c1917;flex-shrink:0;margin-right:6px}
.info-row{display:flex;align-items:flex-start;gap:8px;padding:8px 0;border-bottom:1px solid #fef2f2}
.info-row:last-child{border:none}
.info-lbl{font-size:10px;font-weight:700;color:#a8a29e;width:56px;flex-shrink:0;padding-top:1px}
.info-val{font-size:12px;color:#1c1917;flex:1;line-height:1.5}
.od-header{background:linear-gradient(135deg,var(--red),var(--red2));border-radius:14px;padding:15px;margin-bottom:10px;color:#fff}
.od-pepper{font-size:19px;font-weight:900;line-height:1}
.od-sub{font-size:11px;opacity:.75;margin-top:3px}
.od-price{font-size:22px;font-weight:900;margin-top:7px}
.od-priceSub{font-size:10px;opacity:.65}
/* DANGER ZONE */
.danger-zone{border:1.5px solid #fecaca;border-radius:14px;padding:13px;background:#fff;margin-bottom:10px}
.dz-title{font-size:12px;font-weight:700;color:#dc2626;margin-bottom:10px}
.dz-btn{width:100%;border:none;border-radius:10px;padding:10px;font-size:13px;font-weight:700;cursor:pointer;font-family:inherit;margin-bottom:7px;display:flex;align-items:center;justify-content:center;gap:6px}
.dz-btn:last-child{margin-bottom:0}
.dz-reset{background:#fff4f4;color:#dc2626;border:1.5px solid #fecaca}
.dz-clear-all{background:#fef2f2;color:#b91c1c;border:1.5px solid #fca5a5}
/* INV EDIT */
.inv-edit-row{display:flex;align-items:center;gap:8px;padding:10px 0;border-bottom:1px solid #fef2f2}
.inv-edit-row:last-child{border:none}
.inv-qty-btn{width:30px;height:30px;border:1.5px solid #fecaca;background:#fef2f2;border-radius:8px;font-size:16px;font-weight:900;color:var(--red2);cursor:pointer;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.inv-qty-input{width:60px;border:1.5px solid #fecaca;border-radius:8px;padding:5px 8px;font-size:14px;font-weight:700;text-align:center;font-family:inherit;color:#1c1917;background:#fff;outline:none}
.inv-qty-input:focus{border-color:var(--red2)}
/* PARCEL */
.parcel-card{background:#fff;border-radius:14px;border:1px solid #ffe4e4;padding:13px;margin-bottom:8px;cursor:pointer;animation:fadeUp .2s ease}
.parcel-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:8px}
.parcel-name{font-size:14px;font-weight:900;color:#1c1917}
.parcel-status{display:flex;align-items:center;gap:5px}
.ps-dot{width:8px;height:8px;border-radius:50%}
.ps-ready{background:#f59e0b}.ps-sent{background:#3b82f6}.ps-done{background:#10b981}
.ps-lbl{font-size:10px;font-weight:700}
.ps-ready-t{color:#f59e0b}.ps-sent-t{color:#3b82f6}.ps-done-t{color:#10b981}
.parcel-detail{display:flex;gap:8px;flex-wrap:wrap}
.pd-item{background:#fef9f9;border-radius:8px;padding:4px 8px;font-size:10px;color:#78716c;display:flex;align-items:center;gap:4px}
.pd-item b{color:#1c1917;font-weight:700}
.psum4{display:grid;grid-template-columns:repeat(4,1fr);gap:7px;margin-bottom:10px}
.ps4{background:#fff;border-radius:11px;padding:9px 5px;border:1px solid #ffe4e4;text-align:center}
.ps4v{font-size:15px;font-weight:900;color:var(--red2);line-height:1}
.ps4l{font-size:8px;color:#a8a29e;font-weight:600;margin-top:2px}
/* PRICE EDIT */
.price-edit-row{display:flex;align-items:center;gap:8px;padding:10px 0;border-bottom:1px solid #fef2f2}
.price-edit-row:last-child{border:none}
.price-input{width:90px;border:1.5px solid #fecaca;border-radius:8px;padding:6px 10px;font-size:14px;font-weight:700;text-align:right;font-family:inherit;color:#1c1917;background:#fff;outline:none}
.price-input:focus{border-color:var(--red2)}
/* PEPPER MGR */
.pepper-item-row{display:flex;align-items:center;gap:8px;padding:9px 0;border-bottom:1px solid #fef2f2}
.pepper-item-row:last-child{border:none}
.pi-emoji{width:36px;height:36px;border:1.5px solid #fecaca;border-radius:9px;text-align:center;font-size:18px;padding:0;background:#fef9f9;font-family:inherit}
.pi-name{flex:1;border:1.5px solid #fecaca;border-radius:9px;padding:7px 10px;font-size:13px;font-family:inherit;color:#1c1917;background:#fff;outline:none}
.pi-name:focus{border-color:var(--red2)}
.pi-price{width:80px;border:1.5px solid #fecaca;border-radius:9px;padding:7px 8px;font-size:13px;font-family:inherit;color:#1c1917;background:#fff;outline:none;text-align:right}
.pi-price:focus{border-color:var(--red2)}
.pi-del{width:30px;height:30px;border:none;background:#fee2e2;border-radius:8px;color:#ef4444;font-size:15px;cursor:pointer;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.pi-add-btn{width:100%;padding:10px;border:1.5px dashed #fecaca;background:#fef9f9;border-radius:11px;font-size:12px;font-weight:700;color:var(--red2);cursor:pointer;font-family:inherit;margin-top:8px}
/* SYNC BADGE */
.sync-badge{display:inline-flex;align-items:center;gap:4px;background:#dcfce7;border-radius:99px;padding:2px 8px;font-size:9px;font-weight:700;color:#16a34a}
/* MSG MODAL */
.msg-tabs{display:flex;background:#fef2f2;border-radius:12px;padding:4px;gap:4px;margin-bottom:14px}
.msg-tab{flex:1;padding:9px;border:none;border-radius:9px;font-size:12px;font-weight:700;cursor:pointer;font-family:inherit;background:transparent;color:#78716c;transition:all .2s;display:flex;align-items:center;justify-content:center;gap:5px}
.msg-tab.active-sms{background:#1d4ed8;color:#fff}
.msg-tab.active-kakao{background:#fbbf24;color:#78350f}
.quick-btns{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:10px}
.qbtn{border:1.5px solid #fecaca;background:#fef9f9;border-radius:99px;padding:5px 11px;font-size:11px;font-weight:700;color:var(--red2);cursor:pointer;font-family:inherit;white-space:nowrap;transition:all .15s}
.qbtn:active{background:var(--red2);color:#fff}
.copy-box{background:#f8faff;border:1.5px solid #bfdbfe;border-radius:12px;padding:12px;margin-bottom:12px;font-size:13px;line-height:1.6;color:#1c1917;white-space:pre-wrap;word-break:break-all}
.copy-action-row{display:flex;gap:7px;margin-bottom:12px}
.copy-btn{flex:1;padding:11px;border:none;border-radius:11px;font-size:12px;font-weight:700;cursor:pointer;font-family:inherit;display:flex;align-items:center;justify-content:center;gap:5px}
.cb-copy{background:#dbeafe;color:#1d4ed8}
.cb-kakao{background:#fef9c3;color:#92400e}
/* EXCEL BTNS */
.excel-btns{display:flex;gap:7px;flex-wrap:wrap;margin-bottom:10px}
.excel-btn{flex:1;min-width:100px;padding:11px 8px;border:none;border-radius:12px;font-size:11px;font-weight:700;cursor:pointer;font-family:inherit;display:flex;flex-direction:column;align-items:center;gap:4px}
.excel-btn span{font-size:20px}
.eb-order{background:#e8f5e9;color:#2e7d32}
.eb-cust{background:#e3f2fd;color:#1565c0}
.eb-parcel{background:#fff8e1;color:#f57f17}
.eb-all{background:linear-gradient(135deg,var(--red),var(--red2));color:#fff}
/* PWA 설치 배너 */
#pwa-banner{display:none;position:fixed;bottom:70px;left:10px;right:10px;background:linear-gradient(135deg,var(--red),var(--red2));color:#fff;border-radius:14px;padding:12px 15px;z-index:300;box-shadow:0 4px 20px rgba(139,0,0,.4);animation:fadeUp .3s ease}
#pwa-banner.show{display:flex;align-items:center;gap:10px}
#pwa-banner .pb-icon{font-size:24px;flex-shrink:0}
#pwa-banner .pb-text{flex:1}
#pwa-banner .pb-title{font-size:12px;font-weight:900}
#pwa-banner .pb-sub{font-size:10px;opacity:.8;margin-top:1px}
#pwa-banner .pb-install{background:#fff;color:var(--red2);border:none;border-radius:8px;padding:6px 12px;font-size:11px;font-weight:900;cursor:pointer;font-family:inherit;flex-shrink:0}
#pwa-banner .pb-close{background:rgba(255,255,255,.2);border:none;color:#fff;width:24px;height:24px;border-radius:50%;cursor:pointer;font-size:12px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
</style>
</head>
<body>
<div id="app">
  <!-- HEADER -->
  <div id="header">
    <button id="back-btn" onclick="goBack()">‹ 뒤로</button>
    <div id="logo">
      <span class="le">🌶️</span>
      <div id="logo-text"><h1>고추농가 직판장</h1><p>PREMIUM PEPPER FARM DIRECT MARKET</p></div>
    </div>
    <div id="hdr-title"></div>
    <div id="hdr-btns">
      <button class="hbtn hbtn-g" id="hdr-date">📅 --/--</button>
      <button class="hbtn hbtn-g" onclick="openShare()">📤</button>
      <button class="hbtn hbtn-a" onclick="openOrderModal()">＋ 주문</button>
    </div>
  </div>

  <div id="main">
    <!-- HOME -->
    <div id="pg-home" class="pg active">
      <div class="sgrid">
        <div class="sc" style="background:linear-gradient(135deg,#8b0000,#c0392b)"><div class="lbl">오늘 주문</div><div class="val" id="s-tod">0</div><div class="sub">건</div><div class="ico">📦</div></div>
        <div class="sc" style="background:linear-gradient(135deg,#b45309,#d97706)"><div class="lbl">오늘 매출</div><div class="val" id="s-sales">0</div><div class="sub">천원</div><div class="ico">💰</div></div>
        <div class="sc" style="background:linear-gradient(135deg,#065f46,#10b981)"><div class="lbl">완료</div><div class="val" id="s-done">0</div><div class="sub">건</div><div class="ico">✅</div></div>
        <div class="sc" style="background:linear-gradient(135deg,#1d4ed8,#3b82f6)"><div class="lbl">이번달 누적</div><div class="val" id="s-mon">0</div><div class="sub">천원</div><div class="ico">📈</div></div>
      </div>
      <div class="card"><div class="card-title">🌶️ 고추별 주문 현황</div><div id="home-bars"></div></div>
      <div class="card"><div class="card-title">📋 최근 주문 5건</div><div id="home-recent"></div></div>
      <div class="card">
        <div class="card-title"><span>📢 공지사항</span><button class="card-title-edit" onclick="openNoticeModal()">＋ 추가</button></div>
        <div id="notice-list"></div>
      </div>
    </div>

    <!-- ORDERS -->
    <div id="pg-orders" class="pg">
      <div class="order-save-bar">
        <div style="font-size:11px;font-weight:700;color:#78716c;align-self:center;flex-shrink:0">📋 주문내역 저장</div>
        <button class="osb-btn osb-excel" onclick="exportOrdersExcel('xlsx')"><span>📊</span>Excel</button>
        <button class="osb-btn osb-numbers" onclick="exportOrdersExcel('numbers')"><span>🔢</span>Numbers</button>
        <button class="osb-btn osb-all" onclick="exportOrdersExcel('all')"><span>💾</span>전체기간</button>
      </div>
      <div class="date-bar">
        <button class="dnav" id="btn-prev" onclick="shiftDate(-1)">&#8249;</button>
        <div class="dmid">
          <div class="dmain" id="disp-date">--</div>
          <div class="dday" id="disp-day">--</div>
          <button class="dtbtn" onclick="goToday()">오늘로</button>
        </div>
        <button class="dnav" id="btn-next" onclick="shiftDate(1)">&#8250;</button>
      </div>
      <div class="sum3">
        <div class="s3"><div class="s3v" id="d-cnt">0</div><div class="s3l">총 주문</div></div>
        <div class="s3"><div class="s3v" id="d-kg">0</div><div class="s3l">수량(kg)</div></div>
        <div class="s3"><div class="s3v" id="d-sales">0</div><div class="s3l">매출(천원)</div></div>
      </div>
      <div class="chips" id="oc">
        <button class="chip active" onclick="setOf('all',this)">전체</button>
        <button class="chip" onclick="setOf('pending',this)">⏳ 대기</button>
        <button class="chip" onclick="setOf('done',this)">✅ 완료</button>
        <div id="order-filter-chips" style="display:contents"></div>
      </div>
      <div class="ol-head"><span>고객</span><span>고추</span><span>수량</span><span>관리</span></div>
      <div id="order-body"></div>
    </div>

    <!-- CUSTOMERS -->
    <div id="pg-customers" class="pg">
      <div class="csw">
        <span class="csic">🔍</span>
        <input class="csi" id="csearch" type="text" placeholder="이름·전화번호 검색..." oninput="renderCusts()"/>
      </div>
      <div class="chips" id="cc-chips">
        <button class="chip active" onclick="setCSort('total',this)">💰 매출순</button>
        <button class="chip" onclick="setCSort('count',this)">📦 주문순</button>
        <button class="chip" onclick="setCSort('name',this)">🔤 이름순</button>
        <button class="chip" onclick="setCSort('recent',this)">🕐 최근순</button>
      </div>
      <div class="sum3">
        <div class="s3"><div class="s3v" id="c-all">0</div><div class="s3l">전체</div></div>
        <div class="s3"><div class="s3v" id="c-vip">0</div><div class="s3l">⭐ VIP</div></div>
        <div class="s3"><div class="s3v" id="c-new">0</div><div class="s3l">🌱 신규</div></div>
      </div>
      <div id="cust-list"></div>
    </div>

    <!-- INVENTORY -->
    <div id="pg-inventory" class="pg">
      <div class="card">
        <div class="card-title"><span>📦 재고 현황</span><button class="card-title-edit" onclick="openInvEdit()">수량 수정</button></div>
        <div id="inv-list"></div>
      </div>
      <div class="card">
        <div class="card-title">
          <span>💹 가격표</span>
          <div style="display:flex;gap:5px">
            <button class="card-title-edit" onclick="openPepperMgr()">품목 관리</button>
            <button class="card-title-edit" onclick="openPriceEdit()">가격 수정</button>
          </div>
        </div>
        <div class="tbl-wrap"><table><thead><tr><th>품목</th><th>단위</th><th>판매가</th><th>재고</th></tr></thead><tbody id="ptbl"></tbody></table></div>
      </div>
    </div>

    <!-- PARCEL -->
    <div id="pg-parcel" class="pg">
      <div class="psum4">
        <div class="ps4"><div class="ps4v" id="pc-all">0</div><div class="ps4l">전체</div></div>
        <div class="ps4"><div class="ps4v" id="pc-ready">0</div><div class="ps4l">⏳ 준비중</div></div>
        <div class="ps4"><div class="ps4v" id="pc-sent">0</div><div class="ps4l">🚚 발송</div></div>
        <div class="ps4"><div class="ps4v" id="pc-done">0</div><div class="ps4l">✅ 완료</div></div>
      </div>
      <div class="chips" id="parcel-chips">
        <button class="chip active" onclick="setPFilter('all',this)">전체</button>
        <button class="chip" onclick="setPFilter('ready',this)">⏳ 준비중</button>
        <button class="chip" onclick="setPFilter('sent',this)">🚚 발송완료</button>
        <button class="chip" onclick="setPFilter('done',this)">✅ 수령완료</button>
      </div>
      <div id="parcel-list"></div>
    </div>

    <!-- STATS -->
    <div id="pg-stats" class="pg">
      <div class="card"><div class="card-title">📊 월별 판매</div><div id="st-mon"></div></div>
      <div class="card"><div class="card-title">🌶️ 품목별 비중</div><div id="st-items"></div></div>
      <div class="card"><div class="card-title">👑 단골 TOP 5</div><div id="st-top"></div></div>
      <div class="card">
        <div class="card-title">📊 Excel / Numbers 내보내기</div>
        <p style="font-size:11px;color:#78716c;margin-bottom:12px;line-height:1.6">.xlsx 형식 — Excel과 Numbers 양쪽 호환</p>
        <div class="excel-btns">
          <button class="excel-btn eb-order" onclick="exportExcel('orders')"><span>📋</span>주문 내역</button>
          <button class="excel-btn eb-cust"  onclick="exportExcel('customers')"><span>👥</span>고객 목록</button>
          <button class="excel-btn eb-parcel" onclick="exportExcel('parcels')"><span>🚚</span>택배 내역</button>
          <button class="excel-btn eb-all"   onclick="exportExcel('all')"><span>💾</span>전체 통합</button>
        </div>
      </div>
      <!-- PWA 설치 안내 -->
      <div id="pwa-install-card" class="card" style="display:none">
        <div class="card-title">📱 앱으로 설치하기</div>
        <p style="font-size:11px;color:#78716c;margin-bottom:12px;line-height:1.7">홈 화면에 추가하면 인터넷 없이도 독립 앱으로 실행됩니다.</p>
        <button id="pwa-install-btn" class="bsub" onclick="triggerInstall()" style="margin-bottom:8px">📲 홈 화면에 앱 추가</button>
        <div style="background:#fef9f9;border-radius:10px;padding:10px;font-size:10px;color:#78716c;line-height:1.8">
          <b style="color:var(--red2)">iPhone / iPad (Safari)</b><br>
          하단 공유버튼(□↑) → "홈 화면에 추가"<br>
          <b style="color:var(--red2)">Android (Chrome)</b><br>
          메뉴(⋮) → "앱 설치" 또는 "홈 화면에 추가"
        </div>
      </div>
      <div class="danger-zone">
        <div class="dz-title">⚠️ 데이터 관리</div>
        <button class="dz-btn dz-reset" onclick="resetData()">🔄 샘플 데이터로 초기화</button>
        <button class="dz-btn dz-clear-all" onclick="clearAllData()">🗑️ 모든 데이터 완전 삭제</button>
      </div>
    </div>

    <div id="pg-detail"><div id="det-content"></div></div>
  </div>

  <div id="nav">
    <button class="nb active" onclick="goPage('home',this)"><span class="ni">🏠</span><span>홈</span></button>
    <button class="nb" onclick="goPage('orders',this)"><span class="ni">📋</span><span>주문</span></button>
    <button class="nb" onclick="goPage('customers',this)"><span class="ni">👥</span><span>고객</span></button>
    <button class="nb" onclick="goPage('inventory',this)"><span class="ni">📦</span><span>재고</span></button>
    <button class="nb" onclick="goPage('parcel',this)"><span class="ni">🚚</span><span>택배</span></button>
    <button class="nb" onclick="goPage('stats',this)"><span class="ni">📊</span><span>통계</span></button>
  </div>
</div>
<button class="fab" id="fab">＋</button>

<!-- PWA 설치 배너 -->
<div id="pwa-banner">
  <span class="pb-icon">🌶️</span>
  <div class="pb-text">
    <div class="pb-title">앱으로 설치하기</div>
    <div class="pb-sub">홈 화면에서 바로 실행</div>
  </div>
  <button class="pb-install" onclick="triggerInstall()">설치</button>
  <button class="pb-close" onclick="closePwaBanner()">✕</button>
</div>

<!-- ORDER MODAL -->
<div class="overlay" id="om" onclick="oc2(event,'om')">
  <div class="sheet">
    <div class="sh"></div>
    <div class="stitle" id="om-title">🌶️ 새 주문 등록</div>
    <div class="fg"><label class="fl">고객 이름</label><input class="fi" id="on" type="text" placeholder="예) 홍길동" list="order-cust-list"/><datalist id="order-cust-list"></datalist></div>
    <div class="fr">
      <div class="fg"><label class="fl">연락처</label><input class="fi" id="oph" type="tel" placeholder="010-0000-0000"/></div>
      <div class="fg"><label class="fl">주문일</label><input class="fi" id="od" type="date"/></div>
    </div>
    <div class="fr">
      <div class="fg"><label class="fl">고추 종류</label><select class="fi" id="opp" onchange="syncOrderQty()"></select></div>
      <div class="fg">
        <label class="fl">수량(kg) <span class="sync-badge" id="sync-o" style="display:none">🔗 재고연동</span></label>
        <input class="fi" id="oq" type="number" placeholder="5" min="0.5" step="0.5" oninput="previewOSync()"/>
        <div id="o-stk-preview" style="font-size:10px;margin-top:4px;font-weight:700"></div>
      </div>
    </div>
    <div class="fg"><label class="fl">메모(선택)</label><input class="fi" id="ome" type="text" placeholder="예) 신선하게 포장"/></div>
    <input type="hidden" id="edit-order-id"/>
    <button class="bsub" onclick="submitOrder()">✅ 주문 등록</button>
    <button class="bdel" id="om-del-btn" style="display:none" onclick="deleteOrderFromModal()">🗑 이 주문 삭제</button>
    <button class="bcan" onclick="cm('om')">취소</button>
  </div>
</div>

<!-- CUSTOMER MODAL -->
<div class="overlay" id="cmo" onclick="oc2(event,'cmo')">
  <div class="sheet">
    <div class="sh"></div>
    <div class="stitle" id="cmo-title">👤 고객 등록</div>
    <div class="fg"><label class="fl">이름</label><input class="fi" id="cn" type="text" placeholder="예) 홍길동"/></div>
    <div class="fg"><label class="fl">연락처</label><input class="fi" id="cp" type="tel" placeholder="010-0000-0000"/></div>
    <div class="fg"><label class="fl">주소(선택)</label><input class="fi" id="ca" type="text" placeholder="예) 경북 안동시..."/></div>
    <div class="fg"><label class="fl">메모(선택)</label><input class="fi" id="cmemo" type="text" placeholder="예) 매운 거 선호"/></div>
    <input type="hidden" id="edit-cust-id"/>
    <button class="bsub" onclick="submitCust()">✅ 저장</button>
    <button class="bdel" id="cmo-del-btn" style="display:none" onclick="deleteCustFromModal()">🗑 이 고객 삭제</button>
    <button class="bcan" onclick="cm('cmo')">취소</button>
  </div>
</div>

<!-- MSG MODAL -->
<div class="overlay" id="msg-modal" onclick="oc2(event,'msg-modal')">
  <div class="sheet">
    <div class="sh"></div>
    <div style="background:#fef2f2;border-radius:12px;padding:11px 13px;margin-bottom:13px;display:flex;align-items:center;gap:10px">
      <span style="font-size:20px">👤</span>
      <div>
        <div id="msg-name" style="font-size:14px;font-weight:900;color:#1c1917"></div>
        <div id="msg-phone-disp" style="font-size:11px;color:var(--red2);font-weight:700"></div>
      </div>
    </div>
    <div class="msg-tabs">
      <button class="msg-tab active-sms" id="tab-sms" onclick="switchMsgTab('sms')">💬 문자 (SMS)</button>
      <button class="msg-tab" id="tab-kakao" onclick="switchMsgTab('kakao')">💛 카카오톡</button>
    </div>
    <label class="fl">빠른 문구 선택</label>
    <div class="quick-btns" id="quick-btns">
      <button class="qbtn" onclick="setMsgText('발송')">📦 발송 예정</button>
      <button class="qbtn" onclick="setMsgText('완료')">✅ 발송 완료</button>
      <button class="qbtn" onclick="setMsgText('예약')">🌶 예약 안내</button>
      <button class="qbtn" onclick="setMsgText('할인')">🎁 할인 이벤트</button>
    </div>
    <div class="fg">
      <label class="fl">메시지 내용</label>
      <textarea class="fi" id="msg-text" placeholder="보낼 내용을 입력하세요..." style="min-height:90px" oninput="updateMsgPreview()"></textarea>
    </div>
    <!-- SMS 패널 -->
    <div id="panel-sms">
      <button onclick="doSendSms()" style="width:100%;background:linear-gradient(135deg,#1d4ed8,#3b82f6);color:#fff;border:none;border-radius:13px;padding:13px;font-size:14px;font-weight:900;font-family:inherit;cursor:pointer;margin-bottom:7px">📱 문자 앱으로 보내기</button>
      <button onclick="copyAndOpenSms()" style="width:100%;background:#dbeafe;color:#1d4ed8;border:none;border-radius:13px;padding:11px;font-size:13px;font-weight:700;font-family:inherit;cursor:pointer;margin-bottom:7px">📋 복사 후 문자 앱 열기</button>
    </div>
    <!-- 카카오 패널 -->
    <div id="panel-kakao" style="display:none">
      <div style="background:#fef9c3;border-radius:12px;padding:11px 13px;margin-bottom:10px;font-size:11px;color:#78350f;line-height:1.5">
        💡 카카오톡은 앱 보안 정책상 직접 전송이 불가합니다.<br>아래 버튼으로 내용을 복사한 뒤 카카오톡에 붙여넣기 하세요.
      </div>
      <div class="copy-box" id="kakao-preview"></div>
      <div class="copy-action-row">
        <button class="copy-btn cb-copy" onclick="copyMsgText()">📋 내용 복사</button>
        <button class="copy-btn cb-kakao" onclick="openKakaoApp()">💛 카카오톡 열기</button>
      </div>
    </div>
    <input type="hidden" id="msg-phone"/>
    <button class="bcan" onclick="cm('msg-modal')">닫기</button>
  </div>
</div>

<!-- INV EDIT -->
<div class="overlay" id="inv-modal" onclick="oc2(event,'inv-modal')">
  <div class="sheet">
    <div class="sh"></div>
    <div class="stitle">📦 재고 수량 수정</div>
    <div id="inv-edit-body"></div>
    <button class="bsub" onclick="saveInv()">✅ 저장</button>
    <button class="bcan" onclick="cm('inv-modal')">취소</button>
  </div>
</div>

<!-- PRICE EDIT -->
<div class="overlay" id="price-modal" onclick="oc2(event,'price-modal')">
  <div class="sheet">
    <div class="sh"></div>
    <div class="stitle">💹 고추 가격 수정</div>
    <p style="font-size:11px;color:#78716c;text-align:center;margin-bottom:14px">kg당 판매가격을 입력하세요</p>
    <div id="price-edit-body"></div>
    <button class="bsub" onclick="savePrice()">✅ 가격 저장</button>
    <button class="bcan" onclick="cm('price-modal')">취소</button>
  </div>
</div>

<!-- PEPPER MGR -->
<div class="overlay" id="pepper-mgr-modal" onclick="oc2(event,'pepper-mgr-modal')">
  <div class="sheet">
    <div class="sh"></div>
    <div class="stitle">🌶️ 고추 품목 관리</div>
    <p style="font-size:11px;color:#78716c;text-align:center;margin-bottom:14px">이모지·이름·kg당 가격 수정 가능합니다</p>
    <div id="pepper-mgr-body"></div>
    <button class="pi-add-btn" onclick="addPepperRow()">＋ 품목 추가</button>
    <button class="bsub" style="margin-top:12px" onclick="savePepperMgr()">✅ 저장</button>
    <button class="bcan" onclick="cm('pepper-mgr-modal')">취소</button>
  </div>
</div>

<!-- NOTICE MODAL -->
<div class="overlay" id="notice-modal" onclick="oc2(event,'notice-modal')">
  <div class="sheet">
    <div class="sh"></div>
    <div class="stitle" id="notice-modal-title">📢 공지사항 작성</div>
    <div class="fg"><label class="fl">제목</label><input class="fi" id="notice-title-input" type="text" placeholder="예) 햇고추 예약 접수 시작"/></div>
    <div class="fg"><label class="fl">내용</label><textarea class="fi" id="notice-body-input" placeholder="공지 내용을 입력하세요..."></textarea></div>
    <input type="hidden" id="edit-notice-id"/>
    <button class="bsub" onclick="submitNotice()">✅ 저장</button>
    <button class="bcan" onclick="cm('notice-modal')">취소</button>
  </div>
</div>

<!-- PARCEL MODAL -->
<div class="overlay" id="parcel-modal" onclick="oc2(event,'parcel-modal')">
  <div class="sheet">
    <div class="sh"></div>
    <div class="stitle" id="parcel-modal-title">🚚 택배 등록</div>
    <div style="background:#f0fdf4;border:1.5px solid #86efac;border-radius:12px;padding:11px;margin-bottom:12px">
      <div style="font-size:11px;font-weight:700;color:#16a34a;margin-bottom:7px">🔗 주문에서 자동 불러오기</div>
      <select class="fi" id="pm-order-select" onchange="applyOrderToParcel()" style="background:#fff">
        <option value="">— 직접 입력 —</option>
      </select>
    </div>
    <div class="fg"><label class="fl">고객 이름</label><input class="fi" id="pm-name" type="text" placeholder="예) 홍길동" oninput="pmAutoFill()" list="pm-custs-list"/><datalist id="pm-custs-list"></datalist></div>
    <div class="fr">
      <div class="fg"><label class="fl">연락처</label><input class="fi" id="pm-phone" type="tel" placeholder="010-0000-0000"/></div>
      <div class="fg"><label class="fl">발송일</label><input class="fi" id="pm-date" type="date"/></div>
    </div>
    <div class="fg"><label class="fl">배송지 주소</label><input class="fi" id="pm-addr" type="text" placeholder="예) 서울시 강남구 역삼동 123"/></div>
    <div class="fr">
      <div class="fg"><label class="fl">고추 종류</label><select class="fi" id="pm-pepper" onchange="syncParcelQty()"></select></div>
      <div class="fg">
        <label class="fl">수량(kg) <span class="sync-badge" id="sync-p" style="display:none">🔗 재고연동</span></label>
        <input class="fi" id="pm-qty" type="number" placeholder="5" min="0.5" step="0.5" oninput="previewPSync()"/>
        <div id="p-stk-preview" style="font-size:10px;margin-top:4px;font-weight:700"></div>
      </div>
    </div>
    <div class="fr">
      <div class="fg"><label class="fl">택배사</label>
        <select class="fi" id="pm-company">
          <option>CJ대한통운</option><option>우체국택배</option><option>한진택배</option>
          <option>로젠택배</option><option>롯데택배</option><option>직접배송</option>
        </select>
      </div>
      <div class="fg"><label class="fl">운송장번호</label><input class="fi" id="pm-tracking" type="text" placeholder="(선택)"/></div>
    </div>
    <div class="fg"><label class="fl">메모</label><input class="fi" id="pm-memo" type="text" placeholder="예) 문앞 배송 요청"/></div>
    <div class="fg"><label class="fl">배송 상태</label>
      <select class="fi" id="pm-status">
        <option value="ready">⏳ 준비중</option>
        <option value="sent">🚚 발송완료</option>
        <option value="done">✅ 수령완료</option>
      </select>
    </div>
    <input type="hidden" id="edit-parcel-id"/>
    <button class="bsub" onclick="submitParcel()">✅ 저장</button>
    <button class="bdel" id="pm-del-btn" style="display:none" onclick="deleteParcelFromModal()">🗑 이 택배 삭제</button>
    <button class="bcan" onclick="cm('parcel-modal')">취소</button>
  </div>
</div>

<!-- SHARE MODAL -->
<div class="overlay" id="share-modal" onclick="oc2(event,'share-modal')">
  <div class="sheet">
    <div class="sh"></div>
    <div class="stitle">📤 데이터 공유</div>
    <div style="display:flex;background:#fef2f2;border-radius:12px;padding:4px;margin-bottom:16px;gap:4px">
      <button id="stab-export" onclick="shareTab('export')" style="flex:1;padding:9px;border:none;border-radius:9px;font-size:12px;font-weight:700;cursor:pointer;font-family:inherit;background:var(--red2);color:#fff">📤 내보내기</button>
      <button id="stab-import" onclick="shareTab('import')" style="flex:1;padding:9px;border:none;border-radius:9px;font-size:12px;font-weight:700;cursor:pointer;font-family:inherit;background:transparent;color:#78716c">📥 가져오기</button>
    </div>
    <div id="sp-export">
      <p id="export-info" style="font-size:11px;color:#a8a29e;margin-bottom:12px;text-align:center"></p>
      <button class="bsub" onclick="downloadData()">💾 JSON 백업 저장</button>
      <button class="bcan" onclick="cm('share-modal')">닫기</button>
    </div>
    <div id="sp-import" style="display:none">
      <div class="fg"><label class="fl">JSON 파일 선택</label><input type="file" id="import-file" accept=".json" onchange="loadFile(event)" style="font-size:12px;color:#57534e;width:100%"/></div>
      <div style="display:flex;gap:7px;margin-bottom:7px">
        <button onclick="importMerge()" style="flex:1;padding:12px;border:none;border-radius:12px;background:#dcfce7;color:#16a34a;font-size:12px;font-weight:700;cursor:pointer;font-family:inherit">🔀 합치기</button>
        <button onclick="importReplace()" style="flex:1;padding:12px;border:none;border-radius:12px;background:#fee2e2;color:#dc2626;font-size:12px;font-weight:700;cursor:pointer;font-family:inherit">🔄 덮어쓰기</button>
      </div>
      <button class="bcan" onclick="cm('share-modal')">취소</button>
    </div>
  </div>
</div>

<!-- CONFIRM -->
<div class="overlay" id="conf-modal" onclick="oc2(event,'conf-modal')">
  <div class="sheet">
    <div class="sh"></div>
    <div id="conf-icon" style="text-align:center;font-size:42px;margin-bottom:12px">⚠️</div>
    <div class="stitle" id="conf-title">확인</div>
    <p id="conf-msg" style="text-align:center;font-size:13px;color:#78716c;margin-bottom:18px;line-height:1.6"></p>
    <button class="bsub" id="conf-ok" style="background:linear-gradient(135deg,#dc2626,#ef4444)">확인</button>
    <button class="bcan" onclick="cm('conf-modal')">취소</button>
  </div>
</div>

<script>
// ═══ PWA: MANIFEST 동적 생성 ═══
(function(){
  const manifest={
    name:'고추농가 직판장',
    short_name:'고추직판장',
    description:'고추농가 직판장 주문·고객·재고 관리',
    start_url:'.',
    display:'standalone',
    background_color:'#1a0000',
    theme_color:'#8b0000',
    orientation:'portrait',
    icons:[
      {src:'data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 192 192"><rect width="192" height="192" rx="40" fill="%238b0000"/><text y="130" x="96" text-anchor="middle" font-size="110">🌶️</text></svg>',sizes:'192x192',type:'image/svg+xml'},
      {src:'data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><rect width="512" height="512" rx="100" fill="%238b0000"/><text y="360" x="256" text-anchor="middle" font-size="300">🌶️</text></svg>',sizes:'512x512',type:'image/svg+xml'}
    ]
  };
  const blob=new Blob([JSON.stringify(manifest)],{type:'application/manifest+json'});
  const url=URL.createObjectURL(blob);
  document.getElementById('manifest-link').setAttribute('href',url);
  document.getElementById('manifest-link').setAttribute('rel','manifest');
})();

// ═══ SERVICE WORKER 등록 ═══
if('serviceWorker' in navigator){
  // 인라인 SW — 외부 파일 없이 동작
  const swCode=`
const CACHE='gochu-v2';
self.addEventListener('install',e=>{self.skipWaiting();});
self.addEventListener('activate',e=>{self.clients.claim();});
self.addEventListener('fetch',e=>{
  // tel:, sms:, kakaotalk: 등 비-http 스킴은 SW에서 무시
  if(!e.request.url.startsWith('http')){return;}
  e.respondWith(fetch(e.request).catch(()=>caches.match(e.request)));
});`;
  const swBlob=new Blob([swCode],{type:'text/javascript'});
  const swUrl=URL.createObjectURL(swBlob);
  navigator.serviceWorker.register(swUrl,{scope:'./'}).catch(()=>{});
}

// ═══ PWA 설치 프롬프트 ═══
let deferredPrompt=null;
window.addEventListener('beforeinstallprompt',e=>{
  e.preventDefault();
  deferredPrompt=e;
  // 배너 표시
  setTimeout(()=>{
    if(!localStorage.getItem('pwa-dismissed')){
      document.getElementById('pwa-banner').classList.add('show');
      document.getElementById('pwa-install-card').style.display='block';
    }
  },3000);
});
window.addEventListener('appinstalled',()=>{
  deferredPrompt=null;
  document.getElementById('pwa-banner').classList.remove('show');
  showToast('앱이 설치되었습니다! 🎉');
});

function triggerInstall(){
  if(deferredPrompt){
    deferredPrompt.prompt();
    deferredPrompt.userChoice.then(r=>{
      if(r.outcome==='accepted'){showToast('앱 설치 완료! 🎉');}
      deferredPrompt=null;
      document.getElementById('pwa-banner').classList.remove('show');
    });
  } else {
    showToast('브라우저 메뉴 → "홈 화면에 추가"를 이용해주세요.');
  }
}
function closePwaBanner(){
  document.getElementById('pwa-banner').classList.remove('show');
  localStorage.setItem('pwa-dismissed','1');
}

// ═══ CONSTANTS ═══
const AVC=['#c0392b','#e67e22','#27ae60','#2980b9','#8e44ad','#16a085','#d35400','#2c3e50'];
const DAYS=['일','월','화','수','목','금','토'];
const PEPPER_COLORS=['#c0392b','#ea580c','#16a34a','#a16207','#78350f','#1d4ed8','#7c3aed','#047857'];
const MSG_TEMPLATES={
  '발송': n=>`안녕하세요 ${n}님! 주문하신 고추가 곧 발송될 예정입니다. 🌶️\n신선하게 포장하여 발송드리겠습니다. 감사합니다!`,
  '완료': n=>`안녕하세요 ${n}님! 주문하신 고추가 오늘 발송되었습니다. 📦\n배송 현황은 운송장 번호로 확인 부탁드립니다. 감사합니다!`,
  '예약': n=>`안녕하세요 ${n}님! 🌶️ 이번 시즌 햇고추 예약 접수를 받고 있습니다.\n수량 한정이니 관심 있으시면 빨리 연락 주세요!`,
  '할인': n=>`안녕하세요 ${n}님! 단골 고객님께 특별 할인 이벤트를 안내드립니다. 🎁\n이번 주 주문 시 10% 할인 적용됩니다. 감사합니다!`,
};
let currentMsgTab='sms';

// ═══ DATE UTILS ═══
function lStr(d){return`${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`;}
function pLocal(s){const[y,m,d]=s.split('-').map(Number);return new Date(y,m-1,d);}
const TODAY=new Date();TODAY.setHours(0,0,0,0);
const TSTR=lStr(TODAY);
let viewDate=new Date(TODAY);

// ═══ STATE ═══
let orders,custs,inv,parcels,notices,nid,ncid,npid,nnid;
let importBuffer=null;
let PP={};
function rebuildPP(){PP={};inv.forEach(it=>{PP[it.name]={e:it.e||'🌶️',c:it.c||'pb-r',p:it.price,col:it.col||'#c0392b'};});}

function makeSeed(){
  const d1=lStr(new Date(TODAY.getTime()-86400000));
  const d2=lStr(new Date(TODAY.getTime()-2*86400000));
  return{
    orders:[
      {id:1,name:'김영희',phone:'010-1234-5678',pepper:'청양고추',qty:5,date:TSTR,status:'pending',memo:''},
      {id:2,name:'이철수',phone:'010-2345-6789',pepper:'홍고추',qty:3,date:TSTR,status:'done',memo:'신선하게 포장'},
      {id:3,name:'박미나',phone:'010-3456-7890',pepper:'오이고추',qty:8,date:TSTR,status:'pending',memo:''},
      {id:4,name:'최동현',phone:'010-4567-8901',pepper:'꽈리고추',qty:2,date:TSTR,status:'pending',memo:''},
      {id:5,name:'정수연',phone:'010-5678-9012',pepper:'건고추',qty:1,date:TSTR,status:'done',memo:''},
      {id:6,name:'강민준',phone:'010-6789-0123',pepper:'청양고추',qty:10,date:d1,status:'done',memo:''},
      {id:7,name:'윤지혜',phone:'010-7890-1234',pepper:'홍고추',qty:4,date:d1,status:'done',memo:''},
      {id:8,name:'임성훈',phone:'010-8901-2345',pepper:'오이고추',qty:6,date:d2,status:'done',memo:''},
    ],
    custs:[
      {id:1,name:'김영희',phone:'010-1234-5678',addr:'경북 안동시 풍산읍',memo:'단골, 청양 선호',join:TSTR},
      {id:2,name:'이철수',phone:'010-2345-6789',addr:'서울 강남구 역삼동',memo:'신선 포장 요청',join:TSTR},
      {id:3,name:'박미나',phone:'010-3456-7890',addr:'부산 해운대구 좌동',memo:'',join:TSTR},
      {id:4,name:'최동현',phone:'010-4567-8901',addr:'대전 유성구 봉명동',memo:'꽈리 단골',join:TSTR},
      {id:5,name:'정수연',phone:'010-5678-9012',addr:'인천 남동구 구월동',memo:'건고추 대량',join:TSTR},
      {id:6,name:'강민준',phone:'010-6789-0123',addr:'광주 서구 화정동',memo:'',join:TSTR},
      {id:7,name:'윤지혜',phone:'010-7890-1234',addr:'대구 중구 동인동',memo:'매운 것 선호',join:TSTR},
      {id:8,name:'임성훈',phone:'010-8901-2345',addr:'경기 수원시 팔달구',memo:'오이고추 정기',join:TSTR},
    ],
    inv:[
      {name:'청양고추',e:'🌶️',c:'pb-r',col:'#c0392b',stock:42,max:100,price:8000},
      {name:'홍고추',e:'🔴',c:'pb-o',col:'#ea580c',stock:68,max:100,price:6000},
      {name:'오이고추',e:'🟢',c:'pb-g',col:'#16a34a',stock:15,max:80,price:5000},
      {name:'꽈리고추',e:'🟡',c:'pb-d',col:'#a16207',stock:55,max:80,price:7000},
      {name:'건고추',e:'🌰',c:'pb-d',col:'#78350f',stock:8,max:50,price:15000},
    ],
    parcels:[
      {id:1,name:'이철수',phone:'010-2345-6789',addr:'서울 강남구 역삼동 123',pepper:'홍고추',qty:3,date:TSTR,status:'sent',company:'CJ대한통운',tracking:'1234567890',memo:'',linkedOrderId:2},
      {id:2,name:'정수연',phone:'010-5678-9012',addr:'인천 남동구 구월동 456',pepper:'건고추',qty:1,date:d1,status:'done',company:'우체국택배',tracking:'9876543210',memo:'',linkedOrderId:5},
      {id:3,name:'강민준',phone:'010-6789-0123',addr:'광주 서구 화정동 789',pepper:'청양고추',qty:10,date:d1,status:'ready',company:'CJ대한통운',tracking:'',memo:'냉장 포장',linkedOrderId:6},
    ],
    notices:[
      {id:1,title:'햇고추 예약 접수 시작',body:'올해 수확한 햇고추 예약 주문을 받습니다. 수량 한정!',date:'2024.09.01'},
      {id:2,title:'배송 안내 — 매주 화/목 발송',body:'주문 마감 후 화·목요일에 일괄 발송됩니다.',date:'2024.08.15'},
    ],
    nid:100,ncid:200,npid:10,nnid:10
  };
}
function loadState(){
  try{const r=localStorage.getItem('gochu_v7');if(r){const d=JSON.parse(r);orders=d.o;custs=d.c;inv=d.inv;parcels=d.par||[];notices=d.not||[];nid=d.ni;ncid=d.nc;npid=d.np||10;nnid=d.nn||10;rebuildPP();return;}}catch(e){}
  const s=makeSeed();orders=s.orders;custs=s.custs;inv=s.inv;parcels=s.parcels;notices=s.notices;nid=s.nid;ncid=s.ncid;npid=s.npid;nnid=s.nnid;rebuildPP();
}
function save(){try{localStorage.setItem('gochu_v7',JSON.stringify({o:orders,c:custs,inv:inv,par:parcels,not:notices,ni:nid,nc:ncid,np:npid,nn:nnid}));}catch(e){}}
loadState();
let oFilter='all',cSort='total',pFilter='all';

// ═══ PEPPER SELECTS ═══
function fillPepperSelects(){
  const opts=inv.map(it=>`<option value="${it.name}">${it.e} ${it.name}</option>`).join('');
  ['opp','pm-pepper'].forEach(id=>{const el=document.getElementById(id);if(el)el.innerHTML=opts;});
  const fc=document.getElementById('order-filter-chips');
  if(fc)fc.innerHTML=inv.map(it=>`<button class="chip" onclick="setOf('${it.name}',this)">${it.e} ${it.name}</button>`).join('');
}
function getInvItem(name){return inv.find(it=>it.name===name);}

// ═══ ORDER QTY SYNC ═══
function syncOrderQty(){const p=document.getElementById('opp').value;const it=getInvItem(p);document.getElementById('sync-o').style.display=it?'inline-flex':'none';previewOSync();}
function previewOSync(){const p=document.getElementById('opp').value;const q=parseFloat(document.getElementById('oq').value)||0;const it=getInvItem(p);const pr=document.getElementById('o-stk-preview');if(!it||!q){pr.textContent='';return;}const a=it.stock-q;pr.textContent=`재고: ${it.stock}kg → 주문 후 ${a}kg ${a<0?'⚠️ 부족!':''}`;pr.style.color=a<0?'#ef4444':'#16a34a';}
function syncParcelQty(){const p=document.getElementById('pm-pepper').value;const it=getInvItem(p);document.getElementById('sync-p').style.display=it?'inline-flex':'none';previewPSync();}
function previewPSync(){const p=document.getElementById('pm-pepper').value;const q=parseFloat(document.getElementById('pm-qty').value)||0;const it=getInvItem(p);const pr=document.getElementById('p-stk-preview');if(!it||!q){pr.textContent='';return;}const a=it.stock-q;pr.textContent=`재고: ${it.stock}kg → 발송 후 ${a}kg ${a<0?'⚠️ 부족!':''}`;pr.style.color=a<0?'#ef4444':'#16a34a';}

// ═══ PARCEL ORDER LINK ═══
function fillParcelOrderSelect(){
  const sel=document.getElementById('pm-order-select');if(!sel)return;
  const linked=new Set(parcels.map(p=>p.linkedOrderId).filter(Boolean));
  const pending=orders.filter(o=>!linked.has(o.id));
  sel.innerHTML='<option value="">— 직접 입력 —</option>'+pending.map(o=>`<option value="${o.id}">${o.date} | ${o.name} | ${o.pepper} ${o.qty}kg</option>`).join('');
}
function applyOrderToParcel(){
  const oid=Number(document.getElementById('pm-order-select').value);if(!oid)return;
  const o=orders.find(x=>x.id===oid);if(!o)return;
  document.getElementById('pm-name').value=o.name;document.getElementById('pm-phone').value=o.phone;document.getElementById('pm-pepper').value=o.pepper;document.getElementById('pm-qty').value=o.qty;
  const c=custs.find(x=>x.name===o.name);if(c&&c.addr)document.getElementById('pm-addr').value=c.addr;
  document.getElementById('pm-date').value=TSTR;syncParcelQty();previewPSync();showToast(`${o.name} 주문 정보 자동 입력 완료!`);
}

// ═══ RESET ═══
function resetData(){showConfirm('🔄','샘플 데이터로 초기화','현재 데이터가 삭제되고 샘플 데이터로 복원됩니다.',()=>{const s=makeSeed();orders=s.orders;custs=s.custs;inv=s.inv;parcels=s.parcels;notices=s.notices;nid=s.nid;ncid=s.ncid;npid=s.npid;nnid=s.nnid;rebuildPP();fillPepperSelects();save();renderHome();renderCusts();showToast('초기화 완료!');});}
function clearAllData(){showConfirm('🗑️','모든 데이터 삭제','모든 데이터가 삭제됩니다. 되돌릴 수 없습니다!',()=>{const s=makeSeed();orders=[];custs=[];inv=s.inv;parcels=[];notices=[];nid=100;ncid=200;npid=10;nnid=10;rebuildPP();fillPepperSelects();save();renderHome();renderCusts();showToast('삭제 완료!');});}

// ═══ CONFIRM ═══
function showConfirm(icon,title,msg,onOk){document.getElementById('conf-icon').textContent=icon;document.getElementById('conf-title').textContent=title;document.getElementById('conf-msg').textContent=msg;document.getElementById('conf-ok').onclick=()=>{cm('conf-modal');onOk();};document.getElementById('conf-modal').classList.add('show');}

// ═══ NAVIGATION ═══
let detailStack=[];
function goPage(name,btn){
  closeDetail();
  document.querySelectorAll('.pg').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nb').forEach(b=>b.classList.remove('active'));
  document.getElementById('pg-'+name).classList.add('active');
  if(btn)btn.classList.add('active');
  const fab=document.getElementById('fab');
  if(name==='orders'){fab.classList.add('show');fab.onclick=openOrderModal;}
  else if(name==='customers'){fab.classList.add('show');fab.onclick=openCustModal;}
  else if(name==='parcel'){fab.classList.add('show');fab.onclick=openParcelModal;}
  else fab.classList.remove('show');
  document.getElementById('main').scrollTo(0,0);
  if(name==='home')renderHome();
  if(name==='orders')renderOrders();
  if(name==='customers')renderCusts();
  if(name==='inventory')renderInv();
  if(name==='parcel')renderParcel();
  if(name==='stats')renderStats();
}
function openDetail(title,fn){
  detailStack.push({title,fn});
  document.getElementById('det-content').innerHTML='';
  fn(document.getElementById('det-content'));
  document.getElementById('pg-detail').classList.add('show');
  document.getElementById('logo').style.display='none';
  document.getElementById('hdr-title').textContent=title;
  document.getElementById('hdr-title').classList.add('show');
  document.getElementById('back-btn').classList.add('show');
  document.getElementById('hdr-btns').style.display='none';
  document.getElementById('fab').classList.remove('show');
  document.getElementById('pg-detail').scrollTo(0,0);
}
function goBack(){
  detailStack.pop();
  if(detailStack.length>0){const p=detailStack[detailStack.length-1];document.getElementById('det-content').innerHTML='';p.fn(document.getElementById('det-content'));document.getElementById('hdr-title').textContent=p.title;document.getElementById('pg-detail').scrollTo(0,0);}
  else closeDetail();
}
function closeDetail(){detailStack=[];document.getElementById('pg-detail').classList.remove('show');document.getElementById('logo').style.display='';document.getElementById('hdr-title').classList.remove('show');document.getElementById('back-btn').classList.remove('show');document.getElementById('hdr-btns').style.display='';}
function refreshTopDetail(){if(!detailStack.length)return;const l=detailStack[detailStack.length-1];document.getElementById('det-content').innerHTML='';l.fn(document.getElementById('det-content'));}

// ═══ DATE NAV ═══
function shiftDate(d){viewDate=new Date(viewDate.getFullYear(),viewDate.getMonth(),viewDate.getDate()+d);renderOrders();}
function goToday(){viewDate=new Date(TODAY);renderOrders();}
function updateDateBar(){document.getElementById('disp-date').textContent=`${viewDate.getFullYear()}년 ${viewDate.getMonth()+1}월 ${viewDate.getDate()}일`;document.getElementById('disp-day').textContent=`${DAYS[viewDate.getDay()]}요일`;const f=lStr(viewDate)>=TSTR;document.getElementById('btn-next').style.opacity=f?'0.3':'1';document.getElementById('btn-next').style.pointerEvents=f?'none':'auto';}

// ═══ GRADE ═══
function grade(tot,cnt){if(tot>=50000||cnt>=5)return{l:'⭐ VIP',c:'gv'};if(cnt>=2)return{l:'💙 단골',c:'gr'};return{l:'🌱 신규',c:'gn'};}

// ═══ HOME ═══
function renderHome(){
  const tod=orders.filter(o=>o.date===TSTR);
  const todS=tod.reduce((s,o)=>s+(PP[o.pepper]?.p||0)*o.qty,0);
  const monS=orders.reduce((s,o)=>s+(PP[o.pepper]?.p||0)*o.qty,0);
  document.getElementById('s-tod').textContent=tod.length;
  document.getElementById('s-sales').textContent=Math.round(todS/1000);
  document.getElementById('s-done').textContent=tod.filter(o=>o.status==='done').length;
  document.getElementById('s-mon').textContent=Math.round(monS/1000);
  const pt={};orders.forEach(o=>pt[o.pepper]=(pt[o.pepper]||0)+Number(o.qty));
  const mx=Math.max(...Object.values(pt),1);
  document.getElementById('home-bars').innerHTML=inv.map(it=>{const q=pt[it.name]||0;return`<div class="bar-row"><div class="bar-meta"><span>${it.e} ${it.name}</span><b>${q}kg</b></div><div class="bar-track"><div class="bar-fill" style="width:${Math.round(q/mx*100)}%;background:linear-gradient(90deg,${it.col},${it.col}99)"></div></div></div>`;}).join('');
  const rec=[...orders].sort((a,b)=>b.id-a.id).slice(0,5);
  document.getElementById('home-recent').innerHTML=!rec.length?'<div class="empty"><div class="ei">📭</div><p>주문 없음</p></div>':rec.map(o=>{const p=PP[o.pepper]||{e:'🌶️',c:'pb-r'};const s=o.status==='done'?`<span class="sdot sd"></span><span style="font-size:10px;color:#10b981;font-weight:700">완료</span>`:`<span class="sdot sp"></span><span style="font-size:10px;color:#f59e0b;font-weight:700">대기</span>`;return`<div class="oi" onclick="openOrderDetail(${o.id})"><div><div class="oi-n">${o.name}</div><div class="oi-p">${o.phone}</div></div><div><span class="pb ${p.c}">${p.e} ${o.pepper}</span></div><div style="font-size:12px;font-weight:700">${o.qty}<span style="font-size:10px;color:#a8a29e">kg</span></div><div style="display:flex;align-items:center">${s}</div></div>`;}).join('');
  renderNoticeList();
}

// ═══ NOTICES ═══
function renderNoticeList(){
  const el=document.getElementById('notice-list');if(!el)return;
  if(!notices.length){el.innerHTML='<div style="text-align:center;padding:18px;color:#c4b5a5;font-size:12px">공지사항이 없습니다.</div>';return;}
  el.innerHTML=notices.map(n=>`<div class="notice-item"><div class="nd"></div><div style="flex:1"><div class="nt">${n.title}</div><div class="nb2">${n.body}</div><div class="ntm">${n.date}</div></div><div style="display:flex;gap:4px;flex-shrink:0"><button onclick="editNotice(${n.id})" style="border:none;background:none;font-size:14px;cursor:pointer;padding:2px">✏️</button><button onclick="deleteNotice(${n.id})" style="border:none;background:none;font-size:14px;cursor:pointer;padding:2px">🗑</button></div></div>`).join('');
}
function openNoticeModal(){document.getElementById('notice-modal-title').textContent='📢 공지사항 작성';document.getElementById('notice-title-input').value='';document.getElementById('notice-body-input').value='';document.getElementById('edit-notice-id').value='';document.getElementById('notice-modal').classList.add('show');}
function editNotice(id){const n=notices.find(x=>x.id===id);if(!n)return;document.getElementById('notice-modal-title').textContent='✏️ 공지사항 수정';document.getElementById('notice-title-input').value=n.title;document.getElementById('notice-body-input').value=n.body;document.getElementById('edit-notice-id').value=id;document.getElementById('notice-modal').classList.add('show');}
function submitNotice(){const title=document.getElementById('notice-title-input').value.trim();const body=document.getElementById('notice-body-input').value.trim();if(!title){showToast('제목을 입력하세요.');return;}const editId=Number(document.getElementById('edit-notice-id').value);const d=new Date();const ds=`${d.getFullYear()}.${String(d.getMonth()+1).padStart(2,'0')}.${String(d.getDate()).padStart(2,'0')}`;if(editId){const n=notices.find(x=>x.id===editId);if(n)Object.assign(n,{title,body,date:ds});}else notices.unshift({id:nnid++,title,body,date:ds});save();cm('notice-modal');renderNoticeList();showToast('저장되었습니다!');}
function deleteNotice(id){showConfirm('🗑️','공지 삭제','이 공지사항을 삭제할까요?',()=>{notices=notices.filter(n=>n.id!==id);save();renderNoticeList();});}

// ═══ ORDERS ═══
function setOf(f,btn){oFilter=f;document.querySelectorAll('#oc .chip').forEach(c=>c.classList.remove('active'));btn.classList.add('active');renderOrders();}
function renderOrders(){
  updateDateBar();
  const vs=lStr(viewDate);
  const day=orders.filter(o=>o.date===vs);
  document.getElementById('d-cnt').textContent=day.length;
  document.getElementById('d-kg').textContent=day.reduce((s,o)=>s+Number(o.qty),0);
  document.getElementById('d-sales').textContent=Math.round(day.reduce((s,o)=>s+(PP[o.pepper]?.p||0)*o.qty,0)/1000);
  let f=day;
  if(oFilter==='pending')f=day.filter(o=>o.status==='pending');
  else if(oFilter==='done')f=day.filter(o=>o.status==='done');
  else if(oFilter!=='all')f=day.filter(o=>o.pepper===oFilter);
  const body=document.getElementById('order-body');
  if(!f.length){body.innerHTML='<div class="empty"><div class="ei">📭</div><p>해당 조건의 주문 없음</p></div>';return;}
  body.innerHTML=f.map(o=>{
    const p=PP[o.pepper]||{e:'🌶️',c:'pb-r',p:0};
    const price=(p.p||0)*o.qty;
    const hasP=parcels.some(x=>x.linkedOrderId===o.id);
    const pb=hasP?`<span style="font-size:8px;background:#dcfce7;color:#16a34a;border-radius:99px;padding:1px 5px;font-weight:700">📦</span>`:'';
    const act=o.status==='done'?`<button class="ab ab-undo" onclick="event.stopPropagation();undoO(${o.id})">↩</button>`:`<button class="ab ab-ok" onclick="event.stopPropagation();doneO(${o.id})">✅</button>`;
    return`<div class="oi" onclick="openOrderDetail(${o.id})"><div><div class="oi-n">${o.name} ${pb}</div><div class="oi-p">${o.phone}</div>${o.memo?`<div class="oi-m">📝 ${o.memo}</div>`:''}</div><div><span class="pb ${p.c}">${p.e} ${o.pepper}</span><div style="font-size:9.5px;color:#a8a29e;margin-top:3px">₩${price.toLocaleString()}</div></div><div style="font-size:12px;font-weight:700">${o.qty}<span style="font-size:10px;color:#a8a29e">kg</span></div><div class="abts">${act}<button class="ab ab-del" onclick="event.stopPropagation();delO(${o.id})">🗑</button></div></div>`;
  }).join('');
}
function doneO(id){const o=orders.find(x=>x.id===id);if(o){o.status='done';save();renderOrders();renderHome();}}
function undoO(id){const o=orders.find(x=>x.id===id);if(o){o.status='pending';save();renderOrders();renderHome();}}
function delO(id){showConfirm('🗑️','주문 삭제','이 주문을 삭제할까요?',()=>{orders=orders.filter(o=>o.id!==id);save();renderOrders();renderHome();if(detailStack.length>0)goBack();});}

// ═══ ORDER DETAIL ═══
function openOrderDetail(id){openDetail('주문 상세',el=>renderOrderDetailInto(el,id));}
function renderOrderDetailInto(el,id){
  const o=orders.find(x=>x.id===id);
  if(!o){el.innerHTML='<div class="empty"><div class="ei">❌</div><p>주문을 찾을 수 없습니다</p></div>';return;}
  const p=PP[o.pepper]||{e:'🌶️',c:'pb-r',p:0};
  const price=(p.p||0)*o.qty;
  const st=o.status==='done'?'<span class="tag tg">✅ 완료</span>':'<span class="tag ty">⏳ 대기중</span>';
  const cust=custs.find(c=>c.name===o.name);
  const custOrds=orders.filter(x=>x.name===o.name);
  const custTot=custOrds.reduce((s,x)=>s+(PP[x.pepper]?.p||0)*x.qty,0);
  const g=grade(custTot,custOrds.length);
  const lp=parcels.find(x=>x.linkedOrderId===o.id);
  el.innerHTML=`
    <div class="od-header"><div style="display:flex;align-items:center;justify-content:space-between"><div><div class="od-pepper">${p.e} ${o.pepper}</div><div class="od-sub">${o.date} · ${DAYS[pLocal(o.date).getDay()]}요일</div></div>${st}</div><div class="od-price">₩${price.toLocaleString()}</div><div class="od-priceSub">${o.qty}kg × ₩${(p.p||0).toLocaleString()}/kg</div></div>
    <div class="card"><div class="card-title">👤 고객 정보</div>
      <div class="info-row"><span class="info-lbl">이름</span><span class="info-val" style="font-weight:700">${o.name}</span></div>
      <div class="info-row"><span class="info-lbl">연락처</span><span class="info-val"><a href="tel:${o.phone}" onclick="openTel(event,'${o.phone}')" style="color:var(--red2);font-weight:700;text-decoration:none">📞 ${o.phone}</a></span></div>
      ${o.memo?`<div class="info-row"><span class="info-lbl">메모</span><span class="info-val">${o.memo}</span></div>`:''}
      ${cust?.addr?`<div class="info-row"><span class="info-lbl">주소</span><span class="info-val">${cust.addr}</span></div>`:''}
      <div style="margin-top:11px;display:flex;gap:6px;flex-wrap:wrap">
        <button onclick="openMsgModal('${o.name}','${o.phone}')" style="flex:1;min-width:70px;padding:9px;border:1.5px solid #dbeafe;background:#eff6ff;border-radius:10px;font-size:11px;font-weight:700;color:#1d4ed8;cursor:pointer;font-family:inherit">💬 문자/카카오</button>
        <button onclick="openCustDetail('${o.name}')" style="flex:1;min-width:70px;padding:9px;border:1.5px solid #fecaca;background:#fff0f0;border-radius:10px;font-size:11px;font-weight:700;color:var(--red2);cursor:pointer;font-family:inherit">👤 고객 상세</button>
        <button onclick="openEditOrderModal(${o.id})" style="flex:1;min-width:70px;padding:9px;border:1.5px solid #fef08a;background:#fefce8;border-radius:10px;font-size:11px;font-weight:700;color:#a16207;cursor:pointer;font-family:inherit">✏️ 수정</button>
      </div>
    </div>
    ${lp?`<div class="card" style="border-color:#86efac"><div class="card-title" style="color:#16a34a">🔗 연결된 택배</div><div class="info-row"><span class="info-lbl">상태</span><span class="info-val">${{ready:'⏳ 준비중',sent:'🚚 발송완료',done:'✅ 수령완료'}[lp.status]}</span></div><div class="info-row"><span class="info-lbl">택배사</span><span class="info-val">${lp.company}</span></div>${lp.tracking?`<div class="info-row"><span class="info-lbl">운송장</span><span class="info-val" style="font-weight:700">${lp.tracking}</span></div>`:''}<button onclick="openParcelDetail(${lp.id})" style="margin-top:8px;width:100%;padding:9px;border:1.5px solid #86efac;background:#f0fdf4;border-radius:10px;font-size:11px;font-weight:700;color:#16a34a;cursor:pointer;font-family:inherit">🚚 택배 상세 보기</button></div>`:`<div class="card" style="border-style:dashed"><div style="text-align:center;padding:8px 0"><div style="font-size:11px;color:#a8a29e;margin-bottom:8px">연결된 택배 없음</div><button onclick="qParcelFromOrder(${o.id})" style="padding:9px 18px;border:1.5px solid #86efac;background:#f0fdf4;border-radius:10px;font-size:12px;font-weight:700;color:#16a34a;cursor:pointer;font-family:inherit">🚚 이 주문으로 택배 등록</button></div></div>`}
    <div class="card"><div class="card-title">📊 고객 현황</div><div class="det-stat-row"><div class="dsd"><div class="dsdv">${custOrds.length}</div><div class="dsdl">총 주문</div></div><div class="dsd"><div class="dsdv">${custOrds.reduce((s,x)=>s+Number(x.qty),0)}kg</div><div class="dsdl">총 수량</div></div><div class="dsd"><div class="dsdv">₩${Math.round(custTot/1000)}천</div><div class="dsdl">누적매출</div></div></div><div style="text-align:center"><span class="cgrd ${g.c}">${g.l}</span></div></div>
    <div style="display:flex;gap:7px;margin-bottom:10px">
      ${o.status==='done'?`<button onclick="undoO(${o.id});refreshTopDetail()" style="flex:1;padding:12px;border:none;background:#e0f2fe;border-radius:12px;font-size:13px;font-weight:700;color:#0369a1;cursor:pointer;font-family:inherit">↩ 완료 취소</button>`:`<button onclick="doneO(${o.id});refreshTopDetail()" style="flex:1;padding:12px;border:none;background:#dcfce7;border-radius:12px;font-size:13px;font-weight:700;color:#16a34a;cursor:pointer;font-family:inherit">✅ 완료 처리</button>`}
      <button onclick="delO(${o.id})" style="flex:1;padding:12px;border:none;background:#fee2e2;border-radius:12px;font-size:13px;font-weight:700;color:#dc2626;cursor:pointer;font-family:inherit">🗑 삭제</button>
    </div>`;
}
function qParcelFromOrder(oid){const o=orders.find(x=>x.id===oid);if(!o)return;openParcelModal();setTimeout(()=>{document.getElementById('pm-name').value=o.name;document.getElementById('pm-phone').value=o.phone;document.getElementById('pm-pepper').value=o.pepper;document.getElementById('pm-qty').value=o.qty;const c=custs.find(x=>x.name===o.name);if(c&&c.addr)document.getElementById('pm-addr').value=c.addr;document.getElementById('edit-parcel-id').value='__link__'+oid;syncParcelQty();previewPSync();},80);}

// ═══ ORDER MODAL ═══
function openOrderModal(){
  document.getElementById('om-title').textContent='🌶️ 새 주문 등록';
  document.getElementById('edit-order-id').value='';
  document.getElementById('od').value=lStr(viewDate);
  document.getElementById('om-del-btn').style.display='none';
  ['on','oph','oq','ome'].forEach(i=>document.getElementById(i).value='');
  document.getElementById('o-stk-preview').textContent='';
  document.getElementById('sync-o').style.display='none';
  const dl=document.getElementById('order-cust-list');
  dl.innerHTML=custs.map(c=>`<option value="${c.name}">`).join('');
  document.getElementById('om').classList.add('show');
}
function openEditOrderModal(id){
  const o=orders.find(x=>x.id===id);if(!o)return;
  document.getElementById('om-title').textContent='✏️ 주문 수정';
  document.getElementById('edit-order-id').value=id;
  document.getElementById('on').value=o.name;document.getElementById('oph').value=o.phone;
  document.getElementById('od').value=o.date;document.getElementById('opp').value=o.pepper;
  document.getElementById('oq').value=o.qty;document.getElementById('ome').value=o.memo||'';
  document.getElementById('om-del-btn').style.display='flex';
  syncOrderQty();previewOSync();
  document.getElementById('om').classList.add('show');
}
function submitOrder(){
  const name=document.getElementById('on').value.trim();const phone=document.getElementById('oph').value.trim();const date=document.getElementById('od').value;const pepper=document.getElementById('opp').value;const qty=parseFloat(document.getElementById('oq').value);const memo=document.getElementById('ome').value.trim();
  if(!name||!phone||!date||!qty){showToast('이름, 연락처, 날짜, 수량을 입력하세요.');return;}
  const editId=document.getElementById('edit-order-id').value;
  if(editId){const o=orders.find(x=>x.id===Number(editId));if(o){const io=getInvItem(o.pepper);if(io)io.stock=Math.max(0,io.stock+o.qty);const in2=getInvItem(pepper);if(in2)in2.stock=Math.max(0,in2.stock-qty);Object.assign(o,{name,phone,date,pepper,qty,memo});}}
  else{orders.push({id:nid++,name,phone,pepper,qty,date,status:'pending',memo});viewDate=pLocal(date);if(!custs.find(c=>c.name===name))custs.push({id:ncid++,name,phone,addr:'',memo:'',join:date});const it=getInvItem(pepper);if(it)it.stock=Math.max(0,it.stock-qty);}
  save();cm('om');renderOrders();renderHome();
  if(detailStack.length>0)refreshTopDetail();
  if(!editId)goPage('orders',document.querySelectorAll('.nb')[1]);
  showToast(editId?'주문이 수정되었습니다!':'주문이 등록되었습니다!');
}
function deleteOrderFromModal(){const id=Number(document.getElementById('edit-order-id').value);cm('om');delO(id);}

// ═══ CUSTOMERS ═══
function buildCM(){
  const m={};
  custs.forEach(c=>{m[c.name]={...c,ords:[],tot:0,kgt:0};});
  orders.forEach(o=>{if(!m[o.name])m[o.name]={id:null,name:o.name,phone:o.phone,addr:'',memo:'',join:o.date,ords:[],tot:0,kgt:0};m[o.name].ords.push(o);m[o.name].tot+=(PP[o.pepper]?.p||0)*Number(o.qty);m[o.name].kgt+=Number(o.qty);});
  return Object.values(m);
}
function setCSort(s,btn){cSort=s;document.querySelectorAll('#cc-chips .chip').forEach(c=>c.classList.remove('active'));btn.classList.add('active');renderCusts();}
function renderCusts(){
  const q=(document.getElementById('csearch')?.value||'').trim().toLowerCase();
  let list=buildCM();
  if(q)list=list.filter(c=>c.name.toLowerCase().includes(q)||c.phone.includes(q));
  if(cSort==='total')list.sort((a,b)=>b.tot-a.tot);
  else if(cSort==='count')list.sort((a,b)=>b.ords.length-a.ords.length);
  else if(cSort==='name')list.sort((a,b)=>a.name.localeCompare(b.name,'ko'));
  else list.sort((a,b)=>{const la=a.ords.length?[...a.ords].sort((x,y)=>y.date.localeCompare(x.date))[0].date:'0';const lb=b.ords.length?[...b.ords].sort((x,y)=>y.date.localeCompare(x.date))[0].date:'0';return lb.localeCompare(la);});
  document.getElementById('c-all').textContent=list.length;
  document.getElementById('c-vip').textContent=list.filter(c=>grade(c.tot,c.ords.length).l.includes('VIP')).length;
  document.getElementById('c-new').textContent=list.filter(c=>grade(c.tot,c.ords.length).l.includes('신규')).length;
  if(!list.length){document.getElementById('cust-list').innerHTML='<div class="empty"><div class="ei">👤</div><p>검색 결과 없음</p></div>';return;}
  document.getElementById('cust-list').innerHTML=list.map(c=>{
    const g=grade(c.tot,c.ords.length);const col=AVC[Math.abs(c.name.charCodeAt(0))%AVC.length];
    const pm={};c.ords.forEach(o=>pm[o.pepper]=(pm[o.pepper]||0)+Number(o.qty));
    const pbs=Object.entries(pm).sort((a,b)=>b[1]-a[1]).slice(0,2).map(([n])=>`<span class="pb ${PP[n]?.c||'pb-r'}" style="font-size:9px;padding:2px 6px">${PP[n]?.e||'🌶'} ${n}</span>`).join('');
    const last=c.ords.length?[...c.ords].sort((a,b)=>b.date.localeCompare(a.date))[0].date:null;
    return`<div class="cc" onclick="openCustDetail('${c.name}')"><div class="cct"><div class="cav" style="background:${col}">${c.name.charAt(0)}</div><div class="cinf"><div class="cnam">${c.name}</div><div class="cpho">📞 ${c.phone}</div><div class="cpbs">${pbs}</div></div><div class="crgt"><div class="ctot">₩${c.tot.toLocaleString()}</div><div class="ccnt">${c.ords.length}건 · ${c.kgt}kg</div><div class="cgrd ${g.c}">${g.l}</div><div style="font-size:9px;color:#c4b5a5;margin-top:2px">${last||'주문없음'}</div></div></div></div>`;
  }).join('');
}

// ═══ CUSTOMER DETAIL ═══
function openCustDetail(name){openDetail(name,el=>renderCustDetailInto(el,name));}
function renderCustDetailInto(el,name){
  const list=buildCM();const c=list.find(x=>x.name===name);
  if(!c){el.innerHTML='<div class="empty"><div class="ei">❌</div><p>고객을 찾을 수 없습니다</p></div>';return;}
  const g=grade(c.tot,c.ords.length);const col=AVC[Math.abs(name.charCodeAt(0))%AVC.length];
  const last=c.ords.length?[...c.ords].sort((a,b)=>b.date.localeCompare(a.date))[0].date:null;
  const pm={};c.ords.forEach(o=>pm[o.pepper]=(pm[o.pepper]||0)+Number(o.qty));
  const topPbs=Object.entries(pm).sort((a,b)=>b[1]-a[1]).map(([n,q])=>`<span class="pb ${PP[n]?.c||'pb-r'}" style="margin-bottom:4px">${PP[n]?.e||'🌶'} ${n} <b>${q}kg</b></span>`).join(' ');
  const orderRows=!c.ords.length?'<div class="empty"><div class="ei">📭</div><p>주문 없음</p></div>':[...c.ords].sort((a,b)=>b.date.localeCompare(a.date)).map(o=>{const p=PP[o.pepper]||{e:'🌶️',c:'pb-r',p:0};const st=o.status==='done'?'<span style="font-size:10px;color:#10b981;font-weight:700">✅</span>':'<span style="font-size:10px;color:#f59e0b;font-weight:700">⏳</span>';return`<div class="det-order-row" onclick="openOrderDetail(${o.id})"><span class="dor-date">${o.date}</span><span class="dor-p"><span class="pb ${p.c}" style="font-size:9px;padding:2px 6px">${p.e} ${o.pepper}</span></span><span class="dor-q">${o.qty}kg</span><span style="font-size:10px;color:#a8a29e;margin-right:4px">${st}</span><span style="color:#a8a29e;font-size:12px">›</span></div>`;}).join('');
  const addrEsc=(c.addr||'').replace(/'/g,"\\'");
  el.innerHTML=`
    <div class="det-hero"><div class="det-avatar" style="background:${col}">${c.name.charAt(0)}</div><div class="det-info"><div class="det-name">${c.name}</div><div class="det-phone"><a href="tel:${c.phone}" onclick="openTel(event,'${c.phone}')">📞 ${c.phone}</a></div><div class="det-grade">${g.l}</div></div></div>
    <div class="det-btns">
      <button class="det-btn det-btn-sms" onclick="openMsgModal('${c.name}','${c.phone}')"><span>💬</span>문자</button>
      <button class="det-btn det-btn-kakao" onclick="openMsgModal('${c.name}','${c.phone}','kakao')"><span>💛</span>카카오</button>
      <button class="det-btn det-btn-order" onclick="qOrder('${c.name}','${c.phone}')"><span>🛒</span>주문</button>
      <button class="det-btn det-btn-parcel" onclick="qParcel('${c.name}','${c.phone}','${addrEsc}')"><span>🚚</span>택배</button>
      <button class="det-btn det-btn-edit" onclick="openEditCustModal('${c.name}')"><span>✏️</span>수정</button>
      <button class="det-btn det-btn-del" onclick="deleteCustByName('${c.name}')"><span>🗑</span>삭제</button>
    </div>
    <div class="det-stat-row"><div class="dsd"><div class="dsdv">${c.ords.length}</div><div class="dsdl">총 주문</div></div><div class="dsd"><div class="dsdv">${c.kgt}kg</div><div class="dsdl">총 수량</div></div><div class="dsd"><div class="dsdv">₩${Math.round(c.tot/1000)}천</div><div class="dsdl">누적매출</div></div></div>
    <div class="card"><div class="card-title">📋 기본 정보</div>
      <div class="info-row"><span class="info-lbl">이름</span><span class="info-val" style="font-weight:700">${c.name}</span></div>
      <div class="info-row"><span class="info-lbl">연락처</span><span class="info-val"><a href="tel:${c.phone}" onclick="openTel(event,'${c.phone}')" style="color:var(--red2);font-weight:700;text-decoration:none">📞 ${c.phone}</a></span></div>
      ${c.addr?`<div class="info-row"><span class="info-lbl">주소</span><span class="info-val">${c.addr}</span></div>`:''}
      ${c.memo?`<div class="info-row"><span class="info-lbl">메모</span><span class="info-val">${c.memo}</span></div>`:''}
      <div class="info-row"><span class="info-lbl">가입일</span><span class="info-val">${c.join||'-'}</span></div>
      <div class="info-row"><span class="info-lbl">마지막주문</span><span class="info-val">${last||'없음'}</span></div>
    </div>
    ${topPbs?`<div class="card"><div class="card-title">🌶️ 선호 고추</div><div style="display:flex;flex-wrap:wrap;gap:6px">${topPbs}</div></div>`:''}
    <div class="card"><div class="card-title">📦 주문 이력 (${c.ords.length}건)</div>${orderRows}</div>`;
}

// ═══ CUSTOMER MODAL ═══
function openCustModal(){document.getElementById('cmo-title').textContent='👤 고객 등록';document.getElementById('edit-cust-id').value='';document.getElementById('cmo-del-btn').style.display='none';['cn','cp','ca','cmemo'].forEach(i=>document.getElementById(i).value='');document.getElementById('cmo').classList.add('show');}
function openEditCustModal(name){const c=custs.find(x=>x.name===name)||buildCM().find(x=>x.name===name);if(!c)return;document.getElementById('cmo-title').textContent='✏️ 고객 정보 수정';document.getElementById('edit-cust-id').value=c.id||'__name__'+name;document.getElementById('cn').value=c.name||name;document.getElementById('cp').value=c.phone||'';document.getElementById('ca').value=c.addr||'';document.getElementById('cmemo').value=c.memo||'';document.getElementById('cmo-del-btn').style.display='flex';document.getElementById('cmo').classList.add('show');}
function submitCust(){const name=document.getElementById('cn').value.trim();const phone=document.getElementById('cp').value.trim();if(!name||!phone){showToast('이름과 연락처를 입력하세요.');return;}const addr=document.getElementById('ca').value.trim();const memo=document.getElementById('cmemo').value.trim();const editId=document.getElementById('edit-cust-id').value;if(editId){let c=custs.find(x=>String(x.id)===editId);if(!c&&editId.startsWith('__name__')){const nm=editId.slice(8);c=custs.find(x=>x.name===nm);}if(c)Object.assign(c,{name,phone,addr,memo});else custs.push({id:ncid++,name,phone,addr,memo,join:TSTR});}else{const ex=custs.find(x=>x.name===name);if(ex)Object.assign(ex,{phone,addr,memo});else custs.push({id:ncid++,name,phone,addr,memo,join:TSTR});}save();cm('cmo');renderCusts();if(detailStack.length>0)refreshTopDetail();showToast('저장되었습니다!');}
function deleteCustFromModal(){const editId=document.getElementById('edit-cust-id').value;cm('cmo');let name='';if(editId.startsWith('__name__'))name=editId.slice(8);else{const c=custs.find(x=>String(x.id)===editId);if(c)name=c.name;}if(name)deleteCustByName(name);}
function deleteCustByName(name){showConfirm('🗑️','고객 삭제',`"${name}" 고객을 삭제할까요?`,()=>{custs=custs.filter(c=>c.name!==name);save();renderCusts();if(detailStack.length>0)goBack();});}
function qOrder(name,phone){document.getElementById('on').value=name;document.getElementById('oph').value=phone;document.getElementById('od').value=TSTR;document.getElementById('edit-order-id').value='';document.getElementById('om-del-btn').style.display='none';document.getElementById('om-title').textContent='🌶️ 새 주문 등록';document.getElementById('om').classList.add('show');}

// ═══════════════════════════════════════
//  외부링크 버그 수정 — tel: / sms: / kakaotalk: 핸들러
// ═══════════════════════════════════════

// tel: 링크 — PWA standalone 모드에서도 전화 앱 정상 실행
function openTel(e, phone){
  e.preventDefault();
  e.stopPropagation();
  const clean=phone.replace(/[^0-9+]/g,'');
  // window.location.href 대신 <a> 동적 생성으로 실제 클릭 유발
  const a=document.createElement('a');
  a.href='tel:'+clean;
  a.style.display='none';
  document.body.appendChild(a);
  a.click();
  setTimeout(()=>document.body.removeChild(a),300);
}

// SMS 전송 — iOS/Android 구분 처리 + PWA 모드 대응
function doSendSms(){
  const phone=document.getElementById('msg-phone').value.replace(/[^0-9]/g,'');
  const text=document.getElementById('msg-text').value.trim();
  if(!text){showToast('메시지 내용을 입력하세요.');return;}
  if(!phone){showToast('전화번호가 없습니다.');return;}
  const encoded=encodeURIComponent(text);
  const isIOS=/iPad|iPhone|iPod/.test(navigator.userAgent)&&!window.MSStream;
  const url=isIOS?`sms:${phone}&body=${encoded}`:`sms:${phone}?body=${encoded}`;
  const a=document.createElement('a');
  a.href=url;
  a.style.display='none';
  document.body.appendChild(a);
  a.click();
  setTimeout(()=>{document.body.removeChild(a);cm('msg-modal');},400);
}

function copyAndOpenSms(){
  const text=document.getElementById('msg-text').value.trim();
  if(!text){showToast('메시지 내용을 입력하세요.');return;}
  const phone=document.getElementById('msg-phone').value.replace(/[^0-9]/g,'');
  const doCopy=()=>{
    const a=document.createElement('a');
    a.href='sms:'+phone;
    a.style.display='none';
    document.body.appendChild(a);
    a.click();
    setTimeout(()=>document.body.removeChild(a),300);
    showToast('복사 완료! 문자 앱에 붙여넣기 하세요.');
  };
  if(navigator.clipboard&&navigator.clipboard.writeText){
    navigator.clipboard.writeText(text).then(doCopy).catch(()=>{fallbackCopy(text);doCopy();});
  } else {fallbackCopy(text);doCopy();}
}

function fallbackCopy(text){
  const ta=document.createElement('textarea');
  ta.value=text;ta.style.cssText='position:fixed;opacity:0;top:0;left:0';
  document.body.appendChild(ta);ta.focus();ta.select();
  try{document.execCommand('copy');}catch(e){}
  document.body.removeChild(ta);
}

function copyMsgText(){
  const text=document.getElementById('msg-text').value.trim();
  if(!text){showToast('메시지 내용을 입력하세요.');return;}
  if(navigator.clipboard&&navigator.clipboard.writeText){
    navigator.clipboard.writeText(text).then(()=>showToast('📋 복사 완료! 카카오톡에 붙여넣기 하세요.')).catch(()=>{fallbackCopy(text);showToast('📋 복사 완료! 카카오톡에 붙여넣기 하세요.');});
  } else {fallbackCopy(text);showToast('📋 복사 완료! 카카오톡에 붙여넣기 하세요.');}
}

function openKakaoApp(){
  // PWA/standalone 모드에서도 동작하는 딥링크
  const ua=navigator.userAgent.toLowerCase();
  const a=document.createElement('a');
  if(/iphone|ipad|ipod/.test(ua)){
    a.href='kakaotalk://';
    a.style.display='none';
    document.body.appendChild(a);
    a.click();
    setTimeout(()=>{document.body.removeChild(a);},300);
    setTimeout(()=>{
      const b=document.createElement('a');
      b.href='https://apps.apple.com/kr/app/kakaotalk/id362057947';
      b.target='_blank';b.rel='noopener noreferrer';
      b.style.display='none';document.body.appendChild(b);b.click();
      setTimeout(()=>document.body.removeChild(b),300);
    },1500);
  } else if(/android/.test(ua)){
    a.href='kakaotalk://';
    a.style.display='none';document.body.appendChild(a);a.click();
    setTimeout(()=>{document.body.removeChild(a);},300);
    setTimeout(()=>{
      const b=document.createElement('a');
      b.href='market://details?id=com.kakao.talk';
      b.style.display='none';document.body.appendChild(b);b.click();
      setTimeout(()=>document.body.removeChild(b),300);
    },1500);
  } else {
    const b=document.createElement('a');
    b.href='https://www.kakaotalk.com';b.target='_blank';b.rel='noopener noreferrer';
    b.style.display='none';document.body.appendChild(b);b.click();
    setTimeout(()=>document.body.removeChild(b),300);
  }
}

// MSG MODAL
function openMsgModal(name,phone,tabOverride){
  document.getElementById('msg-name').textContent=name;
  document.getElementById('msg-phone-disp').textContent=phone;
  document.getElementById('msg-phone').value=phone;
  document.getElementById('msg-text').value='';
  document.getElementById('kakao-preview').textContent='';
  switchMsgTab(tabOverride||currentMsgTab);
  document.getElementById('msg-modal').classList.add('show');
}
function switchMsgTab(tab){
  currentMsgTab=tab;
  document.getElementById('tab-sms').className='msg-tab'+(tab==='sms'?' active-sms':'');
  document.getElementById('tab-kakao').className='msg-tab'+(tab==='kakao'?' active-kakao':'');
  document.getElementById('panel-sms').style.display=tab==='sms'?'block':'none';
  document.getElementById('panel-kakao').style.display=tab==='kakao'?'block':'none';
  updateMsgPreview();
}
function setMsgText(key){const name=document.getElementById('msg-name').textContent;const tpl=MSG_TEMPLATES[key];document.getElementById('msg-text').value=tpl?tpl(name):'';updateMsgPreview();}
function updateMsgPreview(){const text=document.getElementById('msg-text').value;document.getElementById('kakao-preview').textContent=text||'(내용을 입력하면 미리보기가 표시됩니다)';}

// ═══ INVENTORY ══
function renderInv(){
  document.getElementById('inv-list').innerHTML=inv.map((it,i)=>{const pct=it.stock/it.max*100;const col=pct<20?'#ef4444':pct<50?'#f59e0b':'#10b981';const tc=pct<20?'tr':pct<50?'ty':'tg';return`<div class="iitem" onclick="openInvEdit()"><div class="ileft"><div class="iico" style="background:${col}22">${it.e}</div><div><div class="iname">${it.name}</div><div class="istk">${it.stock}kg / ${it.max}kg</div><div class="sbar"><div class="sbarf" style="width:${pct}%;background:${col}"></div></div></div></div><div style="text-align:right"><div class="ipr">₩${it.price.toLocaleString()}<span class="ipu">/kg</span></div><span class="tag ${tc}" style="margin-top:4px;display:inline-block">${pct<20?'부족':pct<50?'보통':'충분'}</span></div></div>`;}).join('');
  document.getElementById('ptbl').innerHTML=inv.map(it=>{const pct=it.stock/it.max*100;const tc=pct<20?'tr':pct<50?'ty':'tg';return`<tr><td>${it.e} ${it.name}</td><td>kg</td><td style="font-weight:700;color:var(--red2)">₩${it.price.toLocaleString()}</td><td><span class="tag ${tc}">${pct<20?'부족':pct<50?'보통':'충분'}</span></td></tr>`;}).join('');
}
function openInvEdit(){document.getElementById('inv-edit-body').innerHTML=inv.map((it,i)=>`<div class="inv-edit-row"><span style="font-size:18px;width:28px;flex-shrink:0">${it.e}</span><span style="font-size:12px;font-weight:700;flex:1">${it.name}</span><button class="inv-qty-btn" onclick="adjInv(${i},-5)">−</button><input class="inv-qty-input" id="inv-qty-${i}" type="number" value="${it.stock}" min="0" step="1"/><button class="inv-qty-btn" onclick="adjInv(${i},5)">+</button><span style="font-size:10px;color:#a8a29e;width:22px;text-align:right">kg</span></div>`).join('');document.getElementById('inv-modal').classList.add('show');}
function adjInv(i,d){const el=document.getElementById(`inv-qty-${i}`);el.value=Math.max(0,Number(el.value)+d);}
function saveInv(){inv.forEach((it,i)=>{const el=document.getElementById(`inv-qty-${i}`);if(el)it.stock=Math.max(0,Number(el.value));});save();cm('inv-modal');renderInv();showToast('재고가 저장되었습니다!');}

// ═══ PRICE EDIT ═══
function openPriceEdit(){document.getElementById('price-edit-body').innerHTML=inv.map((it,i)=>`<div class="price-edit-row"><span style="font-size:20px;flex-shrink:0">${it.e}</span><span style="font-size:13px;font-weight:700;flex:1;color:#1c1917">${it.name}</span><span style="font-size:11px;color:#a8a29e;margin-right:4px">₩</span><input class="price-input" id="price-${i}" type="number" value="${it.price}" min="100" step="100"/><span style="font-size:10px;color:#a8a29e;margin-left:4px">/kg</span></div>`).join('');document.getElementById('price-modal').classList.add('show');}
function savePrice(){inv.forEach((it,i)=>{const el=document.getElementById(`price-${i}`);if(el){const p=Math.max(100,Number(el.value));it.price=p;if(PP[it.name])PP[it.name].p=p;}});save();cm('price-modal');renderInv();showToast('가격이 저장되었습니다!');}

// ═══ PEPPER MGR ═══
function openPepperMgr(){renderPepperMgrBody();document.getElementById('pepper-mgr-modal').classList.add('show');}
function renderPepperMgrBody(){document.getElementById('pepper-mgr-body').innerHTML=inv.map((it,i)=>`<div class="pepper-item-row" id="prow-${i}"><input class="pi-emoji" id="pi-e-${i}" value="${it.e}" type="text" maxlength="4"/><input class="pi-name" id="pi-n-${i}" value="${it.name}" type="text" placeholder="품목명"/><input class="pi-price" id="pi-p-${i}" value="${it.price}" type="number" min="100" step="100" title="kg당 가격"/><button class="pi-del" onclick="removePepperRow(${i})">×</button></div>`).join('');}
function addPepperRow(){inv.push({name:'새품목',e:'🌶️',c:'pb-r',col:'#c0392b',stock:0,max:50,price:5000});renderPepperMgrBody();}
function removePepperRow(i){if(inv.length<=1){showToast('품목은 최소 1개 이상이어야 합니다.');return;}showConfirm('🗑️','품목 삭제',`"${inv[i].name}"을 삭제할까요?`,()=>{inv.splice(i,1);renderPepperMgrBody();});}
function savePepperMgr(){const updated=[];for(let i=0;i<inv.length;i++){const eEl=document.getElementById(`pi-e-${i}`);const nEl=document.getElementById(`pi-n-${i}`);const pEl=document.getElementById(`pi-p-${i}`);if(!eEl||!nEl||!pEl)continue;const name=nEl.value.trim();if(!name){showToast('품목 이름을 모두 입력하세요.');return;}updated.push({...inv[i],e:eEl.value.trim()||'🌶️',name,price:Math.max(100,Number(pEl.value)||5000)});}const names=updated.map(x=>x.name);if(new Set(names).size!==names.length){showToast('품목 이름이 중복됩니다.');return;}updated.forEach((it,i)=>{it.col=it.col||PEPPER_COLORS[i%PEPPER_COLORS.length];it.c=it.c||'pb-r';});inv=updated;rebuildPP();fillPepperSelects();save();cm('pepper-mgr-modal');renderInv();renderHome();showToast('품목이 저장되었습니다!');}

// ═══ PARCEL ═══
const P_STATUS={ready:{lbl:'⏳ 준비중',dot:'ps-ready',txt:'ps-ready-t'},sent:{lbl:'🚚 발송완료',dot:'ps-sent',txt:'ps-sent-t'},done:{lbl:'✅ 수령완료',dot:'ps-done',txt:'ps-done-t'}};
function setPFilter(f,btn){pFilter=f;document.querySelectorAll('#parcel-chips .chip').forEach(c=>c.classList.remove('active'));btn.classList.add('active');renderParcel();}
function renderParcel(){
  document.getElementById('pc-all').textContent=parcels.length;document.getElementById('pc-ready').textContent=parcels.filter(p=>p.status==='ready').length;document.getElementById('pc-sent').textContent=parcels.filter(p=>p.status==='sent').length;document.getElementById('pc-done').textContent=parcels.filter(p=>p.status==='done').length;
  let list=pFilter==='all'?[...parcels]:parcels.filter(p=>p.status===pFilter);list=[...list].sort((a,b)=>b.id-a.id);
  const el=document.getElementById('parcel-list');
  if(!list.length){el.innerHTML='<div class="empty"><div class="ei">🚚</div><p>택배 내역 없음</p></div>';return;}
  el.innerHTML=list.map(p=>{const ps=P_STATUS[p.status]||P_STATUS.ready;const pp=PP[p.pepper]||{e:'🌶️',c:'pb-r'};const lk=p.linkedOrderId?'<span style="font-size:9px;background:#dcfce7;color:#16a34a;border-radius:99px;padding:1px 6px;font-weight:700;margin-left:4px">🔗</span>':'';return`<div class="parcel-card" onclick="openParcelDetail(${p.id})"><div class="parcel-head"><div class="parcel-name">${p.name}${lk}</div><div class="parcel-status"><div class="ps-dot ${ps.dot}"></div><span class="ps-lbl ${ps.txt}">${ps.lbl}</span></div></div><div class="parcel-detail"><div class="pd-item"><span>${pp.e}</span><b>${p.pepper}</b> ${p.qty}kg</div><div class="pd-item">📅 <b>${p.date}</b></div><div class="pd-item">🚚 <b>${p.company}</b></div>${p.tracking?`<div class="pd-item">📦 <b>${p.tracking}</b></div>`:''}</div>${p.addr?`<div style="font-size:10px;color:#a8a29e;margin-top:6px;padding-top:6px;border-top:1px solid #fef2f2">📍 ${p.addr}</div>`:''}</div>`;}).join('');
}
function openParcelDetail(id){openDetail('택배 상세',el=>renderParcelDetailInto(el,id));}
function renderParcelDetailInto(el,id){
  const p=parcels.find(x=>x.id===id);if(!p){el.innerHTML='<div class="empty"><div class="ei">❌</div><p>택배를 찾을 수 없습니다</p></div>';return;}
  const ps=P_STATUS[p.status]||P_STATUS.ready;const pp=PP[p.pepper]||{e:'🌶️',c:'pb-r',p:0};const price=(pp.p||0)*p.qty;
  const lo=p.linkedOrderId?orders.find(o=>o.id===p.linkedOrderId):null;
  el.innerHTML=`
    <div style="background:linear-gradient(135deg,#065f46,#10b981);border-radius:16px;padding:17px;margin-bottom:10px;color:#fff"><div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:9px"><div style="font-size:17px;font-weight:900">${p.name}</div><span class="tag tg" style="background:rgba(255,255,255,.2);color:#fff">${ps.lbl}</span></div><div style="font-size:12px;opacity:.8;margin-bottom:4px">${p.company} ${p.tracking?'· '+p.tracking:''}</div><div style="font-size:21px;font-weight:900">₩${price.toLocaleString()}</div><div style="font-size:10px;opacity:.65">${p.qty}kg × ₩${(pp.p||0).toLocaleString()}/kg</div></div>
    <div class="card"><div class="card-title">📋 배송 정보</div>
      <div class="info-row"><span class="info-lbl">고객</span><span class="info-val" style="font-weight:700">${p.name}</span></div>
      <div class="info-row"><span class="info-lbl">연락처</span><span class="info-val"><a href="tel:${p.phone}" onclick="openTel(event,'${p.phone}')" style="color:var(--red2);font-weight:700;text-decoration:none">📞 ${p.phone}</a></span></div>
      <div class="info-row"><span class="info-lbl">주소</span><span class="info-val">${p.addr||'미입력'}</span></div>
      <div class="info-row"><span class="info-lbl">발송일</span><span class="info-val">${p.date}</span></div>
      <div class="info-row"><span class="info-lbl">품목</span><span class="info-val">${pp.e} ${p.pepper} ${p.qty}kg</span></div>
      <div class="info-row"><span class="info-lbl">택배사</span><span class="info-val">${p.company}</span></div>
      ${p.tracking?`<div class="info-row"><span class="info-lbl">운송장</span><span class="info-val" style="font-weight:700;font-size:13px">${p.tracking}</span></div>`:''}
      ${p.memo?`<div class="info-row"><span class="info-lbl">메모</span><span class="info-val">${p.memo}</span></div>`:''}
    </div>
    ${lo?`<div class="card" style="border-color:#86efac"><div class="card-title" style="color:#16a34a">🔗 연결된 주문</div><div class="info-row"><span class="info-lbl">주문일</span><span class="info-val">${lo.date}</span></div><div class="info-row"><span class="info-lbl">품목</span><span class="info-val">${PP[lo.pepper]?.e||'🌶'} ${lo.pepper} ${lo.qty}kg</span></div><button onclick="openOrderDetail(${lo.id})" style="margin-top:8px;width:100%;padding:9px;border:1.5px solid #86efac;background:#f0fdf4;border-radius:10px;font-size:11px;font-weight:700;color:#16a34a;cursor:pointer;font-family:inherit">📋 주문 상세 보기</button></div>`:''}
    <div style="display:flex;gap:7px;margin-bottom:10px;flex-wrap:wrap">
      ${p.status!=='sent'?`<button onclick="setPS(${p.id},'sent')" style="flex:1;padding:10px;border:none;background:#dbeafe;border-radius:12px;font-size:12px;font-weight:700;color:#1d4ed8;cursor:pointer;font-family:inherit;min-width:80px">🚚 발송완료</button>`:''}
      ${p.status!=='done'?`<button onclick="setPS(${p.id},'done')" style="flex:1;padding:10px;border:none;background:#dcfce7;border-radius:12px;font-size:12px;font-weight:700;color:#16a34a;cursor:pointer;font-family:inherit;min-width:80px">✅ 수령완료</button>`:''}
      ${p.status!=='ready'?`<button onclick="setPS(${p.id},'ready')" style="flex:1;padding:10px;border:none;background:#fef9c3;border-radius:12px;font-size:12px;font-weight:700;color:#a16207;cursor:pointer;font-family:inherit;min-width:8
