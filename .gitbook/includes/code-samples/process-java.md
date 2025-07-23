---
title: process-java
---

Accessing a simple value, where `my_simple_field` is the name of the field in the Model.

We need to access the field as a `SimpleField` instance in order to access its `value`.

We also need to specify the type of `value` , the possible types are `String` , `Boolean` , `Double` .\
Notice that these are all classes, not primitives: this is to allow `null` values.

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
SimpleField mySimpleField = fields.get("my_simple_field").getSimpleField();

// Showing a String field example.
// You'll need to choose one of the possible classes:
// String, Double, Boolean
String fieldValue = (String) mySimpleField.getValue();
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its `items`.

For each item in the list, we also need to specify the correct field and value type, as described above.

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
ListField myListField = fields.get("my_list_field").getListField();

List<DynamicField> myListFieldItems = fieldSimpleList.getItems();

// Access a value at a given position
// Showing a String field example, other types are: String, Double, Boolean
String fieldFirstValue = (String) simpleItems.get(0).getSimpleField().getValue()

// loop over all values in the list
for (DynamicField listItem : myListFieldItems) {

    // Showing a String field example, other types are: String, Double, Boolean
    String itemValue = (String) listItem.getValue();
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
ObjectField objectField = fields.get("my_object_field").getObjectField()

// Useful to separate out the fields mapping for easier access
InferenceFields fieldObjectFields = objectField.getFields();

// The subfield is handled like any other SimpleField
SimpleField subField = fieldObjectFields.get("sub_field").getSimpleField();

// Showing a String field example, other types are: String, Double, Boolean
String itemValue = (String) subField.getSimpleField().getValue();
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
ListField objectListField = fields.get("my_object_list_field").getListField();

// Useful to separate out the fields list for easier access
List<DynamicField> objectItems = fieldSimpleList.getItems();

// access an object at a given position
ObjectField objectField0 = objectItems.get(0).getObjectField();
SimpleField subField0 = objectField0.getFields().get("sub_field").getSimpleField();
// Showing a String field example, other types are: String, Double, Boolean
String subField0Value = (String) subField0.getValue();

for (DynamicField objectItem : objectItems.getItems()) {
    ObjectField objectField = objectItem.getObjectField();
    SimpleField subField = objectField.getFields().get("sub_field").getSimpleField();
    // Showing a String field example, other types are: String, Double, Boolean
    String subFieldValue = (String) subField.getValue();
}
```

Depending on your requirements, this can be simplified using various custom methods.
