# budget-tracker

## Table of Contents

- [About](#about)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Code Sample](#code-sample)
- [Acknowledgement](#acknowledgement)
- [Contributing](#contributing)
- [License](#license)

## About <a name = "about"></a>

Budget Tracker is a website app utilizing a NOSQL database, PWA, and service worker for offline functionality. It is a website that allows the user to track and follow their income and expenses.

## Getting Started <a name = "getting-started"></a>

* [Git Hub Pull](https://github.com/nicoguarino/budget-tracker.git)
* [Deployed Website](https://guarded-mountain-60579.herokuapp.com/)

## Installation <a name = "installation"></a>

No installation needed 

## Code Sample <a name = "code-sample"></a>

![Sample Code](https://github.com/nicoguarino/budget-tracker/blob/main/images/sample_code.PNG?raw=true "Sample Code")

### Sample Code
```JavaScript Sample
let db;

const request = indexedDB.open('budget_tracker', 1);

request.onupgradeneeded = function (event) {

    const db = event.target.result;

    db.createObjectStore('new_transaction', { autoIncrement: true });
};
 
request.onsuccess = function (event) {

    db = event.target.result;


    if (navigator.onLine) {
        uploadTransaction();
    }
};

request.onerror = function (event) {

    console.log(event.target.errorCode);
};

function saveRecord(record) {
 
    const transaction = db.transaction(['new_transaction'], 'readwrite');

    
    const transactionObjectStore = transaction.objectStore('new_transaction');


    transactionObjectStore.add(record);
```
```CSS Sample
body {
  font-size: 120%;
  font-family: Arial;
}

button, input {
  font-size: 100%;
  font-family: Arial;
}

table {
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}
```
```HTML
  <div class="wrapper">
    <div class="total">
      <div class="total">Your total is: $<span id="total">0</span></div>
    </div>

    <div class="form">
      <input type="text" id="t-name" placeholder="Name of transaction" />
      <input type="number" min="0" id="t-amount" placeholder="Transaction amount" />
      <button id="add-btn"><i class="fa fa-plus buttons"></i> Add Funds</button>
      <button id="sub-btn"><i class="fa fa-minus"></i> Subtract Funds</button>
      <p class="error"></p>
    </div>

    <div class="transactions">
      <table>
        <thead>
          <th>Transaction</th>
          <th>Amount</th>
        </thead>
        <tbody id="tbody">

        </tbody>
      </table>
    </div>
```

## Authors and acknowledgement <a name = "acknowledgement"></a>

Nico (Filipu) Guarino
Budget Tracker Team


## Contributing <a name = "contributing"></a>

Budget Tracker is open for contrubiting, however check with the creator first before making any permanent changes. The creator is opening to creative ideas and tweeking of design, but it must be approved first.

## License <a name = "license">

(c) 2021 Budget Tracker