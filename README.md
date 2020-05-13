# Drip

Drip generates IDs, pretty much. It’s capable of handling requests asking for thousands of unique IDs in less than 10ms.

Its principle is simple:

1. get the character codes of the first three letters of an origin;
2. generate random numbers if the codes aren’t long enough (23 chars as of 13/05/2020);
3. use the _last_ 3 characters of character codes that are too long; and
4. concatenate all three character codes along with a UNIX nano timestamp.

This ensures that all IDs will be:

* unique every time (unless the same origin is used at the _exact_ same nanosecond; and
* sortable and identifiable with ease.

The first 9 digits will _always_ be the origin’s character codes and possibly some random numbers. The remainder will be a UNIX nano timestamp.
