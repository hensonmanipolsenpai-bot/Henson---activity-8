# Henson---activity-8

import 'package:flutter/material.dart';

void main() {
  runApp(const CalmMindApp());
}

class CalmMindApp extends StatelessWidget {
  const CalmMindApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'CalmMind Activity 08',
      theme: ThemeData(
        brightness: Brightness.dark,
        scaffoldBackgroundColor: const Color(0xFF869240), // Your Signature Olive
        primaryColor: Colors.black,
        textTheme: const TextTheme(
          displayLarge: TextStyle(fontSize: 42, fontWeight: FontWeight.w900, color: Colors.black),
          bodyLarge: TextStyle(fontSize: 15, fontWeight: FontWeight.w600, color: Colors.black87, height: 1.6),
        ),
      ),
      initialRoute: '/',
      routes: {
        '/': (context) => const SplashScreen(),
        '/home': (context) => const HomeScreen(),
        '/menu': (context) => const MenuScreen(),
        '/objectives': (context) => const ContentPage(
              title: "Objectives:",
              body: "1. To develop a mobile application that provides users with a library of ambient sounds and guided meditations for stress relief and relaxation.\n\n"
                  "2. To create a user-friendly interface that allows easy browsing and playback of audio content based on mood or activity (e.g., sleep, focus, anxiety relief).\n\n"
                  "3. To implement a timer feature that automatically stops playback after a set duration to preserve battery and enhance user experience.\n\n"
                  "4. To offer a personalized experience by allowing users to create and save their favorite playlists of sounds and meditations.\n\n"
                  "5. To promote mental wellness by making relaxation tools accessible anytime, anywhere, directly from a user's mobile device.",
            ),
        '/scope': (context) => const ContentPage(
              title: "Scope:",
              body: "1. The system will focus on delivering audio-based content only (ambient sounds and guided meditations).\n"
                  "2. It will cater to individuals seeking relaxation, better sleep, focus, or stress management.\n"
                  "3. The application will include features such as audio libraries, playlist creation, a sleep timer, and offline download capability for premium users.\n"
                  "4. The initial release will support Android and iOS platforms.\n\n"
                  "Limitations:\n"
                  "1. The application does not provide professional mental health counseling or therapy; it is strictly for relaxation and wellness purposes only.\n"
                  "2. It cannot generate personalized meditations based on user biometric data (e.g., heart rate).\n"
                  "3. The app requires a stable internet connection for streaming content, unless users have downloaded tracks.\n"
                  "4. It does not include video content or visual guided exercises; it is audio-only.\n"
                  "5. The free version will contain limited content and advertisements.",
            ),
        '/features': (context) => const ContentPage(
              title: "Features & Functions:",
              body: "1. Audio Library: Provides a categorized collection of ambient sounds (rain, ocean, forest, white noise) and guided meditations (stress relief, sleep, gratitude, focus).\n\n"
                  "2. Playlist Creation: Allows users to create and save custom playlists combining their favorite tracks.\n\n"
                  "3. Sleep Timer: Lets users set a timer to automatically stop playback after a chosen duration (15, 30, 60 minutes).\n\n"
                  "4. Offline Mode: Enables premium users to download content and listen without an internet connection.\n\n"
                  "5. Mood-Based Recommendations: Suggests content based on user-selected moods or activities (e.g., \"I need to sleep,\" \"I feel anxious\").",
            ),
        '/problem': (context) => const ContentPage(
              title: "Problem:",
              body: "In today's fast-paced world, many people experience high levels of stress, anxiety, and difficulty sleeping due to work pressure, academic demands, or personal issues.\n\n"
                  "While professional therapy is effective, it is often expensive, inaccessible, or stigmatized. People frequently turn to unhealthy coping mechanisms or simply suffer in silence.\n\n"
                  "Additionally, finding quality relaxation content online is overwhelming, with users having to jump between different apps, websites, or YouTube channels.\n\n"
                  "There is a clear need for a simple, accessible, and dedicated mobile tool that provides high-quality relaxation audio to help users manage their mental well-being anytime, anywhere.",
              showSolutionLink: true,
            ),
        '/solution2': (context) => const ContentPage(
              title: "Solutions:",
              body: "Solution Description: The proposed solution is CalmMind, a mobile application that serves as a personal relaxation companion. It offers a curated library of ambient nature sounds and professionally recorded guided meditations designed to reduce stress, improve sleep, and enhance focus.\n\n"
                  "How it Addresses the Problem: CalmMind puts mental wellness tools directly into the user's pocket. Instead of searching scattered sources, users have a single app with organized, high-quality audio. The sleep timer helps users fall asleep without worrying about battery drain. Offline downloads ensure help is available even without internet.",
            ),
      },
    );
  }
}

// --- Frame 1: Splash Screen ---
class SplashScreen extends StatelessWidget {
  const SplashScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Icon(Icons.music_note, size: 100, color: Colors.black),
            Text('CalmMind', style: Theme.of(context).textTheme.displayLarge),
            const SizedBox(height: 60),
            _pillButton(context, "Start", Icons.play_arrow, () => Navigator.pushNamed(context, '/home')),
          ],
        ),
      ),
    );
  }
}

// --- Frame 2: Home Screen ---
class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Column(
          children: [
            Expanded(
              child: SingleChildScrollView(
                padding: const EdgeInsets.all(24),
                child: Column(
                  children: [
                    const Text('CalmMind', style: TextStyle(fontSize: 48, fontWeight: FontWeight.w900, color: Colors.black)),
                    const SizedBox(height: 20),
                    Row(
                      mainAxisAlignment: MainAxisAlignment.spaceBetween,
                      children: [
                        _smallPill(context, "Back", Icons.chevron_left, () => Navigator.pop(context)),
                        _smallPill(context, "Start", Icons.play_arrow, () => Navigator.pushNamed(context, '/menu')),
                      ],
                    ),
                    const SizedBox(height: 30),
                    const Align(alignment: Alignment.centerLeft, child: Text('Recently played', style: TextStyle(fontSize: 24, fontWeight: FontWeight.w900, color: Colors.black))),
                    const SizedBox(height: 15),
                    GridView.count(
                      shrinkWrap: true,
                      physics: const NeverScrollableScrollPhysics(),
                      crossAxisCount: 2,
                      mainAxisSpacing: 12,
                      crossAxisSpacing: 12,
                      childAspectRatio: 2.2,
                      children: [
                        _musicTile("You broke me first", Colors.red[900]!),
                        _musicTile("Justice", Colors.teal[900]!),
                        _musicTile("BTS", Colors.indigo[900]!),
                        _musicTile("Midnight Rain", Colors.blueGrey[900]!),
                      ],
                    ),
                  ],
                ),
              ),
            ),
            _footerGradient(),
          ],
        ),
      ),
    );
  }

  Widget _footerGradient() {
    return Container(
      height: 150,
      width: double.infinity,
      decoration: const BoxDecoration(
        gradient: LinearGradient(
          begin: Alignment.topCenter,
          end: Alignment.bottomCenter,
          colors: [Color(0xFF869240), Color(0xFFD4E17F)],
        ),
      ),
    );
  }
}

// --- Frame 3: Menu Screen ---
class MenuScreen extends StatelessWidget {
  const MenuScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.symmetric(horizontal: 40),
          child: Column(
            children: [
              const SizedBox(height: 40),
              const Text('CalmMind', style: TextStyle(fontSize: 42, fontWeight: FontWeight.w900, color: Colors.black)),
              const SizedBox(height: 30),
              _menuBtn(context, "Objectives", '/objectives'),
              _menuBtn(context, "Scope & limitations", '/scope'),
              _menuBtn(context, "Features & Functions", '/features'),
              _menuBtn(context, "Problems and Solutions", '/problem'),
              const Spacer(),
              _smallPill(context, "Back to home", Icons.home, () => Navigator.pop(context)),
              const SizedBox(height: 20),
            ],
          ),
        ),
      ),
    );
  }

  Widget _menuBtn(BuildContext context, String title, String route) {
    return Padding(
      padding: const EdgeInsets.only(bottom: 12),
      child: Material(
        color: Colors.black,
        borderRadius: BorderRadius.circular(12),
        elevation: 4,
        child: InkWell(
          borderRadius: BorderRadius.circular(12),
          onTap: () => Navigator.pushNamed(context, route),
          child: Container(
            width: double.infinity,
            padding: const EdgeInsets.all(18),
            child: Text(title, textAlign: TextAlign.center, style: const TextStyle(color: Colors.white, fontWeight: FontWeight.bold, fontSize: 16)),
          ),
        ),
      ),
    );
  }
}

// --- Shared Content Page (Usability Improved) ---
class ContentPage extends StatelessWidget {
  final String title;
  final String body;
  final bool showSolutionLink;

  const ContentPage({super.key, required this.title, required this.body, this.showSolutionLink = false});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Padding(
          padding: const EdgeInsets.all(24),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              _smallPill(context, "Back", Icons.chevron_left, () => Navigator.pop(context)),
              const SizedBox(height: 25),
              Text(title, style: const TextStyle(fontSize: 34, fontWeight: FontWeight.w900, color: Colors.black)),
              const SizedBox(height: 20),
              Expanded(
                child: Container(
                  width: double.infinity,
                  padding: const EdgeInsets.all(20),
                  decoration: BoxDecoration(
                    // Using .withValues to prevent precision loss warnings
                    color: Colors.white.withValues(alpha: 0.15), 
                    borderRadius: BorderRadius.circular(20),
                    border: Border.all(color: Colors.white.withValues(alpha: 0.2)),
                  ),
                  child: SingleChildScrollView(
                    child: Text(body, style: Theme.of(context).textTheme.bodyLarge),
                  ),
                ),
              ),
              if (showSolutionLink)
                Align(
                  alignment: Alignment.bottomRight,
                  child: TextButton(
                    onPressed: () => Navigator.pushNamed(context, '/solution2'),
                    child: const Text("Solution ➔", style: TextStyle(fontSize: 34, fontWeight: FontWeight.w900, color: Colors.black)),
                  ),
                ),
            ],
          ),
        ),
      ),
    );
  }
}

// --- Reusable Components ---
Widget _pillButton(BuildContext context, String label, IconData icon, VoidCallback onTap) {
  return Material(
    color: Colors.black,
    borderRadius: BorderRadius.circular(30),
    child: InkWell(
      borderRadius: BorderRadius.circular(30),
      onTap: onTap,
      child: Container(
        padding: const EdgeInsets.symmetric(horizontal: 24, vertical: 12),
        child: Row(mainAxisSize: MainAxisSize.min, children: [Icon(icon, color: Colors.white), const SizedBox(width: 8), Text(label, style: const TextStyle(color: Colors.white, fontWeight: FontWeight.bold))]),
      ),
    ),
  );
}

Widget _smallPill(BuildContext context, String label, IconData icon, VoidCallback onTap) {
  return Material(
    color: Colors.black,
    borderRadius: BorderRadius.circular(20),
    child: InkWell(
      borderRadius: BorderRadius.circular(20),
      onTap: onTap,
      child: Container(
        padding: const EdgeInsets.symmetric(horizontal: 14, vertical: 8),
        child: Row(mainAxisSize: MainAxisSize.min, children: [Icon(icon, size: 14, color: Colors.white), const SizedBox(width: 4), Text(label, style: const TextStyle(color: Colors.white, fontSize: 12, fontWeight: FontWeight.bold))]),
      ),
    ),
  );
}

Widget _musicTile(String title, Color color) {
  return Container(
    decoration: BoxDecoration(
      color: const Color(0xFF1E1E1E),
      borderRadius: BorderRadius.circular(10),
      boxShadow: [BoxShadow(color: Colors.black.withValues(alpha: 0.2), blurRadius: 4, offset: const Offset(0, 2))],
    ),
    child: Row(
      children: [
        Container(width: 45, decoration: BoxDecoration(color: color, borderRadius: const BorderRadius.only(topLeft: Radius.circular(10), bottomLeft: Radius.circular(10)))),
        const SizedBox(width: 10),
        Expanded(child: Text(title, style: const TextStyle(fontSize: 10, fontWeight: FontWeight.w800, color: Colors.white))),
      ],
    ),
  );
}
