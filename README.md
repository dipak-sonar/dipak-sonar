#include <DHT.h>

#define DHTPIN 2  // Pin where the DHT22 is connected
#define DHTTYPE DHT 11  // DHT22 or DHT11, change accordingly

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  dht.begin();
}

void loop() {
  delay(2000);  // Wait for 2 seconds between readings

  float humidity = dht.readHumidity();
  float temperature = dht.readTemperature();

  if (isnan(humidity) || isnan(temperature)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }

  Serial.print("Humidity: ");
  Serial.print(humidity);
  Serial.print("%\t");

  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.println("°C");
}
