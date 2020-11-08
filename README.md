# Calculate Total Cost Price

Runtime versions:

* node v12.18.0
* npm 6.14.4

## Library function signature:

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

## Dependency Installation:

    $ cd <working_directory>
    $ npm install
    
## Running Tests from the command line

    $ npm test
    
## Building the library

    $ npm run clean build
    
## Building library distribution

    $ npm run bundle
