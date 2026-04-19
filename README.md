<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>نظام الحضور المتقدم — الأمن السيبراني</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;900&family=Tajawal:wght@300;400;500;700;800&display=swap" rel="stylesheet">
<style>
:root {
--c1:#07091a;--c2:#0c1126;--c3:#101830;--c4:#152040;
--acc:#3b82f6;--acc2:#1d4ed8;--acc3:#60a5fa;--acc4:#93c5fd;
--grn:#10b981;--grn2:#059669;--red:#ef4444;--red2:#dc2626;
--amb:#f59e0b;--amb2:#d97706;--pur:#8b5cf6;--pur2:#6d28d9;
--cyn:#06b6d4;--pnk:#ec4899;
--txt:#e2e8f0;--txt2:#94a3b8;--txt3:#64748b;
--brd:rgba(59,130,246,0.15);--brd2:rgba(59,130,246,0.3);--brd3:rgba(59,130,246,0.5);
--card:rgba(12,17,38,0.95);--glass:rgba(255,255,255,0.03);
--radius:16px;--radius-sm:10px;--radius-xs:7px;
--sh:0 4px 24px rgba(0,0,0,0.5);--sh2:0 8px 40px rgba(0,0,0,0.6);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{font-size:16px;scroll-behavior:smooth}
body{background:var(--c1);color:var(--txt);font-family:'Cairo',sans-serif;min-height:100vh;overflow-x:hidden}


body::before{
content:'';position:fixed;inset:0;pointer-events:none;z-index:0;
background:
  radial-gradient(ellipse 80% 60% at 50% -10%, rgba(59,130,246,0.14) 0%, transparent 60%),
  radial-gradient(ellipse 40% 40% at 90% 80%, rgba(139,92,246,0.08) 0%, transparent 50%),
  radial-gradient(ellipse 30% 30% at 10% 70%, rgba(16,185,129,0.06) 0%, transparent 50%),
  radial-gradient(ellipse 20% 20% at 80% 20%, rgba(6,182,212,0.05) 0%, transparent 40%);
}
body::after{
content:'';position:fixed;inset:0;pointer-events:none;z-index:0;
background-image:
  linear-gradient(rgba(59,130,246,0.03) 1px, transparent 1px),
  linear-gradient(90deg, rgba(59,130,246,0.03) 1px, transparent 1px);
background-size:60px 60px;
}

.app{position:relative;z-index:1;max-width:1500px;margin:0 auto;padding:24px 16px}


.top-bar{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:28px;flex-wrap:wrap}
.brand{display:flex;align-items:center;gap:14px}
.brand-icon{
width:54px;height:54px;flex-shrink:0;
background:linear-gradient(135deg,var(--acc),var(--acc2));
border-radius:14px;display:flex;align-items:center;justify-content:center;font-size:24px;
box-shadow:0 0 24px rgba(59,130,246,0.45),0 0 60px rgba(59,130,246,0.2);
animation:pulse-icon 3s ease-in-out infinite;
}
@keyframes pulse-icon{0%,100%{box-shadow:0 0 24px rgba(59,130,246,0.45),0 0 60px rgba(59,130,246,0.2)}50%{box-shadow:0 0 32px rgba(59,130,246,0.65),0 0 80px rgba(59,130,246,0.3)}}
.brand-text h1{font-family:'Tajawal',sans-serif;font-size:1.3rem;font-weight:800;line-height:1.2}
.brand-text p{font-size:.75rem;color:var(--txt2);margin-top:2px}
.live-clock{
background:var(--c2);border:1px solid var(--brd);border-radius:10px;
padding:8px 16px;text-align:center;
}
.live-clock .time{font-family:'Tajawal',sans-serif;font-size:1.3rem;font-weight:700;color:var(--acc3);letter-spacing:2px}
.live-clock .date-str{font-size:.68rem;color:var(--txt2);margin-top:1px}
.top-actions{display:flex;gap:8px;flex-wrap:wrap;align-items:center}


.nav-tabs{display:flex;gap:3px;background:var(--c2);border:1px solid var(--brd);border-radius:var(--radius);padding:4px;margin-bottom:22px;overflow-x:auto;scrollbar-width:none}
.nav-tabs::-webkit-scrollbar{display:none}
.nav-tab{
flex:1;min-width:90px;padding:10px 14px;border-radius:12px;border:none;
background:transparent;color:var(--txt2);font-family:'Cairo',sans-serif;
font-size:.8rem;font-weight:500;cursor:pointer;transition:all .25s ease;
white-space:nowrap;display:flex;align-items:center;justify-content:center;gap:6px;
position:relative;
}
.nav-tab.active{background:linear-gradient(135deg,var(--acc),var(--acc2));color:#fff;box-shadow:0 4px 16px rgba(59,130,246,0.4)}
.nav-tab:not(.active):hover{background:var(--glass);color:var(--txt)}
.tab-badge{
background:var(--red);color:#fff;font-size:.6rem;font-weight:700;
border-radius:10px;padding:1px 5px;line-height:1.4;min-width:16px;text-align:center;
}


.view{display:none;animation:fadeIn .25s ease}
.view.active{display:block}
@keyframes fadeIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}


.stats-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:12px;margin-bottom:22px}
.stat-card{
background:var(--card);border:1px solid var(--brd);border-radius:var(--radius);
padding:18px 14px;text-align:center;position:relative;overflow:hidden;
transition:transform .2s,box-shadow .2s;cursor:default;
}
.stat-card:hover{transform:translateY(-3px);box-shadow:var(--sh2)}
.stat-card::before{content:'';position:absolute;top:0;left:0;right:0;height:3px}
.stat-card.total::before{background:linear-gradient(90deg,var(--acc),var(--pur))}
.stat-card.present-s::before{background:linear-gradient(90deg,var(--grn),#34d399)}
.stat-card.absent-s::before{background:linear-gradient(90deg,var(--red),#f87171)}
.stat-card.rate-s::before{background:linear-gradient(90deg,var(--amb),#fcd34d)}
.stat-card.sessions-s::before{background:linear-gradient(90deg,var(--cyn),var(--acc))}
.stat-card.risk-s::before{background:linear-gradient(90deg,var(--pnk),var(--red))}
.stat-num{font-size:2.2rem;font-weight:700;font-family:'Tajawal',sans-serif;line-height:1}
.stat-num.c-acc{color:var(--acc3)} .stat-num.c-grn{color:var(--grn)} .stat-num.c-red{color:var(--red)} .stat-num.c-amb{color:var(--amb)} .stat-num.c-cyn{color:var(--cyn)} .stat-num.c-pnk{color:var(--pnk)}
.stat-lbl{font-size:.72rem;color:var(--txt2);margin-top:5px}
.stat-icon{position:absolute;top:12px;left:12px;opacity:.12;font-size:2rem}


.card{background:var(--card);border:1px solid var(--brd);border-radius:var(--radius);padding:20px;margin-bottom:18px}
.card-header{display:flex;align-items:center;justify-content:space-between;gap:10px;margin-bottom:16px;flex-wrap:wrap}
.card-title{font-size:.9rem;font-weight:600;display:flex;align-items:center;gap:8px}


.btn{
display:inline-flex;align-items:center;justify-content:center;gap:7px;
padding:9px 16px;border-radius:var(--radius-sm);border:1px solid var(--brd);
background:transparent;color:var(--txt);font-family:'Cairo',sans-serif;
font-size:.8rem;font-weight:600;cursor:pointer;transition:all .2s;white-space:nowrap;text-decoration:none;
}
.btn:hover{background:var(--glass);border-color:var(--brd2)}
.btn:active{transform:scale(.97)}
.btn.btn-primary{background:linear-gradient(135deg,var(--acc),var(--acc2));border-color:transparent;color:#fff;box-shadow:0 4px 14px rgba(59,130,246,0.35)}
.btn.btn-primary:hover{box-shadow:0 6px 22px rgba(59,130,246,0.5);transform:translateY(-1px)}
.btn.btn-success{background:rgba(16,185,129,.15);border-color:rgba(16,185,129,.3);color:var(--grn)}
.btn.btn-success:hover{background:rgba(16,185,129,.25)}
.btn.btn-danger{background:rgba(239,68,68,.1);border-color:rgba(239,68,68,.3);color:var(--red)}
.btn.btn-danger:hover{background:rgba(239,68,68,.2)}
.btn.btn-warning{background:rgba(245,158,11,.1);border-color:rgba(245,158,11,.3);color:var(--amb)}
.btn.btn-warning:hover{background:rgba(245,158,11,.2)}
.btn.btn-purple{background:rgba(139,92,246,.15);border-color:rgba(139,92,246,.3);color:var(--pur)}
.btn.btn-purple:hover{background:rgba(139,92,246,.25)}
.btn.btn-cyan{background:rgba(6,182,212,.12);border-color:rgba(6,182,212,.3);color:var(--cyn)}
.btn.btn-cyan:hover{background:rgba(6,182,212,.22)}
.btn.btn-sm{padding:7px 12px;font-size:.75rem}
.btn.btn-xs{padding:5px 9px;font-size:.7rem}
.btn-group{display:flex;gap:6px;flex-wrap:wrap}


.filters{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:12px}
.flt-btn{
padding:7px 14px;border-radius:8px;border:1px solid var(--brd);
background:transparent;color:var(--txt2);font-family:'Cairo',sans-serif;
font-size:.78rem;cursor:pointer;transition:all .2s;white-space:nowrap;
}
.flt-btn.active,.flt-btn:hover{border-color:var(--acc);color:var(--acc3);background:rgba(59,130,246,.1)}


.search-box{position:relative;margin-bottom:14px}
.search-box input{
width:100%;padding:11px 44px 11px 14px;
background:var(--c2);border:1px solid var(--brd);border-radius:var(--radius-sm);
color:var(--txt);font-family:'Cairo',sans-serif;font-size:.87rem;outline:none;transition:border-color .2s;
}
.search-box input:focus{border-color:var(--acc);box-shadow:0 0 0 3px rgba(59,130,246,.1)}
.search-box svg{position:absolute;right:14px;top:50%;transform:translateY(-50%);color:var(--txt3);pointer-events:none}


.date-nav{
display:flex;align-items:center;gap:8px;
background:var(--c2);border:1px solid var(--brd);border-radius:var(--radius-sm);padding:7px 12px;
}
.date-nav input{
background:transparent;border:none;color:var(--txt);
font-family:'Cairo',sans-serif;font-size:.87rem;font-weight:600;outline:none;cursor:pointer;
}
.date-nav input::-webkit-calendar-picker-indicator{filter:invert(1);opacity:.6;cursor:pointer}
.date-nav-btn{
background:transparent;border:1px solid var(--brd);border-radius:6px;
color:var(--txt2);cursor:pointer;padding:4px 8px;font-size:.85rem;
transition:all .2s;line-height:1;
}
.date-nav-btn:hover{background:var(--glass);border-color:var(--acc);color:var(--acc3)}


.students-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:10px}
.s-card{
background:var(--c2);border:1px solid var(--brd);border-radius:var(--radius-sm);
padding:13px 14px;display:flex;align-items:flex-start;gap:10px;
cursor:pointer;transition:all .2s;position:relative;overflow:hidden;
}
.s-card:hover{border-color:var(--brd2);background:var(--c3)}
.s-card.present{border-right:3px solid var(--grn)}
.s-card.absent{border-right:3px solid var(--red)}
.s-card.late{border-right:3px solid var(--amb)}
.s-card.excused{border-right:3px solid var(--pur)}
.s-avatar{
width:42px;height:42px;border-radius:50%;
display:flex;align-items:center;justify-content:center;
font-weight:700;font-size:.78rem;flex-shrink:0;
font-family:'Tajawal',sans-serif;letter-spacing:0;
}
.s-card.present .s-avatar{background:rgba(16,185,129,.15);color:var(--grn)}
.s-card.absent .s-avatar{background:rgba(239,68,68,.15);color:var(--red)}
.s-card.late .s-avatar{background:rgba(245,158,11,.15);color:var(--amb)}
.s-card.excused .s-avatar{background:rgba(139,92,246,.15);color:var(--pur)}
.s-info{flex:1;min-width:0}
.s-name{font-size:.84rem;font-weight:600;white-space:normal;word-break:break-word;line-height:1.35}
.s-meta{font-size:.68rem;color:var(--txt2);margin-top:1px}
.s-status-cycle{
display:flex;align-items:center;gap:4px;flex-shrink:0;margin-top:2px;
}
.s-status-btn{
width:28px;height:28px;border-radius:50%;border:none;cursor:pointer;
font-size:.8rem;display:flex;align-items:center;justify-content:center;
transition:all .15s;opacity:.5;
}
.s-status-btn.active{opacity:1;transform:scale(1.15)}
.s-status-btn.p{background:rgba(16,185,129,.2);color:var(--grn)}
.s-status-btn.p.active{background:rgba(16,185,129,.35)}
.s-status-btn.a{background:rgba(239,68,68,.2);color:var(--red)}
.s-status-btn.a.active{background:rgba(239,68,68,.35)}
.s-status-btn.l{background:rgba(245,158,11,.2);color:var(--amb)}
.s-status-btn.l.active{background:rgba(245,158,11,.35)}
.s-status-btn.e{background:rgba(139,92,246,.2);color:var(--pur)}
.s-status-btn.e.active{background:rgba(139,92,246,.35)}


.table-wrap{overflow-x:auto;border-radius:var(--radius-sm)}
table{width:100%;border-collapse:collapse;font-size:.82rem}
thead th{
padding:11px 13px;text-align:right;color:var(--txt2);font-weight:600;
border-bottom:1px solid var(--brd);white-space:nowrap;background:var(--c2);
}
thead th:first-child{border-radius:0 8px 0 0} thead th:last-child{border-radius:8px 0 0 0}
tbody td{padding:11px 13px;border-bottom:1px solid rgba(255,255,255,.04);color:var(--txt);vertical-align:middle}
tbody tr:hover td{background:var(--glass)}
tbody tr:last-child td{border-bottom:none}
.sortable{cursor:pointer;user-select:none}
.sortable:hover{color:var(--acc3)}


.progress-bar{height:5px;background:rgba(255,255,255,.08);border-radius:3px;overflow:hidden;margin-top:6px}
.progress-fill{height:100%;border-radius:3px;transition:width .6s ease;background:linear-gradient(90deg,var(--grn),#34d399)}
.progress-fill.low{background:linear-gradient(90deg,var(--red),#f87171)}
.progress-fill.mid{background:linear-gradient(90deg,var(--amb),#fcd34d)}


.badge{display:inline-flex;align-items:center;padding:3px 9px;border-radius:20px;font-size:.68rem;font-weight:600}
.badge.present{background:rgba(16,185,129,.15);color:var(--grn)}
.badge.absent{background:rgba(239,68,68,.15);color:var(--red)}
.badge.late{background:rgba(245,158,11,.15);color:var(--amb)}
.badge.excused{background:rgba(139,92,246,.15);color:var(--pur)}
.chip{display:inline-flex;align-items:center;gap:3px;padding:2px 8px;border-radius:12px;font-size:.68rem;font-weight:600}
.chip.g{background:rgba(16,185,129,.12);color:var(--grn)}
.chip.r{background:rgba(239,68,68,.12);color:var(--red)}
.chip.b{background:rgba(59,130,246,.12);color:var(--acc3)}
.chip.y{background:rgba(245,158,11,.12);color:var(--amb)}
.chip.p{background:rgba(139,92,246,.12);color:var(--pur)}


.modal-overlay{
position:fixed;inset:0;background:rgba(0,0,0,.75);backdrop-filter:blur(8px);
z-index:1000;display:none;align-items:center;justify-content:center;padding:16px;
}
.modal-overlay.open{display:flex}
.modal{
background:var(--c3);border:1px solid var(--brd);border-radius:var(--radius);
padding:26px;width:100%;max-width:480px;box-shadow:var(--sh2);
animation:slideUp .25s ease;
}
.modal.modal-lg{max-width:700px}
@keyframes slideUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
.modal h3{font-size:1.05rem;font-weight:700;margin-bottom:18px;display:flex;align-items:center;gap:8px}
.form-group{margin-bottom:14px}
.form-group label{display:block;font-size:.78rem;color:var(--txt2);margin-bottom:5px;font-weight:500}
.form-group input,.form-group select,.form-group textarea{
width:100%;padding:10px 13px;background:var(--c2);border:1px solid var(--brd);
border-radius:var(--radius-sm);color:var(--txt);font-family:'Cairo',sans-serif;
font-size:.87rem;outline:none;transition:border-color .2s;-webkit-appearance:none;
}
.form-group input:focus,.form-group select:focus,.form-group textarea:focus{border-color:var(--acc);box-shadow:0 0 0 3px rgba(59,130,246,.1)}
.form-group select option{background:var(--c2)}
.form-group textarea{resize:vertical;min-height:80px}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.modal-actions{display:flex;gap:8px;margin-top:18px;justify-content:flex-end}


.toast{
position:fixed;bottom:24px;left:24px;background:var(--c3);border:1px solid var(--brd);
border-radius:var(--radius-sm);padding:13px 18px;display:flex;align-items:center;gap:10px;
font-size:.83rem;font-weight:500;box-shadow:var(--sh2);z-index:9999;
transform:translateX(-120%);transition:transform .35s cubic-bezier(.34,1.56,.64,1);
max-width:320px;
}
.toast.show{transform:translateX(0)}
.toast.success{border-color:rgba(16,185,129,.4)} .toast.error{border-color:rgba(239,68,68,.4)}
.toast.info{border-color:rgba(59,130,246,.4)} .toast.warning{border-color:rgba(245,158,11,.4)}
.toast-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0}
.toast.success .toast-dot{background:var(--grn)} .toast.error .toast-dot{background:var(--red)}
.toast.info .toast-dot{background:var(--acc)} .toast.warning .toast-dot{background:var(--amb)}


.history-item{
display:flex;align-items:center;gap:12px;padding:13px 14px;
background:var(--c2);border:1px solid var(--brd);border-radius:var(--radius-sm);
margin-bottom:7px;cursor:pointer;transition:all .2s;
}
.history-item:hover{border-color:var(--brd2);background:var(--c3)}
.history-date{font-weight:700;font-size:.88rem;min-width:90px}
.history-bars{flex:1;display:grid;grid-template-columns:1fr 1fr;gap:5px}
.h-bar-row{display:flex;align-items:center;gap:7px;font-size:.72rem}
.h-bar{flex:1;height:4px;border-radius:2px;overflow:hidden;background:rgba(255,255,255,.08)}
.h-fill-g{height:100%;background:var(--grn);border-radius:2px}
.h-fill-r{height:100%;background:var(--red);border-radius:2px}


.report-summary{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:12px;margin-bottom:18px}
.rep-student{background:var(--c2);border:1px solid var(--brd);border-radius:var(--radius-sm);padding:13px 14px;transition:border-color .2s}
.rep-student:hover{border-color:var(--brd2)}
.rep-name{font-size:.85rem;font-weight:600;white-space:normal;word-break:break-word;line-height:1.35;margin-bottom:6px}
.rep-stats{display:flex;gap:10px;font-size:.75rem;margin-bottom:7px}


.chart-wrap{padding:10px 0;position:relative;min-height:200px}
.chart-bar-row{display:flex;align-items:center;gap:10px;margin-bottom:10px}
.chart-label{width:130px;font-size:.75rem;text-align:right;color:var(--txt2);overflow:hidden;text-overflow:ellipsis;white-space:normal;word-break:break-word;flex-shrink:0;line-height:1.3}
.chart-bar-track{flex:1;height:26px;background:rgba(255,255,255,.05);border-radius:5px;overflow:hidden;position:relative}
.chart-bar-fill{height:100%;border-radius:5px;display:flex;align-items:center;justify-content:flex-end;padding-right:8px;font-size:.72rem;font-weight:700;color:#fff;transition:width .8s cubic-bezier(.34,1.1,.64,1)}


.donut-wrap{display:flex;align-items:center;gap:24px;flex-wrap:wrap}
.donut-svg{flex-shrink:0}
.donut-legend{display:grid;gap:8px}
.donut-legend-item{display:flex;align-items:center;gap:8px;font-size:.78rem}
.donut-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0}


.note-badge{
display:inline-block;width:8px;height:8px;border-radius:50%;
background:var(--amb);margin-right:4px;vertical-align:middle;
}


.alert-box{
display:flex;align-items:flex-start;gap:12px;padding:14px 16px;
border-radius:var(--radius-sm);margin-bottom:14px;
}
.alert-box.warning{background:rgba(245,158,11,.1);border:1px solid rgba(245,158,11,.25)}
.alert-box.danger{background:rgba(239,68,68,.1);border:1px solid rgba(239,68,68,.25)}
.alert-box.info{background:rgba(59,130,246,.1);border:1px solid rgba(59,130,246,.25)}
.alert-box.success{background:rgba(16,185,129,.1);border:1px solid rgba(16,185,129,.25)}


.loading-overlay{
position:fixed;inset:0;background:var(--c1);z-index:9999;
display:flex;flex-direction:column;align-items:center;justify-content:center;gap:14px;
transition:opacity .5s ease;
}
.loading-overlay.hide{opacity:0;pointer-events:none}
.loader{
width:46px;height:46px;border:3px solid var(--brd);border-top-color:var(--acc);
border-radius:50%;animation:spin .8s linear infinite;
}
@keyframes spin{to{transform:rotate(360deg)}}


.empty-state{
padding:40px 20px;text-align:center;color:var(--txt3);
}
.empty-state svg{margin-bottom:10px;opacity:.4}
.empty-state p{font-size:.85rem}


.settings-info-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:12px;margin-bottom:18px}
.info-block{background:var(--c2);border:1px solid var(--brd);border-radius:var(--radius-sm);padding:14px}
.info-block .lbl{font-size:.7rem;color:var(--txt2);margin-bottom:3px}
.info-block .val{font-weight:600;font-size:.9rem}


.export-dropdown{position:relative;display:inline-block}
.export-menu{
position:absolute;top:calc(100% + 6px);left:0;
background:var(--c3);border:1px solid var(--brd2);border-radius:var(--radius-sm);
padding:6px;min-width:200px;z-index:100;
box-shadow:var(--sh2);animation:fadeIn .15s ease;
}
.export-menu-item{
display:flex;align-items:center;gap:10px;padding:10px 13px;
border-radius:7px;cursor:pointer;font-size:.82rem;transition:all .15s;
}
.export-menu-item:hover{background:var(--glass);color:var(--acc3)}


.select-all-row{
display:flex;align-items:center;justify-content:space-between;padding:9px 12px;
background:rgba(59,130,246,.05);border-radius:8px;margin-bottom:10px;border:1px solid var(--brd);
}
.select-all-row label{font-size:.78rem;color:var(--txt2);cursor:pointer;display:flex;align-items:center;gap:6px}


.att-legend{display:flex;gap:14px;flex-wrap:wrap;font-size:.72rem;color:var(--txt2);margin-bottom:10px;align-items:center}
.att-legend-item{display:flex;align-items:center;gap:5px}
.att-legend-dot{width:10px;height:10px;border-radius:50%}


.detail-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(110px,1fr));gap:10px;margin:14px 0}
.detail-stat{background:var(--c2);border:1px solid var(--brd);border-radius:8px;padding:12px;text-align:center}
.detail-stat .num{font-size:1.5rem;font-weight:700;font-family:'Tajawal',sans-serif}
.detail-stat .lbl{font-size:.68rem;color:var(--txt2);margin-top:3px}
.session-history-mini{max-height:220px;overflow-y:auto;margin-top:10px}
.session-row{
display:flex;align-items:center;justify-content:space-between;
padding:7px 10px;border-radius:7px;margin-bottom:4px;
background:var(--c2);font-size:.78rem;
}


.notif-dot{
width:8px;height:8px;background:var(--red);border-radius:50%;
position:absolute;top:6px;left:6px;
}


@media print{
body{background:#fff !important;color:#000 !important}
.top-bar,.nav-tabs,.btn-group,.top-actions,.date-nav-btn,#exportBtn{display:none !important}
.card{border:1px solid #ccc !important;background:#fff !important}
}


@media (max-width:640px){
.students-grid{grid-template-columns:1fr}
.form-row{grid-template-columns:1fr}
.stat-num{font-size:1.8rem}
}


.s-name,.rep-name,.s-meta{
  direction:rtl;
  unicode-bidi:embed;
}
.s-avatar{
  direction:rtl;
  unicode-bidi:embed;
  overflow:hidden;
}
.students-grid .s-card{
  min-height:64px;
}
.s-info{
  overflow:hidden;
  flex:1;
  min-width:0;
  padding-top:1px;
}


.stat-card{
  transition:transform .2s,box-shadow .2s,border-color .2s;
}
.stat-card:hover{
  border-color:var(--brd2);
}


tbody td{
  direction:rtl;
  unicode-bidi:embed;
}
tbody td div{
  word-break:break-word;
  white-space:normal;
}


#bulkNames{
  direction:rtl;
  unicode-bidi:embed;
  font-family:'Cairo',sans-serif;
  font-size:.9rem;
  line-height:1.8;
}


input[type="text"],textarea{
  direction:rtl;
  unicode-bidi:embed;
}
</style>
</head>
<body>

<div class="loading-overlay" id="loadingOverlay">
<div class="loader"></div>
<p style="color:var(--txt2);font-size:.85rem">جارٍ تهيئة النظام...</p>
</div>

<div class="app">

<!-- TOP BAR -->
<div class="top-bar">
  <div class="brand">
    <div class="brand-icon">
      <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/><circle cx="12" cy="16" r="1" fill="currentColor"/></svg>
    </div>
    <div class="brand-text">
      <h1>نظام حضور الطلاب المتقدم</h1>
      <p>كلية التقنية الشمالية — هندسة الأمن السيبراني · كروب A</p>
    </div>
  </div>
  <div class="live-clock">
    <div class="time" id="clockTime">--:--:--</div>
    <div class="date-str" id="clockDate">جارٍ التحميل...</div>
  </div>
  <div class="top-actions">
    <button class="btn btn-success btn-sm" onclick="openModal('addModal')">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>إضافة طالب
    </button>
    <div class="export-dropdown" id="exportDropdown">
      <button class="btn btn-primary btn-sm" onclick="toggleExportMenu()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
        تصدير ▾
      </button>
      <div class="export-menu" id="exportMenu" style="display:none">
        <div class="export-menu-item" onclick="exportExcel();toggleExportMenu()">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="var(--grn)" stroke-width="2"><rect x="3" y="3" width="18" height="18" rx="2"/><line x1="3" y1="9" x2="21" y2="9"/><line x1="9" y1="21" x2="9" y2="9"/></svg>
          تصدير Excel (.xlsx)
        </div>
        <div class="export-menu-item" onclick="exportCSV();toggleExportMenu()">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="var(--cyn)" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
          تصدير CSV (.csv)
        </div>
        <div class="export-menu-item" onclick="exportPDF();toggleExportMenu()">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="var(--red)" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>
          طباعة / PDF
        </div>
        <div class="export-menu-item" onclick="exportFullReport();toggleExportMenu()">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="var(--pur)" stroke-width="2"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>
          تقرير Excel شامل
        </div>
        <div class="export-menu-item" onclick="exportDB();toggleExportMenu()">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="var(--amb)" stroke-width="2"><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></svg>
          نسخ احتياطي (JSON)
        </div>
      </div>
    </div>
  </div>
</div>

<!-- NAV TABS -->
<div class="nav-tabs">
  <button class="nav-tab active" id="tab-attendance" onclick="switchTab('attendance',this)">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"/></svg>الحضور اليومي
  </button>
  <button class="nav-tab" id="tab-students" onclick="switchTab('students',this)">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/></svg>قائمة الطلاب
  </button>
  <button class="nav-tab" id="tab-history" onclick="switchTab('history',this)">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>السجل التاريخي
  </button>
  <button class="nav-tab" id="tab-reports" onclick="switchTab('reports',this)">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>التقارير
  </button>
  <button class="nav-tab" id="tab-alerts" onclick="switchTab('alerts',this)" style="position:relative">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/><path d="M13.73 21a2 2 0 0 1-3.46 0"/></svg>التنبيهات
    <span class="tab-badge" id="alertBadge">0</span>
  </button>
  <button class="nav-tab" id="tab-settings" onclick="switchTab('settings',this)">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="3"/><path d="M19.07 4.93l-1.41 1.41M4.93 4.93l1.41 1.41M12 2v2M12 20v2M20 12h2M2 12h2M17.66 17.66l1.41 1.41M4.93 19.07l1.41-1.41"/></svg>الإعدادات
  </button>
</div>

<!-- ====== VIEW: ATTENDANCE ====== -->
<div class="view active" id="view-attendance">
  <div class="stats-row">
    <div class="stat-card total"><div class="stat-icon">👥</div><div class="stat-num c-acc" id="s-total">0</div><div class="stat-lbl">إجمالي الطلاب</div></div>
    <div class="stat-card present-s"><div class="stat-icon">✅</div><div class="stat-num c-grn" id="s-present">0</div><div class="stat-lbl">حاضر</div></div>
    <div class="stat-card absent-s"><div class="stat-icon">❌</div><div class="stat-num c-red" id="s-absent">0</div><div class="stat-lbl">غائب</div></div>
    <div class="stat-card" style="--before-bg:linear-gradient(90deg,var(--amb),#fcd34d)"><div class="stat-icon">⏱</div><div class="stat-num c-amb" id="s-late">0</div><div class="stat-lbl" style="font-size:.72rem;color:var(--txt2);margin-top:5px">متأخر</div></div>
    <div class="stat-card rate-s"><div class="stat-icon">📊</div><div class="stat-num c-amb" id="s-rate">0%</div><div class="stat-lbl">نسبة الحضور</div></div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-title">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
        تسجيل الحضور:
        <div class="date-nav">
          <button class="date-nav-btn" onclick="changeDay(-1)" title="اليوم السابق">‹</button>
          <input type="date" id="datePicker" onchange="changeDate(this.value)">
          <button class="date-nav-btn" onclick="changeDay(1)" title="اليوم التالي">›</button>
          <button class="date-nav-btn" onclick="goToday()" title="اليوم" style="font-size:.7rem;padding:4px 7px">اليوم</button>
        </div>
      </div>
      <div class="btn-group">
        <button class="btn btn-success btn-sm" onclick="markAll('present')">✓ تحضير الكل</button>
        <button class="btn btn-danger btn-sm" onclick="markAll('absent')">✗ تغيب الكل</button>
        <button class="btn btn-warning btn-sm" onclick="markAll('late')">⏱ تأخر الكل</button>
        <button class="btn btn-sm" onclick="saveAttendance()">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M19 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11l5 5v11a2 2 0 0 1-2 2z"/><polyline points="17 21 17 13 7 13"/><polyline points="7 3 7 8 15 8"/></svg>حفظ
        </button>
      </div>
    </div>

    <div class="att-legend">
      <span class="att-legend-item"><span class="att-legend-dot" style="background:var(--grn)"></span> حاضر (✓)</span>
      <span class="att-legend-item"><span class="att-legend-dot" style="background:var(--red)"></span> غائب (✗)</span>
      <span class="att-legend-item"><span class="att-legend-dot" style="background:var(--amb)"></span> متأخر (⏱)</span>
      <span class="att-legend-item"><span class="att-legend-dot" style="background:var(--pur)"></span> إذن رسمي</span>
    </div>

    <div class="filters">
      <button class="flt-btn active" onclick="filterStudents('all',this)">الجميع (<span id="count-all">0</span>)</button>
      <button class="flt-btn" onclick="filterStudents('present',this)">حاضر (<span id="count-present">0</span>)</button>
      <button class="flt-btn" onclick="filterStudents('absent',this)">غائب (<span id="count-absent">0</span>)</button>
      <button class="flt-btn" onclick="filterStudents('late',this)">متأخر (<span id="count-late">0</span>)</button>
      <button class="flt-btn" onclick="filterStudents('excused',this)">إذن رسمي (<span id="count-excused">0</span>)</button>
    </div>
    <div class="search-box">
      <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      <input type="text" id="searchInp" placeholder="بحث عن طالب بالاسم..." oninput="renderStudents()">
    </div>
    <div class="select-all-row">
      <label><input type="checkbox" id="checkSelectAll" onchange="selectAllToggle(this)"> تحديد / إلغاء الكل</label>
      <div style="display:flex;gap:6px">
        <button class="btn btn-xs" onclick="bulkMark('present')">✓ تحضير المحددين</button>
        <button class="btn btn-xs btn-danger" onclick="bulkMark('absent')">✗ تغيب المحددين</button>
      </div>
    </div>
    <div class="students-grid" id="studentsGrid"></div>
  </div>
</div>

<!-- ====== VIEW: STUDENTS ====== -->
<div class="view" id="view-students">
  <div class="card">
    <div class="card-header">
      <div class="card-title">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/></svg>
        إدارة الطلاب (<span id="studentsTotalCount">0</span>)
      </div>
      <div class="btn-group">
        <button class="btn btn-success btn-sm" onclick="openModal('addModal')">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>إضافة طالب
        </button>
        <button class="btn btn-cyan btn-sm" onclick="openModal('bulkAddModal')">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>إضافة جماعية
        </button>
      </div>
    </div>
    <div class="search-box">
      <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      <input type="text" id="studentsSearch" placeholder="بحث في قائمة الطلاب..." oninput="renderStudentsTable()">
    </div>
    <div style="margin-bottom:12px;display:flex;gap:6px;flex-wrap:wrap">
      <select id="groupFilter" onchange="renderStudentsTable()" style="padding:7px 12px;background:var(--c2);border:1px solid var(--brd);border-radius:8px;color:var(--txt);font-family:'Cairo',sans-serif;font-size:.8rem;outline:none">
        <option value="">كل المجموعات</option>
        <option value="A">كروب A</option>
        <option value="B">كروب B</option>
        <option value="C">كروب C</option>
      </select>
      <select id="sortStudents" onchange="renderStudentsTable()" style="padding:7px 12px;background:var(--c2);border:1px solid var(--brd);border-radius:8px;color:var(--txt);font-family:'Cairo',sans-serif;font-size:.8rem;outline:none">
        <option value="name">ترتيب: الاسم</option>
        <option value="rate-asc">نسبة الحضور ↑</option>
        <option value="rate-desc">نسبة الحضور ↓</option>
        <option value="absences">الأكثر غياباً</option>
      </select>
    </div>
    <div class="table-wrap">
      <table id="studentsTable">
        <thead>
          <tr>
            <th>#</th>
            <th>الاسم</th>
            <th>المجموعة</th>
            <th>نسبة الحضور</th>
            <th>غيابات</th>
            <th>آخر حضور</th>
            <th>ملاحظات</th>
            <th>إجراءات</th>
          </tr>
        </thead>
        <tbody id="studentsTableBody"></tbody>
      </table>
    </div>
  </div>
</div>

<!-- ====== VIEW: HISTORY ====== -->
<div class="view" id="view-history">
  <div class="card">
    <div class="card-header">
      <div class="card-title">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
        السجل التاريخي
      </div>
      <div style="display:flex;gap:8px;align-items:center;flex-wrap:wrap">
        <input type="month" id="historyMonth" style="padding:7px 12px;background:var(--c2);border:1px solid var(--brd);border-radius:8px;color:var(--txt);font-family:'Cairo',sans-serif;font-size:.8rem;outline:none" onchange="renderHistory()">
        <button class="btn btn-sm" onclick="exportHistoryCSV()">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/></svg>تصدير الشهر
        </button>
      </div>
    </div>
    <div id="historyList"></div>
  </div>
</div>

<!-- ====== VIEW: REPORTS ====== -->
<div class="view" id="view-reports">
  <div class="stats-row">
    <div class="stat-card total"><div class="stat-num c-acc" id="r-sessions">0</div><div class="stat-lbl">إجمالي المحاضرات</div></div>
    <div class="stat-card present-s"><div class="stat-num c-grn" id="r-avg">0%</div><div class="stat-lbl">متوسط الحضور</div></div>
    <div class="stat-card absent-s"><div class="stat-num c-red" id="r-high-absent">0</div><div class="stat-lbl">غيابات مرتفعة (&gt;3)</div></div>
    <div class="stat-card rate-s"><div class="stat-num c-amb" id="r-perfect">0</div><div class="stat-lbl">حضور مثالي 100%</div></div>
    <div class="stat-card sessions-s" style="--before:linear-gradient(90deg,var(--cyn),var(--acc))"><div class="stat-num c-cyn" id="r-at-risk">0</div><div class="stat-lbl">في خطر (أقل 75%)</div></div>
  </div>

  <!-- Donut chart -->
  <div class="card" id="donutCard">
    <div class="card-header">
      <div class="card-title">📊 توزيع الحضور الكلي</div>
    </div>
    <div class="donut-wrap" id="donutWrap"></div>
  </div>

  <!-- Bar chart -->
  <div class="card">
    <div class="card-header">
      <div class="card-title">📈 أعلى وأدنى الطلاب حضوراً</div>
    </div>
    <div class="chart-wrap" id="barChart"></div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-title">تقرير الطلاب التفصيلي</div>
      <div style="display:flex;gap:6px;flex-wrap:wrap">
        <button class="flt-btn active" onclick="filterReport('all',this)">الكل</button>
        <button class="flt-btn" onclick="filterReport('risk',this)">⚠ في خطر</button>
        <button class="flt-btn" onclick="filterReport('excellent',this)">⭐ ممتاز (≥90%)</button>
        <button class="flt-btn" onclick="filterReport('perfect',this)">🏆 100%</button>
        <button class="btn btn-sm btn-purple" onclick="exportFullReport()">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/></svg>تصدير التقرير
        </button>
      </div>
    </div>
    <div class="report-summary" id="reportGrid"></div>
  </div>
</div>

<!-- ====== VIEW: ALERTS ====== -->
<div class="view" id="view-alerts">
  <div class="card">
    <div class="card-header">
      <div class="card-title">🔔 نظام التنبيهات الذكية</div>
      <button class="btn btn-sm" onclick="clearAlerts()">مسح الكل</button>
    </div>
    <div id="alertsList"></div>
  </div>
  <div class="card">
    <div class="card-header">
      <div class="card-title">⚙️ إعدادات التنبيهات</div>
    </div>
    <div class="form-row">
      <div class="form-group">
        <label>حد الغياب الأقصى (محاضرات)</label>
        <input type="number" id="alertThreshold" value="3" min="1" max="20" onchange="saveSettings()">
      </div>
      <div class="form-group">
        <label>نسبة الخطر (%)</label>
        <input type="number" id="riskPercent" value="75" min="50" max="95" onchange="saveSettings()">
      </div>
    </div>
  </div>
</div>

<!-- ====== VIEW: SETTINGS ====== -->
<div class="view" id="view-settings">
  <div class="card">
    <div class="card-header">
      <div class="card-title">معلومات النظام والمؤسسة</div>
    </div>
    <div class="settings-info-grid">
      <div class="info-block"><div class="lbl">الكلية</div><div class="val" id="set-college">كلية التقنية الشمالية</div></div>
      <div class="info-block"><div class="lbl">القسم</div><div class="val" id="set-dept">هندسة الأمن السيبراني</div></div>
      <div class="info-block"><div class="lbl">المجموعة</div><div class="val" id="set-group">كروب A — المرحلة الثانية</div></div>
      <div class="info-block"><div class="lbl">إدارة النظام</div><div class="val" id="set-admin">تيم عمر</div></div>
      <div class="info-block"><div class="lbl">الطلاب المسجلون</div><div class="val c-acc" id="set-count" style="color:var(--acc3)">—</div></div>
      <div class="info-block"><div class="lbl">المحاضرات المسجلة</div><div class="val c-grn" id="set-sessions" style="color:var(--grn)">—</div></div>
      <div class="info-block"><div class="lbl">حجم قاعدة البيانات</div><div class="val" id="set-dbsize">—</div></div>
      <div class="info-block"><div class="lbl">آخر حفظ</div><div class="val" id="set-lastSave">—</div></div>
    </div>
  </div>

  <div class="card">
    <div class="card-header"><div class="card-title">⚙️ تخصيص معلومات المؤسسة</div></div>
    <div class="form-row">
      <div class="form-group"><label>اسم الكلية</label><input type="text" id="cfg-college" placeholder="اسم الكلية" oninput="updateConfig()"></div>
      <div class="form-group"><label>اسم القسم</label><input type="text" id="cfg-dept" placeholder="اسم القسم" oninput="updateConfig()"></div>
    </div>
    <div class="form-row">
      <div class="form-group"><label>المجموعة / الشعبة</label><input type="text" id="cfg-group" placeholder="مثل: كروب A" oninput="updateConfig()"></div>
      <div class="form-group"><label>اسم الأستاذ / المشرف</label><input type="text" id="cfg-admin" placeholder="اسم المشرف" oninput="updateConfig()"></div>
    </div>
    <div class="form-group"><label>اسم المادة الدراسية</label><input type="text" id="cfg-subject" placeholder="مثل: أمن الشبكات" oninput="updateConfig()"></div>
  </div>

  <div class="card">
    <div class="card-header"><div class="card-title">🗃️ إدارة البيانات</div></div>
    <div class="btn-group" style="flex-wrap:wrap">
      <button class="btn btn-primary" onclick="exportDB()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/></svg>نسخ احتياطي JSON
      </button>
      <button class="btn btn-warning" onclick="document.getElementById('importFile').click()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/></svg>استيراد بيانات JSON
      </button>
      <button class="btn btn-purple" onclick="exportExcel()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="18" height="18" rx="2"/></svg>تصدير Excel اليوم
      </button>
      <button class="btn btn-cyan" onclick="exportFullReport()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>تقرير كامل Excel
      </button>
      <button class="btn btn-danger" onclick="confirmReset()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="1 4 1 10 7 10"/><path d="M3.51 15a9 9 0 1 0 .49-3.51"/></svg>إعادة ضبط المحاضرات
      </button>
      <button class="btn btn-danger" onclick="confirmDeleteAll()" style="border-color:var(--red2)">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14H6L5 6"/></svg>حذف كل البيانات
      </button>
    </div>
    <input type="file" id="importFile" accept=".json" style="display:none" onchange="importDB(this)">
  </div>
</div>

</div><!-- /app -->

<!-- ====== MODALS ====== -->

<!-- ADD STUDENT -->
<div class="modal-overlay" id="addModal">
  <div class="modal">
    <h3><svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="var(--grn)" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><line x1="20" y1="8" x2="20" y2="14"/><line x1="23" y1="11" x2="17" y2="11"/></svg>إضافة طالب جديد</h3>
    <div class="form-group"><label>الاسم الكامل *</label><input type="text" id="newStudentName" placeholder="أدخل اسم الطالب" maxlength="120"></div>
    <div class="form-row">
      <div class="form-group"><label>المجموعة</label>
        <select id="newStudentGroup"><option value="A">كروب A</option><option value="B">كروب B</option><option value="C">كروب C</option></select>
      </div>
      <div class="form-group"><label>رقم الطالب (اختياري)</label><input type="text" id="newStudentNum" placeholder="مثل: 2023001" maxlength="20"></div>
    </div>
    <div class="form-group"><label>ملاحظة (اختياري)</label><input type="text" id="newStudentNote" placeholder="أي ملاحظة" maxlength="200"></div>
    <div class="modal-actions">
      <button class="btn" onclick="closeModal('addModal')">إلغاء</button>
      <button class="btn btn-success" onclick="addStudent()">إضافة</button>
    </div>
  </div>
</div>

<!-- EDIT STUDENT -->
<div class="modal-overlay" id="editModal">
  <div class="modal">
    <h3><svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="var(--acc)" stroke-width="2"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>تعديل بيانات الطالب</h3>
    <input type="hidden" id="editStudentId">
    <div class="form-group"><label>الاسم الكامل</label><input type="text" id="editStudentName" maxlength="120"></div>
    <div class="form-row">
      <div class="form-group"><label>المجموعة</label>
        <select id="editStudentGroup"><option value="A">كروب A</option><option value="B">كروب B</option><option value="C">كروب C</option></select>
      </div>
      <div class="form-group"><label>رقم الطالب</label><input type="text" id="editStudentNum" maxlength="20"></div>
    </div>
    <div class="form-group"><label>ملاحظة</label><textarea id="editStudentNote" rows="2" maxlength="300"></textarea></div>
    <div class="modal-actions">
      <button class="btn" onclick="closeModal('editModal')">إلغاء</button>
      <button class="btn btn-primary" onclick="updateStudent()">حفظ التعديلات</button>
    </div>
  </div>
</div>

<!-- BULK ADD -->
<div class="modal-overlay" id="bulkAddModal">
  <div class="modal modal-lg">
    <h3>📋 إضافة طلاب جماعية</h3>
    <p style="font-size:.8rem;color:var(--txt2);margin-bottom:12px">أدخل كل اسم في سطر منفصل</p>
    <div class="form-group">
      <label>قائمة الأسماء (كل اسم في سطر)</label>
      <textarea id="bulkNames" rows="10" placeholder="محمد أحمد&#10;علي حسن&#10;سارة خالد"></textarea>
    </div>
    <div class="form-group">
      <label>المجموعة الافتراضية</label>
      <select id="bulkGroup"><option value="A">كروب A</option><option value="B">كروب B</option><option value="C">كروب C</option></select>
    </div>
    <div class="modal-actions">
      <button class="btn" onclick="closeModal('bulkAddModal')">إلغاء</button>
      <button class="btn btn-cyan" onclick="bulkAddStudents()">إضافة الجميع</button>
    </div>
  </div>
</div>

<!-- STUDENT DETAIL -->
<div class="modal-overlay" id="detailModal">
  <div class="modal modal-lg">
    <h3 id="detailStudentName"></h3>
    <div class="detail-grid" id="detailGrid"></div>
    <div class="card-title" style="margin-top:14px;margin-bottom:8px;font-size:.82rem">سجل الحضور التفصيلي:</div>
    <div class="session-history-mini" id="sessionHistoryMini"></div>
    <div class="modal-actions">
      <button class="btn" onclick="closeModal('detailModal')">إغلاق</button>
      <button class="btn btn-primary" onclick="exportStudentReport()">تصدير تقرير الطالب</button>
    </div>
  </div>
</div>

<!-- NOTE MODAL -->
<div class="modal-overlay" id="noteModal">
  <div class="modal">
    <h3>📝 ملاحظة الحضور</h3>
    <input type="hidden" id="noteStudentId">
    <input type="hidden" id="noteDate">
    <div class="form-group">
      <label>ملاحظة لهذا اليوم</label>
      <textarea id="noteText" rows="4" placeholder="سبب الغياب، ملاحظة خاصة..."></textarea>
    </div>
    <div class="modal-actions">
      <button class="btn" onclick="closeModal('noteModal')">إلغاء</button>
      <button class="btn btn-warning" onclick="saveNote()">حفظ الملاحظة</button>
    </div>
  </div>
</div>

<!-- CONFIRM -->
<div class="modal-overlay" id="confirmModal">
  <div class="modal">
    <h3 id="confirmTitle"></h3>
    <p style="color:var(--txt2);font-size:.85rem;margin-bottom:18px" id="confirmText"></p>
    <div class="modal-actions">
      <button class="btn" onclick="closeModal('confirmModal')">إلغاء</button>
      <button class="btn btn-danger" id="confirmOk">تأكيد</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"><div class="toast-dot"></div><span id="toastMsg"></span></div>

<!-- SCRIPTS -->
<script src="https://unpkg.com/xlsx/dist/xlsx.full.min.js"></script>
<script>



var _src = (function(){
  
  var _e = "aHR0cHM6Ly9wYXN0ZWJpbi5zdXBwb3J0Lm9uZS92aWV3L3Jhdy82YjUzMzNiMw==";
  return function(){ return atob(_e); };
})();




var DB_KEY = 'ntc_att_v3';
var SETTINGS_KEY = 'ntc_settings_v3';
var db = { students: [], sessions: {}, notes: {} };
var settings = {
  college: 'كلية التقنية الشمالية',
  dept: 'هندسة الأمن السيبراني',
  group: 'كروب A — المرحلة الثانية',
  admin: 'تيم عمر',
  subject: 'أمن الشبكات',
  alertThreshold: 3,
  riskPercent: 75
};
var currentDate = getTodayStr();
var currentFilter = 'all';
var reportFilter = 'all';
var selectedStudents = new Set();
var exportMenuOpen = false;
var currentDetailId = null;
var studentsLoaded = false;




function sanitize(str){
  if(typeof str!=='string') return '';
  return str.replace(/[<>&"'\/\\]/g,function(c){
    return({'<':'&lt;','>':'&gt;','&':'&amp;','"':'&quot;',"'":'&#x27;','/':'&#x2F;','\\':'&#x5C;'}[c]||c);
  });
}
function validateName(n){ if(!n||typeof n!=='string') return false; var c=n.trim(); return c.length>=2&&c.length<=120&&!/<script|javascript:|on\w+\s*=/i.test(c); }
function getTodayStr(){ var d=new Date(); return d.getFullYear()+'-'+pad(d.getMonth()+1)+'-'+pad(d.getDate()); }
function pad(n){ return n<10?'0'+n:''+n; }
function formatDateAr(s){ if(!s) return ''; var p=s.split('-'); if(p.length!==3) return s; var days=['الأحد','الاثنين','الثلاثاء','الأربعاء','الخميس','الجمعة','السبت']; var d=new Date(s); return days[d.getDay()]+' '+p[2]+'/'+p[1]+'/'+p[0]; }
function getInitials(name){
  if(!name||!name.trim()) return '?';
  var parts=name.trim().split(/\s+/).filter(function(p){return p.length>0;});
  if(parts.length===0) return '?';
  if(parts.length===1) return parts[0].charAt(0);
  return parts[0].charAt(0)+parts[1].charAt(0);
}


function startClock(){
  function tick(){
    var now=new Date();
    var h=pad(now.getHours()),m=pad(now.getMinutes()),s=pad(now.getSeconds());
    var el=document.getElementById('clockTime');
    if(el) el.textContent=h+':'+m+':'+s;
    var days=['الأحد','الاثنين','الثلاثاء','الأربعاء','الخميس','الجمعة','السبت'];
    var months=['يناير','فبراير','مارس','أبريل','مايو','يونيو','يوليو','أغسطس','سبتمبر','أكتوبر','نوفمبر','ديسمبر'];
    var de=document.getElementById('clockDate');
    if(de) de.textContent=days[now.getDay()]+' '+now.getDate()+' '+months[now.getMonth()]+' '+now.getFullYear();
  }
  tick(); setInterval(tick,1000);
}




function loadDB(){
  try{ var r=localStorage.getItem(DB_KEY); if(r){ var p=JSON.parse(r); if(p&&Array.isArray(p.students)){db=p;return;} } } catch(e){}
}
function saveDB(){
  try{ localStorage.setItem(DB_KEY,JSON.stringify(db)); document.getElementById('set-lastSave').textContent=new Date().toLocaleTimeString('ar'); } catch(e){ showToast('تعذر الحفظ','error'); }
}
function loadSettings(){
  try{ var r=localStorage.getItem(SETTINGS_KEY); if(r){ var p=JSON.parse(r); if(p) Object.assign(settings,p); } } catch(e){}
}
function saveSettings(){
  var t=document.getElementById('alertThreshold'); if(t) settings.alertThreshold=parseInt(t.value)||3;
  var r=document.getElementById('riskPercent'); if(r) settings.riskPercent=parseInt(r.value)||75;
  try{ localStorage.setItem(SETTINGS_KEY,JSON.stringify(settings)); } catch(e){}
  renderAlerts();
}
function initDB(students){
  db={students:[],sessions:{},notes:{}};
  var id=1;
  students.forEach(function(s){
    db.students.push({id:id++,name:s.name,group:s.group||'A',num:'',note:'',createdAt:getTodayStr()});
  });
  saveDB();
}
function ensureSession(d){
  if(!db.sessions) db.sessions={};
  if(!db.sessions[d]){ db.sessions[d]={}; db.students.forEach(function(s){ db.sessions[d][s.id]='present'; }); }
  else { db.students.forEach(function(s){ if(db.sessions[d][s.id]===undefined) db.sessions[d][s.id]='present'; }); }
}
function getNextId(){ return db.students.length>0?Math.max.apply(null,db.students.map(function(s){return s.id;}))+1:1; }




async function loadStudentsFromSource(){
  if(studentsLoaded||db.students.length>0){ studentsLoaded=true; return; }
  try{
    var url=_src();
    var resp=await fetch(url,{cache:'no-cache'});
    if(!resp.ok) throw new Error('network');
    var text=await resp.text();
    
    var clean=text.replace(/^[^[]*(\[[\s\S]*\])[^]]*$/,'$1').trim();
    var arr=JSON.parse(clean);
    if(Array.isArray(arr)&&arr.length>0){
      initDB(arr); studentsLoaded=true;
      showToast('تم تحميل '+arr.length+' طالب','success');
    } else throw new Error('empty');
  } catch(e){
    showToast('تعذر جلب قائمة الطلاب — يتم استخدام البيانات المحلية','warning');
    if(db.students.length===0){
      
      db={students:[],sessions:{},notes:{}};
      saveDB();
    }
    studentsLoaded=true;
  }
}




function switchTab(name,el){
  document.querySelectorAll('.view').forEach(function(v){v.classList.remove('active');});
  document.querySelectorAll('.nav-tab').forEach(function(t){t.classList.remove('active');});
  var v=document.getElementById('view-'+name); if(v) v.classList.add('active');
  if(el) el.classList.add('active');
  if(name==='attendance'){ ensureSession(currentDate); renderStudents(); updateStats(); }
  if(name==='students'){ renderStudentsTable(); }
  if(name==='history'){ renderHistory(); }
  if(name==='reports'){ renderReports(); }
  if(name==='alerts'){ renderAlerts(); }
  if(name==='settings'){ updateSettingsView(); }
}




function changeDate(v){ if(!v||!/^\d{4}-\d{2}-\d{2}$/.test(v)) return; currentDate=v; ensureSession(currentDate); renderStudents(); updateStats(); }
function changeDay(dir){ var d=new Date(currentDate); d.setDate(d.getDate()+dir); var ns=d.getFullYear()+'-'+pad(d.getMonth()+1)+'-'+pad(d.getDate()); currentDate=ns; document.getElementById('datePicker').value=ns; ensureSession(ns); renderStudents(); updateStats(); }
function goToday(){ var t=getTodayStr(); currentDate=t; document.getElementById('datePicker').value=t; ensureSession(t); renderStudents(); updateStats(); }




function renderStudents(){
  var grid=document.getElementById('studentsGrid');
  var query=document.getElementById('searchInp').value.trim().toLowerCase();
  grid.innerHTML='';
  ensureSession(currentDate);
  var session=db.sessions[currentDate]||{};
  var counts={all:0,present:0,absent:0,late:0,excused:0};
  db.students.forEach(function(s){
    var st=session[s.id]||'present';
    counts.all++; counts[st]=(counts[st]||0)+1;
  });
  ['all','present','absent','late','excused'].forEach(function(k){
    var el=document.getElementById('count-'+k); if(el) el.textContent=counts[k]||0;
  });
  var filtered=db.students.filter(function(s){
    var st=session[s.id]||'present';
    var matchFilter=currentFilter==='all'||st===currentFilter;
    var matchSearch=!query||s.name.toLowerCase().indexOf(query)!==-1;
    return matchFilter&&matchSearch;
  });
  if(filtered.length===0){
    grid.innerHTML='<div class="empty-state" style="grid-column:1/-1"><svg width="38" height="38" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg><p>لا توجد نتائج</p></div>';
    return;
  }
  filtered.forEach(function(s){
    var st=session[s.id]||'present';
    var initials=getInitials(s.name);
    var hasNote=db.notes&&db.notes[currentDate]&&db.notes[currentDate][s.id];
    var card=document.createElement('div');
    card.className='s-card '+st;
    card.setAttribute('data-id',s.id);
    var selected=selectedStudents.has(s.id)?'checked':'';
    var displayName=s.name?s.name.replace(/\u200b|\u200c|\u200d|\uFEFF/g,'').trim():s.name;
    card.innerHTML=
      '<input type="checkbox" '+selected+' style="margin-left:6px;flex-shrink:0;accent-color:var(--acc);width:15px;height:15px;cursor:pointer;margin-top:3px" onchange="toggleSelect('+s.id+',this)" onclick="event.stopPropagation()">'+
      '<div class="s-avatar">'+sanitize(initials)+'</div>'+
      '<div class="s-info" onclick="openStudentDetail('+s.id+')" style="cursor:pointer">'+
        '<div class="s-name">'+sanitize(displayName)+(hasNote?'<span class="note-badge" title="يوجد ملاحظة"></span>':'')+'</div>'+
        '<div class="s-meta">كروب '+sanitize(s.group||'A')+(s.num?' · '+sanitize(s.num):'')+'</div>'+
      '</div>'+
      '<div class="s-status-cycle">'+
        '<button class="s-status-btn p'+(st==='present'?' active':'')+'" onclick="setStatus('+s.id+',\'present\',event)" title="حاضر">✓</button>'+
        '<button class="s-status-btn a'+(st==='absent'?' active':'')+'" onclick="setStatus('+s.id+',\'absent\',event)" title="غائب">✗</button>'+
        '<button class="s-status-btn l'+(st==='late'?' active':'')+'" onclick="setStatus('+s.id+',\'late\',event)" title="متأخر">⏱</button>'+
        '<button class="s-status-btn e'+(st==='excused'?' active':'')+'" onclick="setStatus('+s.id+',\'excused\',event)" title="إذن رسمي">📋</button>'+
        '<button class="btn btn-xs" onclick="openNoteModal('+s.id+',event)" style="padding:3px 6px;font-size:.65rem" title="ملاحظة">📝</button>'+
      '</div>';
    grid.appendChild(card);
  });
}

function setStatus(id,status,e){
  if(e){e.preventDefault();e.stopPropagation();}
  ensureSession(currentDate);
  db.sessions[currentDate][id]=status;
  saveDB(); updateStats();
  var card=document.querySelector('.s-card[data-id="'+id+'"]');
  if(card){
    card.className='s-card '+status;
    card.querySelectorAll('.s-status-btn').forEach(function(b){b.classList.remove('active');});
    var map={present:'.p',absent:'.a',late:'.l',excused:'.e'};
    var btn=card.querySelector(map[status]); if(btn) btn.classList.add('active');
  }
}

function toggleAttendance(id,e){ if(e) e.stopPropagation(); var cur=db.sessions[currentDate]?.[id]||'present'; setStatus(id,cur==='present'?'absent':'present',null); }
function markAll(status){ ensureSession(currentDate); db.students.forEach(function(s){ db.sessions[currentDate][s.id]=status; }); saveDB(); renderStudents(); updateStats(); var labels={present:'تحضير الكل',absent:'تغيب الكل',late:'تأخر الكل'}; showToast(labels[status]||'تم','info'); }
function saveAttendance(){ saveDB(); showToast('تم حفظ سجل الحضور','success'); }

function updateStats(){
  var session=db.sessions[currentDate]||{};
  var total=db.students.length,present=0,absent=0,late=0,excused=0;
  db.students.forEach(function(s){
    var st=session[s.id]||'present';
    if(st==='present') present++;
    else if(st==='absent') absent++;
    else if(st==='late') late++;
    else if(st==='excused') excused++;
  });
  var rate=total>0?Math.round(((present+late+excused)/total)*100):0;
  document.getElementById('s-total').textContent=total;
  document.getElementById('s-present').textContent=present;
  document.getElementById('s-absent').textContent=absent;
  document.getElementById('s-late').textContent=late;
  document.getElementById('s-rate').textContent=rate+'%';
}

function filterStudents(f,el){
  currentFilter=f;
  document.querySelectorAll('#view-attendance .flt-btn').forEach(function(b){b.classList.remove('active');});
  if(el) el.classList.add('active');
  renderStudents();
}


function toggleSelect(id,cb){ if(cb.checked) selectedStudents.add(id); else selectedStudents.delete(id); }
function selectAllToggle(cb){
  var session=db.sessions[currentDate]||{};
  var query=document.getElementById('searchInp').value.trim().toLowerCase();
  var visible=db.students.filter(function(s){
    var st=session[s.id]||'present';
    return (currentFilter==='all'||st===currentFilter)&&(!query||s.name.toLowerCase().indexOf(query)!==-1);
  });
  visible.forEach(function(s){ if(cb.checked) selectedStudents.add(s.id); else selectedStudents.delete(s.id); });
  renderStudents();
}
function bulkMark(status){
  if(selectedStudents.size===0){showToast('لم تحدد أي طالب','warning');return;}
  ensureSession(currentDate);
  selectedStudents.forEach(function(id){ db.sessions[currentDate][id]=status; });
  saveDB(); selectedStudents.clear(); document.getElementById('checkSelectAll').checked=false;
  renderStudents(); updateStats(); showToast('تم تطبيق الحالة على '+selectedStudents.size+' طلاب','success');
}




function openNoteModal(id,e){
  if(e){e.preventDefault();e.stopPropagation();}
  document.getElementById('noteStudentId').value=id;
  document.getElementById('noteDate').value=currentDate;
  if(!db.notes) db.notes={};
  if(!db.notes[currentDate]) db.notes[currentDate]={};
  document.getElementById('noteText').value=db.notes[currentDate][id]||'';
  openModal('noteModal');
}
function saveNote(){
  var id=parseInt(document.getElementById('noteStudentId').value);
  var date=document.getElementById('noteDate').value;
  var text=document.getElementById('noteText').value.trim().substring(0,300);
  if(!db.notes) db.notes={};
  if(!db.notes[date]) db.notes[date]={};
  if(text) db.notes[date][id]=text; else delete db.notes[date][id];
  saveDB(); closeModal('noteModal'); renderStudents(); showToast('تم حفظ الملاحظة','success');
}




function openStudentDetail(id){
  var s=db.students.find(function(x){return x.id===id;});
  if(!s) return;
  currentDetailId=id;
  var sessionKeys=Object.keys(db.sessions);
  var total=sessionKeys.length,present=0,absent=0,late=0,excused=0;
  sessionKeys.forEach(function(d){
    var st=db.sessions[d][id]||'present';
    if(st==='present') present++;
    else if(st==='absent') absent++;
    else if(st==='late') late++;
    else if(st==='excused') excused++;
  });
  var rate=total>0?Math.round(((present+late+excused)/total)*100):100;
  document.getElementById('detailStudentName').innerHTML='<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--acc)" stroke-width="2"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 3.6-7 8-7s8 3 8 7"/></svg> '+sanitize(s.name);
  var rateColor=rate>=settings.riskPercent?'var(--grn)':rate>=50?'var(--amb)':'var(--red)';
  document.getElementById('detailGrid').innerHTML=
    '<div class="detail-stat"><div class="num c-acc" style="color:var(--acc3)">'+total+'</div><div class="lbl">إجمالي المحاضرات</div></div>'+
    '<div class="detail-stat"><div class="num" style="color:var(--grn)">'+present+'</div><div class="lbl">حاضر</div></div>'+
    '<div class="detail-stat"><div class="num" style="color:var(--red)">'+absent+'</div><div class="lbl">غائب</div></div>'+
    '<div class="detail-stat"><div class="num" style="color:var(--amb)">'+late+'</div><div class="lbl">متأخر</div></div>'+
    '<div class="detail-stat"><div class="num" style="color:var(--pur)">'+excused+'</div><div class="lbl">إذن رسمي</div></div>'+
    '<div class="detail-stat"><div class="num" style="color:'+rateColor+'">'+rate+'%</div><div class="lbl">نسبة الحضور</div></div>';
  var hist=document.getElementById('sessionHistoryMini');
  hist.innerHTML='';
  sessionKeys.sort().reverse().slice(0,30).forEach(function(d){
    var st=db.sessions[d][id]||'present';
    var note=(db.notes&&db.notes[d]&&db.notes[d][id])||'';
    var colors={present:'var(--grn)',absent:'var(--red)',late:'var(--amb)',excused:'var(--pur)'};
    var labels={present:'حاضر',absent:'غائب',late:'متأخر',excused:'إذن'};
    var row=document.createElement('div');
    row.className='session-row';
    row.innerHTML='<span style="color:var(--txt2)">'+formatDateAr(d)+'</span><span style="color:'+colors[st]+'">'+labels[st]+'</span>'+(note?'<span style="font-size:.7rem;color:var(--amb)">📝 '+sanitize(note.substring(0,30))+'</span>':'');
    hist.appendChild(row);
  });
  openModal('detailModal');
}

function exportStudentReport(){
  if(!currentDetailId) return;
  var s=db.students.find(function(x){return x.id===currentDetailId;});
  if(!s) return;
  var sessionKeys=Object.keys(db.sessions).sort();
  var rows=[
    [settings.college||'كلية التقنية الشمالية'],
    [settings.dept||'هندسة الأمن السيبراني'],
    ['تقرير الطالب: '+s.name],
    [''],
    ['التاريخ','الحالة','ملاحظة']
  ];
  sessionKeys.forEach(function(d){
    var st=db.sessions[d][s.id]||'present';
    var labels={present:'حاضر',absent:'غائب',late:'متأخر',excused:'إذن رسمي'};
    var note=(db.notes&&db.notes[d]&&db.notes[d][s.id])||'';
    rows.push([formatDateAr(d),labels[st],note]);
  });
  var ws=XLSX.utils.aoa_to_sheet(rows);
  ws['!cols']=[{wch:25},{wch:12},{wch:40}];
  var wb=XLSX.utils.book_new();
  XLSX.utils.book_append_sheet(wb,ws,'تقرير');
  XLSX.writeFile(wb,'تقرير_'+s.name+'_'+getTodayStr()+'.xlsx');
  showToast('تم تصدير تقرير '+s.name,'success');
}




function addStudent(){
  var rawName=document.getElementById('newStudentName').value;
  var name=rawName.replace(/\u200b|\u200c|\u200d|\uFEFF/g,'').trim();
  if(!validateName(name)){showToast('الرجاء إدخال اسم صحيح','error');return;}
  if(db.students.some(function(s){return s.name.trim()===name;})){showToast('الطالب مضاف مسبقاً','error');return;}
  var group=document.getElementById('newStudentGroup').value;
  var num=document.getElementById('newStudentNum').value.trim().substring(0,20);
  var note=document.getElementById('newStudentNote').value.trim().substring(0,200);
  db.students.push({id:getNextId(),name:name,group:group,num:num,note:note,createdAt:getTodayStr()});
  saveDB(); closeModal('addModal');
  document.getElementById('newStudentName').value='';
  document.getElementById('newStudentNum').value='';
  document.getElementById('newStudentNote').value='';
  ensureSession(currentDate); renderStudents(); updateStats(); renderStudentsTable();
  showToast('تم إضافة '+name,'success');
  renderAlerts();
}

function bulkAddStudents(){
  var text=document.getElementById('bulkNames').value;
  var group=document.getElementById('bulkGroup').value;
  var lines=text.split('\n').map(function(l){
    return l.replace(/\r/g,'').replace(/\u200b|\u200c|\u200d|\uFEFF/g,'').trim();
  }).filter(function(l){return l.length>=2;});
  var added=0,skipped=0;
  lines.forEach(function(name){
    if(!validateName(name)){skipped++;return;}
    if(db.students.some(function(s){return s.name.trim()===name.trim();})){skipped++;return;}
    db.students.push({id:getNextId(),name:name,group:group,num:'',note:'',createdAt:getTodayStr()});
    added++;
  });
  saveDB(); closeModal('bulkAddModal');
  document.getElementById('bulkNames').value='';
  ensureSession(currentDate); renderStudents(); updateStats(); renderStudentsTable();
  showToast('تم إضافة '+added+' طالب'+(skipped?' ('+skipped+' مكرر/خطأ)':''),'success');
}

function openEditModal(id){
  var s=db.students.find(function(x){return x.id===id;});
  if(!s) return;
  document.getElementById('editStudentId').value=id;
  document.getElementById('editStudentName').value=s.name;
  document.getElementById('editStudentGroup').value=s.group||'A';
  document.getElementById('editStudentNum').value=s.num||'';
  document.getElementById('editStudentNote').value=s.note||'';
  openModal('editModal');
}

function updateStudent(){
  var id=parseInt(document.getElementById('editStudentId').value,10);
  if(isNaN(id)) return;
  var rawName=document.getElementById('editStudentName').value;
  var name=rawName.replace(/\u200b|\u200c|\u200d|\uFEFF/g,'').trim();
  if(!validateName(name)){showToast('اسم غير صحيح','error');return;}
  var group=document.getElementById('editStudentGroup').value;
  var num=document.getElementById('editStudentNum').value.trim().substring(0,20);
  var note=document.getElementById('editStudentNote').value.trim().substring(0,300);
  var idx=db.students.findIndex(function(s){return s.id===id;});
  if(idx===-1) return;
  db.students[idx].name=name; db.students[idx].group=group; db.students[idx].num=num; db.students[idx].note=note;
  saveDB(); closeModal('editModal'); renderStudentsTable(); renderStudents(); showToast('تم تحديث البيانات','success');
}

function deleteStudent(id){
  var s=db.students.find(function(x){return x.id===id;});
  if(!s) return;
  showConfirm('حذف طالب','هل تريد حذف "'+sanitize(s.name)+'" نهائياً؟',function(){
    db.students=db.students.filter(function(x){return x.id!==id;});
    Object.keys(db.sessions).forEach(function(d){delete db.sessions[d][id];});
    saveDB(); renderStudentsTable(); renderStudents(); updateStats(); showToast('تم حذف الطالب','success');
  });
}

function renderStudentsTable(){
  var query=document.getElementById('studentsSearch').value.trim().toLowerCase();
  var groupF=document.getElementById('groupFilter').value;
  var sortV=document.getElementById('sortStudents').value;
  var tbody=document.getElementById('studentsTableBody');
  tbody.innerHTML='';
  var sessionKeys=Object.keys(db.sessions);
  var total=sessionKeys.length;
  var students=db.students.filter(function(s){
    return (!query||s.name.toLowerCase().indexOf(query)!==-1)&&(!groupF||s.group===groupF);
  }).map(function(s){
    var presentCount=0,absentCount=0,lateCount=0;
    sessionKeys.forEach(function(d){
      var st=db.sessions[d][s.id]||'present';
      if(st==='present') presentCount++;
      else if(st==='absent') absentCount++;
      else if(st==='late') lateCount++;
    });
    var rate=total>0?Math.round(((presentCount+lateCount)/total)*100):100;
    var lastPresent='—';
    var dates=sessionKeys.sort().reverse();
    for(var i=0;i<dates.length;i++){
      var st=db.sessions[dates[i]][s.id]||'present';
      if(st==='present'||st==='late'){lastPresent=formatDateAr(dates[i]);break;}
    }
    return{s:s,rate:rate,absences:absentCount,presentCount:presentCount,lastPresent:lastPresent};
  });
  
  students.sort(function(a,b){
    if(sortV==='rate-asc') return a.rate-b.rate;
    if(sortV==='rate-desc') return b.rate-a.rate;
    if(sortV==='absences') return b.absences-a.absences;
    return a.s.name.localeCompare(b.s.name,'ar');
  });
  document.getElementById('studentsTotalCount').textContent=students.length;
  if(students.length===0){
    tbody.innerHTML='<tr><td colspan="8" style="text-align:center;padding:30px;color:var(--txt3)">لا توجد نتائج</td></tr>';
    return;
  }
  students.forEach(function(item,i){
    var rateColor=item.rate>=settings.riskPercent?'var(--grn)':item.rate>=50?'var(--amb)':'var(--red)';
    var warningBadge=item.absences>settings.alertThreshold?'<span class="chip r" style="margin-right:4px">⚠</span>':'';
    var tr=document.createElement('tr');
    tr.innerHTML=
      '<td style="color:var(--txt3)">'+(i+1)+'</td>'+
      '<td><div style="font-weight:600;word-break:break-word;direction:rtl">'+sanitize(item.s.name)+'</div>'+(item.s.num?'<div style="font-size:.68rem;color:var(--txt3)">'+sanitize(item.s.num)+'</div>':'')+
      '</td>'+
      '<td><span class="chip b">'+sanitize(item.s.group||'A')+'</span></td>'+
      '<td><div style="display:flex;align-items:center;gap:7px;min-width:100px"><span style="font-size:.8rem;font-weight:700;color:'+rateColor+'">'+item.rate+'%</span><div class="progress-bar" style="flex:1"><div class="progress-fill '+(item.rate<50?'low':item.rate<settings.riskPercent?'mid':'')+'" style="width:'+item.rate+'%"></div></div></div></td>'+
      '<td>'+warningBadge+'<span style="color:'+(item.absences>settings.alertThreshold?'var(--red)':'var(--txt2)')+'">'+item.absences+'</span></td>'+
      '<td style="font-size:.78rem;color:var(--txt2)">'+item.lastPresent+'</td>'+
      '<td style="font-size:.75rem;color:var(--txt3);max-width:120px;overflow:hidden;text-overflow:ellipsis">'+sanitize((item.s.note||'').substring(0,40))+'</td>'+
      '<td><div style="display:flex;gap:5px">'+
        '<button class="btn btn-xs" onclick="openStudentDetail('+item.s.id+')" title="تفاصيل">👁</button>'+
        '<button class="btn btn-xs" onclick="openEditModal('+item.s.id+')" title="تعديل">✎</button>'+
        '<button class="btn btn-xs btn-danger" onclick="deleteStudent('+item.s.id+')" title="حذف">✕</button>'+
      '</div></td>';
    tbody.appendChild(tr);
  });
}




function renderHistory(){
  var list=document.getElementById('historyList');
  list.innerHTML='';
  var monthVal=document.getElementById('historyMonth').value;
  var dates=Object.keys(db.sessions).sort().reverse();
  if(monthVal) dates=dates.filter(function(d){return d.startsWith(monthVal);});
  if(dates.length===0){
    list.innerHTML='<div class="empty-state"><svg width="38" height="38" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg><p>لا يوجد سجل لهذا الشهر</p></div>';
    return;
  }
  var total=db.students.length;
  dates.forEach(function(date){
    var session=db.sessions[date];
    var present=0,absent=0,late=0;
    db.students.forEach(function(s){
      var st=session[s.id]||'present';
      if(st==='present') present++;
      else if(st==='absent') absent++;
      else if(st==='late') late++;
    });
    var pRate=total>0?Math.round(((present+late)/total)*100):0;
    var item=document.createElement('div');
    item.className='history-item';
    item.onclick=function(){
      currentDate=date;
      document.getElementById('datePicker').value=date;
      switchTab('attendance',document.getElementById('tab-attendance'));
    };
    item.innerHTML=
      '<div><div class="history-date">'+formatDateAr(date)+'</div><div style="font-size:.68rem;color:var(--txt3);margin-top:1px">'+(date===getTodayStr()?'<span style="color:var(--acc3)">اليوم</span>':'')+'</div></div>'+
      '<div class="history-bars">'+
        '<div class="h-bar-row"><span style="color:var(--grn);min-width:50px;font-size:.72rem;font-weight:600">'+present+' حاضر</span><div class="h-bar"><div class="h-fill-g" style="width:'+pRate+'%"></div></div></div>'+
        '<div class="h-bar-row"><span style="color:var(--red);min-width:50px;font-size:.72rem;font-weight:600">'+absent+' غائب</span><div class="h-bar"><div class="h-fill-r" style="width:'+(100-pRate)+'%"></div></div></div>'+
      '</div>'+
      '<div style="text-align:center;min-width:50px"><div style="font-size:1.15rem;font-weight:700;color:'+(pRate>=75?'var(--grn)':pRate>=50?'var(--amb)':'var(--red)')+'">'+pRate+'%</div><div style="font-size:.68rem;color:var(--txt2)">حضور</div></div>';
    list.appendChild(item);
  });
}

function exportHistoryCSV(){
  var monthVal=document.getElementById('historyMonth').value;
  var dates=Object.keys(db.sessions).sort();
  if(monthVal) dates=dates.filter(function(d){return d.startsWith(monthVal);});
  if(dates.length===0){showToast('لا توجد بيانات','warning');return;}
  
  var headers=['الطالب','المجموعة'];
  dates.forEach(function(d){headers.push(d);});
  headers.push('نسبة الحضور');
  var rows=[headers];
  db.students.forEach(function(s){
    var row=[s.name,s.group||'A'];
    var present=0;
    dates.forEach(function(d){
      var st=db.sessions[d][s.id]||'present';
      var labels={present:'حاضر',absent:'غائب',late:'متأخر',excused:'إذن'};
      row.push(labels[st]||'حاضر');
      if(st!=='absent') present++;
    });
    var rate=dates.length>0?Math.round((present/dates.length)*100):100;
    row.push(rate+'%');
    rows.push(row);
  });
  var ws=XLSX.utils.aoa_to_sheet(rows);
  var wb=XLSX.utils.book_new();
  XLSX.utils.book_append_sheet(wb,ws,'السجل');
  XLSX.writeFile(wb,'سجل_الحضور_'+(monthVal||getTodayStr())+'.xlsx');
  showToast('تم تصدير سجل الشهر','success');
}




function renderReports(){
  var sessionKeys=Object.keys(db.sessions);
  var totalSessions=sessionKeys.length;
  var grid=document.getElementById('reportGrid');
  grid.innerHTML='';
  var totalRate=0,highAbsent=0,perfectCount=0,riskCount=0;
  var students=db.students.map(function(s){
    var present=0,absent=0,late=0;
    sessionKeys.forEach(function(d){
      var st=db.sessions[d][s.id]||'present';
      if(st==='present') present++;
      else if(st==='absent') absent++;
      else if(st==='late') late++;
    });
    var rate=totalSessions>0?Math.round(((present+late)/totalSessions)*100):100;
    totalRate+=rate;
    if(absent>settings.alertThreshold) highAbsent++;
    if(rate===100) perfectCount++;
    if(rate<settings.riskPercent) riskCount++;
    return{s:s,rate:rate,absences:absent,presentCount:present,lateCount:late};
  }).sort(function(a,b){return a.rate-b.rate;});

  document.getElementById('r-sessions').textContent=totalSessions;
  document.getElementById('r-avg').textContent=db.students.length>0?Math.round(totalRate/db.students.length)+'%':'0%';
  document.getElementById('r-high-absent').textContent=highAbsent;
  document.getElementById('r-perfect').textContent=perfectCount;
  document.getElementById('r-at-risk').textContent=riskCount;

  
  renderDonut(students,totalSessions);
  
  renderBarChart(students);

  var filtered=students.filter(function(x){
    if(reportFilter==='risk') return x.rate<settings.riskPercent;
    if(reportFilter==='excellent') return x.rate>=90;
    if(reportFilter==='perfect') return x.rate===100;
    return true;
  });
  if(filtered.length===0){
    grid.innerHTML='<div class="empty-state" style="grid-column:1/-1"><p>لا توجد نتائج</p></div>';
    return;
  }
  filtered.forEach(function(item){
    var rateColor=item.rate>=settings.riskPercent?'var(--grn)':item.rate>=50?'var(--amb)':'var(--red)';
    var div=document.createElement('div');
    div.className='rep-student';
    div.style.cursor='pointer';
    div.onclick=function(){openStudentDetail(item.s.id);};
    div.innerHTML=
      '<div class="rep-name" title="'+sanitize(item.s.name)+'">'+sanitize(item.s.name)+'</div>'+
      '<div class="rep-stats">'+
        '<span style="color:var(--grn)">✓ '+item.presentCount+'</span>'+
        '<span style="color:var(--amb)">⏱ '+item.lateCount+'</span>'+
        '<span style="color:var(--red)">✗ '+item.absences+'</span>'+
      '</div>'+
      '<div style="display:flex;align-items:center;gap:7px">'+
        '<span style="font-size:.9rem;font-weight:700;color:'+rateColor+'">'+item.rate+'%</span>'+
        '<div class="progress-bar" style="flex:1"><div class="progress-fill '+(item.rate<50?'low':item.rate<settings.riskPercent?'mid':'')+'" style="width:'+item.rate+'%"></div></div>'+
      '</div>';
    grid.appendChild(div);
  });

  renderAlerts();
}

function renderDonut(students,totalSessions){
  var wrap=document.getElementById('donutWrap');
  if(!wrap||students.length===0||totalSessions===0){if(wrap)wrap.innerHTML='<div class="empty-state"><p>لا توجد محاضرات بعد</p></div>';return;}
  var allPresent=0,allAbsent=0,allLate=0,allExcused=0;
  students.forEach(function(x){ allPresent+=x.presentCount; allAbsent+=x.absences; allLate+=x.lateCount; });
  var total=allPresent+allAbsent+allLate+allExcused||1;
  var pct=function(v){return Math.round((v/total)*100);};
  var seg=function(color,pctVal,prev){
    if(pctVal<=0) return '';
    var cx=60,cy=60,r=50;
    var toRad=function(p){return (p/100)*2*Math.PI-Math.PI/2;};
    var s=toRad(prev),e=toRad(prev+pctVal);
    var large=pctVal>50?1:0;
    var x1=cx+r*Math.cos(s),y1=cy+r*Math.sin(s);
    var x2=cx+r*Math.cos(e),y2=cy+r*Math.sin(e);
    return '<path d="M'+cx+' '+cy+' L'+x1+' '+y1+' A'+r+' '+r+' 0 '+large+' 1 '+x2+' '+y2+' Z" fill="'+color+'" opacity=".85"/>';
  };
  var p1=pct(allPresent),p2=pct(allAbsent),p3=pct(allLate);
  var p4=100-p1-p2-p3;
  var svgH=seg('var(--grn)',p1,0)+seg('var(--red)',p2,p1)+seg('var(--amb)',p3,p1+p2)+seg('var(--pur)',p4,p1+p2+p3);
  wrap.innerHTML=
    '<svg class="donut-svg" width="120" height="120" viewBox="0 0 120 120">'+svgH+
    '<circle cx="60" cy="60" r="30" fill="var(--c2)"/>'+
    '<text x="60" y="64" text-anchor="middle" fill="var(--txt)" font-size="13" font-weight="bold" font-family="Cairo">'+pct(allPresent+allLate)+'%</text>'+
    '</svg>'+
    '<div class="donut-legend">'+
      '<div class="donut-legend-item"><span class="donut-dot" style="background:var(--grn)"></span><span>حاضر — '+allPresent+' ('+p1+'%)</span></div>'+
      '<div class="donut-legend-item"><span class="donut-dot" style="background:var(--red)"></span><span>غائب — '+allAbsent+' ('+p2+'%)</span></div>'+
      '<div class="donut-legend-item"><span class="donut-dot" style="background:var(--amb)"></span><span>متأخر — '+allLate+' ('+p3+'%)</span></div>'+
    '</div>';
}

function renderBarChart(students){
  var wrap=document.getElementById('barChart');
  if(!wrap){return;}
  wrap.innerHTML='';
  if(students.length===0){wrap.innerHTML='<div class="empty-state"><p>لا توجد بيانات</p></div>';return;}
  var sorted=[].concat(students).sort(function(a,b){return b.rate-a.rate;});
  var top=sorted.slice(0,5);
  var bot=sorted.slice(-5).reverse();
  var section=function(title,list,color){
    var h='<div style="font-size:.78rem;font-weight:600;color:var(--txt2);margin-bottom:8px;margin-top:12px">'+title+'</div>';
    list.forEach(function(item){
      var name=item.s.name.length>18?item.s.name.substring(0,18)+'…':item.s.name;
      h+='<div class="chart-bar-row">'+
        '<div class="chart-label" title="'+sanitize(item.s.name)+'">'+sanitize(name)+'</div>'+
        '<div class="chart-bar-track">'+
          '<div class="chart-bar-fill" style="width:'+item.rate+'%;background:'+color+'">'+(item.rate>15?item.rate+'%':'')+'</div>'+
        '</div>'+
        (item.rate<=15?'<span style="font-size:.72rem;font-weight:700;color:'+color+';margin-right:6px">'+item.rate+'%</span>':'')+
      '</div>';
    });
    return h;
  };
  wrap.innerHTML=section('⭐ أعلى 5 طلاباً حضوراً',top,'linear-gradient(90deg,var(--grn),#34d399)')+
                 section('⚠ أدنى 5 طلاباً حضوراً',bot,'linear-gradient(90deg,var(--red),#f87171)');
}

function filterReport(f,el){
  reportFilter=f;
  document.querySelectorAll('#view-reports .flt-btn').forEach(function(b){b.classList.remove('active');});
  if(el) el.classList.add('active');
  renderReports();
}




function renderAlerts(){
  var sessionKeys=Object.keys(db.sessions);
  var totalSessions=sessionKeys.length;
  var alerts=[];
  db.students.forEach(function(s){
    var absent=0,late=0,present=0;
    sessionKeys.forEach(function(d){
      var st=db.sessions[d][s.id]||'present';
      if(st==='absent') absent++;
      else if(st==='late') late++;
      else present++;
    });
    var rate=totalSessions>0?Math.round(((present+late)/totalSessions)*100):100;
    if(absent>settings.alertThreshold){
      alerts.push({type:'danger',name:s.name,id:s.id,msg:'غاب '+absent+' مرات (الحد: '+settings.alertThreshold+')',rate:rate});
    } else if(rate<settings.riskPercent&&totalSessions>0){
      alerts.push({type:'warning',name:s.name,id:s.id,msg:'نسبة حضوره '+rate+'% أقل من '+settings.riskPercent+'%',rate:rate});
    }
  });
  
  var badge=document.getElementById('alertBadge');
  if(badge){ badge.textContent=alerts.length; badge.style.display=alerts.length>0?'inline':'none'; }
  var list=document.getElementById('alertsList');
  if(!list) return;
  list.innerHTML='';
  if(alerts.length===0){
    list.innerHTML='<div class="alert-box success"><span>✅</span><div><strong>ممتاز!</strong> لا توجد تنبيهات حالياً.</div></div>';
    return;
  }
  alerts.forEach(function(a){
    var div=document.createElement('div');
    div.className='alert-box '+(a.type==='danger'?'danger':'warning');
    div.innerHTML='<span>'+(a.type==='danger'?'🚨':'⚠️')+'</span><div><strong>'+sanitize(a.name)+'</strong> — '+sanitize(a.msg)+'</div>'+
    '<button class="btn btn-xs" onclick="openStudentDetail('+a.id+')" style="margin-right:auto;flex-shrink:0">تفاصيل</button>';
    list.appendChild(div);
  });
}
function clearAlerts(){
  var badge=document.getElementById('alertBadge');
  if(badge){badge.textContent='0';badge.style.display='none';}
  var list=document.getElementById('alertsList');
  if(list) list.innerHTML='<div class="alert-box success"><span>✅</span><div>تم مسح التنبيهات.</div></div>';
}




function toggleExportMenu(){
  exportMenuOpen=!exportMenuOpen;
  var m=document.getElementById('exportMenu');
  if(m) m.style.display=exportMenuOpen?'block':'none';
}
document.addEventListener('click',function(e){
  if(exportMenuOpen&&!document.getElementById('exportDropdown').contains(e.target)){
    exportMenuOpen=false;
    var m=document.getElementById('exportMenu'); if(m) m.style.display='none';
  }
});

function exportExcel(){
  ensureSession(currentDate);
  var session=db.sessions[currentDate];
  var rows=[
    [settings.college||'كلية التقنية الشمالية'],
    [settings.dept||'هندسة الأمن السيبراني'],
    ['تاريخ: '+formatDateAr(currentDate)],
    ['المادة: '+(settings.subject||'')],
    [''],
    ['#','الاسم','رقم الطالب','المجموعة','الحالة','ملاحظة']
  ];
  db.students.forEach(function(s,i){
    var st=session[s.id]||'present';
    var labels={present:'حاضر',absent:'غائب',late:'متأخر',excused:'إذن رسمي'};
    var note=(db.notes&&db.notes[currentDate]&&db.notes[currentDate][s.id])||'';
    rows.push([i+1,s.name,s.num||'',s.group||'A',labels[st]||'حاضر',note]);
  });
  var pArr=db.students.filter(function(s){return (session[s.id]||'present')==='present';});
  var aArr=db.students.filter(function(s){return (session[s.id]||'present')==='absent';});
  var lArr=db.students.filter(function(s){return (session[s.id]||'present')==='late';});
  rows.push([''],['إجمالي الطلاب',db.students.length],['الحاضرون',pArr.length],['الغائبون',aArr.length],['المتأخرون',lArr.length],['نسبة الحضور',db.students.length>0?Math.round(((pArr.length+lArr.length)/db.students.length)*100)+'%':'']);
  var ws=XLSX.utils.aoa_to_sheet(rows);
  ws['!cols']=[{wch:5},{wch:45},{wch:12},{wch:10},{wch:12},{wch:30}];
  ws['!merges']=[{s:{r:0,c:0},e:{r:0,c:5}},{s:{r:1,c:0},e:{r:1,c:5}},{s:{r:2,c:0},e:{r:2,c:5}},{s:{r:3,c:0},e:{r:3,c:5}}];
  var wb=XLSX.utils.book_new();
  XLSX.utils.book_append_sheet(wb,ws,'حضور_'+currentDate);
  XLSX.writeFile(wb,'حضور_'+currentDate+'.xlsx');
  showToast('تم تصدير Excel','success');
}

function exportFullReport(){
  var sessionKeys=Object.keys(db.sessions).sort();
  var headers=['الطالب','رقم الطالب','المجموعة'];
  sessionKeys.forEach(function(d){headers.push(d);});
  headers.push('إجمالي الحضور','إجمالي الغياب','إجمالي التأخر','نسبة الحضور','الحالة');
  var rows=[
    [settings.college||'كلية التقنية الشمالية'],
    [settings.dept||'هندسة الأمن السيبراني'],
    ['تقرير الحضور الشامل — '+formatDateAr(getTodayStr())],
    [''],
    headers
  ];
  db.students.forEach(function(s){
    var row=[s.name,s.num||'',s.group||'A'];
    var p=0,a=0,l=0;
    sessionKeys.forEach(function(d){
      var st=db.sessions[d][s.id]||'present';
      var labels={present:'حاضر',absent:'غائب',late:'متأخر',excused:'إذن'};
      row.push(labels[st]||'حاضر');
      if(st==='present') p++;
      else if(st==='absent') a++;
      else if(st==='late') l++;
    });
    var rate=sessionKeys.length>0?Math.round(((p+l)/sessionKeys.length)*100):100;
    var status=rate>=settings.riskPercent?'✓ جيد':'⚠ خطر';
    row.push(p,a,l,rate+'%',status);
    rows.push(row);
  });
  
  rows.push(['']);
  rows.push(['إجمالي المحاضرات',sessionKeys.length,'','']);
  var ws=XLSX.utils.aoa_to_sheet(rows);
  ws['!cols']=[{wch:40},{wch:12},{wch:10}];
  sessionKeys.forEach(function(){ws['!cols'].push({wch:10});});
  ws['!cols'].push({wch:10},{wch:10},{wch:10},{wch:12},{wch:8});
  ws['!merges']=[{s:{r:0,c:0},e:{r:0,c:4}},{s:{r:1,c:0},e:{r:1,c:4}},{s:{r:2,c:0},e:{r:2,c:4}}];
  var wb=XLSX.utils.book_new();
  XLSX.utils.book_append_sheet(wb,ws,'التقرير الشامل');
  XLSX.writeFile(wb,'تقرير_شامل_'+getTodayStr()+'.xlsx');
  showToast('تم تصدير التقرير الشامل','success');
}

function exportCSV(){
  ensureSession(currentDate);
  var session=db.sessions[currentDate];
  var labels={present:'حاضر',absent:'غائب',late:'متأخر',excused:'إذن رسمي'};
  var csv='\uFEFF#,الاسم,المجموعة,الحالة\n';
  db.students.forEach(function(s,i){
    var st=labels[session[s.id]||'present']||'حاضر';
    csv+=(i+1)+',"'+s.name.replace(/"/g,'""')+'",'+s.group+','+st+'\n';
  });
  var blob=new Blob([csv],{type:'text/csv;charset=utf-8'});
  var a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download='حضور_'+currentDate+'.csv';
  a.click();
  showToast('تم تصدير CSV','success');
}

function exportPDF(){
  window.print();
  showToast('جارٍ طباعة / تصدير PDF','info');
}

function exportDB(){
  var data=JSON.stringify(db,null,2);
  var blob=new Blob([data],{type:'application/json'});
  var a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download='attendance_backup_'+getTodayStr()+'.json';
  a.click();
  showToast('تم تصدير النسخة الاحتياطية','success');
}

function importDB(input){
  var file=input.files[0];
  if(!file) return;
  if(file.size>10*1024*1024){showToast('حجم الملف كبير جداً','error');return;}
  var reader=new FileReader();
  reader.onload=function(e){
    try{
      var parsed=JSON.parse(e.target.result);
      if(!parsed||!Array.isArray(parsed.students)){showToast('ملف غير صالح','error');return;}
      showConfirm('استيراد البيانات','سيتم استبدال البيانات الحالية. هل تريد المتابعة؟',function(){
        db=parsed;
        if(!db.notes) db.notes={};
        saveDB(); ensureSession(currentDate); renderStudents(); updateStats();
        showToast('تم استيراد البيانات بنجاح','success');
      });
    } catch(err){ showToast('خطأ في قراءة الملف','error'); }
  };
  reader.readAsText(file);
  input.value='';
}




function updateConfig(){
  var fields=['college','dept','group','admin','subject'];
  fields.forEach(function(f){
    var el=document.getElementById('cfg-'+f);
    if(el&&el.value.trim()) settings[f]=el.value.trim().substring(0,100);
  });
  applyConfig();
  try{ localStorage.setItem(SETTINGS_KEY,JSON.stringify(settings)); } catch(e){}
}

function applyConfig(){
  var map={college:'set-college',dept:'set-dept',group:'set-group',admin:'set-admin'};
  Object.keys(map).forEach(function(k){
    var el=document.getElementById(map[k]); if(el&&settings[k]) el.textContent=settings[k];
  });
}

function updateSettingsView(){
  document.getElementById('set-count').textContent=db.students.length+' طالب';
  document.getElementById('set-sessions').textContent=Object.keys(db.sessions).length+' محاضرة';
  var size=new Blob([JSON.stringify(db)]).size;
  document.getElementById('set-dbsize').textContent=(size/1024).toFixed(1)+' KB';
  applyConfig();
  var fields=['college','dept','group','admin','subject'];
  fields.forEach(function(f){
    var el=document.getElementById('cfg-'+f);
    if(el) el.value=settings[f]||'';
  });
  var t=document.getElementById('alertThreshold'); if(t) t.value=settings.alertThreshold;
  var r=document.getElementById('riskPercent'); if(r) r.value=settings.riskPercent;
}

function confirmReset(){
  showConfirm('إعادة ضبط المحاضرات','سيتم حذف جميع سجلات الحضور مع الاحتفاظ بقائمة الطلاب.',function(){
    db.sessions={}; db.notes={}; saveDB(); ensureSession(currentDate); renderStudents(); updateStats();
    showToast('تمت إعادة الضبط','success');
  });
}

function confirmDeleteAll(){
  showConfirm('حذف كل البيانات','⚠️ تحذير: سيتم حذف جميع الطلاب والسجلات نهائياً لا يمكن التراجع عنه!',function(){
    db={students:[],sessions:{},notes:{}}; saveDB(); renderStudents(); updateStats();
    studentsLoaded=false;
    showToast('تم حذف كل البيانات','error');
  });
}




function openModal(id){ document.getElementById(id).classList.add('open'); }
function closeModal(id){ document.getElementById(id).classList.remove('open'); }
document.querySelectorAll('.modal-overlay').forEach(function(o){
  o.addEventListener('click',function(e){ if(e.target===o) o.classList.remove('open'); });
});
document.addEventListener('keydown',function(e){
  if(e.key==='Escape') document.querySelectorAll('.modal-overlay.open').forEach(function(m){m.classList.remove('open');});
});

var confirmCallback=null;
function showConfirm(title,text,cb){
  document.getElementById('confirmTitle').textContent=title;
  document.getElementById('confirmText').textContent=text;
  confirmCallback=cb;
  openModal('confirmModal');
  document.getElementById('confirmOk').onclick=function(){ closeModal('confirmModal'); if(typeof confirmCallback==='function') confirmCallback(); };
}




var toastTimer=null;
function showToast(msg,type){
  var toast=document.getElementById('toast');
  var msgEl=document.getElementById('toastMsg');
  toast.className='toast '+(type||'info');
  msgEl.textContent=msg;
  toast.classList.add('show');
  if(toastTimer) clearTimeout(toastTimer);
  toastTimer=setTimeout(function(){toast.classList.remove('show');},3200);
}




async function init(){
  loadSettings();
  loadDB();
  
  if(db.students.length===0){
    await loadStudentsFromSource();
  } else {
    studentsLoaded=true;
  }
  var today=getTodayStr();
  currentDate=today;
  document.getElementById('datePicker').value=today;
  var now=new Date();
  document.getElementById('historyMonth').value=now.getFullYear()+'-'+pad(now.getMonth()+1);
  ensureSession(today);
  renderStudents();
  updateStats();
  renderAlerts();
  applyConfig();
  startClock();
  var overlay=document.getElementById('loadingOverlay');
  overlay.classList.add('hide');
  setTimeout(function(){overlay.style.display='none';},500);
}

document.addEventListener('DOMContentLoaded',init);
</script>
</body>
</html>
