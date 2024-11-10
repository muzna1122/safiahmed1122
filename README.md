// Scroll animations
const elements = document.querySelectorAll('.property-card, #mortgage-form, #contact-form');
window.addEventListener('scroll', () => {
  elements.forEach(element => {
    const position = element.getBoundingClientRect().top;
    const windowHeight = window.innerHeight;
    if (position < windowHeight - 100) {
      element.classList.add('show');
    }
  });
});

// Mortgage Calculator
function calculateMortgage() {
  const loanAmount = parseFloat(document.getElementById('loanAmount').value);
  const interestRate = parseFloat(document.getElementById('interestRate').value) / 100 / 12;
  const loanTerm = parseFloat(document.getElementById('loanTerm').value) * 12;
  const mortgageResult = document.getElementById('mortgageResult');

  if (loanAmount && interestRate && loanTerm) {
    const monthlyPayment = (loanAmount * interestRate) / (1 - Math.pow(1 + interestRate, -loanTerm));
    mortgageResult.textContent = `Estimated Monthly Payment: $${monthlyPayment.toFixed(2)}`;
  } else {
    mortgageResult.textContent = "Please enter all fields.";
  }
}

// Contact Form Submission (using EmailJS for example)
document.getElementById('contact-form').addEventListener('submit', function(event) {
  event.preventDefault();
  // Integrate with EmailJS or other email service
  alert('Message sent! Thank you for contacting us.');
});
