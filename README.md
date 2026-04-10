[towbin-guest-sheet.html](https://github.com/user-attachments/files/26640871/towbin-guest-sheet.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Towbin Automotive — Guest Sheet</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
:root {
  --ink: #0f0f0f; --mid: #5a5a5a; --muted: #999; --rule: #e0ddd8;
  --accent: #b8922a; --accent-light: #f5edda; --bg: #f9f7f4; --white: #fff; --radius: 14px;
}
html, body { font-family: 'DM Sans', sans-serif; background: var(--bg); color: var(--ink); min-height: 100vh; -webkit-tap-highlight-color: transparent; }

/* LANDING */
#landing { display: flex; flex-direction: column; align-items: center; justify-content: center; min-height: 100vh; padding: 40px 24px; text-align: center; }
.logo-mark { width: 64px; height: 64px; background: var(--ink); border-radius: 16px; display: flex; align-items: center; justify-content: center; font-size: 30px; margin: 0 auto 18px; }
#landing h1 { font-family: 'Playfair Display', serif; font-size: 28px; margin-bottom: 4px; }
#landing .brands { font-size: 11px; color: var(--accent); letter-spacing: 2px; text-transform: uppercase; margin-bottom: 4px; }
#landing .location { font-size: 11px; color: var(--mid); margin-bottom: 32px; }
.btn-start { padding: 18px 40px; background: linear-gradient(135deg, #b8922a, #d4a84b); color: white; border: none; border-radius: 14px; font-size: 17px; font-family: 'DM Sans', sans-serif; font-weight: 500; cursor: pointer; }

/* FORM */
#form-screen { display: none; }
.topbar { position: sticky; top: 0; z-index: 100; background: var(--white); border-bottom: 1px solid var(--rule); padding: 14px 20px 0; box-shadow: 0 2px 12px rgba(0,0,0,0.06); }
.topbar-inner { display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; }
.brand h2 { font-family: 'Playfair Display', serif; font-size: 18px; line-height: 1.1; }
.brand .sub2 { font-size: 9px; color: var(--accent); letter-spacing: 2px; text-transform: uppercase; margin-top: 2px; }
.step-counter { font-size: 11px; color: var(--muted); text-align: right; }
.step-counter strong { font-size: 18px; color: var(--ink); font-weight: 600; }
.progress-track { height: 3px; background: var(--rule); border-radius: 99px; overflow: hidden; margin: 0 -20px; }
.progress-fill { height: 100%; background: linear-gradient(90deg, var(--accent), #d4a84b); border-radius: 99px; transition: width 0.4s cubic-bezier(0.4,0,0.2,1); }
.main { padding: 28px 20px 120px; max-width: 540px; margin: 0 auto; }
.step-panel { display: none; animation: fadeUp 0.3s ease; }
.step-panel.active { display: block; }
@keyframes fadeUp { from { opacity:0; transform:translateY(14px); } to { opacity:1; transform:translateY(0); } }
.step-eyebrow { font-size: 10px; letter-spacing: 2px; text-transform: uppercase; color: var(--accent); font-weight: 500; margin-bottom: 6px; }
.step-heading { font-family: 'Playfair Display', serif; font-size: 26px; line-height: 1.2; margin-bottom: 6px; }
.step-desc { font-size: 13px; color: var(--mid); margin-bottom: 28px; line-height: 1.5; }

.field { margin-bottom: 20px; }
.field-label { display: block; font-size: 11px; text-transform: uppercase; letter-spacing: 1px; color: var(--muted); font-weight: 500; margin-bottom: 8px; }
.field input[type="text"], .field input[type="tel"], .field input[type="email"], .field textarea {
  width: 100%; background: var(--white); border: 1.5px solid var(--rule); border-radius: 10px;
  padding: 14px 16px; font-size: 16px; font-family: 'DM Sans', sans-serif; color: var(--ink);
  outline: none; transition: border-color 0.2s, box-shadow 0.2s; -webkit-appearance: none;
}
.field input:focus, .field textarea:focus { border-color: var(--accent); box-shadow: 0 0 0 3px rgba(184,146,42,0.12); }
.field textarea { resize: none; line-height: 1.5; }
.field-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }

.pill-group { display: flex; flex-wrap: wrap; gap: 8px; }
.pill-group:not(.multi) .pill-btn { flex: 1 1 calc(50% - 4px); }
.pill-group.wide .pill-btn { flex: 1 1 100%; }
.pill-group.three .pill-btn { flex: 1 1 calc(33% - 6px); }
.pill-btn { display: flex; align-items: center; gap: 8px; padding: 12px 16px; border: 1.5px solid var(--rule); border-radius: 10px; background: var(--white); font-size: 14px; font-family: 'DM Sans', sans-serif; color: var(--ink); cursor: pointer; transition: all 0.15s; user-select: none; flex: 0 0 auto; }
.pill-btn .pill-icon { width: 20px; height: 20px; border-radius: 50%; border: 2px solid var(--rule); flex-shrink: 0; display: flex; align-items: center; justify-content: center; transition: all 0.15s; }
.pill-btn.check .pill-icon { border-radius: 5px; }
.pill-btn.selected { border-color: var(--accent); background: var(--accent-light); }
.pill-btn.selected .pill-icon { background: var(--accent); border-color: var(--accent); }
.pill-btn.selected .pill-icon::after { content: '✓'; font-size: 11px; color: white; font-weight: bold; }
.pill-btn:active { transform: scale(0.98); }
.pill-label { flex: 1; line-height: 1.3; }

.trade-reveal { display: none; }
.trade-reveal.show { display: block; }

.card { background: var(--white); border: 1px solid var(--rule); border-radius: var(--radius); padding: 18px; margin-bottom: 16px; }
.card-title { font-size: 12px; font-weight: 600; text-transform: uppercase; letter-spacing: 1px; color: var(--mid); margin-bottom: 14px; padding-bottom: 10px; border-bottom: 1px solid var(--rule); }

.bottom-nav { position: fixed; bottom: 0; left: 0; right: 0; background: var(--white); border-top: 1px solid var(--rule); padding: 14px 20px calc(14px + env(safe-area-inset-bottom)); display: flex; gap: 10px; max-width: 540px; margin: 0 auto; }
@media (min-width: 540px) { .bottom-nav { left: 50%; transform: translateX(-50%); width: 540px; } }
.btn { flex: 1; padding: 16px; border-radius: 12px; font-size: 15px; font-family: 'DM Sans', sans-serif; font-weight: 500; border: none; cursor: pointer; transition: all 0.15s; }
.btn-back { background: var(--bg); color: var(--mid); border: 1.5px solid var(--rule); flex: 0 0 80px; }
.btn-next { background: var(--ink); color: white; }
.btn-submit { background: linear-gradient(135deg, #b8922a, #d4a84b); color: white; }
.btn:active { transform: scale(0.97); }

/* SUCCESS */
.success-screen { display: none; text-align: center; padding: 48px 20px 60px; animation: fadeUp 0.4s ease; }
.success-screen.show { display: block; }
.success-icon { width: 72px; height: 72px; background: #e8f5ed; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 32px; margin: 0 auto 20px; }
.success-screen h2 { font-family: 'Playfair Display', serif; font-size: 26px; margin-bottom: 8px; }
.success-screen > p { font-size: 13px; color: var(--mid); line-height: 1.6; margin-bottom: 24px; }

.summary-card { background: var(--white); border: 1px solid var(--rule); border-radius: var(--radius); padding: 20px; margin: 0 auto 20px; max-width: 420px; text-align: left; }
.sum-sec { font-size: 10px; font-weight: 600; text-transform: uppercase; letter-spacing: 1.2px; color: var(--accent); margin: 14px 0 8px; padding-top: 14px; border-top: 1px solid var(--rule); }
.sum-sec:first-child { margin-top: 0; padding-top: 0; border-top: none; }
.sum-row { display: flex; justify-content: space-between; align-items: baseline; padding: 6px 0; border-bottom: 1px solid var(--rule); font-size: 13px; }
.sum-row:last-child { border-bottom: none; }
.s-label { color: var(--muted); font-size: 11px; text-transform: uppercase; letter-spacing: 0.8px; flex-shrink: 0; margin-right: 12px; }
.s-val { font-weight: 500; text-align: right; }

.sp-card { background: var(--accent-light); border: 1.5px solid var(--accent); border-radius: var(--radius); padding: 18px; margin: 0 auto 20px; max-width: 420px; text-align: left; }
.sp-card .card-title { color: var(--accent); border-color: rgba(184,146,42,0.25); }
.sp-card input, .sp-card textarea { width: 100%; background: var(--white); border: 1.5px solid var(--rule); border-radius: 10px; padding: 12px 14px; font-size: 15px; font-family: 'DM Sans', sans-serif; color: var(--ink); outline: none; margin-bottom: 12px; -webkit-appearance: none; }
.sp-card textarea { resize: none; }
.sp-card .field-label { display: block; font-size: 10px; text-transform: uppercase; letter-spacing: 1px; color: var(--muted); font-weight: 500; margin-bottom: 6px; }

.action-btns { display: flex; flex-direction: column; gap: 10px; max-width: 420px; margin: 0 auto; }
.btn-pdf { width: 100%; padding: 18px; border-radius: 12px; font-size: 16px; font-weight: 500; font-family: 'DM Sans', sans-serif; border: none; cursor: pointer; background: var(--ink); color: white; transition: all 0.15s; }
.btn-pdf:active { transform: scale(0.98); }
.btn-pdf.loading { opacity: 0.6; pointer-events: none; }
.btn-new { width: 100%; padding: 14px; border-radius: 12px; font-size: 14px; font-family: 'DM Sans', sans-serif; color: var(--mid); background: transparent; border: 1.5px solid var(--rule); cursor: pointer; }
.pdf-status { font-size: 12px; color: var(--mid); text-align: center; min-height: 18px; margin-top: 4px; }

.consent-box { padding: 14px 16px; background: var(--accent-light); border-radius: 10px; border-left: 3px solid var(--accent); margin-top: 4px; }
.consent-box p { font-size: 11px; color: var(--mid); line-height: 1.6; }
</style>
</head>
<body>

<!-- ══ LANDING ══ -->
<div id="landing">
  <div class="logo-mark">🏁</div>
  <h1>Towbin Automotive Group</h1>
  <div class="brands">Kia · Dodge · Alfa Romeo</div>
  <div class="location">Henderson, NV</div>
  <button class="btn-start" onclick="startForm()">📋 &nbsp;Open Guest Form</button>
</div>

<!-- ══ FORM ══ -->
<div id="form-screen">
  <div class="topbar" id="topbar">
    <div class="topbar-inner">
      <div class="brand"><h2>Towbin Automotive</h2><div class="sub2">Guest Information Sheet</div></div>
      <div class="step-counter"><strong id="step-num">1</strong> <span>of 5</span></div>
    </div>
    <div class="progress-track"><div class="progress-fill" id="progress-fill" style="width:20%"></div></div>
  </div>

  <div class="main">

    <!-- STEP 1 -->
    <div class="step-panel active" id="step-1">
      <div class="step-eyebrow">Step 1 of 5</div>
      <h2 class="step-heading">Welcome to Towbin!</h2>
      <p class="step-desc">Let's get a few details so we can find your perfect vehicle.</p>
      <div class="field-row">
        <div class="field"><label class="field-label">First Name</label><input type="text" id="fname" placeholder="Jane" autocomplete="given-name"></div>
        <div class="field"><label class="field-label">Last Name</label><input type="text" id="lname" placeholder="Smith" autocomplete="family-name"></div>
      </div>
      <div class="field"><label class="field-label">Best Phone Number</label><input type="tel" id="phone" placeholder="(702) 000-0000" autocomplete="tel"></div>
      <div class="field"><label class="field-label">Email Address</label><input type="email" id="email" placeholder="jane@email.com" autocomplete="email"></div>
      <div class="field"><label class="field-label">ZIP Code</label><input type="text" id="zip" placeholder="00000" inputmode="numeric" maxlength="5"></div>
    </div>

    <!-- STEP 2 -->
    <div class="step-panel" id="step-2">
      <div class="step-eyebrow">Step 2 of 5</div>
      <h2 class="step-heading">What are you looking for?</h2>
      <p class="step-desc">Help us point you in the right direction.</p>
      <div class="field">
        <label class="field-label">New or Pre-Owned?</label>
        <div class="pill-group three" data-group="new_used" data-single="true">
          <button class="pill-btn" data-val="New"><span class="pill-icon"></span>New</button>
          <button class="pill-btn" data-val="Pre-Owned"><span class="pill-icon"></span>Pre-Owned</button>
          <button class="pill-btn" data-val="Open to Either"><span class="pill-icon"></span>Open to Either</button>
        </div>
      </div>
      <div class="field">
        <label class="field-label">How soon are you buying?</label>
        <div class="pill-group" data-group="timeline" data-single="true">
          <button class="pill-btn" data-val="Today">🔑 <span class="pill-label">Today</span></button>
          <button class="pill-btn" data-val="This Week">📅 <span class="pill-label">This Week</span></button>
          <button class="pill-btn" data-val="This Month">🗓 <span class="pill-label">This Month</span></button>
          <button class="pill-btn" data-val="Just Browsing">👀 <span class="pill-label">Just Browsing</span></button>
        </div>
      </div>
      <div class="field">
        <label class="field-label">Body Style <span style="font-size:10px;text-transform:none;letter-spacing:0;">(tap all that interest you)</span></label>
        <div class="pill-group multi" data-group="body_style">
          <button class="pill-btn check" data-val="Sedan / Car">🚗 <span class="pill-label">Sedan / Car</span></button>
          <button class="pill-btn check" data-val="SUV / Crossover">🚙 <span class="pill-label">SUV / Crossover</span></button>
          <button class="pill-btn check" data-val="Truck">🛻 <span class="pill-label">Truck</span></button>
          <button class="pill-btn check" data-val="Minivan">🚐 <span class="pill-label">Minivan</span></button>
          <button class="pill-btn check" data-val="Coupe / Sport">🏎 <span class="pill-label">Coupe / Sport</span></button>
          <button class="pill-btn check" data-val="Electric / Hybrid">⚡ <span class="pill-label">Electric / Hybrid</span></button>
          <button class="pill-btn check" data-val="Open to Suggestions">🤷 <span class="pill-label">Open to Suggestions</span></button>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Specific Vehicle in Mind? (optional)</div>
        <div class="field-row" style="margin-bottom:12px;">
          <div class="field" style="margin-bottom:0;"><label class="field-label">Year</label><input type="text" id="veh-year" placeholder="2025" inputmode="numeric" maxlength="4"></div>
          <div class="field" style="margin-bottom:0;"><label class="field-label">Make</label><input type="text" id="veh-make" placeholder="Kia"></div>
        </div>
        <div class="field-row">
          <div class="field" style="margin-bottom:0;"><label class="field-label">Model</label><input type="text" id="veh-model" placeholder="Telluride"></div>
          <div class="field" style="margin-bottom:0;"><label class="field-label">Color</label><input type="text" id="veh-color" placeholder="White, Blue…"></div>
        </div>
      </div>
    </div>

    <!-- STEP 3 -->
    <div class="step-panel" id="step-3">
      <div class="step-eyebrow">Step 3 of 5</div>
      <h2 class="step-heading">What matters most?</h2>
      <p class="step-desc">Select everything that's important to you.</p>
      <div class="field">
        <label class="field-label">Must-Have Features</label>
        <div class="pill-group multi" data-group="features">
          <button class="pill-btn check" data-val="Fuel Economy">⛽ <span class="pill-label">Fuel Economy</span></button>
          <button class="pill-btn check" data-val="All-Wheel Drive">🌨 <span class="pill-label">All-Wheel Drive</span></button>
          <button class="pill-btn check" data-val="Towing / Payload">🪝 <span class="pill-label">Towing / Payload</span></button>
          <button class="pill-btn check" data-val="Safety Features">🛡 <span class="pill-label">Safety Features</span></button>
          <button class="pill-btn check" data-val="Tech & Infotainment">📱 <span class="pill-label">Tech &amp; Infotainment</span></button>
          <button class="pill-btn check" data-val="Seating Capacity">👨‍👩‍👧‍👦 <span class="pill-label">Seating Capacity</span></button>
          <button class="pill-btn check" data-val="Cargo Space">📦 <span class="pill-label">Cargo Space</span></button>
          <button class="pill-btn check" data-val="Performance">🏁 <span class="pill-label">Performance</span></button>
          <button class="pill-btn check" data-val="Comfort / Luxury">💺 <span class="pill-label">Comfort / Luxury</span></button>
          <button class="pill-btn check" data-val="Low Monthly Payment">💰 <span class="pill-label">Low Monthly Payment</span></button>
        </div>
      </div>
    </div>

    <!-- STEP 4 -->
    <div class="step-panel" id="step-4">
      <div class="step-eyebrow">Step 4 of 5</div>
      <h2 class="step-heading">Trade-in &amp; Budget</h2>
      <p class="step-desc">This helps us build the right deal from the start.</p>
      <div class="field">
        <label class="field-label">Do you have a vehicle to trade in?</label>
        <div class="pill-group wide" data-group="trade" data-single="true">
          <button class="pill-btn" data-val="Yes"><span class="pill-icon"></span>Yes, I have a trade</button>
          <button class="pill-btn" data-val="No"><span class="pill-icon"></span>No trade-in</button>
          <button class="pill-btn" data-val="Not Sure Yet"><span class="pill-icon"></span>Not sure yet</button>
        </div>
      </div>
      <div class="trade-reveal" id="trade-fields">
        <div class="card">
          <div class="card-title">Trade-In Details</div>
          <div class="field-row" style="margin-bottom:12px;">
            <div class="field" style="margin-bottom:0;"><label class="field-label">Year</label><input type="text" id="t-year" placeholder="2020" inputmode="numeric"></div>
            <div class="field" style="margin-bottom:0;"><label class="field-label">Make</label><input type="text" id="t-make" placeholder="Ford"></div>
          </div>
          <div class="field-row" style="margin-bottom:12px;">
            <div class="field" style="margin-bottom:0;"><label class="field-label">Model</label><input type="text" id="t-model" placeholder="F-150"></div>
            <div class="field" style="margin-bottom:0;"><label class="field-label">Mileage</label><input type="text" id="t-miles" placeholder="45,000" inputmode="numeric"></div>
          </div>
          <div class="field">
            <label class="field-label">Condition</label>
            <div class="pill-group three" data-group="trade_cond" data-single="true">
              <button class="pill-btn" data-val="Excellent"><span class="pill-icon"></span>Excellent</button>
              <button class="pill-btn" data-val="Good"><span class="pill-icon"></span>Good</button>
              <button class="pill-btn" data-val="Fair"><span class="pill-icon"></span>Fair</button>
            </div>
          </div>
          <div class="field-row">
            <div class="field" style="margin-bottom:0;"><label class="field-label">Amount Owed</label><input type="text" id="t-owed" placeholder="$0" inputmode="numeric"></div>
            <div class="field" style="margin-bottom:0;"><label class="field-label">Hoping to Get</label><input type="text" id="t-want" placeholder="$0" inputmode="numeric"></div>
          </div>
        </div>
      </div>
      <div class="field">
        <label class="field-label">How would you like to purchase?</label>
        <div class="pill-group" data-group="finance" data-single="true">
          <button class="pill-btn" data-val="Finance"><span class="pill-icon"></span>Finance</button>
          <button class="pill-btn" data-val="Lease"><span class="pill-icon"></span>Lease</button>
          <button class="pill-btn" data-val="Cash"><span class="pill-icon"></span>Cash</button>
          <button class="pill-btn" data-val="Not Sure"><span class="pill-icon"></span>Not Sure</button>
        </div>
      </div>
      <div class="field-row">
        <div class="field"><label class="field-label">Target Monthly</label><input type="text" id="monthly" placeholder="$500" inputmode="numeric"></div>
        <div class="field"><label class="field-label">Down Payment</label><input type="text" id="down" placeholder="$2,000" inputmode="numeric"></div>
      </div>
    </div>

    <!-- STEP 5 -->
    <div class="step-panel" id="step-5">
      <div class="step-eyebrow">Step 5 of 5</div>
      <h2 class="step-heading">Almost done!</h2>
      <p class="step-desc">Just a couple more things and we're set.</p>
      <div class="field">
        <label class="field-label">How did you hear about us?</label>
        <div class="pill-group multi" data-group="source">
          <button class="pill-btn check" data-val="Google / Search">🔍 <span class="pill-label">Google / Search</span></button>
          <button class="pill-btn check" data-val="Our Website">🌐 <span class="pill-label">Our Website</span></button>
          <button class="pill-btn check" data-val="Social Media">📲 <span class="pill-label">Social Media</span></button>
          <button class="pill-btn check" data-val="Friend / Family">👥 <span class="pill-label">Friend or Family</span></button>
          <button class="pill-btn check" data-val="Drive By">🚗 <span class="pill-label">Drive By</span></button>
          <button class="pill-btn check" data-val="Previous Customer">⭐ <span class="pill-label">Previous Customer</span></button>
          <button class="pill-btn check" data-val="Advertisement">📺 <span class="pill-label">Advertisement</span></button>
        </div>
      </div>
      <div class="field">
        <label class="field-label">Anything else we should know?</label>
        <textarea id="notes" rows="4" placeholder="e.g. need third row seating, specific deadline, hauling needs…"></textarea>
      </div>
      <div class="consent-box">
        <p>By submitting, you consent to being contacted by Towbin Automotive Group via phone, email, or text. Your information is kept strictly confidential and will never be sold or shared.</p>
      </div>
    </div>

    <!-- SUCCESS -->
    <div class="success-screen" id="success-screen">
      <div class="success-icon">✓</div>
      <h2>You're all set!</h2>
      <p>Welcome to the Towbin family! Your information has been shared with our team and we'll be right with you.</p>
      <div class="summary-card" id="summary-card"></div>
      <div class="sp-card">
        <div class="card-title">For Salesperson Use</div>
        <label class="field-label">Salesperson Name</label>
        <input type="text" id="sp-name" placeholder="Your name">
        <label class="field-label">Notes / First Impression</label>
        <textarea id="sp-notes" rows="3" placeholder="Customer priorities, vehicles shown, first impression…"></textarea>
      </div>
      <div class="action-btns">
        <button class="btn-pdf" id="pdf-btn" onclick="savePDF()">📄 &nbsp;Save Guest Sheet as PDF</button>
        <div class="pdf-status" id="pdf-status"></div>
        <button class="btn-new" onclick="location.reload()">Start New Guest Sheet</button>
      </div>
    </div>

  </div><!-- /main -->

  <div class="bottom-nav" id="bottom-nav">
    <button class="btn btn-back" id="btn-back" style="display:none;" onclick="prevStep()">← Back</button>
    <button class="btn btn-next" id="btn-next" onclick="nextStep()">Continue →</button>
  </div>
</div><!-- /form-screen -->

<script>
/* ══════════════════════════════════════════════
   PURE JS PDF ENGINE — no external libraries
   Writes raw PDF spec, encodes as blob, downloads
══════════════════════════════════════════════ */
const PDF = {
  // PDF coordinate system: origin bottom-left, y increases upward
  // Letter page: 612 x 792 pts
  PW: 612, PH: 792,
  ML: 44, MR: 44, MT: 44, MB: 44,

  // Approximate character widths for Helvetica at 1000 units/pt
  CW: {"a":556,"b":556,"c":500,"d":556,"e":556,"f":278,"g":556,"h":556,"i":222,
       "j":222,"k":500,"l":222,"m":833,"n":556,"o":556,"p":556,"q":556,"r":333,
       "s":500,"t":278,"u":556,"v":500,"w":722,"x":500,"y":500,"z":500,
       "A":667,"B":667,"C":722,"D":722,"E":667,"F":611,"G":778,"H":722,"I":278,
       "J":500,"K":667,"L":611,"M":833,"N":722,"O":778,"P":667,"Q":778,"R":722,
       "S":667,"T":611,"U":722,"V":667,"W":944,"X":667,"Y":667,"Z":611,
       "0":556,"1":556,"2":556,"3":556,"4":556,"5":556,"6":556,"7":556,"8":556,"9":556,
       " ":278,".":278,",":278,":":278,";":278,"!":278,"?":556,"-":333,"$":556,
       "(":333,")":333,"/":278,"&":667,"@":1015,"#":556,"+":584,"'":222,"\"":333},

  tw(str, size, bold) {
    const factor = bold ? 1.08 : 1.0;
    return [...String(str)].reduce((a,c) => a + (this.CW[c] || 500), 0) / 1000 * size * factor;
  },

  wrap(str, maxW, size, bold) {
    const words = String(str).split(' ');
    const lines = []; let cur = '';
    for (const w of words) {
      const test = cur ? cur + ' ' + w : w;
      if (this.tw(test, size, bold) <= maxW) { cur = test; }
      else { if (cur) lines.push(cur); cur = w; }
    }
    if (cur) lines.push(cur);
    return lines.length ? lines : [''];
  },

  esc(s) {
    return String(s || '').replace(/\\/g,'\\\\').replace(/\(/g,'\\(').replace(/\)/g,'\\)').replace(/\r?\n/g,' ');
  },

  generate(data) {
    const pages = [];
    let ops = [];
    const PW = this.PW, PH = this.PH, ML = this.ML, MR = this.MR;
    const CW = PW - ML - MR; // 524
    let y = PH - this.MT;

    const GOLD   = '0.722 0.573 0.165';
    const INK    = '0.059 0.059 0.059';
    const MID    = '0.353 0.353 0.353';
    const MUTED  = '0.600 0.600 0.600';
    const BGROW  = '0.976 0.969 0.957';
    const WHITE  = '1.000 1.000 1.000';
    const GOLDLT = '0.961 0.929 0.855';
    const RULE   = '0.878 0.867 0.847';

    const me = this;

    function newPage() {
      if (ops.length) pages.push([...ops]);
      ops = [];
      y = PH - me.MT;
    }

    function needSpace(h) {
      if (y - h < me.MB + 10) { newPage(); return true; }
      return false;
    }

    function rect(x, yr, w, h, colorStr, stroke) {
      ops.push(`${colorStr} ${stroke?'RG':'rg'}`);
      ops.push(`${x.toFixed(1)} ${yr.toFixed(1)} ${w.toFixed(1)} ${h.toFixed(1)} re ${stroke?'S':'f'}`);
    }

    function hline(x1, yr, x2, lw, colorStr) {
      ops.push(`${colorStr} RG`);
      ops.push(`${lw} w`);
      ops.push(`${x1.toFixed(1)} ${yr.toFixed(1)} m ${x2.toFixed(1)} ${yr.toFixed(1)} l S`);
    }

    function txt(x, yr, str, font, size, colorStr) {
      ops.push(`${colorStr} rg`);
      ops.push(`BT /${font} ${size} Tf ${x.toFixed(1)} ${yr.toFixed(1)} Td (${me.esc(str)}) Tj ET`);
    }

    function txtR(x, yr, str, font, size, colorStr) {
      const w = me.tw(str, size, font==='F2');
      txt(x - w, yr, str, font, size, colorStr);
    }

    const d = data;
    const dateStr  = new Date().toLocaleDateString('en-US',{month:'long',day:'numeric',year:'numeric'});
    const guestName = [d.fname, d.lname].filter(Boolean).join(' ') || 'Guest';
    const spName   = d.sp_name  || '—';
    const spNotes  = d.sp_notes || '—';

    // ── GOLD TOP BAR ──
    rect(0, PH - 6, PW, 6, GOLD, false);
    y = PH - 6 - 18;

    // ── HEADER ──
    txt(ML, y, 'Towbin Automotive Group', 'F2', 20, INK);
    y -= 13;
    txt(ML, y, 'KIA  \u00B7  DODGE  \u00B7  ALFA ROMEO', 'F1', 8, GOLD);
    y -= 11;
    txt(ML, y, 'Henderson, NV  \u00B7  towbinautogroup.com', 'F1', 7.5, MID);

    // Right meta
    let metaY = PH - 6 - 18;
    for (const [label, val] of [['Date:', dateStr],['Salesperson:', spName],['Guest:', guestName]]) {
      txtR(PW - MR, metaY, `${label}  ${val}`, 'F2', 9, MID);
      metaY -= 13;
    }

    y -= 10;
    hline(ML, y, PW - MR, 1.5, INK);
    y -= 14;

    // ── SECTION RENDERER ──
    const LW = CW * 0.36;
    const VW = CW * 0.64;
    const ROW_H = 18;

    function section(title, rows) {
      const valid = rows.filter(([,v]) => v);
      if (!valid.length) return;

      // Estimate height
      let est = 16 + 4;
      for (const [,v] of valid) est += me.wrap(v, VW - 16, 11).length * 14 + 4;
      needSpace(est);

      // Title pill
      rect(ML, y - 11, CW, 16, INK, false);
      txt(ML + 8, y - 7, title.toUpperCase(), 'F2', 8, WHITE);
      y -= 18;

      valid.forEach(([label, val], i) => {
        const wrapped = me.wrap(val, VW - 10, 11);
        const rowH = Math.max(ROW_H, wrapped.length * 13 + 6);
        needSpace(rowH + 2);

        // Alternating row bg
        rect(ML, y - rowH + 4, CW, rowH, i % 2 === 0 ? WHITE : BGROW, false);

        txt(ML + 6, y - 4, label.toUpperCase(), 'F1', 7.5, MUTED);
        wrapped.forEach((line, li) => {
          txt(ML + LW, y - 4 - li * 13, line, 'F1', 11, INK);
        });

        // Row rule
        hline(ML, y - rowH + 4, ML + CW, 0.4, RULE);
        y -= rowH;
      });
      y -= 12;
    }

    function gv(k) { const v = d[k]; return Array.isArray(v) && v.length ? v[0] : (v || null); }
    function jv(k) { const v = d[k]; return Array.isArray(v) && v.length ? v.join(', ') : null; }
    function veh(...keys) { const s = keys.map(k=>d[k]).filter(Boolean).join(' '); return s || null; }

    section('Contact Information', [
      ['Name', guestName], ['Phone', d.phone], ['Email', d.email], ['ZIP Code', d.zip],
    ]);
    section('Vehicle Interest', [
      ['Shopping For', gv('new_used')], ['Timeline', gv('timeline')],
      ['Body Style', jv('body_style')], ['Vehicle in Mind', veh('veh_year','veh_make','veh_model')],
      ['Color Preference', d.veh_color], ['Key Features', jv('features')],
    ]);
    section('Trade-In', [
      ['Has Trade-In', gv('trade')], ['Trade Vehicle', veh('t_year','t_make','t_model')],
      ['Mileage', d.t_miles], ['Condition', gv('trade_cond')],
      ['Amount Owed', d.t_owed ? '$'+d.t_owed : null],
      ['Hoping to Get', d.t_want ? '$'+d.t_want : null],
    ]);
    section('Financing & Budget', [
      ['Purchase Method', gv('finance')],
      ['Monthly Target', d.monthly ? '$'+d.monthly : null],
      ['Down Payment', d.down ? '$'+d.down : null],
    ]);
    section('Additional Info', [
      ['Heard About Us', jv('source')], ['Guest Notes', d.notes],
    ]);

    // ── SALESPERSON BOX ──
    needSpace(80);
    const spLines = me.wrap(spNotes, CW - 24, 11);
    const spBoxH = 16 + 13 + spLines.length * 13 + 20;
    needSpace(spBoxH);

    rect(ML, y - spBoxH + 8, CW, spBoxH, GOLDLT, false);
    rect(ML, y - spBoxH + 8, 4, spBoxH, GOLD, false);
    txt(ML + 12, y - 2, 'SALESPERSON NOTES', 'F2', 8, GOLD);
    txt(ML + 12, y - 14, `Written by: ${spName}`, 'F1', 8, MUTED);
    spLines.forEach((line, i) => txt(ML + 12, y - 26 - i * 13, line, 'F1', 11, INK));
    y -= spBoxH + 10;

    // ── FOOTER ──
    hline(ML, y, PW - MR, 0.5, RULE);
    y -= 10;
    const footerTxt = 'Confidential \u2014 Towbin Automotive Group use only. Guest information will not be shared.';
    txt(PW/2 - me.tw(footerTxt, 7)/2, y, footerTxt, 'F1', 7, MUTED);
    y -= 10;
    const genTxt = `Generated ${dateStr}`;
    txt(PW/2 - me.tw(genTxt, 7)/2, y, genTxt, 'F1', 7, GOLD);

    // Push final page
    pages.push([...ops]);

    // ── BUILD PDF BYTES ──
    return this._buildPDF(pages);
  },

  _buildPDF(pages) {
    const enc = s => [...s].map(c => c.charCodeAt(0));
    const chunks = [];
    const offsets = [];

    function emit(s) { chunks.push(enc(s)); }
    function bytes() { return chunks.reduce((a,b) => a+b.length, 0); }

    // Header
    emit('%PDF-1.4\n%\xFF\xFF\xFF\xFF\n');

    // We'll have: catalog(1), pages(2), font F1(3), font F2(4), then each page content+page obj pairs
    // page content obj = 5,7,9...  page obj = 6,8,10...
    const nPages = pages.length;
    const fontF1Obj = 3, fontF2Obj = 4;
    const firstContentObj = 5;
    // content objs: 5, 7, 9 ...  page objs: 6, 8, 10 ...
    const pageObjs = [];
    for (let i = 0; i < nPages; i++) pageObjs.push(firstContentObj + i*2 + 1);

    // obj 1: catalog
    offsets[1] = bytes();
    emit(`1 0 obj\n<< /Type /Catalog /Pages 2 0 R >>\nendobj\n`);

    // obj 2: pages
    offsets[2] = bytes();
    const kidsStr = pageObjs.map(n => `${n} 0 R`).join(' ');
    emit(`2 0 obj\n<< /Type /Pages /Kids [${kidsStr}] /Count ${nPages} >>\nendobj\n`);

    // obj 3: font Helvetica
    offsets[fontF1Obj] = bytes();
    emit(`3 0 obj\n<< /Type /Font /Subtype /Type1 /BaseFont /Helvetica /Encoding /WinAnsiEncoding >>\nendobj\n`);

    // obj 4: font Helvetica-Bold
    offsets[fontF2Obj] = bytes();
    emit(`4 0 obj\n<< /Type /Font /Subtype /Type1 /BaseFont /Helvetica-Bold /Encoding /WinAnsiEncoding >>\nendobj\n`);

    // page content + page objects
    for (let i = 0; i < nPages; i++) {
      const contentObj = firstContentObj + i * 2;
      const pageObj    = firstContentObj + i * 2 + 1;
      const stream = pages[i].join('\n') + '\n';

      offsets[contentObj] = bytes();
      emit(`${contentObj} 0 obj\n<< /Length ${stream.length} >>\nstream\n${stream}endstream\nendobj\n`);

      offsets[pageObj] = bytes();
      emit(`${pageObj} 0 obj\n<< /Type /Page /Parent 2 0 R `+
           `/MediaBox [0 0 ${this.PW} ${this.PH}] `+
           `/Contents ${contentObj} 0 R `+
           `/Resources << /Font << /F1 3 0 R /F2 4 0 R >> >> >>\nendobj\n`);
    }

    // xref
    const xrefOffset = bytes();
    const totalObjs = 1 + fontF2Obj + nPages * 2; // catalog + pages + 2 fonts + 2 per page
    emit(`xref\n0 ${totalObjs + 1}\n`);
    emit(`0000000000 65535 f \n`);
    for (let i = 1; i <= totalObjs; i++) {
      emit(`${String(offsets[i] || 0).padStart(10,'0')} 00000 n \n`);
    }
    emit(`trailer\n<< /Size ${totalObjs + 1} /Root 1 0 R >>\n`);
    emit(`startxref\n${xrefOffset}\n%%EOF\n`);

    return new Uint8Array(chunks.flat());
  }
};

/* ══ FORM LOGIC ══ */
const TOTAL = 5;
let current = 1;
const fd = {};

function startForm() {
  document.getElementById('landing').style.display = 'none';
  document.getElementById('form-screen').style.display = 'block';
}

function updateProgress() {
  document.getElementById('step-num').textContent = current;
  document.getElementById('progress-fill').style.width = (current / TOTAL * 100) + '%';
  document.getElementById('btn-back').style.display = current > 1 ? 'block' : 'none';
  const nb = document.getElementById('btn-next');
  nb.textContent = current === TOTAL ? '✓  Submit' : 'Continue →';
  nb.className = 'btn ' + (current === TOTAL ? 'btn-submit' : 'btn-next');
}

function showStep(n) {
  document.querySelectorAll('.step-panel').forEach(p => p.classList.remove('active'));
  const p = document.getElementById('step-' + n);
  if (p) p.classList.add('active');
  window.scrollTo({ top: 0, behavior: 'smooth' });
  updateProgress();
}

function v(id) { const el = document.getElementById(id); return el ? el.value.trim() : ''; }

function collect() {
  if (current===1){ fd.fname=v('fname'); fd.lname=v('lname'); fd.phone=v('phone'); fd.email=v('email'); fd.zip=v('zip'); }
  if (current===2){ fd.veh_year=v('veh-year'); fd.veh_make=v('veh-make'); fd.veh_model=v('veh-model'); fd.veh_color=v('veh-color'); }
  if (current===4){ fd.monthly=v('monthly'); fd.down=v('down'); fd.t_year=v('t-year'); fd.t_make=v('t-make'); fd.t_model=v('t-model'); fd.t_miles=v('t-miles'); fd.t_owed=v('t-owed'); fd.t_want=v('t-want'); }
  if (current===5){ fd.notes=v('notes'); }
}

function nextStep() { collect(); if (current<TOTAL){ current++; showStep(current); } else submitForm(); }
function prevStep() { if (current>1){ current--; showStep(current); } }

function submitForm() {
  document.querySelectorAll('[data-group]').forEach(g => {
    const sel = [...g.querySelectorAll('.pill-btn.selected')].map(b => b.dataset.val);
    if (sel.length) fd[g.dataset.group] = sel;
  });
  document.querySelectorAll('.step-panel').forEach(p => p.classList.remove('active'));
  document.getElementById('topbar').style.display = 'none';
  document.getElementById('bottom-nav').style.display = 'none';
  document.getElementById('success-screen').classList.add('show');
  buildSummary();
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

function buildSummary() {
  const d = fd;
  const secs = [
    { t:'Contact', rows:[['Name',[d.fname,d.lname].filter(Boolean).join(' ')],['Phone',d.phone],['Email',d.email],['ZIP',d.zip]] },
    { t:'Vehicle Interest', rows:[['Shopping For',d.new_used?.[0]],['Timeline',d.timeline?.[0]],['Body Style',d.body_style?.join(', ')],['Vehicle',[d.veh_year,d.veh_make,d.veh_model].filter(Boolean).join(' ')],['Color',d.veh_color],['Features',d.features?.join(', ')]] },
    { t:'Trade-In', rows:[['Has Trade',d.trade?.[0]],['Trade Vehicle',[d.t_year,d.t_make,d.t_model].filter(Boolean).join(' ')],['Mileage',d.t_miles],['Condition',d.trade_cond?.[0]],['Owed',d.t_owed?'$'+d.t_owed:null],['Hoping',d.t_want?'$'+d.t_want:null]] },
    { t:'Financing', rows:[['Method',d.finance?.[0]],['Monthly',d.monthly?'$'+d.monthly:null],['Down',d.down?'$'+d.down:null]] },
    { t:'Additional', rows:[['Source',d.source?.join(', ')],['Notes',d.notes]] },
  ];
  let html = '';
  secs.forEach(s => {
    const valid = s.rows.filter(([,v]) => v);
    if (!valid.length) return;
    html += `<div class="sum-sec">${s.t}</div>`;
    valid.forEach(([l,v]) => { html += `<div class="sum-row"><span class="s-label">${l}</span><span class="s-val">${v}</span></div>`; });
  });
  document.getElementById('summary-card').innerHTML = html;
}

/* ══ PDF SAVE ══ */
function savePDF() {
  const btn = document.getElementById('pdf-btn');
  const status = document.getElementById('pdf-status');
  btn.classList.add('loading');
  btn.textContent = '⏳  Building PDF…';
  status.textContent = '';

  // Slight delay so UI updates before CPU work
  setTimeout(() => {
    try {
      const payload = {
        ...fd,
        sp_name:  document.getElementById('sp-name').value.trim(),
        sp_notes: document.getElementById('sp-notes').value.trim(),
      };
      // Capture any last pill selections
      document.querySelectorAll('[data-group]').forEach(g => {
        const sel = [...g.querySelectorAll('.pill-btn.selected')].map(b => b.dataset.val);
        if (sel.length) payload[g.dataset.group] = sel;
      });

      const pdfBytes = PDF.generate(payload);
      const blob = new Blob([pdfBytes], { type: 'application/pdf' });
      const url  = URL.createObjectURL(blob);

      const a = document.createElement('a');
      const name = [fd.fname, fd.lname].filter(Boolean).join('_') || 'Guest';
      const date = new Date().toISOString().slice(0,10);
      a.href = url;
      a.download = `GuestSheet_${name}_${date}.pdf`;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      setTimeout(() => URL.revokeObjectURL(url), 5000);

      btn.classList.remove('loading');
      btn.textContent = '✓  PDF Saved!';
      status.textContent = 'Check your Downloads or Files app.';
      setTimeout(() => { btn.textContent = '📄  Save Guest Sheet as PDF'; status.textContent=''; }, 5000);
    } catch(e) {
      btn.classList.remove('loading');
      btn.textContent = '📄  Save Guest Sheet as PDF';
      status.textContent = '⚠  Something went wrong. Please try again.';
      console.error(e);
    }
  }, 60);
}

/* ══ PILL LOGIC ══ */
document.querySelectorAll('.pill-group').forEach(group => {
  const isSingle = group.dataset.single === 'true';
  group.querySelectorAll('.pill-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      if (isSingle) {
        group.querySelectorAll('.pill-btn').forEach(b => b.classList.remove('selected'));
        btn.classList.add('selected');
        if (group.dataset.group === 'trade') {
          const tf = document.getElementById('trade-fields');
          btn.dataset.val === 'Yes' ? tf.classList.add('show') : tf.classList.remove('show');
        }
      } else { btn.classList.toggle('selected'); }
      fd[group.dataset.group] = [...group.querySelectorAll('.pill-btn.selected')].map(b => b.dataset.val);
    });
  });
});

updateProgress();
</script>
</body>
</html>
