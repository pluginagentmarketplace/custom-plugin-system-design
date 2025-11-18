---
name: mobile-platforms
description: Master mobile development platforms including Android, iOS, React Native, Flutter, and Swift. Use when building native or cross-platform mobile applications.
---

# Mobile Development Platforms

## Quick Start

### Android with Kotlin
```kotlin
@Composable
fun UserScreen(userId: String) {
    val userState by viewModel.user.collectAsState()

    Column(modifier = Modifier.fillMaxSize()) {
        userState?.let { user ->
            Text(user.name, style = MaterialTheme.typography.headlineMedium)
            Text(user.email)
        }
    }
}

// Activity
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            MyTheme {
                UserScreen("123")
            }
        }
    }
}
```

### iOS with SwiftUI
```swift
struct UserView: View {
    @StateObject var viewModel = UserViewModel()
    @State var user: User?

    var body: some View {
        VStack {
            if let user = user {
                Text(user.name)
                    .font(.title)
                Text(user.email)
            }
        }
        .onAppear {
            Task {
                user = await viewModel.fetchUser("123")
            }
        }
    }
}

@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            UserView()
        }
    }
}
```

### React Native
```javascript
import React, { useState, useEffect } from 'react';
import { View, Text, StyleSheet, ActivityIndicator } from 'react-native';

const UserScreen = ({ userId }) => {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetchUser(userId).then(setUser).finally(() => setLoading(false));
  }, [userId]);

  if (loading) return <ActivityIndicator />;

  return (
    <View style={styles.container}>
      <Text style={styles.name}>{user?.name}</Text>
      <Text>{user?.email}</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: { flex: 1, padding: 20 },
  name: { fontSize: 24, fontWeight: 'bold' }
});

export default UserScreen;
```

### Flutter with Dart
```dart
class UserScreen extends StatefulWidget {
  final String userId;

  const UserScreen({Key? key, required this.userId}) : super(key: key);

  @override
  State<UserScreen> createState() => _UserScreenState();
}

class _UserScreenState extends State<UserScreen> {
  late Future<User> _userFuture;

  @override
  void initState() {
    super.initState();
    _userFuture = fetchUser(widget.userId);
  }

  @override
  Widget build(BuildContext context) {
    return FutureBuilder<User>(
      future: _userFuture,
      builder: (context, snapshot) {
        if (snapshot.hasData) {
          return Column(
            children: [
              Text(snapshot.data!.name, style: TextStyle(fontSize: 24)),
              Text(snapshot.data!.email),
            ],
          );
        }
        return CircularProgressIndicator();
      },
    );
  }
}
```

## Native Development

### Android (Kotlin + Jetpack)
- **Jetpack Compose**: Modern declarative UI
- **Lifecycle**: Activity, Fragment lifecycle management
- **ViewModel**: UI-related data management
- **LiveData/StateFlow**: Observable data holders
- **Room**: Local database library
- **Retrofit**: HTTP client
- **Dagger Hilt**: Dependency injection
- **Navigation**: Fragment-based navigation

### iOS (Swift + SwiftUI)
- **SwiftUI**: Modern declarative UI framework
- **Combine**: Reactive programming framework
- **Async/Await**: Modern concurrency
- **Core Data**: Object-relational database
- **URLSession**: Networking API
- **UserDefaults**: Key-value storage
- **CloudKit**: iCloud integration
- **WidgetKit**: Home screen widgets

## Cross-Platform Development

### React Native
- **Components**: View, Text, ScrollView, FlatList
- **Navigation**: React Navigation (Stacks, Tabs, Drawers)
- **State Management**: Redux, Context API, Zustand
- **Native Modules**: Bridge for native code
- **Expo**: Managed React Native platform
- **Testing**: Jest, Detox, Appium
- **Performance**: Bridge optimization, native modules

### Flutter
- **Widgets**: Stateless, Stateful widgets
- **Material & Cupertino**: Design systems
- **Navigation**: Named routes, GoRouter
- **State Management**: Provider, Riverpod, GetX, BLoC
- **Packages**: pub.dev ecosystem
- **Platform Channels**: Native code integration
- **Performance**: Just-in-time and ahead-of-time compilation

## UI/UX Patterns

### Common Patterns
```kotlin
// Android - MVVM with LiveData
class UserViewModel : ViewModel() {
    private val _user = MutableLiveData<User>()
    val user: LiveData<User> = _user

    fun loadUser(id: String) {
        viewModelScope.launch {
            _user.value = repository.getUser(id)
        }
    }
}
```

```swift
// iOS - MVVM with Combine
class UserViewModel: ObservableObject {
    @Published var user: User?

    func loadUser(_ id: String) {
        Task {
            user = await repository.getUser(id)
        }
    }
}
```

## Mobile-Specific Features

### Networking
- Offline-first architecture
- Caching strategies
- Request/response interceptors
- Certificate pinning
- Network optimization

### Data Persistence
- Local databases (Room, Core Data, SQLite)
- Key-value storage (SharedPreferences, UserDefaults)
- File storage
- Encryption

### Platform Integration
- Camera and photo library
- Contacts and calendar
- Location services
- Push notifications
- Deep linking
- Share intents

## Performance Optimization

### Android
- Minimize bridge calls (React Native)
- Use ProGuard/R8 minification
- App startup optimization
- Memory profiling (Profiler tool)
- Battery and network optimization

### iOS
- View complexity reduction
- Lazy loading images
- Memory management
- Profiling with Instruments
- Battery usage optimization

## Testing

### Unit Testing
- JUnit, Kotest (Android)
- XCTest (iOS)
- Dart Test (Flutter)

### UI Testing
- Espresso (Android)
- XCUITest (iOS)
- Patrol (Flutter)
- Detox (React Native)

### Integration Testing
- End-to-end app flows
- Network mocking
- Database testing

## Resources

- **Android Docs**: https://developer.android.com/
- **iOS Docs**: https://developer.apple.com/documentation/
- **React Native Docs**: https://reactnative.dev/
- **Flutter Docs**: https://flutter.dev/
- **Jetpack Compose**: https://developer.android.com/jetpack/compose
- **SwiftUI Tutorials**: https://developer.apple.com/tutorials/swiftui

---

**See Also**: frontend-technologies, system-design
