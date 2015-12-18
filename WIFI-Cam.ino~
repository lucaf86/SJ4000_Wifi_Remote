
#include <ESP8266WiFi.h>

#include <ESP8266HTTPClient.h>

/**
   WIFI-Cam.ino

   Created on: 18.12.2015

   Copyright (c) 2015 Joshua Petry. All rights reserved.
   Feel free to use, but respect my work and don't present it as your own!

*/

const char* ssid     = "JoshCam";
const char* password = "665644446";
int led= 4 ;
void setup() {
  pinMode(led, OUTPUT);
  digitalWrite(led, LOW);
  Serial.begin(115200);
  Serial.print("Connecting to ");
  Serial.println(ssid);

  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
  
  Serial.println("Start Record");
  HTTPClient http;
  http.begin("192.168.1.254", 80, "/?custom=1&cmd=2001&par=1 HTTP/1.1");
  http.GET();
  http.end();
  delay(5000);
  Serial.println("Stop Record");
  http.begin("192.168.1.254", 80, "/?custom=1&cmd=2001&par=0 HTTP/1.1");
  http.GET();
  http.end();
  digitalWrite(led, HIGH);
}

void loop() {

}
