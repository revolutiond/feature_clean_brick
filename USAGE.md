# Quick Start Guide

## Install

```bash
# BrickHub
mason add feature_clean

# Or from Git source
mason add feature_clean \
  --git-url https://github.com/revolutiond/feature_clean_brick.git \
  --git-ref v1.0.0
```

## Generate

```bash
mason make feature_clean
```

### Example session

```text
$ mason make feature_clean
? What is your app package name? (e.g. my_app) my_app
? What is the feature name? user_profile
? What is the entity name? UserProfile
? Use BLoC instead of Cubit? (y/N) N
? Which architecture profile do you need? full_stack
? Which presentation profile fits best? paged_list
? Which CRUD operations do you need? (comma separated) list,detail,create,update,delete
? Include remote data source (Retrofit/Dio)? (Y/n) y
? Include local cache data source? (Y/n) y
```

## After generation

1. Run codegen:

```bash
dart run build_runner build --delete-conflicting-outputs
```

2. Update generated datasource/repository methods for your project APIs.
3. Register the generated page in your routes.
4. Add unit/widget tests.

## Important note

This brick is designed for Flutter apps using `flutter_dcore` base types and conventions.
