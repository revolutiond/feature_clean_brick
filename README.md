# feature_clean

A Mason brick for generating Clean Architecture feature modules for Flutter projects using `flutter_dcore` conventions.

## Features

- Clean Architecture module scaffolding (`data`, `domain`, `presentation`)
- Flatter feature layout under `lib/src/<feature_name>/`
- Configurable architecture profile (`presentation_only`, `domain_presentation`, `full_stack`)
- Configurable presentation profile (`paged_list`, `single_item`, `blank_screen`)
- Selective CRUD use case generation
- Optional remote/local datasource generation
- Cubit or BLoC state management
- Functional error handling with `TaskEither`

## Project Links

- Repository: https://github.com/revolutiond/feature_clean_brick
- Issue tracker: https://github.com/revolutiond/feature_clean_brick/issues
- Documentation: https://github.com/revolutiond/feature_clean_brick#readme

## Prerequisites

- Flutter app already set up with `flutter_dcore`
- Mason CLI installed

```bash
dart pub global activate mason_cli
```

## Installation

### From BrickHub

```bash
mason add feature_clean
```

### From Git

```bash
mason add feature_clean \
  --git-url https://github.com/revolutiond/feature_clean_brick.git \
  --git-ref v1.0.0
```

## Usage

```bash
mason make feature_clean
```

You will be prompted for:

1. `app_package_name`: root Dart package name (for example: `my_app`)
2. `feature_name`: feature name in snake_case (for example: `user_profile`)
3. `entity_name`: main entity name in PascalCase (for example: `UserProfile`)
4. `use_bloc`: use BLoC instead of Cubit
5. `architecture_profile`: `presentation_only`, `domain_presentation`, `full_stack`
6. `presentation_profile`: `paged_list`, `single_item`, `blank_screen`
7. `crud_operations`: comma-separated list (for example: `list,detail,create,update,delete`)
8. `include_remote_datasource`: include Retrofit/Dio datasource
9. `include_local_cache`: include local cache datasource

## Example

```bash
$ mason make feature_clean
? What is your app package name? (e.g. my_app) my_app
? What is the feature name? user_profile
? What is the entity name? UserProfile
? Use BLoC instead of Cubit? false
? Which architecture profile do you need? full_stack
? Which presentation profile fits best? paged_list
? Which CRUD operations do you need? (comma separated) list,detail,create,update,delete
? Include remote data source (Retrofit/Dio)? (Y/n) y
? Include local cache data source? (Y/n) y
```

Generated hub import uses your input package:

```dart
import 'package:my_app/my_app.dart';
```

## Post-generation

1. Run code generation:

```bash
dart run build_runner build --delete-conflicting-outputs
```

2. Update generated API/data source implementations for your backend.
3. Wire navigation/routes to the generated page.
4. Add tests under `test/unit/<feature>/`.

## License

Apache-2.0. See `LICENSE`.
