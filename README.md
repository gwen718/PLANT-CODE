# PLANT-CODE
Plant watering system using matlab.

a = arduino('COM3','uno');

function (soilmoisture) = MainProject1011(reallyDryValue, moisturethreshold, watersaturatedvalue);

%Define Constant
reallyDryValue = 3.4;
moisturethreshold = 3.2;
watersaturatedValue = 3;

soilmoisture = readVoltage(a, 'A1');

while true
soilmoisture = readVolatge(a, 'A1');

  if (soilmoisture > reallyDryValue)
     disp(" Signal Recieved. Soild Dry, time to water!");
     writeDigitalPin(a, 'D2', 1);
  elseif (soilmoisture > moisturethreshold)
     disp(" still needs more water")
     writeDigitalPin(a, 'D2', 1);
  else
     soilmoisture >= watersaturatedValue;
     disp("  Soild is wet!");
     pause(1);
     writeDigitalPin(a, 'D2', 0);
  end


     %Display System Status
     fprinf('Soil Moisture: %.2f\n', soilmoisture);

     %Wait for next sammpling period
     pause(1)

  end
