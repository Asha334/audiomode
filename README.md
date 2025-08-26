import 'package:flutter/material.dart';

void main() => runApp(MaterialApp(home: AudioModeApp()));

class AudioModeApp extends StatefulWidget {
  @override
  _AudioModeAppState createState() => _AudioModeAppState();
}

class _AudioModeAppState extends State<AudioModeApp> {
  String mode = 'NORMAL';

  final Map<String, IconData> icons = {
    'NORMAL': Icons.volume_up,
    'SILENT': Icons.volume_off,
    'VIBRATE': Icons.vibration,
  };

  final Map<String, Color> colors = {
    'NORMAL': Colors.green,
    'SILENT': Colors.red,
    'VIBRATE': Colors.orange,
  };

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Audio Mode')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(icons[mode], size: 80, color: colors[mode]),
            SizedBox(height: 10),
            Text(
              'Mode: $mode',
              style: TextStyle(fontSize: 22, color: colors[mode]),
            ),
            SizedBox(height: 20),
            Wrap(
              spacing: 10,
              children: icons.keys.map((m) => ElevatedButton.icon(
                    onPressed: () => setState(() => mode = m),
                    icon: Icon(icons[m]),
                    label: Text(m),
                    style: ElevatedButton.styleFrom(
                      backgroundColor: colors[m],
                      foregroundColor: Colors.white,
                    ),
                  )).toList(),
            ),
          ],
        ),
      ),
    );
  }
}
