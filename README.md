# AutoCommerce
"AutoCommerce automates your e-commerce stores with workflow automation, multi-store sync, and real-time analytics. Save time, increase sales, and put your online business on autopilot."
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AutoCommerce - E-commerce Automation</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <script src="https://js.stripe.com/v3/"></script>
  <style>
    body { font-family: 'Inter', sans-serif; margin:0; padding:0; color:#333; line-height:1.6; }
    a { text-decoration:none; color:inherit; }
    header { background:#1E3A8A; color:#fff; padding:20px 0; text-align:center; }
    header h1 { margin:0; font-size:2.5rem; }
    header p { margin:10px 0 0; font-size:1.2rem; }
    .btn { display:inline-block; background:#FACC15; color:#1E3A8A; padding:12px 24px; margin:10px 0; border-radius:8px; font-weight:600; transition:0.3s; cursor:pointer; }
    .btn:hover { background:#FFD43B; }
    section { padding:60px 20px; max-width:1200px; margin:0 auto; }
    h2 { text-align:center; font-size:2rem; margin-bottom:40px; }
    .features, .pricing, .testimonials { display:grid; gap:20px; grid-template-columns:repeat(auto-fit, minmax(280px, 1fr)); }
    .card { background:#f9f9f9; padding:20px; border-radius:12px; box-shadow:0 2px 10px rgba(0,0,0,0.05); text-align:center; }
    footer { background:#111827; color:#fff; text-align:center; padding:20px 0; }
    form { display:flex; flex-direction:column; align-items:center; gap:10px; }
    input[type=email] { padding:12px; border-radius:8px; border:1px solid #ccc; width:100%; max-width:300px; }
    @media(max-width:600px){ header h1{font-size:2rem;} header p{font-size:1rem;} }
  </style>
</head>
<body>

<!-- Header / Hero -->
<header>
  <h1>AutoCommerce</h1>
  <p>Put Your E-commerce Store on Autopilot</p>
  <button class="btn" id="startTrialBtn">Start Free Trial</button>
</header>

<!-- Features -->
<section id="features">
  <h2>Powerful Automation Features</h2>
  <div class="features">
    <div class="card">
      <h3>Workflow Automation</h3>
      <p>Automate repetitive store tasks and save hours every week.</p>
    </div>
    <div class="card">
      <h3>Multi-Store Sync</h3>
      <p>Manage multiple e-commerce stores from one dashboard seamlessly.</p>
    </div>
    <div class="card">
      <h3>Pre-Built Templates</h3>
      <p>Choose from ready-made automations for Shopify, Etsy, and Amazon.</p>
    </div>
    <div class="card">
      <h3>Analytics Dashboard</h3>
      <p>Track performance and monitor all automated workflows in real-time.</p>
    </div>
  </div>
</section>

<!-- Pricing & Signup -->
<section id="pricing">
  <h2>Pricing Plans</h2>
  <div class="pricing">
    <div class="card">
      <h3>Starter</h3>
      <p><strong>$29/month</strong></p>
      <p>Perfect for small stores starting automation.</p>
      <button class="btn" onclick="startCheckout('price_1StarterID')">Start Free Trial</button>
    </div>
    <div class="card">
      <h3>Pro</h3>
      <p><strong>$99/month</strong></p>
      <p>Advanced automations for growing stores.</p>
      <button class="btn" onclick="startCheckout('price_1ProID')">Start Free Trial</button>
    </div>
    <div class="card">
      <h3>Business</h3>
      <p><strong>$299/month</strong></p>
      <p>Multi-store sync and agency-level automation.</p>
      <button class="btn" onclick="startCheckout('price_1BusinessID')">Start Free Trial</button>
    </div>
  </div>
</section>

<!-- Email Capture -->
<section id="email-capture">
  <h2>Join the Waitlist / Free Trial</h2>
  <form id="emailForm">
    <input type="email" id="emailInput" placeholder="Enter your email" required>
    <button type="submit" class="btn">Get Started</button>
  </form>
  <p id="emailMsg" style="text-align:center; color:green; margin-top:10px;"></p>
</section>

<!-- Testimonials -->
<section id="testimonials">
  <h2>What Our Users Say</h2>
  <div class="testimonials">
    <div class="card">
      <p>“AutoCommerce cut our store management time in half! Incredible tool.”</p>
      <strong>- Sarah L., Shopify Store Owner</strong>
    </div>
    <div class="card">
      <p>“The multi-store sync feature is a game-changer for our growing business.”</p>
      <strong>- Mark T., E-commerce Consultant</strong>
    </div>
    <div class="card">
      <p>“We saw immediate ROI after automating workflows with AutoCommerce.”</p>
      <strong>- Emily R., Etsy Seller</strong>
    </div>
  </div>
</section>

<!-- Footer -->
<footer>
  <p>© 2025 AutoCommerce. All rights reserved.</p>
</footer>

<script>
  // Stripe Checkout Integration
  const stripe = Stripe('pk_test_YOUR_PUBLIC_KEY'); // Replace with your Stripe public key

  function startCheckout(priceId) {
    stripe.redirectToCheckout({
      lineItems: [{ price: priceId, quantity: 1 }],
      mode: 'subscription',
      successUrl: window.location.href + '?success=true',
      cancelUrl: window.location.href + '?canceled=true'
    }).then(function (result) {
      if (result.error) {
        alert(result.error.message);
      }
    });
  }

  // Email Capture
  const form = document.getElementById('emailForm');
  const msg = document.getElementById('emailMsg');

  form.addEventListener('submit', function(e){
    e.preventDefault();
    const email = document.getElementById('emailInput').value;
    // You can replace this with a backend endpoint like Mailchimp, Sendgrid, or Firebase
    console.log('Captured email:', email);
    msg.textContent = "Thanks! We’ll notify you about your trial.";
    form.reset();
  });

  // Hero CTA button scroll
  document.getElementById('startTrialBtn').addEventListener('click', () => {
    document.getElementById('pricing').scrollIntoView({behavior: "smooth"});
  });
</script>

</body>
</html>
