<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Credit Plan Calculator</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 20px;
      font-family: Arial, sans-serif;
      background: #f7f7f7;
      color: #111;
    }

    .container {
      max-width: 920px;
      margin: 0 auto;
      background: #fff;
      border-radius: 16px;
      padding: 24px;
      box-shadow: 0 4px 18px rgba(0, 0, 0, 0.08);
    }

    h1,
    h2 {
      text-align: center;
      margin: 0 0 20px;
    }

    h2 {
      font-size: 22px;
      margin-top: 8px;
    }

    label {
      display: block;
      font-weight: 700;
      margin-bottom: 6px;
    }

    input,
    button {
      width: 100%;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 16px;
    }

    button {
      border: none;
      cursor: pointer;
      background: #000;
      color: #fff;
    }

    button:hover {
      opacity: 0.92;
    }

    .secondary-btn {
      background: #444;
      margin-bottom: 20px;
    }

    .remove-btn {
      width: auto;
      padding: 12px 16px;
      background: #b00020;
    }

    .item-row {
      display: grid;
      grid-template-columns: 1fr auto;
      gap: 12px;
      align-items: end;
      margin-bottom: 12px;
    }

    .results {
      margin-top: 20px;
      padding: 16px;
      border-radius: 12px;
      background: #f2f2f2;
    }

    .results p {
      margin: 8px 0;
    }

    .plans-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 14px;
      margin-top: 18px;
    }

    .plan-card {
      background: #fff;
      border: 1px solid #ddd;
      border-radius: 12px;
      padding: 16px;
      text-align: center;
    }

    .plan-card h3 {
      margin: 0 0 10px;
      font-size: 20px;
    }

    .plan-monthly {
      font-size: 36px;
      font-weight: 800;
      margin: 10px 0;
      letter-spacing: 0.5px;
    }

    .plan-meta {
      font-size: 14px;
      color: #555;
      margin: 6px 0;
    }

    .not-eligible {
      opacity: 0.6;
      background: #fafafa;
    }

    .eligibility-note,
    .disclaimer {
      margin-top: 14px;
      color: #555;
      line-height: 1.5;
    }

    .disclaimer {
      font-size: 12px;
      color: #666;
      margin-top: 20px;
    }

    @media (max-width: 640px) {
      .item-row {
        grid-template-columns: 1fr;
      }

      .remove-btn {
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Credit Plan Calculator</h1>

    <h2>Items</h2>
    <div id="itemsContainer"></div>

    <button type="button" class="secondary-btn" onclick="addItem()">+ Add Item</button>

    <label for="downPayment">Down Payment ($)</label>
    <input
      type="number"
      id="downPayment"
      placeholder="Enter down payment"
      value="0"
      min="0"
      step="0.01"
    />

    <div class="results" id="results">
      <p><strong>Subtotal After Down Payment:</strong> $<span id="subtotal">0.00</span></p>
      <p><strong>Tax (13%):</strong> $<span id="tax">0.00</span></p>
      <p><strong>Total After Tax / Before Admin Fee:</strong> $<span id="afterTaxBeforeFee">0.00</span></p>

      <div id="plansContainer" class="plans-grid"></div>

      <div class="eligibility-note">
        Eligibility is based on the amount after tax and before admin fee. For unavailable plans, the calculator shows how much more needs to be added before tax to qualify.
      </div>
    </div>

    <div class="disclaimer">
      Payment estimates are for informational purposes only and may vary based on approval and provider terms.
    </div>
  </div>

  <script>
    const TAX_RATE = 0.13;

    const PLANS = [
      { months: 3, adminFee: 0.00, minSpend: 500 },
      { months: 6, adminFee: 24.99, minSpend: 500 },
      { months: 12, adminFee: 49.99, minSpend: 1000 },
      { months: 18, adminFee: 74.99, minSpend: 2000 },
      { months: 24, adminFee: 99.99, minSpend: 3000 },
      { months: 45, adminFee: 249.00, minSpend: 5000 }
    ];

    function formatMoney(value) {
      return Number(value).toFixed(2);
    }

    function updateItemLabels() {
      const rows = document.querySelectorAll('.item-row');
      rows.forEach((row, index) => {
        const label = row.querySelector('.item-label');
        label.textContent = `Item ${index + 1}`;
      });
    }

    function addItem(price = '') {
      const container = document.getElementById('itemsContainer');
      const row = document.createElement('div');
      row.className = 'item-row';

      row.innerHTML = `
        <div>
          <label class="item-label">Item</label>
          <input
            type="number"
            class="item-price"
            placeholder="Price ($)"
            min="0"
            step="0.01"
            value="${price}"
          />
        </div>
        <div>
          <button type="button" class="remove-btn">Remove</button>
        </div>
      `;

      container.appendChild(row);

      const priceInput = row.querySelector('.item-price');
      const removeButton = row.querySelector('.remove-btn');

      priceInput.addEventListener('input', calculatePayment);
      removeButton.addEventListener('click', () => removeItem(removeButton));

      updateItemLabels();
      calculatePayment();
    }

    function removeItem(button) {
      const row = button.closest('.item-row');
      if (row) {
        row.remove();
      }

      updateItemLabels();
      calculatePayment();
    }

    function getItemsTotal() {
      const prices = document.querySelectorAll('.item-price');
      let total = 0;

      prices.forEach((input) => {
        total += parseFloat(input.value) || 0;
      });

      return total;
    }

    function renderPlans(amountAfterTaxBeforeFee) {
      const plansContainer = document.getElementById('plansContainer');
      plansContainer.innerHTML = '';

      PLANS.forEach((plan) => {
        const eligible = amountAfterTaxBeforeFee >= plan.minSpend;
        const totalWithFee = amountAfterTaxBeforeFee + plan.adminFee;
        const monthlyPayment = totalWithFee / plan.months;
        const card = document.createElement('div');

        card.className = `plan-card${eligible ? '' : ' not-eligible'}`;

        if (eligible) {
          card.innerHTML = `
            <h3>${plan.months} Months</h3>
            <div class="plan-monthly">$${formatMoney(monthlyPayment)}</div>
            <div class="plan-meta">per month</div>
            <div class="plan-meta">Admin fee: $${formatMoney(plan.adminFee)}</div>
            <div class="plan-meta">Total financed: $${formatMoney(totalWithFee)}</div>
          `;
        } else {
          const additionalAfterTaxNeeded = Math.max(plan.minSpend - amountAfterTaxBeforeFee, 0);
          const additionalBeforeTaxNeeded = additionalAfterTaxNeeded / (1 + TAX_RATE);

          card.innerHTML = `
            <h3>${plan.months} Months</h3>
            <div class="plan-meta"><strong>Not eligible</strong></div>
            <div class="plan-meta">Minimum required: $${formatMoney(plan.minSpend)}</div>
            <div class="plan-meta">Current amount: $${formatMoney(amountAfterTaxBeforeFee)}</div>
            <div class="plan-meta">Add before tax: $${formatMoney(additionalBeforeTaxNeeded)}</div>
          `;
        }

        plansContainer.appendChild(card);
      });
    }

    function calculatePayment() {
      const itemsTotal = getItemsTotal();
      const downPayment = parseFloat(document.getElementById('downPayment').value) || 0;
      const subtotal = Math.max(itemsTotal - downPayment, 0);
      const tax = subtotal * TAX_RATE;
      const afterTaxBeforeFee = subtotal + tax;

      document.getElementById('subtotal').textContent = formatMoney(subtotal);
      document.getElementById('tax').textContent = formatMoney(tax);
      document.getElementById('afterTaxBeforeFee').textContent = formatMoney(afterTaxBeforeFee);

      renderPlans(afterTaxBeforeFee);
    }

    document.getElementById('downPayment').addEventListener('input', calculatePayment);

    addItem();
  </script>
</body>
</html>
