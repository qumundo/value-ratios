# Value Ratios
Value-based enterprise performance determination of listed and unlisted companies based on an input-based API calculation engine. The enhanced and standardized value approach developed and applied extends the commonly used Profit-and-Lost-based approach by new shareholder value-based ratios and enable comparable and precise value-based enterprise performance determination. Value-based ratios such as Value Added, Value Rate, Value Added per Share, Price-Value-Ratio and Value Performance-Ratio identify and determine value performance of self-defined companies, flexible, comparable and use-case specific.

Documentation, Examples, FAQ, Terms & Conditions and License: [https://www.qumundo.com/docs/value-ratios-api](https://www.qumundo.com/docs/value-ratios-api).

If you see a feature that is missing or not correctly enforced, please [open an issue](https://github.com/qumundo/value-ratios/issues).

_You can find example request and response schema in the JSON file here: [example.json](https://github.com/qumundo/value-ratios/blob/master/res/example.json)_

**:de: Crafted in Frankfurt am Main, Germany.**

## Last changes

Last changes and the version history can be found in the [CHANGELOG.md](https://github.com/qumundo/value-ratios/blob/master/CHANGELOG.md) file.

_As this library is SemVer-compatible, any breaking change would be released as a MAJOR version only. Non-breaking changes and features are released as MINOR. Feature updates and bug fixes are released as PATCH (note that feature updates may as well be bundled under a MINOR release, if it comes with new settings or minor changes)._

## How to install?

Include `value-ratios` in your `package.json` dependencies:

```bash
npm install --save @qumundo/value-ratios
```

## How to use?

This module may be used to calculate, determine and retrieve value ratios of listed and unlisted companies. You may self-define the required input parameter to calculate current, historical, future and/or scenario-based value ratios based on your own data and assumptions.

### :link: Import the module

Import the module in your code:

`const ValueRatios = require("@qumundo/value-ratios");`

### :arrow_right: Create request schema and define input parameters

```javascript
let value_item =
{
  "id": "",
  "id_type": "",
  "legal_entity": "Company X",
  "sector": "",
  "sub_sector": "",
  "fiscal_year": 2020,
  "date": "2020-12-31",
  "currency": "EUR",
  "balance_sheet": {
    "non_current_liabilities": 83175000000,
    "deferred_tax_liabilities": 509000000,
    "other_current_financial_liabilities": 38986000000,
    "equity": 61520000000
  },
  "balance_sheet_prev": {
    "non_current_liabilities": 85502000000,
    "deferred_tax_liabilities": 632000000,
    "other_current_financial_liabilities": 46093000000,
    "equity": 59907000000
  },
  "finance_income": 116000000,
  "finance_costs": 458000000,
  "income_tax_expense_continuing_operations": 1365000000,
  "profit_loss": 3857000000,
  "wacc": 0.033013,
  "wacc_equity": null,
  "weighted_average_shares": 658862400,
  "share_price": 72.33
}
```

### :arrow_right: Get value ratios for created schema and defined input parameters

```javascript

let value_request = { data: [] };

value_request.data.push(value_item);  // Up to 5 items/calculation per request

let value_ratios = await ValueRatios.getValueRatios(value_request);

/*
value_ratios.data[0] ===

{
  "success": true,
  "message": "",
  "id": "",
  "id_type": "",
  "legal_entity": "Company X",
  "fiscal_year": 2020,
  "date": "2020-12-31",
  "currency": "EUR",
  "value_added": -610124273,
  "value_added_per_share": -0.926,
  "value_rate": -0.0033,
  "price_value_ratio": -78.1079,
  "share_price_value_return": -0.0128,
  "value_rate_price_return_ratio": -0.2548,
  "value_performance_ratio": 0,
  "value_added_ebit_ratio": -0.1097,
  "value_earnings_per_share_ratio": -0.1582,
  "price_value_earnings_ratio": -6.3217
},

*/
```

### :arrow_right: Get example request schema

```javascript
let value_request = await ValueRatios.getExample(true, false);  // (request, response)
```

### :arrow_right: Get example response schema

```javascript
let value_response = await ValueRatios.getExample(false, true);  // (request, response)
```

## Need more value ratios?

Choose between various subscription options for your use case: [https://www.qumundo.com/api/value-ratios-api](https://www.qumundo.com/api/value-ratios-api).

Once subscribed and enabled, login to our platform and provide authentication along your request.

### :arrow_right: Login to our platform to receive authentication token

```javascript
let credentials = { email: config.YOUR_EMAIL, password: config.YOUR_PASSWORD };   // Keep your login credentials secure and secret

let login = await ValueRatios.getLogin(credentials);

let token = login.token;
```

### :arrow_right: Get value ratios with your subscription

```javascript
let value_ratios = await ValueRatios.getValueRatios(value_request, token);
```

_If you need additional features, changes or notice any discrepancies, feel free to submit a Pull Request._

**Consider supporting the development by [making a donation](https://github.com/sponsors/qumundo).**
