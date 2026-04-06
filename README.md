
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bazario — Shop Everything</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Manrope:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}

:root {
  --coral: #FF5733;
  --coral-light: #FF7A57;
  --coral-dim: #E84E2D;
  --coral-pale: #FFF0ED;
  --mint: #00C896;
  --mint-light: #00E5AB;
  --mint-pale: #E6FFF9;
  --amber: #FFB020;
  --amber-pale: #FFF8E6;
  --electric: #6C63FF;
  --electric-pale: #F0EFFE;
  --ink: #1A1A2E;
  --ink-mid: #2D2D4E;
  --ink-soft: #4A4A6A;
  --fog: #F4F3FF;
  --white: #FFFFFF;
  --slate: #8B8BA7;
  --border: #E8E6F0;
  --r: 14px;
  --r-sm: 8px;
  --r-pill: 100px;
}

body {
  font-family: 'Manrope', sans-serif;
  background: var(--fog);
  color: var(--ink);
  min-height: 100vh;
  overflow-x: hidden;
}

/* ── ANNOUNCEMENT ── */
.announce {
  background: var(--ink);
  color: white;
  text-align: center;
  padding: 9px 16px;
  font-size: 12.5px;
  font-weight: 500;
  letter-spacing: 0.2px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}
.announce-badge {
  background: var(--coral);
  color: white;
  font-size: 10px;
  font-weight: 800;
  letter-spacing: 1.5px;
  padding: 2px 9px;
  border-radius: var(--r-pill);
  text-transform: uppercase;
}

/* ── NAVBAR ── */
nav {
  background: var(--white);
  border-bottom: 1.5px solid var(--border);
  position: sticky;
  top: 0;
  z-index: 200;
}
.nav-inner {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 28px;
  display: flex;
  align-items: center;
  gap: 20px;
  height: 66px;
}
.logo {
  font-family: 'Syne', sans-serif;
  font-size: 27px;
  font-weight: 800;
  color: var(--coral);
  letter-spacing: -1px;
  white-space: nowrap;
  flex-shrink: 0;
}
.logo sup {
  font-size: 13px;
  color: var(--mint);
  vertical-align: super;
  font-weight: 700;
}

.search-wrap {
  flex: 1;
  position: relative;
  display: flex;
}
.search-input {
  width: 100%;
  height: 42px;
  border: 2px solid var(--border);
  border-radius: var(--r-pill);
  padding: 0 140px 0 20px;
  font-family: 'Manrope', sans-serif;
  font-size: 14px;
  color: var(--ink);
  outline: none;
  background: var(--fog);
  transition: border-color .2s, box-shadow .2s;
}
.search-input:focus {
  border-color: var(--coral);
  box-shadow: 0 0 0 3px rgba(255,87,51,.1);
  background: white;
}
.search-input::placeholder { color: var(--slate); }
.search-btn {
  position: absolute;
  right: 4px;
  top: 4px;
  height: 34px;
  padding: 0 20px;
  background: var(--coral);
  color: white;
  border: none;
  border-radius: var(--r-pill);
  font-family: 'Manrope', sans-serif;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: background .2s;
}
.search-btn:hover { background: var(--coral-dim); }

.nav-right {
  display: flex;
  align-items: center;
  gap: 4px;
  flex-shrink: 0;
}
.nav-icon-btn {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3px;
  padding: 6px 12px;
  border-radius: var(--r-sm);
  border: none;
  background: transparent;
  cursor: pointer;
  font-family: 'Manrope', sans-serif;
  color: var(--ink-soft);
  transition: background .15s, color .15s;
  position: relative;
}
.nav-icon-btn:hover { background: var(--fog); color: var(--coral); }
.nav-icon-btn svg { width: 20px; height: 20px; }
.nav-icon-btn .lbl { font-size: 10.5px; font-weight: 600; }
.dot {
  position: absolute;
  top: 5px; right: 8px;
  width: 17px; height: 17px;
  background: var(--coral);
  color: white;
  border-radius: 50%;
  font-size: 10px;
  font-weight: 800;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px solid white;
}

/* ── CATEGORY NAV ── */
.cat-nav {
  background: white;
  border-bottom: 1.5px solid var(--border);
  overflow-x: auto;
  scrollbar-width: none;
}
.cat-nav::-webkit-scrollbar { display: none; }
.cat-nav-inner {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 28px;
  display: flex;
  gap: 2px;
}
.cat-tab {
  padding: 13px 18px;
  font-size: 13px;
  font-weight: 600;
  color: var(--ink-soft);
  cursor: pointer;
  white-space: nowrap;
  border-bottom: 2.5px solid transparent;
  transition: color .2s, border-color .2s;
  display: flex;
  align-items: center;
  gap: 6px;
}
.cat-tab:hover { color: var(--coral); }
.cat-tab.active { color: var(--coral); border-bottom-color: var(--coral); }
.cat-tab .em { font-size: 15px; }

/* ── LAYOUT ── */
.page { max-width: 1280px; margin: 0 auto; padding: 0 28px; }

/* ── HERO ── */
.hero-zone {
  display: grid;
  grid-template-columns: 1fr 300px;
  gap: 18px;
  padding: 22px 0;
}
.hero-main {
  background: linear-gradient(135deg, #FF5733 0%, #FF8C42 45%, #FFB020 100%);
  border-radius: 20px;
  padding: 48px 52px;
  position: relative;
  overflow: hidden;
  min-height: 280px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.hero-main::before {
  content: '';
  position: absolute;
  right: -40px; bottom: -60px;
  width: 300px; height: 300px;
  background: rgba(255,255,255,0.12);
  border-radius: 50%;
}
.hero-main::after {
  content: '';
  position: absolute;
  right: 80px; top: -80px;
  width: 200px; height: 200px;
  background: rgba(255,255,255,0.08);
  border-radius: 50%;
}
.hero-chip {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  background: rgba(255,255,255,0.25);
  color: white;
  border-radius: var(--r-pill);
  padding: 5px 14px;
  font-size: 11.5px;
  font-weight: 700;
  letter-spacing: 0.5px;
  margin-bottom: 18px;
  width: fit-content;
  backdrop-filter: blur(4px);
}
.hero-title {
  font-family: 'Syne', sans-serif;
  font-size: 44px;
  font-weight: 800;
  color: white;
  line-height: 1.1;
  margin-bottom: 14px;
  position: relative;
  z-index: 1;
}
.hero-desc {
  font-size: 15px;
  color: rgba(255,255,255,0.88);
  margin-bottom: 28px;
  z-index: 1;
  position: relative;
}
.hero-cta {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: white;
  color: var(--coral);
  font-family: 'Syne', sans-serif;
  font-size: 15px;
  font-weight: 700;
  padding: 13px 28px;
  border-radius: var(--r-pill);
  border: none;
  cursor: pointer;
  z-index: 1;
  position: relative;
  width: fit-content;
  transition: transform .15s, box-shadow .15s;
  box-shadow: 0 4px 20px rgba(0,0,0,0.15);
}
.hero-cta:hover { transform: translateY(-2px); box-shadow: 0 8px 28px rgba(0,0,0,0.2); }

.hero-side { display: flex; flex-direction: column; gap: 18px; }
.side-card {
  border-radius: 16px;
  padding: 22px 20px;
  flex: 1;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  transition: transform .2s;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}
.side-card:hover { transform: translateY(-3px); }
.side-card.mint { background: linear-gradient(135deg, #00C896, #00A87A); }
.side-card.elec { background: linear-gradient(135deg, #6C63FF, #4F46E5); }
.side-card-icon {
  font-size: 36px;
  margin-bottom: 10px;
}
.side-card-label {
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.75);
  margin-bottom: 4px;
}
.side-card-title {
  font-family: 'Syne', sans-serif;
  font-size: 18px;
  font-weight: 800;
  color: white;
}
.side-card-sub {
  font-size: 12px;
  color: rgba(255,255,255,0.75);
  margin-top: 4px;
}

/* ── STATS STRIP ── */
.stats-strip {
  background: white;
  border-radius: 16px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  border: 1.5px solid var(--border);
  overflow: hidden;
  margin: 0 0 24px;
}
.stat-item {
  padding: 20px 24px;
  border-right: 1.5px solid var(--border);
  display: flex;
  align-items: center;
  gap: 14px;
}
.stat-item:last-child { border-right: none; }
.stat-icon {
  width: 44px; height: 44px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  flex-shrink: 0;
}
.ic-coral { background: var(--coral-pale); }
.ic-mint  { background: var(--mint-pale); }
.ic-amber { background: var(--amber-pale); }
.ic-elec  { background: var(--electric-pale); }
.stat-num {
  font-family: 'Syne', sans-serif;
  font-size: 20px;
  font-weight: 800;
  color: var(--ink);
  line-height: 1;
}
.stat-lbl {
  font-size: 11.5px;
  color: var(--slate);
  font-weight: 500;
  margin-top: 3px;
}

/* ── SECTION ── */
.section { margin-bottom: 32px; }
.section-hd {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}
.section-title {
  font-family: 'Syne', sans-serif;
  font-size: 22px;
  font-weight: 800;
  color: var(--ink);
  display: flex;
  align-items: center;
  gap: 10px;
}
.section-title .tag {
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  padding: 3px 10px;
  border-radius: var(--r-pill);
}
.tag-coral { background: var(--coral-pale); color: var(--coral); }
.tag-mint  { background: var(--mint-pale);  color: var(--mint);  }
.tag-amber { background: var(--amber-pale); color: #D4900A; }
.see-all {
  font-size: 13px;
  font-weight: 700;
  color: var(--coral);
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 4px;
  transition: gap .2s;
}
.see-all:hover { gap: 8px; }

/* ── CATEGORY ICONS ── */
.cat-icons {
  display: grid;
  grid-template-columns: repeat(9, 1fr);
  gap: 12px;
}
.cat-icon-item {
  background: white;
  border: 1.5px solid var(--border);
  border-radius: 16px;
  padding: 18px 8px 14px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 9px;
  cursor: pointer;
  transition: border-color .2s, transform .2s, background .2s;
}
.cat-icon-item:hover {
  border-color: var(--coral);
  transform: translateY(-4px);
  background: var(--coral-pale);
}
.ci-emoji { font-size: 26px; }
.ci-name {
  font-size: 11.5px;
  font-weight: 600;
  color: var(--ink-soft);
  text-align: center;
  line-height: 1.3;
}

/* ── DEAL BANNER ── */
.deal-banner {
  border-radius: 18px;
  background: var(--ink);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 28px 36px;
  gap: 24px;
  overflow: hidden;
  position: relative;
  margin-bottom: 32px;
}
.deal-banner::before {
  content: '';
  position: absolute;
  width: 400px; height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255,87,51,0.15) 0%, transparent 70%);
  top: -200px; right: -100px;
}
.deal-info .deal-sup {
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 2.5px;
  text-transform: uppercase;
  color: var(--coral);
  margin-bottom: 8px;
}
.deal-info .deal-h {
  font-family: 'Syne', sans-serif;
  font-size: 30px;
  font-weight: 800;
  color: white;
  line-height: 1.15;
  margin-bottom: 8px;
}
.deal-info .deal-sub {
  font-size: 13px;
  color: var(--slate);
}
.deal-timer { display: flex; align-items: center; gap: 10px; }
.timer-box {
  background: rgba(255,255,255,0.07);
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 12px;
  padding: 14px 18px;
  text-align: center;
  min-width: 72px;
}
.t-num {
  display: block;
  font-family: 'Syne', sans-serif;
  font-size: 30px;
  font-weight: 800;
  color: var(--coral);
  line-height: 1;
}
.t-lbl {
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  color: var(--slate);
  margin-top: 4px;
}
.t-sep {
  font-size: 26px;
  font-weight: 800;
  color: rgba(255,255,255,0.2);
}
.deal-btn {
  background: var(--coral);
  color: white;
  border: none;
  border-radius: var(--r-pill);
  padding: 14px 32px;
  font-family: 'Syne', sans-serif;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: background .2s, transform .15s;
  flex-shrink: 0;
}
.deal-btn:hover { background: var(--coral-dim); transform: scale(1.02); }

/* ── PRODUCT GRID ── */
.prod-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 16px;
}

.prod-card {
  background: white;
  border: 1.5px solid var(--border);
  border-radius: var(--r);
  overflow: hidden;
  cursor: pointer;
  transition: border-color .25s, transform .2s, box-shadow .25s;
  position: relative;
}
.prod-card:hover {
  border-color: var(--coral);
  transform: translateY(-5px);
  box-shadow: 0 16px 40px rgba(255,87,51,0.12);
}
.prod-img-wrap {
  position: relative;
  background: var(--fog);
  aspect-ratio: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 64px;
  overflow: hidden;
}
.prod-badge {
  position: absolute;
  top: 10px; left: 10px;
  font-size: 10px;
  font-weight: 800;
  letter-spacing: .8px;
  text-transform: uppercase;
  padding: 4px 10px;
  border-radius: var(--r-pill);
}
.b-hot  { background: var(--coral-pale); color: var(--coral); }
.b-new  { background: var(--mint-pale);  color: #007A5C; }
.b-top  { background: var(--amber-pale); color: #9A6800; }
.b-lim  { background: var(--electric-pale); color: #4338CA; }

.fav-btn {
  position: absolute;
  top: 10px; right: 10px;
  width: 32px; height: 32px;
  border-radius: 50%;
  background: white;
  border: 1.5px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  font-size: 15px;
  line-height: 1;
  transition: all .2s;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
}
.fav-btn:hover { border-color: var(--coral); background: var(--coral-pale); }

.prod-body { padding: 14px; }
.prod-brand {
  font-size: 10.5px;
  font-weight: 700;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  color: var(--coral);
  margin-bottom: 4px;
}
.prod-name {
  font-size: 13.5px;
  font-weight: 600;
  color: var(--ink);
  line-height: 1.4;
  margin-bottom: 10px;
}
.prod-rating {
  display: flex;
  align-items: center;
  gap: 6px;
  margin-bottom: 10px;
}
.star-pill {
  background: var(--mint);
  color: white;
  font-size: 11px;
  font-weight: 800;
  padding: 2px 8px;
  border-radius: var(--r-pill);
  display: flex;
  align-items: center;
  gap: 3px;
}
.rev-count { font-size: 11.5px; color: var(--slate); }

.prod-price { display: flex; align-items: baseline; gap: 7px; flex-wrap: wrap; }
.price-main {
  font-family: 'Syne', sans-serif;
  font-size: 18px;
  font-weight: 800;
  color: var(--ink);
}
.price-old {
  font-size: 12.5px;
  color: var(--slate);
  text-decoration: line-through;
}
.price-save {
  font-size: 11.5px;
  font-weight: 700;
  color: var(--mint);
  background: var(--mint-pale);
  padding: 1px 7px;
  border-radius: var(--r-pill);
}
.cart-btn {
  width: 100%;
  margin-top: 12px;
  padding: 9px;
  border-radius: var(--r-sm);
  border: 2px solid var(--coral);
  background: transparent;
  color: var(--coral);
  font-family: 'Manrope', sans-serif;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: background .2s, color .2s;
}
.cart-btn:hover { background: var(--coral); color: white; }

/* ── BRAND SCROLL ── */
.brand-scroll {
  display: flex;
  gap: 12px;
  overflow-x: auto;
  padding-bottom: 4px;
  scrollbar-width: none;
}
.brand-scroll::-webkit-scrollbar { display: none; }
.brand-pill {
  flex-shrink: 0;
  background: white;
  border: 1.5px solid var(--border);
  border-radius: var(--r-pill);
  padding: 9px 22px;
  font-size: 13px;
  font-weight: 700;
  color: var(--ink-soft);
  cursor: pointer;
  transition: all .2s;
}
.brand-pill:hover, .brand-pill.active {
  background: var(--coral);
  border-color: var(--coral);
  color: white;
}

/* ── 3-PROMO BLOCKS ── */
.promo-trio {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 18px;
  margin-bottom: 32px;
}
.promo-block {
  border-radius: 16px;
  padding: 28px 24px;
  cursor: pointer;
  transition: transform .2s;
  position: relative;
  overflow: hidden;
}
.promo-block:hover { transform: translateY(-3px); }
.promo-block.pb1 { background: linear-gradient(135deg, #FF5733 0%, #FF8C42 100%); }
.promo-block.pb2 { background: linear-gradient(135deg, #00C896 0%, #00A0D1 100%); }
.promo-block.pb3 { background: linear-gradient(135deg, #6C63FF 0%, #C084FC 100%); }
.promo-block::after {
  content: '';
  position: absolute;
  bottom: -30px; right: -30px;
  width: 120px; height: 120px;
  background: rgba(255,255,255,0.1);
  border-radius: 50%;
}
.pb-emoji { font-size: 36px; margin-bottom: 14px; }
.pb-sup {
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.75);
  margin-bottom: 6px;
}
.pb-title {
  font-family: 'Syne', sans-serif;
  font-size: 22px;
  font-weight: 800;
  color: white;
  margin-bottom: 6px;
  line-height: 1.2;
}
.pb-sub { font-size: 13px; color: rgba(255,255,255,0.8); }

/* ── FOOTER ── */
footer {
  background: var(--ink);
  color: white;
  padding: 48px 0 0;
  margin-top: 40px;
}
.footer-grid {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 28px 36px;
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr 1fr;
  gap: 36px;
}
.footer-logo {
  font-family: 'Syne', sans-serif;
  font-size: 24px;
  font-weight: 800;
  color: var(--coral);
  letter-spacing: -0.5px;
  margin-bottom: 14px;
}
.footer-logo sup { font-size: 13px; color: var(--mint); }
.footer-desc {
  font-size: 13px;
  color: #6B7280;
  line-height: 1.7;
  margin-bottom: 20px;
}
.footer-socials { display: flex; gap: 10px; }
.soc {
  width: 36px; height: 36px;
  border-radius: 10px;
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.08);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  cursor: pointer;
  transition: background .2s;
}
.soc:hover { background: rgba(255,87,51,0.2); border-color: rgba(255,87,51,0.3); }
.footer-col-h {
  font-size: 11px;
  font-weight: 800;
  letter-spacing: 2.5px;
  text-transform: uppercase;
  color: var(--coral);
  margin-bottom: 16px;
}
.footer-lnk {
  display: block;
  font-size: 13px;
  color: #6B7280;
  margin-bottom: 10px;
  cursor: pointer;
  transition: color .15s;
}
.footer-lnk:hover { color: white; }
.footer-bottom {
  max-width: 1280px;
  margin: 0 auto;
  padding: 18px 28px;
  border-top: 1px solid rgba(255,255,255,0.07);
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 12px;
  color: #4B5563;
}
.pay-badges { display: flex; gap: 8px; }
.pay-b {
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 6px;
  padding: 4px 11px;
  font-size: 11px;
  font-weight: 700;
  color: #9CA3AF;
}

/* ── ANIMATIONS ── */
@keyframes slideUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}
.hero-main > * {
  animation: slideUp .5s ease both;
}
.hero-main > *:nth-child(1) { animation-delay: .06s; }
.hero-main > *:nth-child(2) { animation-delay: .13s; }
.hero-main > *:nth-child(3) { animation-delay: .2s; }
.hero-main > *:nth-child(4) { animation-delay: .27s; }

@keyframes popIn {
  from { opacity: 0; transform: scale(0.93); }
  to   { opacity: 1; transform: scale(1); }
}
.prod-card { animation: popIn .4s ease both; }
.prod-card:nth-child(1) { animation-delay: .04s }
.prod-card:nth-child(2) { animation-delay: .08s }
.prod-card:nth-child(3) { animation-delay: .12s }
.prod-card:nth-child(4) { animation-delay: .16s }
.prod-card:nth-child(5) { animation-delay: .20s }

/* ── RESPONSIVE ── */
@media (max-width: 1100px) {
  .prod-grid { grid-template-columns: repeat(4,1fr); }
  .cat-icons { grid-template-columns: repeat(5,1fr); }
}
@media (max-width: 800px) {
  .hero-zone { grid-template-columns: 1fr; }
  .hero-side { flex-direction: row; }
  .prod-grid { grid-template-columns: repeat(2,1fr); }
  .promo-trio { grid-template-columns: 1fr; }
  .stats-strip { grid-template-columns: repeat(2,1fr); }
  .footer-grid { grid-template-columns: 1fr 1fr; gap: 24px; }
}
</style>
</head>
<body>

<!-- ANNOUNCEMENT -->
<div class="announce">
  <span class="announce-badge">New</span>
  🎉 Free delivery on orders above ₹599 &nbsp;·&nbsp; Extra 10% off with BAZARIO10
</div>

<!-- NA
