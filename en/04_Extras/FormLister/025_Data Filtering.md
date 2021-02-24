## Data filtering
Filtering means form data preprocessing according to given rules. 
Rules list is an array, where the key is field name, and the value is an array of filters. Filter is a method of filterer class, which gets the value and returns it transformed.
```
{
    "field 1": ["trim", "alpha"]
    "field 2": ["trim", "email"]
}
```

The default filterer class (\FormLister\Filters) contains the following filters:

- trim: removes whitespace and other predefined characters from both sides of a string;
- ltrim: removes whitespace and other predefined characters from the left of a string;
- rtrim: removes whitespace and other predefined characters from the right of a string;
- alpha: removes everything but letters;
- numeric: removes everything but digits;
- alphaNumeric: removes everything but letters and digits;
- removeExtraSpaces: removes extra whitespaces and line breaks;
- compressText: removes extra whitespaces but preserves line breaks;
- stripTags: removes html tags;
- lcfirst: converts the first character to the lowercase;
- ucfirst: converts the first character to the uppercase;
- ucwords: converts the first character of every word to the uppercase
- upper: converts all characters to the uppercase;
- lower: converts all characters to the lowercase;
- phone: remove all charactes not allowed to be used in phone numbers;
- url: remove all charactes not allowed to be used in urls;
- email: remove all charactes not allowed to be used in email addreses;
- int: remove all charactes not allowed to be used in integer numbers;
- float: remove all charactes not allowed to be used in floating point numbers;
- castInt: converts value to the integer number;
- castFloat: converts value to the floating point number.
