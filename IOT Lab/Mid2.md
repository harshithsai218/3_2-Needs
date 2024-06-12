# Week 6

`WriteSingleField`
```c
#define TS_ENABLE_SSL 

#include <ESP8266WiFi.h>
#include <WiFiClientSecure.h>
#include "secrets.h"
#include "ThingSpeak.h" 

char ssid[] = SECRET_SSID;   // your network SSID (name) 
char pass[] = SECRET_PASS;   // your network password
int keyIndex = 0;            // your network key Index number (needed only for WEP)
WiFiClientSecure  client;

unsigned long myChannelNumber = SECRET_CH_ID;
const char * myWriteAPIKey = SECRET_WRITE_APIKEY;

int number = 0;

const char * fingerprint = NULL; // use SECRET_SHA1_FINGERPRINT for fingerprint check

void setup() {
  Serial.begin(115200);  // Initialize serial
  while (!Serial) {
    ; 
  }
  
  WiFi.mode(WIFI_STA);

  if(fingerprint!=NULL){
    client.setFingerprint(fingerprint);
  }
  else{
    client.setInsecure(); 
  }
  
  ThingSpeak.begin(client);  // Initialize ThingSpeak
}

void loop() {

  if(WiFi.status() != WL_CONNECTED){
    Serial.print("Attempting to connect to SSID: ");
    Serial.println(SECRET_SSID);
    while(WiFi.status() != WL_CONNECTED){
      WiFi.begin(ssid, pass);  
      Serial.print(".");
      delay(5000);     
    } 
    Serial.println("\nConnected.");
  }

  int x = ThingSpeak.writeField(myChannelNumber, 1, number, myWriteAPIKey);
  if(x == 200){
    Serial.println("Channel update successful.");
  }
  else{
    Serial.println("Problem updating channel. HTTP error code " + String(x));
  }

  // change the value
  number++;
  if(number > 99){
    number = 0;
  }
  
  delay(5000); 
}

```

`secrets.h`

```c
#define SECRET_SSID "MySSID"		// replace MySSID with your WiFi network name
#define SECRET_PASS "MyPassword"	// replace MyPassword with your WiFi password

#define SECRET_CH_ID 000000			// replace 0000000 with your channel number
#define SECRET_WRITE_APIKEY "XYZ"   // replace XYZ with your channel write API Key

// ThingSpeak Certificate Fingerprint, Expiration Date: August 3, 2022 at 8:00:00 AM EST 
#define SECRET_SHA1_FINGERPRINT "27 18 92 DD A4 26 C3 07 09 B9 7A E6 C5 21 B9 5B 48 F7 16 E1"
```


# Week 7

```c

#include <ESP8266WiFi.h>
#include "secrets.h"
#include "ThingSpeak.h" // always include thingspeak header file after other header files and custom macros

char ssid[] = SECRET_SSID;   // your network SSID (name) 
char pass[] = SECRET_PASS;   // your network password
int keyIndex = 0;            // your network key Index number (needed only for WEP)
WiFiClient  client;

unsigned long myChannelNumber = SECRET_CH_ID;
const char * myWriteAPIKey = SECRET_WRITE_APIKEY;

// Initialize our values
int number1 = 0;
int number2 = random(0,100);
int number3 = random(0,100);
int number4 = random(0,100);
String myStatus = "";

void setup() {
  Serial.begin(115200);  // Initialize serial
  while (!Serial) {
    ; // wait for serial port to connect. Needed for Leonardo native USB port only
  }
  
  WiFi.mode(WIFI_STA); 
  ThingSpeak.begin(client);  // Initialize ThingSpeak
}

void loop() {

  // Connect or reconnect to WiFi
  if(WiFi.status() != WL_CONNECTED){
    Serial.print("Attempting to connect to SSID: ");
    Serial.println(SECRET_SSID);
    while(WiFi.status() != WL_CONNECTED){
      WiFi.begin(ssid, pass);  // Connect to WPA/WPA2 network. Change this line if using open or WEP network
      Serial.print(".");
      delay(5000);     
    } 
    Serial.println("\nConnected.");
  }

  // set the fields with the values
  ThingSpeak.setField(1, number1);
  ThingSpeak.setField(2, number2);
  ThingSpeak.setField(3, number3);
  ThingSpeak.setField(4, number4);

  // figure out the status message
  if(number1 > number2){
    myStatus = String("field1 is greater than field2"); 
  }
  else if(number1 < number2){
    myStatus = String("field1 is less than field2");
  }
  else{
    myStatus = String("field1 equals field2");
  }
  
  // set the status
  ThingSpeak.setStatus(myStatus);
  
  // write to the ThingSpeak channel
  int x = ThingSpeak.writeFields(myChannelNumber, myWriteAPIKey);
  if(x == 200){
    Serial.println("Channel update successful.");
  }
  else{
    Serial.println("Problem updating channel. HTTP error code " + String(x));
  }
  
  // change the values
  number1++;
  if(number1 > 99){
    number1 = 0;
  }
  number2 = random(0,100);
  number3 = random(0,100);
  number4 = random(0,100);
  
  delay(20000); // Wait 20 seconds to update the channel again
}
```

```c
#define SECRET_SSID "MySSID"		// replace MySSID with your WiFi network name
#define SECRET_PASS "MyPassword"	// replace MyPassword with your WiFi password

#define SECRET_CH_ID 000000			// replace 0000000 with your channel number
#define SECRET_WRITE_APIKEY "XYZ"   // replace XYZ with your channel write API Key
```

# Week 8

```cpp
#include "ThingSpeak.h"  // Library for connecting to ThingSpeak
#include <ESP8266WiFi.h> // Library for WiFi connectivity on ESP8266

// WiFi credentials
const char* ssid = "YOUR_SSID"; // Your WiFi network SSID
const char* password = "YOUR_PASSWORD"; // Your WiFi network password

int statusCode = 0; // Variable to store HTTP status code
WiFiClient client; // WiFi client for connecting to ThingSpeak

// ThingSpeak channel details
unsigned long counterChannelNumber = YOUR_CHANNEL_NUMBER; // Your ThingSpeak channel number
const char * counterWriteAPIKey = "YOUR_WRITE_API_KEY"; // Your ThingSpeak write API key

const int fieldNumber1 = 1; // Field number for temperature data
const int fieldNumber2 = 2; // Field number for humidity data

void setup(){
    Serial.begin(115200); // Initialize serial communication for debugging
    WiFi.mode(WIFI_STA); // Set WiFi mode to station mode
    ThingSpeak.begin(client); // Initialize ThingSpeak client
}

void loop(){
    // Check WiFi connection and reconnect if necessary
    if(WiFi.status() != WL_CONNECTED){
        Serial.print("Attempting to connect to SSID: ");
        Serial.println(ssid);
        while(WiFi.status() != WL_CONNECTED){
            WiFi.begin(ssid, password);
            delay(5000);
        }
        Serial.println("\nConnected.");
    }

    // Read temperature data from ThingSpeak channel
    long temp = ThingSpeak.readLongField(counterChannelNumber, fieldNumber1, counterWriteAPIKey);
    statusCode = ThingSpeak.getLastReadStatus(); // Get HTTP status code
    if(statusCode == 200){ // Check if reading was successful
        Serial.print("Field 1: ");
        Serial.println(temp);
    }
    else{
        Serial.println("Problem reading channel. HTTP error code " + String(statusCode));
    }

    delay(1000);

    // Read humidity data from ThingSpeak channel
    long humidity = ThingSpeak.readLongField(counterChannelNumber, fieldNumber2, counterWriteAPIKey);
    statusCode = ThingSpeak.getLastReadStatus(); // Get HTTP status code
    if(statusCode == 200){ // Check if reading was successful
        Serial.print("Field 2: ");
        Serial.println(humidity);
    }
    else{
        Serial.println("Problem reading channel. HTTP error code " + String(statusCode));
    }

    delay(1000);
}
```

# Week 9

```cpp
// Include the necessary libraries
#include "ESP8266WiFi.h"
#include "DHT.h"

// Define the WiFi credentials
const char* ssid = "YOUR_SSID";
const char* password = "YOUR_PASSWORD";

// Create a WiFi server object on port 8080
WiFiServer wifiServer(8080);

// Create a DHT sensor object on pin D3 and specify the sensor type
DHT dht(D3, DHT22);

void setup(){
    // Start the serial communication
    Serial.begin(115200);
    delay(1000);
    
    // Connect to WiFi
    WiFi.begin(ssid, password);
    // Wait for the connection to be established
    while(WiFi.status() != WL_CONNECTED){
        delay(1000);
        Serial.println("Connecting to WiFi...");
    }
    // Print a message when connected to WiFi
    Serial.println("Connected to WiFi.");

    // Start the WiFi server
    Serial.println("Starting TCP server...");
    wifiServer.begin();
    // Print a message when the server is started
    Serial.println("TCP server started.");
    
    // Initialize the DHT sensor
    dht.begin();
}

void loop(){
    // Check if a client is connected
    WiFiClient client = wifiServer.available();
    if(client){
        // Keep the client connected as long as it remains connected
        while(client.connected()){
            // Check if there is data available from the client
            while(client.available() > 0){
                // Read the temperature and humidity from the DHT sensor
                float t = dht.readTemperature();
                float h = dht.readHumidity();
                
                // Send the humidity data to the client
                client.print("Humidity: ");
                client.println(h);
                Serial.println(h);
                
                // Send the temperature data to the client
                client.print("Temperature: ");
                client.println(t);
                Serial.println(t);
                
                // Delay for 2 seconds before reading the sensor again
                delay(2000);
            }
        }
        // Disconnect the client when it is no longer connected
        client.stop();
        Serial.println("Client disconnected.");
    }
}
```
