## unit-openapi-node-sdk@0.1.0

This library provides a typescript wrapper to [Unit's API](https://docs.unit.co/#introduction).

## Documentation
See https://docs.unit.co/

## Installation

```bash
npm install @unit-finance/unit-openapi-node-sdk
```

## Usage

#### Create an individual application (es6)
```js
import { UnitApi } from '@unit-finance/unit-openapi-node-sdk';

const unit = new UnitApi({
    accessToken: UNIT_TOKEN,
}, UNIT_API_URL);

let createApplicationRequest = {
    type: "individualApplication",
    attributes: {
        "ssn": "000000002",
        "fullName": {
            first: "Richard",
            last: "Hendricks"
        },
        "dateOfBirth": "2001-08-10",
        "address": {
            street: "20 Ingram St",
            city: "Forest Hills",
            state: "CA",
            postalCode: "11375",
            country: "US"
        },
        "email": "april@baxter.com",
        "phone": {
            countryCode: "1",
            number: "2025550158"
        },
        "ip": "127.0.0.1",
        "ein": "123456789",
        "dba": "Pied Piper Inc",
        "soleProprietorship": true,
        "sourceOfIncome": "EmploymentOrPayrollIncome",
        "annualIncome": "Between50kAnd100k",
        "occupation": "ArchitectOrEngineer",
        "numberOfEmployees": "Between5And10",
        "businessVertical": "TechnologyMediaOrTelecom",
        "website": "https://www.piedpiper.com",
    }
}


const application = await unit.createApplication({ data: createApplicationRequest }).catch(err => {
    // handle errors
    return err
});

console.log(application)

```


#### Fetching a customer
```js
import { UnitApi } from '@unit-finance/unit-openapi-node-sdk';

const unit = new UnitApi({
    accessToken: UNIT_TOKEN,
}, UNIT_API_URL);

(async () => {
    let customer = await unit.getCustomer(customerId).catch<UnitError>(err => {
        // handle errors
        return err
    })

    console.log(customer)
})();
```