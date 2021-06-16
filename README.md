# EbayPriceRegex
Contains a Regex for finding the Prices as they appear in the HTML Source of an Ebay search.

For example, search on Ebay:
`curl curl https://www.ebay.com/sch/i.html?_nkw=GTX+970+4GB -o some.html` 

Then `egrep >[$][+-]?[0-9]{1,3}(?:,?[0-9]{3})*\.[0-9]{2}<  some.html`
