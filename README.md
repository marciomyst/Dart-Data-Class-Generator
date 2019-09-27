# Dart Data Class Generator (Beta)

Create dart data classes easily, fast and without writing boilerplate or running code generation.  

## Features

The generator can generate the constructor, copyWidth, toMap, fromMap, toJson, fromJson, toString, value equality and hashCode methods from a class based on class properties or raw JSON.

## Create data classes based on class properties

![](assets/gif_from_class.gif)

### **How?**

You can generate data classes either by the quick fix dialog or by running a command. In the quick fix dialog you have the option to not only generate whole data classes but also only specific methods. The command has the advantage of being able to generate multiple classes at the same time and also giving you error messages if there are errors in your class that make it impossible for the generator to work.

#### **Quick fix**

- Create a class with properties.
- Place your cursor on the first line of the class where it is declared.
- Hit **CTRL + .** to open the quick fix dialog.
- Choose one of the available options.

#### **Command**

- Create a class with properties.
- Hit **CTRL + P** to open the command dialog.
- Search for **Dart Data Class Generator: Generate from class properties** and hit enter.
- When there are multiple classes in the current file, choose the ones you'd like to create data classes of in the dialog.

It is also possible to run the generator on an existing data class (e.g. when some parameters changed). The generator will then try 
to find the changes and replace the class with its updated version. **Note that custom changes will be overriden**.

**Note:**  
**Class properties must be declared before the constructor in order for the generator to detect them.**  
**If the class is a Widget (Stateless or Stateful) or abstract, only the constructor will be generated. State classes wont be detected.**  

## Create data classes based on JSON (beta)

![](assets/gif_from_json.gif)

### **How?**

- Create an **empty dart** file.
- Paste the **raw JSON** into the otherwise empty file.
- Hit **CTRL + P** to open the command dialog.
- Search for **Dart Data Class Generator: Generate from JSON** and hit enter.
- Type in a class name in the input dialog. This will be the name of the **top level class**, all other class names will be infered.
- When there are nested objects in the JSON, a dialog will be appear if you want to seperate the classes into multiple files or if all classes should be in the same file.

**Note:**  
**This feature is still in beta!**  
**Many API's return numbers like 0 or 1 as an integer and not as a double even when they otherwise are. Thus the generator may confuse a value that is usually a double as an int.**  

## Settings

You can customize the generator to only generate the functions you want in your settings file.

* `dart_data_class_generator.quick_fixes`: If true, enables quick fixes to quickly generate data classes or specific methods only.
* `dart_data_class_generator.fromMap.default_values`: If true, checks if a field is null when deserializing and provides a non-null default value.
* `dart_data_class_generator.constructor.default_values`: If true, generates default values for the constructor.
* `dart_data_class_generator.constructor.required`: If true, generates @required annotation for every constructor parameter. Note: The generator wont generate default values for the constructor if enabled!
* `dart_data_class_generator.json.seperate`: Whether to seperate a JSON into multiple files, when the JSON contains nested objects. ask: choose manually every time, seperate: always seperate into multiple files, current_file: always insert all classes into the current file.
* `dart_data_class_generator.override.manual`: If true, asks, when overriding a class (running the command on an existing class), for every single function/constructor that needs to be changed whether the generator should override the function or not. This allows you to preserve custom changes you made to the function/constructor that would be otherwise overwritten by the generator.
* `dart_data_class_generator.constructor`: If true, generates a constructor for a data class.
* `dart_data_class_generator.copyWith`: If true, generates a copyWith function for a data class.
* `dart_data_class_generator.toMap`: If true, generates a toMap function for a data class.
* `dart_data_class_generator.fromMap`: If true, generates a fromMap function for a data class.
* `dart_data_class_generator.toJson`: If true, generates a toJson function for a data class.
* `dart_data_class_generator.fromJson`: If true, generates a fromJson function for a data class.
* `dart_data_class_generator.toString`: If true, generates a toString function for a data class.
* `dart_data_class_generator.equality`: If true, generates a value equality function for a data class.
* `dart_data_class_generator.hashCode`: If true, generates a hashCode function for a data class.
* `dart_data_class_generator.hashCode.use_jenkins`: If true, uses the Jenkins SMI hash function instead of bitwise operator from dart:ui.

## Release Notes

### 0.1.0
Initial release (Beta).

### 0.2.0
Added support for @required annotation.  
Changed the default hashCode implementation to bitwise operator.

## 0.3.0
Added quick fixes