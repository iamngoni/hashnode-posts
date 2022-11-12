# Flutter (Dart) Extensions

Well, programming doesn't have to be boring and Dart goes out of its way to make sure we enjoy the experience. Dart includes multiple cool features most of which we have used or use unknowingly on a daily basis. 

Extension methods are one of the cool features that make me fall so much in love (yes in love 🤣) with the language. They make it easier for developers to add new functionality to existing code without modifying or changing the existing code directly.

## Syntax
The syntax used for creating our own extensions is fairly simple.

```dart
extension <ExtensionName> on <Type> {
    // body
}
```

> To create an extension that will only be visible within the same file it was created in you may omit the extension name or add an underscore before the extension name.

## Let's Do The Dirty Work

For practice purposes let us extend the existing List type by adding a method that splits the list into smaller lists of the specified size:

```dart
extension TestExtension<T> on List<T> {
        List<List<T>> splitList({int size = 2}) {
                List<List<T>>  sublists = [];
                
                for (int i = 0; i < length; i += size) {
                        sublists.add(this.sublist(i, (i + size) > this.length ? this.length : (i + size))).toList();
                } 

                return sublists;
        }
}
```

## Making use of the extension method

We can now use this new extension method to split any lists we have into smaller lists of our preferred size. Let's try this on a list of positive integers between 0 and 20.

```dart
List<int> ourIntegers = [2, 4, 6, 8, 10, 12, 14, 16, 18];
List<List<int>> ourSmallerLists = ourIntegers.splitList(size: 2);
print(ourSmallerLists);
```

The output:

```shell
> [[2, 4], [6, 8], [10, 12], [14, 16], [18]]
```

## API conflicts and resolution


![Tips-to-Resolve-Conflict-at-Work.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1658757510362/pueoEXGqE.jpg align="left")

There may be times were the same extension methods may be created in different files and this will result in a conflict. There's a way to go around this conflict so don't panic when faced with such a situation. Dart allows us to hide or show the extensions we don't need

```dart
import 'extension_file_1.dart';
import 'extension_file_2.dart' hide TestExtension;
```

## More resources on dart extensions

%[https://dart.dev/guides/language/extension-methods]

%[https://medium.com/dartlang/extension-methods-2d466cd8b308]

%[https://github.com/dart-lang/language/blob/master/accepted/2.7/static-extension-methods/feature-specification.md#dart-static-extension-methods-design]

%[https://github.com/dart-lang/samples/tree/master/extension_methods]

You can also check out this package with a couple of extension methods on the core types in Dart.

%[https://pub.dev/packages/handy_extensions]

