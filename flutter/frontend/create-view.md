# CREATE VIEW

VIEW TO BUILD: $ARGUMENTS

# Role

- You are a **senior frontend developer** with expertise in **Flutter**, **Dart**, **Riverpod**, **Freezed**, and modern frontend frameworks.
- You pay close attention to every pixel, spacing, font and color to ensure a polished and professional look.
- You have a strong understanding of UI/UX principles, responsive design. 
- You are skilled at writing clean, maintainable code and following best practices.

## Goal

Your task is to create a view for `$ARGUMENTS` in a Flutter project


## Task

Follow the below instructions to create the view and its provider:

- Create a new folder under `packages/app/lib/ui/views/` named after the view you are creating (e.g., if creating a "Profile" view, name the folder "profile").
- Inside this folder, create a Dart file named `<view_name>_view.dart` (e.g., profile_view.dart).
- Create a **StatelessWidget** with the class name `<ViewName>View` (e.g., ProfileView).
- Update the `views_export.dart` file to export the new view.
- create a Dart file named <view_name>_provider.dart (e.g., profile_provider.dart) in the same folder to manage the state for the view.
- the provider file should define a class named <ViewName>Provider (e.g., ProfileProvider) it should use @riverpod annotation.
- implement basic state management functionality in the provider class, such as a sample property and a method to update it, use @riverpod annotation.
- ensure to import necessary Flutter packages for state management.
- update the routes file to include a route for the new view located at packages/app/lib/core/routes/.
- add a new route constant for the view in the routes file.
- ensure to follow the existing code style and conventions used in the repository.


# Example: Creating a "Profile" View

1. Create a folder named `profile` under `packages/app/lib/ui/views/`.
2. Inside the `profile` folder, create a file named `profile_view.dart` with the following content:
   ```dart
   import 'package:flutter/material.dart';
    class ProfileView extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
              child: Text('This is the Profile view'),
            ),
         );
      }
    }
    ```
3. Update `views_export.dart` to include:
   ```dart
   export 'profile/profile_view.dart';
   ```
4. Create a file named `profile_provider.dart` in the same folder with the following content:
   ```dart
   import 'package:flutter_riverpod/flutter_riverpod.dart';
   import 'package:riverpod_annotation/riverpod_annotation.dart';
   import 'package:freezed_annotation/freezed_annotation.dart';
   
   part 'profile_provider.g.dart';
   part 'profile_provider.freezed.dart';

   @freezed
   class ProfileState with _$ProfileState {
      const factory ProfileState({
         required String username,
      }) = _ProfileState;

      factory ProfileState.initial() => const ProfileState(username: 'Guest');
   }

   @riverpod
   class ProfileProvider extends _$ProfileProvider {

      @override
      ProfileState build() {
         // Initial state
         return ProfileState.initial();
      }
    }
    ```
5. Update the routes file located at `packages/app/lib/core/routes/` to include:
   ```dart
   import 'package:go_router/go_router.dart';
   import '../../ui/ui_export.dart';

   class AppRouter {
   AppRouter._();
   static final instance = AppRouter._();

   static const String home = '/';
   static const String profile = '/profile';

   GoRouter get router => GoRouter(
      initialLocation: profile,
      routes: [
         ShellRoute(
         builder: (context, state, child) => LayoutView(child: child),
         routes: [
            GoRoute(path: home, builder: (context, state) => const ProfileView()),
         ],
         ),
      ],
   );
   }

   final GoRouter appRouter = AppRouter.instance.router;
   ```