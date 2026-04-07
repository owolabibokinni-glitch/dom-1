# dom-1
// SELECT ALL ELEMENTS
const plusBtns = document.querySelectorAll(".plus");
const minusBtns = document.querySelectorAll(".minus");
const deleteBtns = document.querySelectorAll(".delete");
const likeBtns = document.querySelectorAll(".like");

// FUNCTION TO UPDATE TOTAL PRICE
function updateTotal() {
  let total = 0;
  const items = document.querySelectorAll(".cart-item");

  items.forEach(item => {
    const price = parseInt(item.querySelector(".item-price").textContent);
    const quantity = parseInt(item.querySelector(".quantity").textContent);

    total += price * quantity;
  });

  document.getElementById("total").textContent = total;
}

// ➕ INCREASE QUANTITY
plusBtns.forEach(btn => {
  btn.addEventListener("click", () => {
    const quantitySpan = btn.previousElementSibling;
    quantitySpan.textContent++;
    updateTotal();
  });
});

// ➖ DECREASE QUANTITY
minusBtns.forEach(btn => {
  btn.addEventListener("click", () => {
    const quantitySpan = btn.nextElementSibling;

    if (quantitySpan.textContent > 1) {
      quantitySpan.textContent--;
      updateTotal();
    }
  });
});

// ❌ DELETE ITEM
deleteBtns.forEach(btn => {
  btn.addEventListener("click", () => {
    btn.parentElement.remove();
    updateTotal();
  });
});

// ❤️ LIKE ITEM (toggle color)
likeBtns.forEach(btn => {
  btn.addEventListener("click", () => {
    btn.classList.toggle("liked");
  });
});

// INITIAL TOTAL
updateTotal();
