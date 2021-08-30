+++
title = "Binary_Clock_Code_Rev1_0"
description = "Binary Clock Code"
date = "2021-08-29"
aliases = ["about-us", "about-hugo", "contact"]
author = "Vincent The-Lifting-Engineer"
+++
#include <NTPClient.h>
#include <ESP8266WiFi.h>
#include <WiFiUdp.h>

int latchPin1 = D2;
int clockPin1 = D0;
int dataPin1 = D1;

int latchPin2 = D5;
int clockPin2 = D3;
int dataPin2 = D4;

byte data1 = 0;
byte data2 = 0;
byte dataArray[60];

const char *ssid     = "totally legit wifi";
const char *password = "goodlife";

const long utcOffsetInSeconds = -25200;

// Define NTP Client to get time
WiFiUDP ntpUDP;
NTPClient timeClient(ntpUDP, "pool.ntp.org", utcOffsetInSeconds);

void setup(){
  //Shift rego setup

  pinMode(latchPin1, OUTPUT);
  pinMode(clockPin1, OUTPUT);
  pinMode(dataPin1, OUTPUT);
  pinMode(latchPin2, OUTPUT);
  pinMode(clockPin2, OUTPUT);
  pinMode(dataPin2, OUTPUT);

  dataArray[0] = 0x00; 
  
  dataArray[1] = 0x01;

  dataArray[2] = 0x02; 

  dataArray[3] = 0x03; 

  dataArray[4] = 0x04; 

  dataArray[5] = 0x05; 

  dataArray[6] = 0x06; 
  
  dataArray[7] = 0x07; 

  dataArray[8] = 0x08; 

  dataArray[9] = 0x09; 
  
  dataArray[10] = 0x10; 
  
  dataArray[11] = 0x11;

  dataArray[12] = 0x12; 

  dataArray[13] = 0x13; 

  dataArray[14] = 0x14; 

  dataArray[15] = 0x15; 

  dataArray[16] = 0x16; 
  
  dataArray[17] = 0x17; 

  dataArray[18] = 0x18; 

  dataArray[19] = 0x19;

  dataArray[20] = 0x20; 

  dataArray[21] = 0x21; 
  
  dataArray[22] = 0x22; 

  dataArray[23] = 0x23;

  dataArray[24] = 0x24; 
  
  dataArray[25] = 0x25;

  dataArray[26] = 0x26; 

  dataArray[27] = 0x27; 

  dataArray[28] = 0x28; 

  dataArray[29] = 0x29; 

  dataArray[30] = 0x30; 
 
  dataArray[31] = 0x31; 

  dataArray[32] = 0x32; 

  dataArray[33] = 0x33; 
  
  dataArray[34] = 0x34; 
  
  dataArray[35] = 0x35;

  dataArray[36] = 0x36; 

  dataArray[37] = 0x37; 

  dataArray[38] = 0x38; 

  dataArray[39] = 0x39; 

  dataArray[40] = 0x40; 
  
  dataArray[41] = 0x41; 

  dataArray[42] = 0x42; 

  dataArray[43] = 0x43;

  dataArray[44] = 0x44; 

  dataArray[45] = 0x45; 
  
  dataArray[46] = 0x46; 

  dataArray[47] = 0x47;

  dataArray[48] = 0x48; 
  
  dataArray[49] = 0x49; 

  dataArray[50] = 0x50; 

  dataArray[51] = 0x51;

  dataArray[52] = 0x52; 

  dataArray[53] = 0x53; 
  
  dataArray[54] = 0x54; 

  dataArray[55] = 0x55;

  dataArray[56] = 0x56; 

  dataArray[57] = 0x57; 
  
  dataArray[58] = 0x58; 

  dataArray[59] = 0x59;
  //wifi setup
  
  Serial.begin(115200);

  WiFi.begin(ssid, password);

  while ( WiFi.status() != WL_CONNECTED ) {
    delay ( 500 );
    Serial.print ( "." );
  }

  timeClient.begin();
}

void loop() {
 
  timeClient.update();
  
  int hr = timeClient.getHours();
  Serial.print(hr);
  Serial.print(":");
  int mins = timeClient.getMinutes();
  Serial.print(mins);
  Serial.print(":");
  int sec = timeClient.getSeconds();
  Serial.print(sec);
  Serial.println(" ");

  data1 = dataArray[hr];
  data2 = dataArray[mins];

  digitalWrite(latchPin1, LOW);
  shiftOut(dataPin1, clockPin1, MSBFIRST, data1);
  digitalWrite(latchPin1, HIGH);
  
  digitalWrite(latchPin2, LOW);
  shiftOut(dataPin2, clockPin2, MSBFIRST, data2);
  digitalWrite(latchPin2, HIGH);
  
}
