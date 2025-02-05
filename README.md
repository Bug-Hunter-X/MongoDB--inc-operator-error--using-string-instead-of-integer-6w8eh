# MongoDB $inc Operator Error
This example demonstrates an uncommon error when using the `$inc` operator in MongoDB update operations.  The error occurs when providing a string value instead of a numeric value to the `$inc` operator, leading to unexpected behavior and potential data corruption.  The solution provides the correct usage of `$inc` with a numeric value.

## Bug Report
The bug arises from incorrectly using a string value ('1') for the increment value within the `$inc` operator.  This causes the update operation to either fail silently or to set the field to the string value instead of incrementing it numerically.  This can lead to unexpected results and difficulty in debugging the issue.  The following code demonstrates the incorrect implementation:

```javascript
// Incorrect usage of $inc operator in MongoDB update
db.collection('myCollection').updateOne({fieldName: 'value'}, {$inc: {counter: '1'}});
```

## Solution
The correct usage of the `$inc` operator requires a numeric value for the increment amount.  The following code provides the correct solution:

```javascript
// Correct usage of $inc operator in MongoDB update
db.collection('myCollection').updateOne({fieldName: 'value'}, {$inc: {counter: 1}});
```
By changing the string '1' to the integer 1, the update operation works as intended, incrementing the `counter` field correctly.
