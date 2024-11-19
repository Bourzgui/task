// Function to get the directory where you can save the file
Future<String> get _localPath async {
  final directory = await getApplicationDocumentsDirectory();
  return directory.path;
}

// Function to get the file reference
Future<File> get _localFile async {
  final path = await _localPath;
  return File('$path/my_file.txt');
}

// Function to write data to the file
Future<File> writeData(String data) async {
  final file = await _localFile;

  // Write the file
  return file.writeAsString(data);
}

// Function to read data from the file
Future<String> readData() async {
  try {
    final file = await _localFile;

    // Read the file
    final contents = await file.readAsString();

    return contents;
  } catch (e) {
    // If encountering an error, return an empty string
    return '';
  }
}
