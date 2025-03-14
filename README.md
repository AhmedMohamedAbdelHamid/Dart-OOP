# Dart-OOP
## Easy Problems

### Problem 1

class User {
  String name;
  String email;
  int age;

  User(this.name, this.email, this.age);

  void displayInfo() {
    print("Name: $name, Email: $email, Age: $age");
  }
}

void main() {
  final user = User("Maxy", "Maxy@gmail.com", 19);
  user.displayInfo();
}

### Problem 2
class BankAccount {
  double _balance = 0;

  void deposit(double amount) {
    if (amount > 0) {
      _balance += amount;
    }
  }

  void withdraw(double amount) {
    if (amount > 0 && amount <= _balance) {
      _balance -= amount;
    } else {
      print("Invalid withdrawal amount or insufficient funds.");
    }
  }

  double getBalance() => _balance;
}

void main() {
  final account = BankAccount();
  account.deposit(100);
  account.withdraw(50);
  print(account.getBalance()); // Output: 50.0
}

### Problem 3
import 'dart:math';

class Shape {
  double area() => 0;
}

class Circle extends Shape {
  final double radius;
  Circle(this.radius);

  @override
  double area() => pi * radius * radius;
}

class Rectangle extends Shape {
  final double length;
  final double width;
  Rectangle(this.length, this.width);

  @override
  double area() => length * width;
}

void main() {
  final circle = Circle(5);
  print("Circle area: ${circle.area().toStringAsFixed(2)}"); // ~78.54

  final rectangle = Rectangle(4, 7);
  print("Rectangle area: ${rectangle.area()}"); // 28.0
}

## Easy Scenario:

### 1. Employee Management System (Encapsulation & Getters/Setters)
class Employee {
  String name;
  String position;
  double _salary;

  Employee(this.name, this.position, double salary) {
    this.salary = salary; // Use setter to validate
  }

  double get salary => _salary;

  set salary(double value) {
    _salary = (value < 0) ? 0 : value;
  }
}

void main() {
  final emp = Employee("John", "Developer", -5000);
  print("Salary: ${emp.salary}"); // Output: 0.0
}

### 2. Library Book Tracking (Class & Object Creation)
class Book {
  String title;
  String author;
  String isbn;

  Book(this.title, this.author, this.isbn);

  void displayDetails() {
    print("Book: $title by $author (ISBN: $isbn)");
  }
}

void main() {
  final book = Book("Dart Basics", "Alice", "978-1234567890");
  book.displayDetails();
}

### 3. E-commerce Product (Constructor & Named Constructor)
class Product {
  final String name;
  final double price;
  final String category;

  Product(this.name, this.price, this.category);

  Product.discounted(String name, double originalPrice, String category, double discount)
      : this(name, originalPrice * (1 - discount / 100), category);
}

void main() {
  final discountedProduct = Product.discounted("Laptop", 1000, "Electronics", 20);
  print("Discounted Price: ${discountedProduct.price}"); // Output: 800.0
}


### 4. AI-Powered Weather App (Encapsulation & Getters/Setters)

class WeatherData {
  double _temperature;
  double humidity;
  double windSpeed;

  WeatherData(this._temperature, this.humidity, this.windSpeed);

  double get temperature => _temperature;

  set temperature(double value) {
    _temperature = (value < -273.15) ? -273.15 : value;
  }

  void displayInsights() {
    print("AI Insights:");
    print("Temperature: $_temperature°C | Humidity: $humidity% | Wind: $windSpeed km/h");
    if (_temperature > 30) {
      print("Warning: Extreme heat detected!");
    }
  }
}

void main() {
  final weather = WeatherData(35, 80, 10);
  weather.displayInsights();
}

### 5. AI Chatbot (Class & Object Creation)
class AIChatbot {
  String name;
  String language;
  double responseTime;

  AIChatbot(this.name, this.language, this.responseTime);

  String generateResponse(String userInput) {
    if (userInput.toLowerCase().contains("hello")) {
      return "Can I assist you?";
    } else {
      return "Rephrase your question.";
    }
  }
}

void main() {
  final bot = AIChatbot("ChatGPT", "English", 0.5);
  print(bot.generateResponse("Hello!"));
}

### 6. AI-Based Translator (Constructor & Named Constructor)
class Translator {
  String sourceLanguage;
  String targetLanguage;

  Translator(this.sourceLanguage, this.targetLanguage);

  Translator.detectLanguage(String text) {
    if (text.contains("hola")) {
      sourceLanguage = "Spanish";
    } else {
      sourceLanguage = "English";
    }
    targetLanguage = "English";
  }

  String translate(String text) => "[Translated to $targetLanguage] $text";
}

void main() {
  final translator = Translator.detectLanguage("hola");
  print(translator.translate("Hola mundo")); // Output: [Translated to English] Hola mundo
}

### 7. Voice Assistant (Method Overriding & Inheritance)
class VoiceAssistant {
  void listen() => print("Listening...");
  void respond(String input) => print("Base response: $input");
}

class GoogleAssistant extends VoiceAssistant {
  @override
  void respond(String input) => print("Google: Here's the info for '$input'");
}

class SiriAssistant extends VoiceAssistant {
  @override
  void respond(String input) => print("Siri: Searching for '$input'...");
}

void main() {
  final google = GoogleAssistant();
  google.respond("Weather today"); // Output: Google: Here's the info for 'Weather today'

  final siri = SiriAssistant();
  siri.respond("News updates"); // Output: Siri: Searching for 'News updates'...
}

## Medium Scenario:

### 1. Messaging App (Abstract Class & Interface)
abstract class Message {
  void send();
}

class TextMessage implements Message {
  @override
  void send() => print("Text message sent");
}

class ImageMessage implements Message {
  @override
  void send() => print("Image message sent");
}

class VideoMessage implements Message {
  @override
  void send() => print("Video message sent");
}

void main() {
  final messages = [TextMessage(), ImageMessage(), VideoMessage()];
  messages.forEach((msg) => msg.send());
}

### 2. AI-Based Personal Trainer App (Polymorphism & Inheritance)
class Workout {
  String generateRoutine() => "Generic workout routine";
}

class StrengthTraining extends Workout {
  @override
  String generateRoutine() => "AI recommends: Deadlifts, Squats, Bench Press (3 sets)";
}

class Cardio extends Workout {
  @override
  String generateRoutine() => "AI recommends: 30-minute HIIT session";
}

class Yoga extends Workout {
  @override
  String generateRoutine() => "AI recommends: Sun Salutations and Warrior Flow";
}

void main() {
  final routines = [StrengthTraining(), Cardio(), Yoga()];
  routines.forEach((r) => print(r.generateRoutine()));
}

### 3. AI-Powered Health Monitoring (Abstract Class & Interface)
abstract class HealthMonitor {
  String analyzeData();
}

class HeartRateMonitor implements HealthMonitor {
  @override
  String analyzeData() => "AI analysis: Heart rate normal (72 BPM)";
}

class SleepTracker implements HealthMonitor {
  @override
  String analyzeData() => "AI analysis: 7.5 hours of quality sleep detected";
}

void main() {
  final monitors = [HeartRateMonitor(), SleepTracker()];
  monitors.forEach((m) => print(m.analyzeData()));
}

### 4. AI-Driven Resume Scanner (Factory Constructor)
abstract class ResumeAnalyzer {
  String analyze();

  factory ResumeAnalyzer(String jobField) {
    switch (jobField) {
      case "Software":
        return SoftwareEngineerAnalyzer();
      case "Marketing":
        return MarketingAnalyzer();
      default:
        throw UnsupportedError("Job field not supported");
    }
  }
}

class SoftwareEngineerAnalyzer implements ResumeAnalyzer {
  @override
  String analyze() => "AI scanning for programming skills and frameworks...";
}

class MarketingAnalyzer implements ResumeAnalyzer {
  @override
  String analyze() => "AI scanning for SEO and campaign experience...";
}

void main() {
  final analyzer = ResumeAnalyzer("Software");
  print(analyzer.analyze());
}

### 5. Smart Home Automation (Composition & Inheritance)
class AIPredictor {
  String predictPreference() => "AI predicts user preference: ";
}

class SmartDevice {
  final AIPredictor _ai = AIPredictor();
  String get prediction => _ai.predictPreference();
}

class SmartLight extends SmartDevice {
  String activate() => "${prediction}Adjusting brightness to 75%";
}

class SmartThermostat extends SmartDevice {
  String activate() => "${prediction}Setting temperature to 22°C";
}

void main() {
  final light = SmartLight();
  print(light.activate());
}

### 6. AI-Powered Fraud Detection (Exception Handling)
class FraudDetectedException implements Exception {
  final String message;
  FraudDetectedException(this.message);
}

class TransactionValidator {
  void validate(double amount) {
    if (amount > 10000) {
      throw FraudDetectedException("AI detected suspicious transaction: \$$amount");
    }
    print("Transaction approved");
  }
}

void main() {
  final validator = TransactionValidator();
  try {
    validator.validate(15000);
  } catch (e) {
    print(e);
  }
}
