<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Certificate Verification</title>
  <style>
    :root{--blue:#0b63a8;--muted:#666}
    body{font-family:system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;margin:0;background:#f3f6fb;color:#111}
    .wrap{max-width:820px;margin:28px auto;padding:20px}
    .card{background:#fff;border-radius:12px;box-shadow:0 8px 24px rgba(13,40,60,0.08);overflow:hidden}
    header{background:linear-gradient(90deg,var(--blue),#0a83c9);color:#fff;padding:18px 20px;display:flex;align-items:center;justify-content:space-between}
    header h1{font-size:18px;margin:0}
    .body{padding:24px}
    .row{display:flex;gap:16px;flex-wrap:wrap}
    .col{flex:1;min-width:220px}
    dt{color:var(--muted);font-size:13px;margin-top:12px}
    dd{margin:4px 0 0;font-weight:600}
    .amount{font-size:20px;color:var(--blue);font-weight:700;margin-top:8px}
    .words{color:var(--muted);margin-top:6px}
    .qrwrap{display:flex;align-items:center;gap:16px;margin-top:18px}
    .qrwrap img{width:110px;height:110px;background:#fff;padding:8px;border-radius:8px}
    .verified{display:inline-block;background:#e6f7ee;color:#0a6f37;padding:6px 10px;border-radius:999px;font-weight:700}
    .controls{display:flex;gap:8px;align-items:center;margin-top:16px}
    .btn{background:var(--blue);color:#fff;padding:10px 12px;border-radius:8px;text-decoration:none;display:inline-block}
    .mutebtn{background:#f1f5f8;color:#0a3450;padding:10px 12px;border-radius:8px;text-decoration:none}
    .searchbox{display:flex;gap:8px;margin-bottom:12px}
    input[type="text"]{flex:1;padding:10px;border-radius:8px;border:1px solid #e0e6ef}
    footer{padding:16px 20px;background:#fbfdff;border-top:1px solid #eef5fb;color:var(--muted);font-size:13px}
    @media(print){.controls,.searchbox,header,footer{display:none}body{background:white} .wrap{box-shadow:none}}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="card" id="card">
      <header>
        <h1>Document Verification Portal</h1>
        <div id="headerRight"><span id="statusBadge" class="verified" style="display:none">Verified</span></div>
      </header>

      <div class="body">
        <div class="searchbox">
          <input id="searchInput" type="text" placeholder="Enter certificate ID (e.g. CERT001) or account number" />
          <a class="btn" id="searchBtn">Verify</a>
          <a class="mutebtn" id="printBtn">Print</a>
        </div>

        <div id="notFoundMsg" style="display:none;color:#b00020;margin-bottom:14px">Certificate not found.</div>

        <section id="certificate" style="display:none">
          <div class="row">
            <div class="col">
              <dl>
                <dt>Certificate / Account</dt><dd id="acct">—</dd>
                <dt>Account Type</dt><dd id="acctType">—</dd>
                <dt>NRC/Passport</dt><dd id="nid">—</dd>
                <dt>Address</dt><dd id="addr">—</dd>
              </dl>
            </div>
            <div class="col">
              <dl>
                <dt>Issuing Branch</dt><dd id="branch">—</dd>
                <dt>Issuing Date</dt><dd id="issueDate">—</dd>
                <dt>Date of Balance</dt><dd id="balDate">—</dd>
              </dl>
            </div>
          </div>

          <div style="margin-top:18px;border-top:1px dashed #eef5fb;padding-top:16px">
            <div class="amount" id="amount">—</div>
            <div class="words" id="amountWords">—</div>

            <div class="qrwrap">
              <img id="qrImg" alt="QR code"/>
              <div>
                <div style="font-weight:700" id="holderName">—</div>
                <div style="color:var(--muted);margin-top:6px">Valid until <span id="validUntil">—</span></div>
                <div class="controls">
                  <a id="openLink" class="mutebtn" target="_blank">Open link</a>
                  <a id="downloadBtn" class="btn">Download PDF</a>
                </div>
              </div>
            </div>
          </div>
        </section>
      </div>

      <footer>
        This is a verification page. If you suspect tampering, contact the issuer.
      </footer>
    </div>
  </div>

  <script>
    // ====== Example data: Add your certificates here ======
    const certificates = {
      "CERT001": {
        id:"CERT001",
        account:"32451132400218601",
        acctType:"Call Deposit Account",
        nid:"14/AHMANA(N)088212",
        addr:"No(1149)B, Sayar Thein Street (1)QTR, Hmawbi Yangon",
        branch:"Hmawbi Branch (324)",
        issueDate:"03 Sep 2025",
        balDate:"03 Sep 2025",
        amount:"106,510,000.00 MMK",
        amountWords:"Kyats One Hundred Six Million Five Hundred Ten Thousand Only",
        holderName:"Ahmana (Example)",
        validUntil:"02 Dec 2025",
        sourceUrl:"https://qrscan.example.com/?id=CERT001"
      },

      // add more entries below:
      "CERT002": {
        id:"CERT002",
        account:"1234567890",
        acctType:"Savings",
        nid:"12/XXXXX00001",
        addr:"Yangon, Myanmar",
        branch:"Example Branch",
        issueDate:"01 Jan 2025",
        balDate:"01 Jan 2025",
        amount:"5,000,000.00 MMK",
        amountWords:"Kyats Five Million Only",
        holderName:"Zwe Htet",
        validUntil:"01 Jul 2025",
        sourceUrl:"https://qrscan.example.com/?id=CERT002"
      }
    };

    // ====== Utility ======
    function $(id){return document.getElementById(id)}
    function getParam(name){
      const p = new URLSearchParams(location.search);
      return p.get(name)
    }

    function showCertificate(data){
      $('certificate').style.display = 'block';
      $('notFoundMsg').style.display = 'none';
      $('acct').textContent = data.account || "—";
      $('acctType').textContent = data.acctType || "—";
      $('nid').textContent = data.nid || "—";
      $('addr').textContent = data.addr || "—";
      $('branch').textContent = data.branch || "—";
      $('issueDate').textContent = data.issueDate || "—";
      $('balDate').textContent = data.balDate || "—";
      $('amount').textContent = data.amount || "—";
      $('amountWords').textContent = data.amountWords || "—";
      $('holderName').textContent = data.holderName || "—";
      $('validUntil').textContent = data.validUntil || "—";
      // QR image via Google Charts API (replace with your preferred generator if you wish)
      const link = data.sourceUrl || location.href;
      const qrUrl = encodeURI('https://chart.googleapis.com/chart?cht=qr&chs=300x300&chl=' + link);
      $('qrImg').src = qrUrl;
      $('openLink').href = link;
      $('statusBadge').style.display = 'inline-block';
    }

    function showNotFound(){
      $('certificate').style.display = 'none';
      $('notFoundMsg').style.display = 'block';
      $('statusBadge').style.display = 'none';
    }

    function lookup(id){
      if(!id) return null;
      id = id.toString().trim().toUpperCase();
      // try direct id lookup
      if(certificates[id]) return certificates[id];
      // try by account number
      for(const k in certificates){
        if(certificates[k].account && certificates[k].account.replace(/\s/g,'') === id.replace(/\s/g,'')) return certificates[k];
      }
      return null;
    }

    // event handlers
    $('searchBtn').addEventListener('click', ()=>{
      const q = $('searchInput').value.trim();
      if(!q){ alert('Enter certificate ID or account number'); return; }
      const found = lookup(q);
      if(found) {
        // update URL without reload
        history.replaceState(null,'', '?id=' + encodeURIComponent(found.id));
        showCertificate(found);
      } else showNotFound();
    });

    $('printBtn').addEventListener('click', ()=> window.print());
    $('downloadBtn').addEventListener('click', ()=> {
      // simple PDF download using print-to-PDF (opens print dialog)
      window.print();
    });

    // on load: check URL param
    window.addEventListener('DOMContentLoaded', ()=>{
      const id = getParam('id');
      if(id){
        const found = lookup(id);
        if(found) showCertificate(found);
        else showNotFound();
        $('searchInput').value = id;
      }
    });
  </script>
</body>
</html>
