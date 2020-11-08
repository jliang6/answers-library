# Original Insructions

## Instructions

1. Please solve the following problem using the language your interviewer asked you to use, either `JavaScript` or `Java`. 
1. We are looking for clean, well factored code in order to start a conversation with you. 
1. Treat this problem as a library. No UI or file/console input is expected or required.
1. Provide a full suite of unit tests.
1. Add a `README.md` file that at least includes:
    - runtime versions
    - how to install any dependencies
    - how to run your tests from the command line
1. Clone this repo, and create a feature branch to work on.
1. Please commit your work regularly as you go, so we can see how you work through a problem.
1. Create a [Merge Request](https://docs.gitlab.com/ee/gitlab-basics/add-merge-request.html) into the `master` branch from your branch when you are ready for us to review your solution.


## Pricing Problem

We have a network of vendors who re-sell our products. We wish to provide them an application to calculate the total cost of an order.

The app needs to give volume discounts and include sales tax.

Another system will accept input from the user, and will call this component with 3 inputs:

* number of items
* price per item
* 2-letter province/state code

The application should output the total price.

The total price is calculated by:

* calculate the total cost for the items
* deduct discount based on the quantity
* add sales tax based on the province/state code

The following tables give the discount rate and tax rates:

| Order Value | Discount Rate |
| ------------- |-------------:|
| $1,000        | 3% |
| $5,000        | 5% |
| $7,000        | 7% |
| $10,000       | 10% |

| Province | Tax Rate |
| ------------- |-------------:|
| AB | 5% |
| ON | 13% |
| QC | 14.975% |
| MI | 6% |
| DE | 0% |


### Example 1:

    Input:  500 items, $1 per item, Ontario
    Output: $565.00

### Example 2:

    Input:  3600 items, $2.25 per item, Michigan
    Output: $7984.98

# Development Instruction

## Calculate Total Cost Price

Runtime versions:

* node v12.18.0
* npm 6.14.4

### Library function signature:

There are two variations within this library.

    
The first variation takes 3 input formal parameters as follows:

    calTotalPrice(numItems: number | string, pricePerItem: number | string, provinceStateCode: string) : number
    
numItems = number of items in zero or positive integer (number or string typed)
pricePerItem = Price per item (Unit price) in zero or positive floating number (number or string typed)
provinceStateCode = 
1. Province in Postal and ISO 3166-2:CA abbreviation or Full Province name for Canada
2. Or State in ISO-3166-2:US abbreviation or Full State name

If illegal argument(s) is/are passed into this function,

    IllegalArgumentException
    
will be thrown with invalid values.

The second variation takes a single JSON of type

    interface CalTotalPriceInput {
      numItems: number | string;
      pricePerItem: number | string;
      provinceStateCode: string;
    }
    
as input formal parameters.  Function signature as follows:

    calTotalPriceByInput(calTotalPriceInput: CalTotalPriceInput) : number
    
Similarly, IllegalArgumentException will be thrown when invalid values are passed into this function.

### Dependency Installation:

    $ cd <working_directory>
    $ npm install
    
### Running Tests from the command line

    $ npm test
    
### Building the library

    $ npm run clean build
    
### Building library distribution

    $ npm run bundle
