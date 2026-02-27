# Task-4-ShreeAgalawe
Example implementation (Arduino C++) 
Building on the sensor simulation from Task 2, here is how you can implement basic 
automation logic: 
// Define our limits 
const float TEMP_LIMIT = 30.0; 
const int FAN_PIN = 5; // Example digital pin connected to a relay/fan 
 
void setup() { 
  Serial.begin(115200); 
  pinMode(FAN_PIN, OUTPUT); 
  digitalWrite(FAN_PIN, LOW); // Ensure fan is off initially 
} 
 
void loop() { 
  // 1. Simulate reading (from previous task) 
  float currentTemp = random(200, 351) / 10.0;  
   
  Serial.print("Temp: "); 
  Serial.print(currentTemp); 
  Serial.println(" °C"); 
 
  // 2. Define Conditions & Triggers 
  if (currentTemp > TEMP_LIMIT) { 
    // Condition met: Trigger Action 
    digitalWrite(FAN_PIN, HIGH);  
     
    // 3. Display Results 
    Serial.println("ALERT: Temp threshold exceeded! Fan turned ON."); 
     
    // In a real system, you would also push an alert flag to the cloud here 
    // e.g., pushToCloud("status", "warning"); 
     
  } else { 
    // Condition normal: Ensure action is reversed/off 
    digitalWrite(FAN_PIN, LOW); 
    Serial.println("Status: Normal. Fan is OFF."); 
  } 
   
  Serial.println("-------------------------"); 
delay(5000); 
}
