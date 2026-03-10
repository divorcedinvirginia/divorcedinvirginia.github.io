---
layout: default
title: Find a Virginia Divorce Attorney
description: Search for family law attorneys near you by zip code
permalink: /find-attorney/
---

Enter your zip code to search Virginia family law attorneys in your area across multiple directories.

<div class="attorney-search-box">
  <div class="search-row">
    <input type="text" id="zip-input" placeholder="Enter zip code" maxlength="5" pattern="[0-9]{5}" inputmode="numeric">
    <button onclick="searchAttorneys()">Search</button>
  </div>
  <p class="search-note">Opens results in the directory of your choice.</p>
</div>

<div class="directory-links" id="directory-links" style="display:none;">
  <h3>Search results near <span id="zip-display"></span></h3>
  <ul>
    <li>
      <a id="link-avvo" href="#" target="_blank" rel="noopener">
        <strong>Avvo</strong> — Attorney profiles with client reviews and disciplinary history
      </a>
    </li>
    <li>
      <a id="link-findlaw" href="#" target="_blank" rel="noopener">
        <strong>FindLaw</strong> — Directory with peer and client ratings
      </a>
    </li>
    <li>
      <a id="link-superlawyers" href="#" target="_blank" rel="noopener">
        <strong>Super Lawyers</strong> — Attorneys selected through peer nomination and review
      </a>
    </li>
    <li>
      <a id="link-vsb" href="#" target="_blank" rel="noopener">
        <strong>Virginia State Bar</strong> — Official VSB member directory to verify licensing and check disciplinary records
      </a>
    </li>
  </ul>
</div>

---

## What to Look for When Using These Directories

Attorney directories are a starting point, not a final answer. A listing in any directory — including a high rating — reflects what that directory measures, which varies significantly. Here is how to use them effectively:

**Use the VSB directory to verify, not discover.** The Virginia State Bar member search is the authoritative source for confirming that an attorney is licensed in Virginia and checking whether they have any public disciplinary history. Always verify an attorney's VSB status before hiring, regardless of how you found them.

**Ratings reflect different things.** Avvo ratings are algorithm-based and factor in years of experience, disciplinary records, and professional activity. Super Lawyers selections are based on peer nominations and independent research. No rating system is a guarantee of quality or fit for your specific situation.

**Read the reviews critically.** Client reviews on attorney directories can be useful for understanding communication style and client experience, but they are self-selected and unverified. A pattern of reviews describing the same specific issue — poor communication, unexpected billing, missed deadlines — is more meaningful than any individual review.

**Proximity matters.** In Virginia, family law is administered circuit by circuit, and local court knowledge is genuinely valuable. An attorney who regularly appears in your county's circuit court knows the judges, the local rules, and the informal norms that affect outcomes. Prioritize attorneys who practice in the jurisdiction where your case will be filed.

**Consult at least two attorneys.** Most charge for initial consultations ($150–$300). The difference in how two attorneys assess your case, discuss your options, and communicate with you tells you far more than any directory listing.

For more guidance on selecting an attorney, see our full page on [Legal Representation](/legal-representation/).

<style>
  .attorney-search-box {
    background: #f5f5f5;
    border-left: 3px solid #333;
    padding: 1.25rem 1.5rem;
    margin: 1.5rem 0;
  }
  .search-row {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-bottom: 0.5rem;
  }
  .search-row input {
    flex: 1;
    min-width: 160px;
    max-width: 220px;
    padding: 0.5rem 0.75rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 3px;
    color: #222;
  }
  .search-row button {
    padding: 0.5rem 1.25rem;
    font-size: 1rem;
    background: #333;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
    white-space: nowrap;
  }
  .search-row button:hover {
    background: #555;
  }
  .search-note {
    margin: 0;
    font-size: 0.82rem;
    color: #777;
  }
  .directory-links {
    margin-top: 1.5rem;
  }
  .directory-links h3 {
    margin-bottom: 0.75rem;
  }
  .directory-links ul {
    list-style: none;
    padding: 0;
  }
  .directory-links ul li {
    margin-bottom: 0.75rem;
    padding-bottom: 0.75rem;
    border-bottom: 1px solid #eee;
  }
  .directory-links ul li:last-child {
    border-bottom: none;
  }
  .directory-links a {
    text-decoration: none;
    color: #222;
    display: block;
  }
  .directory-links a:hover {
    color: #555;
  }
  .directory-links a strong {
    display: block;
    margin-bottom: 0.15rem;
    color: #333;
  }
</style>

<script>
  function searchAttorneys() {
    var zip = document.getElementById('zip-input').value.trim();
    if (!/^\d{5}$/.test(zip)) {
      alert('Please enter a valid 5-digit zip code.');
      return;
    }

    document.getElementById('zip-display').textContent = zip;

    document.getElementById('link-avvo').href =
      'https://www.avvo.com/find-a-lawyer';

    document.getElementById('link-findlaw').href =
      `https://lawyers.findlaw.com/family-law/virginia/?keyword=Family+Law&location=${zip}%2C+USA&stype=BY_ADDR_OR_ZIP`

    document.getElementById('link-superlawyers').href =
      `https://www.superlawyers.com/virginia?zip=${zip}`

    document.getElementById('link-vsb').href =
      'https://vsb.org/Site/Shared_Content/Directory/va-lawyer-directory.aspx?zip=' + zip;

    document.getElementById('directory-links').style.display = 'block';
    document.getElementById('directory-links').scrollIntoView({ behavior: 'smooth', block: 'start' });
  }

  document.getElementById('zip-input').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') searchAttorneys();
  });
</script>
