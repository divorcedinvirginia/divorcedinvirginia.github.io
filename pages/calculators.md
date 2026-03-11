---
layout: default
title: Calculators
description: Free calculators for Virginia divorce
permalink: /calculators/
---

## Virginia Support Calculator

This calculator first estimates spousal support using the Fairfax formula (28%/58%), then adjusts each spouse's income by that amount before calculating child support under Virginia's guidelines (Va. Code § 20-108.2). Virginia has no statutory spousal support formula — courts weigh 13 factors under Va. Code § 20-107.1 — so the spousal support figure is a rough reference point only.

<div class="tool-card">
  <h3 class="tool-title">Combined Support Estimator</h3>

  <p class="section-label">Incomes</p>
  <div class="input-grid">
    <div class="input-group">
      <label for="income1">Spouse 1 — Gross Monthly Income</label>
      <div class="input-prefix-wrap">
        <span class="prefix">$</span>
        <input type="number" id="income1" min="0" step="1" placeholder="0">
      </div>
    </div>
    <div class="input-group">
      <label for="income2">Spouse 2 — Gross Monthly Income</label>
      <div class="input-prefix-wrap">
        <span class="prefix">$</span>
        <input type="number" id="income2" min="0" step="1" placeholder="0">
      </div>
    </div>
  </div>

  <p class="section-label">Marriage</p>
  <div class="input-grid">
    <div class="input-group">
      <label for="marriage-years">Length of Marriage (years)</label>
      <input type="number" id="marriage-years" min="0" step="1" placeholder="e.g. 12">
    </div>
    <div class="input-group"></div>
  </div>

  <p class="section-label">Children</p>
  <div class="input-grid">
    <div class="input-group">
      <label for="numChildren">Number of Children</label>
      <select id="numChildren">
        <option value="0">No children</option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
        <option value="6">6 or more</option>
      </select>
    </div>
    <div class="input-group"></div>
    <div class="input-group" id="days1-group">
      <label for="days1">Spouse 1 — Days with Children per Year</label>
      <input type="number" id="days1" min="0" max="365" step="1" placeholder="e.g. 182" oninput="syncDays()">
    </div>
    <div class="input-group" id="days2-group">
      <label for="days2">Spouse 2 — Days with Children per Year</label>
      <input type="number" id="days2" min="0" max="365" step="1" placeholder="e.g. 183" oninput="syncDaysReverse()">
    </div>
  </div>

  <div id="days-warning" class="days-warning" style="display:none;">
    Days entered do not add up to 365. Please verify.
  </div>

  <button class="calc-btn" onclick="calculate()">Calculate</button>

  <div id="result" class="result" style="display:none;"></div>
</div>

<div class="tool-disclaimer">
  <strong>Important limitations.</strong> Virginia has no statutory spousal support formula. The spousal support estimate uses the informal Fairfax pendente lite formula (28%/58%) as a rough reference point and does not account for the 13 statutory factors under Va. Code § 20-107.1, fault grounds (adultery bars support), the marital standard of living, actual needs and expenses, or property division. Child support does not include work-related childcare costs, health insurance premiums, or other routine adjustments. Duration estimates reflect general judicial patterns and are not binding. This tool is for general informational purposes only and is not legal advice. Consult a licensed Virginia family law attorney for guidance specific to your situation.
</div>

*More calculators coming soon.*

<style>
  .tool-card {
    background: #f9f9f9;
    border: 1px solid #ddd;
    border-top: 3px solid #333;
    padding: 1.5rem;
    margin-bottom: 1.5rem;
  }
  .tool-title {
    margin: 0 0 1.25rem;
    font-size: 1rem;
    color: #222;
  }
  .section-label {
    font-size: 0.72rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: #888;
    margin: 1.1rem 0 0.5rem;
  }
  .section-label:first-of-type { margin-top: 0; }
  .input-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem 1.5rem;
    margin-bottom: 0.25rem;
  }
  @media (max-width: 600px) {
    .input-grid { grid-template-columns: 1fr; }
  }
  .input-group {
    display: flex;
    flex-direction: column;
    gap: 0.3rem;
  }
  .input-group label {
    font-size: 0.85rem;
    font-weight: 600;
    color: #333;
  }
  .input-prefix-wrap {
    display: flex;
    align-items: center;
    border: 1px solid #ccc;
    border-radius: 3px;
    overflow: hidden;
  }
  .prefix {
    padding: 0.45rem 0.6rem;
    background: #eee;
    color: #555;
    font-size: 0.9rem;
    border-right: 1px solid #ccc;
    user-select: none;
  }
  .input-prefix-wrap input {
    flex: 1;
    border: none;
    padding: 0.45rem 0.6rem;
    font-size: 0.9rem;
    color: #222;
    outline: none;
    min-width: 0;
  }
  .input-group input[type="number"],
  .input-group select {
    padding: 0.45rem 0.6rem;
    font-size: 0.9rem;
    border: 1px solid #ccc;
    border-radius: 3px;
    color: #222;
    background: #fff;
  }
  .input-group input[type="number"]:focus,
  .input-group select:focus {
    outline: none;
    border-color: #888;
  }
  .days-warning {
    font-size: 0.85rem;
    color: #b85c00;
    margin: 0.5rem 0 0.75rem;
    padding: 0.4rem 0.75rem;
    background: #fff8f0;
    border-left: 3px solid #b85c00;
  }
  .calc-btn {
    margin-top: 1.25rem;
    padding: 0.55rem 1.5rem;
    font-size: 0.95rem;
    background: #333;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
  }
  .calc-btn:hover { background: #555; }
  .result {
    margin-top: 1.25rem;
    background: #fff;
    border: 1px solid #ddd;
  }
  .result-section {
    padding: 1.1rem 1.25rem;
    border-bottom: 1px solid #eee;
  }
  .result-section:last-child { border-bottom: none; }
  .result-section-title {
    font-size: 0.72rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: #888;
    margin: 0 0 0.6rem;
  }
  .result-headline {
    font-size: 1.4rem;
    font-weight: 700;
    color: #222;
    margin: 0 0 0.15rem;
  }
  .result-sub {
    font-size: 0.88rem;
    color: #555;
    margin: 0 0 0.75rem;
  }
  .result-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 0.86rem;
  }
  .result-table td {
    padding: 0.3rem 0.4rem;
    border-bottom: 1px solid #f0f0f0;
  }
  .result-table td:first-child { color: #555; width: 60%; }
  .result-table td:last-child { font-weight: 600; color: #222; text-align: right; }
  .result-table tr:last-child td { border-bottom: none; }
  .result-table .highlight td { background: #f5f5f5; }
  .badge {
    display: inline-block;
    padding: 0.12rem 0.55rem;
    font-size: 0.72rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    border-radius: 2px;
    margin-bottom: 0.6rem;
  }
  .result-section-summary { background: #f0f0f0; }
  .result-section-summary .result-section-title { color: #555; }
  .badge-ss   { background: #f0e8f5; color: #5a2a7a; }
  .badge-shared  { background: #e8f0e8; color: #2a5e2a; }
  .badge-primary { background: #e8eaf0; color: #2a3a5e; }
  .tool-disclaimer {
    font-size: 0.82rem;
    color: #666;
    background: #f5f5f5;
    border-left: 3px solid #ccc;
    padding: 0.75rem 1rem;
    margin-bottom: 2rem;
  }
</style>

<script>
  // Virginia Basic Child Support Obligation Table (Va. Code § 20-108.2, effective July 1, 2025)
  var TABLE = [
    [350,   68,   104,  126,  141,  155,  169],
    [500,   97,   148,  179,  200,  220,  239],
    [1000,  206,  311,  389,  434,  478,  519],
    [5000,  872,  1304, 1637, 1829, 2012, 2187],
    [10000, 1251, 1824, 2308, 2578, 2835, 3082],
    [20000, 1990, 2853, 3525, 3937, 4331, 4708],
    [30000, 2581, 3763, 4673, 5220, 5742, 6242],
    [42500, 3306, 4792, 5867, 6554, 7209, 7837]
  ];
  var ABOVE_CAP = [0, 0.026, 0.034, 0.038, 0.042, 0.046, 0.050];

  function getBasicObligation(combined, nChildren) {
    var col = Math.min(nChildren, 6);
    if (combined <= TABLE[0][0]) return TABLE[0][col];
    if (combined > TABLE[TABLE.length - 1][0]) {
      return TABLE[TABLE.length - 1][col] + (combined - TABLE[TABLE.length - 1][0]) * ABOVE_CAP[col];
    }
    for (var i = 0; i < TABLE.length - 1; i++) {
      if (combined >= TABLE[i][0] && combined <= TABLE[i + 1][0]) {
        var t = (combined - TABLE[i][0]) / (TABLE[i + 1][0] - TABLE[i][0]);
        return TABLE[i][col] + t * (TABLE[i + 1][col] - TABLE[i][col]);
      }
    }
    return TABLE[TABLE.length - 1][col];
  }

  function fmt(n) { return '$' + Math.round(n).toLocaleString('en-US'); }
  function pct(n) { return (n * 100).toFixed(1) + '%'; }

  function syncDays() {
    var d1 = parseFloat(document.getElementById('days1').value);
    if (!isNaN(d1) && d1 >= 0 && d1 <= 365) document.getElementById('days2').value = 365 - d1;
    checkDaysWarning();
  }
  function syncDaysReverse() {
    var d2 = parseFloat(document.getElementById('days2').value);
    if (!isNaN(d2) && d2 >= 0 && d2 <= 365) document.getElementById('days1').value = 365 - d2;
    checkDaysWarning();
  }
  function checkDaysWarning() {
    var d1 = parseFloat(document.getElementById('days1').value) || 0;
    var d2 = parseFloat(document.getElementById('days2').value) || 0;
    document.getElementById('days-warning').style.display =
      (d1 + d2 !== 365 && d1 > 0 && d2 > 0) ? 'block' : 'none';
  }

  function durationText(yrs) {
    if (yrs < 5) {
      return Math.max(1, Math.round(yrs * 0.4)) + '–' + Math.max(2, Math.round(yrs * 0.6)) + ' years (short-term marriage)';
    } else if (yrs < 10) {
      return Math.round(yrs * 0.35) + '–' + Math.round(yrs * 0.5) + ' years';
    } else if (yrs < 20) {
      return Math.round(yrs * 0.4) + '–' + Math.round(yrs * 0.6) + ' years';
    }
    return 'Potentially indefinite (20+ year marriage)';
  }

  function calculate() {
    var gross1 = parseFloat(document.getElementById('income1').value) || 0;
    var gross2 = parseFloat(document.getElementById('income2').value) || 0;
    var marriageYears = parseFloat(document.getElementById('marriage-years').value);
    var nChildren = parseInt(document.getElementById('numChildren').value);
    var days1 = parseFloat(document.getElementById('days1').value) || 0;
    var days2 = parseFloat(document.getElementById('days2').value) || 0;

    var resultEl = document.getElementById('result');

    if (gross1 <= 0 && gross2 <= 0) {
      resultEl.style.display = 'block';
      resultEl.innerHTML = '<div class="result-section"><p style="color:#b00;margin:0;">Please enter at least one spouse\'s income.</p></div>';
      return;
    }

    // ── Step 1: Spousal support (Fairfax formula) ─────────────────────────────
    var ssAmount = 0;
    var ssPayorIs1 = null; // true = spouse 1 pays, false = spouse 2 pays
    var ssPayorIncome = 0, ssPayeeIncome = 0;
    var ssPayorLabel = '', ssPayeeLabel = '';
    var ssHtml = '';

    if (gross1 !== gross2) {
      ssPayorIs1 = gross1 > gross2;
      ssPayorIncome = ssPayorIs1 ? gross1 : gross2;
      ssPayeeIncome = ssPayorIs1 ? gross2 : gross1;
      ssPayorLabel = ssPayorIs1 ? 'Spouse 1' : 'Spouse 2';
      ssPayeeLabel = ssPayorIs1 ? 'Spouse 2' : 'Spouse 1';
      ssAmount = Math.max(0, (ssPayorIncome * 0.28) - (ssPayeeIncome * 0.58));
    }

    ssHtml += '<div class="result-section">';
    ssHtml += '<div class="result-section-title">Step 1 — Spousal Support</div>';
    ssHtml += '<span class="badge badge-ss">Fairfax Formula</span>';
    if (ssAmount > 0) {
      ssHtml += '<div class="result-headline">' + fmt(ssAmount) + ' / month</div>';
      ssHtml += '<div class="result-sub">' + ssPayorLabel + ' pays ' + ssPayeeLabel + '</div>';
    } else {
      ssHtml += '<div class="result-headline">$0 / month</div>';
      ssHtml += '<div class="result-sub">No spousal support indicated at these income levels.</div>';
    }
    ssHtml += '<table class="result-table">';
    ssHtml += '<tr><td>' + (ssPayorLabel || 'Higher earner') + ' gross income</td><td>' + fmt(ssPayorIncome || Math.max(gross1, gross2)) + '</td></tr>';
    ssHtml += '<tr><td>' + (ssPayeeLabel || 'Lower earner') + ' gross income</td><td>' + fmt(ssPayeeIncome || Math.min(gross1, gross2)) + '</td></tr>';
    ssHtml += '<tr><td>28% of payor income</td><td>' + fmt((ssPayorIncome || Math.max(gross1, gross2)) * 0.28) + '</td></tr>';
    ssHtml += '<tr><td>58% of payee income</td><td>' + fmt((ssPayeeIncome || Math.min(gross1, gross2)) * 0.58) + '</td></tr>';
    ssHtml += '<tr class="highlight"><td><strong>Estimated spousal support</strong></td><td><strong>' + fmt(ssAmount) + '</strong></td></tr>';
    if (!isNaN(marriageYears) && marriageYears > 0 && ssAmount > 0) {
      ssHtml += '<tr><td>Estimated duration</td><td>' + durationText(marriageYears) + '</td></tr>';
    }
    ssHtml += '</table>';
    ssHtml += '</div>';

    // ── Step 2: Adjust incomes ────────────────────────────────────────────────
    var adj1 = gross1, adj2 = gross2;
    if (ssAmount > 0) {
      if (ssPayorIs1) { adj1 = gross1 - ssAmount; adj2 = gross2 + ssAmount; }
      else            { adj2 = gross2 - ssAmount; adj1 = gross1 + ssAmount; }
    }
    // Floor at zero
    adj1 = Math.max(0, adj1);
    adj2 = Math.max(0, adj2);

    var adjHtml = '';
    if (ssAmount > 0) {
      adjHtml += '<div class="result-section">';
      adjHtml += '<div class="result-section-title">Step 2 — Income Adjustment for Child Support</div>';
      adjHtml += '<table class="result-table">';
      adjHtml += '<tr><td>Spouse 1 gross income</td><td>' + fmt(gross1) + '</td></tr>';
      adjHtml += '<tr><td>Spouse 2 gross income</td><td>' + fmt(gross2) + '</td></tr>';
      adjHtml += '<tr><td>Spousal support adjustment</td><td>' + fmt(ssAmount) + '</td></tr>';
      adjHtml += '<tr class="highlight"><td><strong>Spouse 1 adjusted income</strong></td><td><strong>' + fmt(adj1) + '</strong></td></tr>';
      adjHtml += '<tr class="highlight"><td><strong>Spouse 2 adjusted income</strong></td><td><strong>' + fmt(adj2) + '</strong></td></tr>';
      adjHtml += '</table>';
      adjHtml += '</div>';
    }

    // ── Step 3: Child support ────────────────────────────────────────────────
    var csAmount = 0;
    var csPayorIs1 = null; // true = spouse 1 pays child support
    var csHtml = '';
    if (nChildren > 0) {
      if (days1 > 0 && days2 <= 0) days2 = 365 - days1;
      if (days2 > 0 && days1 <= 0) days1 = 365 - days2;

      var combined = adj1 + adj2;
      var basicObligation = getBasicObligation(combined, nChildren);
      var share1 = combined > 0 ? adj1 / combined : 0.5;
      var share2 = combined > 0 ? adj2 / combined : 0.5;
      var isShared = days1 >= 91 && days2 >= 91;

      csHtml += '<div class="result-section">';
      csHtml += '<div class="result-section-title">Step 3 — Child Support</div>';

      if (isShared) {
        var sharedNeed = basicObligation * 1.4;
        var custPct1 = days1 / 365, custPct2 = days2 / 365;
        var ob1 = share1 * sharedNeed * custPct2;
        var ob2 = share2 * sharedNeed * custPct1;
        var net = Math.abs(ob1 - ob2);
        csPayorIs1 = ob1 > ob2;
        csAmount = net;
        var csPayorLabel = csPayorIs1 ? 'Spouse 1 pays Spouse 2' : 'Spouse 2 pays Spouse 1';

        csHtml += '<span class="badge badge-shared">Shared Custody — Schedule B</span>';
        csHtml += '<div class="result-headline">' + fmt(net) + ' / month</div>';
        csHtml += '<div class="result-sub">' + csPayorLabel + '</div>';
        csHtml += '<table class="result-table">';
        csHtml += '<tr><td>Spouse 1 adjusted income</td><td>' + fmt(adj1) + '</td></tr>';
        csHtml += '<tr><td>Spouse 2 adjusted income</td><td>' + fmt(adj2) + '</td></tr>';
        csHtml += '<tr><td>Combined adjusted income</td><td>' + fmt(combined) + '</td></tr>';
        csHtml += '<tr><td>Basic guideline obligation (' + nChildren + ' child' + (nChildren > 1 ? 'ren' : '') + ')</td><td>' + fmt(basicObligation) + '</td></tr>';
        csHtml += '<tr><td>Shared custody adjustment (× 1.4)</td><td>' + fmt(sharedNeed) + '</td></tr>';
        csHtml += '<tr><td>Spouse 1 income share / custody time</td><td>' + pct(share1) + ' / ' + pct(custPct1) + '</td></tr>';
        csHtml += '<tr><td>Spouse 2 income share / custody time</td><td>' + pct(share2) + ' / ' + pct(custPct2) + '</td></tr>';
        csHtml += '<tr><td>Spouse 1 gross obligation</td><td>' + fmt(ob1) + '</td></tr>';
        csHtml += '<tr><td>Spouse 2 gross obligation</td><td>' + fmt(ob2) + '</td></tr>';
        csHtml += '<tr class="highlight"><td><strong>Net monthly child support</strong></td><td><strong>' + fmt(net) + '</strong></td></tr>';
        csHtml += '</table>';
      } else {
        var custodialSpouse = days1 >= days2 ? 1 : 2;
        var ncShare = custodialSpouse === 1 ? share2 : share1;
        var ncDays = custodialSpouse === 1 ? days2 : days1;
        var csLabel = 'Spouse ' + (custodialSpouse === 1 ? '2' : '1') + ' pays Spouse ' + custodialSpouse;
        var csSupport = basicObligation * ncShare;
        csPayorIs1 = custodialSpouse === 2;
        csAmount = csSupport;

        csHtml += '<span class="badge badge-primary">Primary Custody — Schedule A</span>';
        csHtml += '<div class="result-headline">' + fmt(csSupport) + ' / month</div>';
        csHtml += '<div class="result-sub">' + csLabel + '</div>';
        csHtml += '<table class="result-table">';
        csHtml += '<tr><td>Spouse 1 adjusted income</td><td>' + fmt(adj1) + '</td></tr>';
        csHtml += '<tr><td>Spouse 2 adjusted income</td><td>' + fmt(adj2) + '</td></tr>';
        csHtml += '<tr><td>Combined adjusted income</td><td>' + fmt(combined) + '</td></tr>';
        csHtml += '<tr><td>Basic guideline obligation (' + nChildren + ' child' + (nChildren > 1 ? 'ren' : '') + ')</td><td>' + fmt(basicObligation) + '</td></tr>';
        csHtml += '<tr><td>Spouse 1 income share</td><td>' + pct(share1) + '</td></tr>';
        csHtml += '<tr><td>Spouse 2 income share</td><td>' + pct(share2) + '</td></tr>';
        csHtml += '<tr><td>Custodial spouse</td><td>Spouse ' + custodialSpouse + ' (' + (custodialSpouse === 1 ? days1 : days2) + ' days)</td></tr>';
        csHtml += '<tr><td>Noncustodial spouse days</td><td>' + ncDays + ' days/year</td></tr>';
        csHtml += '<tr class="highlight"><td><strong>Monthly child support</strong></td><td><strong>' + fmt(csSupport) + '</strong></td></tr>';
        csHtml += '</table>';
      }
      csHtml += '</div>';
    }

    // ── Summary ───────────────────────────────────────────────────────────────
    var summaryHtml = '';
    var hasAnything = ssAmount > 0 || csAmount > 0;
    if (hasAnything) {
      // Net obligation from Spouse 1's perspective (positive = pays, negative = receives)
      var net1 = 0;
      if (ssAmount > 0) net1 += ssPayorIs1 ? ssAmount : -ssAmount;
      if (csAmount > 0 && csPayorIs1 !== null) net1 += csPayorIs1 ? csAmount : -csAmount;
      var net2 = -net1;

      summaryHtml += '<div class="result-section result-section-summary">';
      summaryHtml += '<div class="result-section-title">Total Monthly Support Obligation</div>';
      summaryHtml += '<table class="result-table">';

      if (ssAmount > 0) {
        summaryHtml += '<tr><td>Spousal support (' + (ssPayorIs1 ? 'Spouse 1 → Spouse 2' : 'Spouse 2 → Spouse 1') + ')</td><td>' + fmt(ssAmount) + '</td></tr>';
      }
      if (csAmount > 0) {
        summaryHtml += '<tr><td>Child support (' + (csPayorIs1 ? 'Spouse 1 → Spouse 2' : 'Spouse 2 → Spouse 1') + ')</td><td>' + fmt(csAmount) + '</td></tr>';
      }

      summaryHtml += '<tr class="highlight"><td><strong>Spouse 1 net monthly obligation</strong></td>';
      if (net1 > 0) {
        summaryHtml += '<td><strong>' + fmt(net1) + ' paid out</strong></td></tr>';
      } else if (net1 < 0) {
        summaryHtml += '<td><strong>' + fmt(-net1) + ' received</strong></td></tr>';
      } else {
        summaryHtml += '<td><strong>$0</strong></td></tr>';
      }

      summaryHtml += '<tr class="highlight"><td><strong>Spouse 2 net monthly obligation</strong></td>';
      if (net2 > 0) {
        summaryHtml += '<td><strong>' + fmt(net2) + ' paid out</strong></td></tr>';
      } else if (net2 < 0) {
        summaryHtml += '<td><strong>' + fmt(-net2) + ' received</strong></td></tr>';
      } else {
        summaryHtml += '<td><strong>$0</strong></td></tr>';
      }

      summaryHtml += '</table>';
      summaryHtml += '</div>';
    }

    resultEl.style.display = 'block';
    resultEl.innerHTML = ssHtml + adjHtml + csHtml + summaryHtml;
  }

  // Show/hide custody days fields based on children selection
  document.getElementById('numChildren').addEventListener('change', function() {
    var show = this.value !== '0';
    document.getElementById('days1-group').style.display = show ? '' : 'none';
    document.getElementById('days2-group').style.display = show ? '' : 'none';
    document.getElementById('days-warning').style.display = 'none';
  });
  // Init state
  (function() {
    var show = document.getElementById('numChildren').value !== '0';
    document.getElementById('days1-group').style.display = show ? '' : 'none';
    document.getElementById('days2-group').style.display = show ? '' : 'none';
  })();
</script>
