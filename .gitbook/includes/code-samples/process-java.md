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
SimpleField mySimpleField = fields.getSimpleField("my_simple_field");

// Showing a String field example.
// You'll need to choose one of the possible classes:
// String, Double, Boolean
String fieldValue = mySimpleField.getStringValue();
```

Accessing a list of values, where `my_list_field` is the name of the field in the Model.

We need to specify that the field is a `ListField` in order to access its `SimpleItems`.

For each item in the list, we also need to specify the correct field and value type, as described above.

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
ListField myListField = fields.getLisField("my_list_field");

List<SimpleField> myListFieldItems = myListField.getSimpleItems();

// Access a value at a given position
// You'll need to choose one of the possible classes:
// String, Double, Boolean
String fieldFirstValue = myListFieldItems.get(0).getStringValue();

// loop over all values in the list
for (SimpleField listItem : myListFieldItems) {

    // You'll need to choose one of the possible classes:
    // String, Double, Boolean
    String itemValue = listItem.getStringValue();
}
```

Accessing an object field, where `my_object_field` is the name of the field in the Model.\
In this hypothetical case, the object has a sub-field named `sub_field` .

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();
ObjectField objectField = fields.getObjectField("my_object_field");

// Useful to separate out the fields mapping for easier access
InferenceFields fieldObjectFields = objectField.getSimpleFields();

// The subfield is handled like any other SimpleField
SimpleField subField = fieldObjectFields.get("sub_field");

// Showing a String field example, other types are: String, Double, Boolean
String itemValue = subField.getStringValue();
```

Accessing a list of objects, where `my_object_list_field` is the name of the field in the Model.

```java
import com.mindee.parsing.v2.field.*;


InferenceFields fields = response.getInference().getResult().getFields();

ListField objectListField = fields.getListField("my_object_list_field");

// Useful to separate out the fields list for easier access
List<ObjectField> objectItems = fieldSimpleList.getObjectItems();

// access an object at a given position
ObjectField objectField0 = objectItems.get(0);
SimpleField subField0 = objectField0.getSimpleField("sub_field");
// Showing a String field example, other types are: String, Double, Boolean
String subField0Value = subField0.getStringValue();

// Loop over the list of Object fields
for (ObjectField itemField : objectItems) {
    // Object sub-fields will always be Simple fields
    HashMap<String, SimpleField> subFields = itemField.getSimpleFields();
    
    // grab a single sub-field
    SimpleField subfield1 = subFields.get("subfield_1");
    
    // Choose the appropriate value type accessor method:
    // String, Double, Boolean
    String subFieldValue = subfield1.getStringValue();
}
```

Depending on your requirements, this can be simplified using various custom methods.
