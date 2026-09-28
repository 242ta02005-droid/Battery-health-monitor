# Battery-health-monitor
# Battery Health Monitoring System

print("======================================")
print("       BATTERY HEALTH MONITOR")
print("======================================")

# Input battery parameters
rated_voltage = float(input("Enter rated battery voltage (V): "))
voltage = float(input("Enter present battery voltage (V): "))
temperature = float(input("Enter battery temperature (°C): "))
cycles = int(input("Enter number of charge cycles: "))

# Calculate voltage health percentage
voltage_health = (voltage / rated_voltage) * 100

# Estimate battery SOH
if cycles <= 300:
    cycle_health = 100
elif cycles <= 600:
    cycle_health = 85
elif cycles <= 1000:
    cycle_health = 70
else:
    cycle_health = 50

# Overall health
soh = (voltage_health + cycle_health) / 2

print("\n----------- BATTERY STATUS -----------")
print("Voltage        :", voltage, "V")
print("Temperature    :", temperature, "°C")
print("Charge Cycles  :", cycles)
print("Estimated SOH  :", round(soh, 2), "%")

# Health evaluation
if temperature > 60:
    print("\n⚠️ WARNING: Battery temperature is too high!")

if soh >= 80:
    print("🟢 Battery Health: GOOD")

elif soh >= 60:
    print("🟡 Battery Health: MODERATE")

else:
    print("🔴 Battery Health: POOR")
    print("Battery inspection/replacement may be required.")

print("\n======================================")
print("       MONITORING COMPLETED")
print("======================================")
