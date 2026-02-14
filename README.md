# Star Eater
Star Eater is a multiplayer survival game built with Flutter and the Flame/Forge2D engine. Players grow by collecting star dust, avoid procedurally spawning enemies, and engage with live opponents whose state syncs through Firebase Firestore rooms.

## Key features
- **Fast physics gameplay** using Forge2D, with adaptive enemy spawning, power-ups, and a glassy HUD.
- **Realtime multiplayer** powered by `rooms/{code}/players` documents in Firestore. Each client writes its position/mass and listens for remote players via `MultiplayerManager`.
- **Dynamic theming** via a theme manager so the UI matches the expressive “cosmic” aesthetic.

## Setup
1. Install Flutter and ensure the Android toolchain is configured (`flutter doctor`).
2. Run `flutter pub get`.
3. Build `flutter build apk --release` (or use `flutter run` for debug).
4. Firebase uses the `acffcs` project (`lib/firebase_options.dart`), so make sure your Firestore rules let the client write to `rooms/$roomId` and `rooms/$roomId/players/$playerId`.

## Notes
- The app initializes Firebase in `lib/main.dart` before showing the splash/menu flows.
- Multiplayer rules: each player generates a `uuid`, writes their state every 250 ms, and stops when Firebase reports their document missing.
