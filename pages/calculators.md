---
layout: default
title: Calculators
description: Free calculators for Virginia divorce
permalink: /calculators/
---

## Virginia Child Support Calculator

This calculator estimates monthly child support under Virginia's Child Support Guidelines (Va. Code § 20-108.2). Enter each parent's gross monthly income, the number of children, and the number of days per year each parent has the children.

<div class="tool-card">
  <h3 class="tool-title">Child Support Estimator</h3>

  <div class="input-grid">
    <div class="input-group">
      <label for="income1">Parent 1 — Gross Monthly Income</label>
      <div class="input-prefix-wrap">
        <span class="prefix">$</span>
        <input type="number" id="income1" min="0" step="1" placeholder="0">
      </div>
    </div>
    <div class="input-group">
      <label for="income2">Parent 2 — Gross Monthly Income</label>
      <div class="input-prefix-wrap">
        <span class="prefix">$</span>
        <input type="number" id="income2" min="0" step="1" placeholder="0">
      </div>
    </div>
    <div class="input-group">
      <label for="numChildren">Number of Children</label>
      <select id="numChildren">
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
        <option value="6">6 or more</option>
      </select>
    </div>
    <div class="input-group"></div>
    <div class="input-group">
      <label for="days1">Parent 1 — Days with Children per Year</label>
      <input type="number" id="days1" min="0" max="365" step="1" placeholder="e.g. 182" oninput="syncDays()">
    </div>
    <div class="input-group">
      <label for="days2">Parent 2 — Days with Children per Year</label>
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
  <strong>Important limitations.</strong> This calculator provides an estimate based on the basic child support obligation from Virginia's guidelines table. It does not include work-related childcare costs, health insurance premiums, or other adjustments courts routinely add to the base amount. Actual court-ordered support may differ. This tool is for general informational purposes only and is not legal advice. Consult a licensed Virginia family law attorney for guidance specific to your situation.
</div>

---

## Virginia Spousal Support Estimator

Virginia has no statutory formula for spousal support — courts weigh 13 factors under Va. Code § 20-107.1. However, many Virginia circuit courts apply an informal formula at the **pendente lite** (temporary support) stage when there is not time for a full factor analysis. The most widely referenced is the Fairfax formula: **28% of the higher earner's gross monthly income minus 58% of the lower earner's gross monthly income.**

This calculator applies that formula and provides a rough duration estimate based on observed judicial patterns. Both figures are starting points only — actual awards vary significantly by judge, jurisdiction, and the facts of the case.

<div class="tool-card">
  <h3 class="tool-title">Spousal Support Estimator</h3>

  <div class="input-grid">
    <div class="input-group">
      <label for="ss-income1">Spouse 1 — Gross Monthly Income</label>
      <div class="input-prefix-wrap">
        <span class="prefix">$</span>
        <input type="number" id="ss-income1" min="0" step="1" placeholder="0">
      </div>
    </div>
    <div class="input-group">
      <label for="ss-income2">Spouse 2 — Gross Monthly Income</label>
      <div class="input-prefix-wrap">
        <span class="prefix">$</span>
        <input type="number" id="ss-income2" min="0" step="1" placeholder="0">
      </div>
    </div>
    <div class="input-group">
      <label for="ss-marriage-years">Length of Marriage (years)</label>
      <input type="number" id="ss-marriage-years" min="0" step="1" placeholder="e.g. 12">
    </div>
    <div class="input-group"></div>
  </div>

  <button class="calc-btn" onclick="calculateSpousalSupport()">Calculate</button>

  <div id="ss-result" class="result" style="display:none;"></div>
</div>

<div class="tool-disclaimer">
  <strong>Important limitations.</strong> Virginia has no statutory spousal support formula. This calculator applies the informal Fairfax pendente lite formula (28%/58%) as a rough reference point. It does not account for the 13 statutory factors under Va. Code § 20-107.1, the marital standard of living, actual needs and expenses, fault grounds (including adultery, which bars support), property division, or other case-specific circumstances. A spouse who committed adultery is generally barred from receiving spousal support under Virginia law. Duration estimates reflect general judicial patterns and are not binding. This tool is for general informational purposes only and is not legal advice. Consult a licensed Virginia family law attorney for guidance specific to your situation.
</div>

---

*More tools coming soon.*

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
  .input-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem 1.5rem;
    margin-bottom: 1.25rem;
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
    margin-bottom: 0.75rem;
    padding: 0.4rem 0.75rem;
    background: #fff8f0;
    border-left: 3px solid #b85c00;
  }
  .calc-btn {
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
    padding: 1.25rem;
    background: #fff;
    border: 1px solid #ddd;
    border-left: 4px solid #333;
  }
  .result-headline {
    font-size: 1.5rem;
    font-weight: 700;
    color: #222;
    margin: 0 0 0.25rem;
  }
  .result-sub {
    font-size: 0.9rem;
    color: #555;
    margin: 0 0 1rem;
  }
  .result-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 0.88rem;
    margin-top: 0.75rem;
  }
  .result-table td {
    padding: 0.35rem 0.5rem;
    border-bottom: 1px solid #eee;
  }
  .result-table td:first-child {
    color: #555;
    width: 55%;
  }
  .result-table td:last-child {
    font-weight: 600;
    color: #222;
    text-align: right;
  }
  .result-table tr:last-child td { border-bottom: none; }
  .custody-badge {
    display: inline-block;
    padding: 0.15rem 0.6rem;
    font-size: 0.75rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    border-radius: 2px;
    margin-bottom: 0.75rem;
  }
  .badge-shared { background: #e8f0e8; color: #2a5e2a; }
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
  // Columns: [combined monthly income, 1 child, 2 children, 3 children, 4 children, 5 children, 6 children]
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

  // For income above $42,500: percentage of excess applied per child count (index 1-6)
  var ABOVE_CAP = [0, 0.026, 0.034, 0.038, 0.042, 0.046, 0.050];

  function getBasicObligation(combined, nChildren) {
    var col = Math.min(nChildren, 6); // col 1–6
    if (combined <= TABLE[0][0]) return TABLE[0][col];
    if (combined > TABLE[TABLE.length - 1][0]) {
      var base = TABLE[TABLE.length - 1][col];
      return base + (combined - TABLE[TABLE.length - 1][0]) * ABOVE_CAP[col];
    }
    for (var i = 0; i < TABLE.length - 1; i++) {
      if (combined >= TABLE[i][0] && combined <= TABLE[i + 1][0]) {
        var t = (combined - TABLE[i][0]) / (TABLE[i + 1][0] - TABLE[i][0]);
        return TABLE[i][col] + t * (TABLE[i + 1][col] - TABLE[i][col]);
      }
    }
    return TABLE[TABLE.length - 1][col];
  }

  function fmt(n) {
    return '$' + Math.round(n).toLocaleString('en-US');
  }

  function pct(n) {
    return (n * 100).toFixed(1) + '%';
  }

  function syncDays() {
    var d1 = parseFloat(document.getElementById('days1').value);
    if (!isNaN(d1) && d1 >= 0 && d1 <= 365) {
      document.getElementById('days2').value = 365 - d1;
    }
    checkDaysWarning();
  }

  function syncDaysReverse() {
    var d2 = parseFloat(document.getElementById('days2').value);
    if (!isNaN(d2) && d2 >= 0 && d2 <= 365) {
      document.getElementById('days1').value = 365 - d2;
    }
    checkDaysWarning();
  }

  function checkDaysWarning() {
    var d1 = parseFloat(document.getElementById('days1').value) || 0;
    var d2 = parseFloat(document.getElementById('days2').value) || 0;
    var warn = document.getElementById('days-warning');
    warn.style.display = (d1 + d2 !== 365 && d1 > 0 && d2 > 0) ? 'block' : 'none';
  }

  function calculate() {
    var income1 = parseFloat(document.getElementById('income1').value) || 0;
    var income2 = parseFloat(document.getElementById('income2').value) || 0;
    var nChildren = parseInt(document.getElementById('numChildren').value);
    var days1 = parseFloat(document.getElementById('days1').value) || 0;
    var days2 = parseFloat(document.getElementById('days2').value) || 0;

    var resultEl = document.getElementById('result');

    if (income1 <= 0 && income2 <= 0) {
      resultEl.style.display = 'block';
      resultEl.innerHTML = '<p style="color:#b00;margin:0;">Please enter at least one parent\'s income.</p>';
      return;
    }
    if (days1 <= 0 && days2 <= 0) {
      resultEl.style.display = 'block';
      resultEl.innerHTML = '<p style="color:#b00;margin:0;">Please enter the number of days for at least one parent.</p>';
      return;
    }

    // If only one side entered, infer the other
    if (days1 > 0 && days2 <= 0) days2 = 365 - days1;
    if (days2 > 0 && days1 <= 0) days1 = 365 - days2;

    var combined = income1 + income2;
    var basicObligation = getBasicObligation(combined, nChildren);

    var share1 = combined > 0 ? income1 / combined : 0.5;
    var share2 = combined > 0 ? income2 / combined : 0.5;

    var isShared = days1 >= 91 && days2 >= 91;

    var html = '';

    if (isShared) {
      // Shared custody (Schedule B): both parents have ≥ 91 days
      var sharedNeed = basicObligation * 1.4;
      var custPct1 = days1 / 365;
      var custPct2 = days2 / 365;

      // Each parent's obligation accounts for the time the OTHER parent has the child
      var ob1 = share1 * sharedNeed * custPct2;
      var ob2 = share2 * sharedNeed * custPct1;

      var net = Math.abs(ob1 - ob2);
      var payorLabel = ob1 > ob2 ? 'Parent 1 pays Parent 2' : 'Parent 2 pays Parent 1';

      html += '<span class="custody-badge badge-shared">Shared Custody — Schedule B</span>';
      html += '<div class="result-headline">' + fmt(net) + ' / month</div>';
      html += '<div class="result-sub">' + payorLabel + '</div>';
      html += '<table class="result-table">';
      html += '<tr><td>Combined gross monthly income</td><td>' + fmt(combined) + '</td></tr>';
      html += '<tr><td>Basic guideline obligation (' + nChildren + ' child' + (nChildren > 1 ? 'ren' : '') + ')</td><td>' + fmt(basicObligation) + '</td></tr>';
      html += '<tr><td>Shared custody adjustment (× 1.4)</td><td>' + fmt(sharedNeed) + '</td></tr>';
      html += '<tr><td>Parent 1 income share</td><td>' + pct(share1) + '</td></tr>';
      html += '<tr><td>Parent 2 income share</td><td>' + pct(share2) + '</td></tr>';
      html += '<tr><td>Parent 1 custody time (' + days1 + ' days)</td><td>' + pct(custPct1) + '</td></tr>';
      html += '<tr><td>Parent 2 custody time (' + days2 + ' days)</td><td>' + pct(custPct2) + '</td></tr>';
      html += '<tr><td>Parent 1 gross obligation</td><td>' + fmt(ob1) + '</td></tr>';
      html += '<tr><td>Parent 2 gross obligation</td><td>' + fmt(ob2) + '</td></tr>';
      html += '<tr><td><strong>Net monthly support</strong></td><td><strong>' + fmt(net) + '</strong></td></tr>';
      html += '</table>';
    } else {
      // Primary custody (Schedule A): one parent has < 91 days
      var custodialParent = days1 >= days2 ? 1 : 2;
      var noncustodialShare = custodialParent === 1 ? share2 : share1;
      var noncustodialDays = custodialParent === 1 ? days2 : days1;
      var noncustodialLabel = 'Parent ' + (custodialParent === 1 ? '2' : '1') + ' pays Parent ' + custodialParent;

      var support = basicObligation * noncustodialShare;

      html += '<span class="custody-badge badge-primary">Primary Custody — Schedule A</span>';
      html += '<div class="result-headline">' + fmt(support) + ' / month</div>';
      html += '<div class="result-sub">' + noncustodialLabel + '</div>';
      html += '<table class="result-table">';
      html += '<tr><td>Combined gross monthly income</td><td>' + fmt(combined) + '</td></tr>';
      html += '<tr><td>Basic guideline obligation (' + nChildren + ' child' + (nChildren > 1 ? 'ren' : '') + ')</td><td>' + fmt(basicObligation) + '</td></tr>';
      html += '<tr><td>Parent 1 income share</td><td>' + pct(share1) + '</td></tr>';
      html += '<tr><td>Parent 2 income share</td><td>' + pct(share2) + '</td></tr>';
      html += '<tr><td>Custodial parent</td><td>Parent ' + custodialParent + ' (' + (custodialParent === 1 ? days1 : days2) + ' days)</td></tr>';
      html += '<tr><td>Noncustodial parent days</td><td>' + noncustodialDays + ' days/year</td></tr>';
      html += '<tr><td><strong>Monthly support obligation</strong></td><td><strong>' + fmt(support) + '</strong></td></tr>';
      html += '</table>';
    }

    resultEl.style.display = 'block';
    resultEl.innerHTML = html;
  }

  // ── Spousal Support Calculator ──────────────────────────────────────────────

  function calculateSpousalSupport() {
    var income1 = parseFloat(document.getElementById('ss-income1').value) || 0;
    var income2 = parseFloat(document.getElementById('ss-income2').value) || 0;
    var marriageYears = parseFloat(document.getElementById('ss-marriage-years').value);

    var resultEl = document.getElementById('ss-result');

    if (income1 <= 0 && income2 <= 0) {
      resultEl.style.display = 'block';
      resultEl.innerHTML = '<p style="color:#b00;margin:0;">Please enter at least one spouse\'s income.</p>';
      return;
    }

    if (income1 === income2) {
      resultEl.style.display = 'block';
      resultEl.innerHTML = '<div class="result-headline">$0 / month</div><div class="result-sub">Incomes are equal — no support indicated by this formula.</div>';
      return;
    }

    // Identify payor (higher earner) and payee (lower earner)
    var payorIncome = Math.max(income1, income2);
    var payeeIncome = Math.min(income1, income2);
    var payorLabel = income1 > income2 ? 'Spouse 1' : 'Spouse 2';
    var payeeLabel = income1 > income2 ? 'Spouse 2' : 'Spouse 1';

    // Fairfax formula: 28% of payor's gross − 58% of payee's gross
    var support = (payorIncome * 0.28) - (payeeIncome * 0.58);

    var html = '';

    if (support <= 0) {
      html += '<div class="result-headline">$0 / month</div>';
      html += '<div class="result-sub">The formula produces no support obligation at these income levels.</div>';
      html += '<table class="result-table">';
      html += '<tr><td>' + payorLabel + ' gross monthly income (payor)</td><td>' + fmt(payorIncome) + '</td></tr>';
      html += '<tr><td>' + payeeLabel + ' gross monthly income (payee)</td><td>' + fmt(payeeIncome) + '</td></tr>';
      html += '<tr><td>28% of payor income</td><td>' + fmt(payorIncome * 0.28) + '</td></tr>';
      html += '<tr><td>58% of payee income</td><td>' + fmt(payeeIncome * 0.58) + '</td></tr>';
      html += '<tr><td><strong>Estimated monthly support</strong></td><td><strong>$0</strong></td></tr>';
      html += '</table>';
    } else {
      html += '<div class="result-headline">' + fmt(support) + ' / month</div>';
      html += '<div class="result-sub">' + payorLabel + ' pays ' + payeeLabel + '</div>';
      html += '<table class="result-table">';
      html += '<tr><td>' + payorLabel + ' gross monthly income (payor)</td><td>' + fmt(payorIncome) + '</td></tr>';
      html += '<tr><td>' + payeeLabel + ' gross monthly income (payee)</td><td>' + fmt(payeeIncome) + '</td></tr>';
      html += '<tr><td>28% of payor income</td><td>' + fmt(payorIncome * 0.28) + '</td></tr>';
      html += '<tr><td>58% of payee income</td><td>' + fmt(payeeIncome * 0.58) + '</td></tr>';
      html += '<tr><td><strong>Estimated monthly support</strong></td><td><strong>' + fmt(support) + '</strong></td></tr>';

      // Duration estimate if marriage length provided
      if (!isNaN(marriageYears) && marriageYears > 0) {
        var durationText;
        if (marriageYears < 5) {
          var low = Math.max(1, Math.round(marriageYears * 0.4));
          var high = Math.max(2, Math.round(marriageYears * 0.6));
          durationText = low + '–' + high + ' years (short-term marriage)';
        } else if (marriageYears < 10) {
          var low = Math.round(marriageYears * 0.35);
          var high = Math.round(marriageYears * 0.5);
          durationText = low + '–' + high + ' years';
        } else if (marriageYears < 20) {
          var low = Math.round(marriageYears * 0.4);
          var high = Math.round(marriageYears * 0.6);
          durationText = low + '–' + high + ' years';
        } else {
          durationText = 'Potentially indefinite (20+ year marriage)';
        }
        html += '<tr><td>Marriage length</td><td>' + marriageYears + ' years</td></tr>';
        html += '<tr><td>Estimated duration range</td><td>' + durationText + '</td></tr>';
      }

      html += '</table>';
    }

    resultEl.style.display = 'block';
    resultEl.innerHTML = html;
  }
</script>
