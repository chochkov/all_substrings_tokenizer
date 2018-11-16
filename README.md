## All Substrings Tokenizer

This is a PostgreSQL extension that provides functions to extract all substrings
from a given string. Currently there's a hard coded minimum limit of 3 characters per
substring.

### Usecase

The intended use case for this extension is to enable Btree indexing on
substrings.

It's also worth as an example for writing set-returning functions in C and
handling multi-byte characters.

### Installation

To use the extension, clone the repository and build it against your Postgres
server by running the following from the project directory:

```
make install
```

Then you need to `create` the extension in PostgreSQL using the following SQL:

```sql
CREATE EXTENSION all_substrings_tokenizer;
```

### Example usage:

```
SELECT token FROM all_substrings_set('1二湖楽a');

  token
----------
1二湖
1二湖楽
1二湖楽a
二湖楽
二湖楽a
湖楽a
(6 rows)
```
