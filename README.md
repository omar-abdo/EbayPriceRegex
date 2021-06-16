# EbayPriceRegex
Contains a Regex for finding the Prices as they appear in the HTML Source of an Ebay search.

For example, search on Ebay:
`curl curl https://www.ebay.com/sch/i.html?_nkw=GTX+970+4GB -o some.html` 

Then `egrep -o >[$][+-]?[0-9]{1,3}(?:,?[0-9]{3})*\.[0-9]{2}<  some.html`:
```
>$127.25<
>$220.00<
>$133.41<
>$150.50<
>$129.99<
>$195.00<
>$128.00<
>$102.50<
>$274.99<
>$274.97<
>$125.00<
>$108.50<
>$209.95<
>$272.94<
>$246.30<
>$289.99<
>$175.00<
>$275.00<
>$260.00<
>$254.51<
>$269.99<
>$230.00<
>$279.00<
>$127.50<
>$199.99<
>$299.99<
>$118.50<
>$285.00<
>$224.99<
>$349.99<
>$284.97<
>$299.99<
>$75.00<
>$259.00<
>$299.00<
>$364.85<
>$649.99<
>$284.99<
>$249.00<
>$299.99<
>$434.99<
>$279.90<
>$249.99<
>$356.76<
>$299.99<
>$269.00<
>$230.00<
>$285.00<
>$311.99<
>$350.00<
>$350.00<
>$399.99<
>$289.89<
>$162.52<
>$211.00<
>$202.50<
>$138.50<
>$150.00<
>$132.50<
>$229.99<
>$265.00<
>$269.99<
>$662.86<
```

or with Python:
```
import re

REGEX ='>[$][+-]?[0-9]{1,3}(?:,?[0-9]{3})*\.[0-9]{2}<'
with open('Test.html') as f:
        HTML = f.read()

m = [ price[1:-1] for price in re.findall(REGEX, HTML) ]

print(m)

>>>['$127.25', '$220.00', '$133.41', '$150.50', '$129.99', '$195.00', '$128.00', '$102.50', '$274.99', '$274.97', '$125.00', '$108.50', '$209.95', '$272.94', '$246.30', '$289.99', '$175.00', '$275.00', '$260.00', '$254.51', '$269.99', '$230.00', '$279.00', '$127.50', '$199.99', '$299.99', '$118.50', '$285.00', '$224.99', '$349.99', '$284.97', '$299.99', '$75.00', '$259.00', '$299.00', '$364.85', '$649.99', '$284.99', '$249.00', '$299.99', '$434.99', '$279.90', '$249.99', '$356.76', '$299.99', '$269.00', '$230.00', '$285.00', '$311.99', '$350.00', '$350.00', '$399.99', '$289.89', '$162.52', '$211.00', '$202.50', '$138.50', '$150.00', '$132.50', '$229.99', '$265.00', '$269.99', '$662.86']```
