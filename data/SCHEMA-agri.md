# Esquema de datos técnicos de tractores (data/agri/<marca>.json)

Archivo = array JSON; una entrada por modelo de tractor (versión estándar/base). Regla de oro: NUNCA inventar ni estimar; si no está en la fuente → null. Cada entrada lleva `source` (URL oficial o ruta del PDF local + página) y `notes` (configuración a la que se refieren las cifras: con/sin overboost, potencia ECE R120 / ISO 14396 / 97/68/EC, versión de cambio, etc.).

```json
{
 "brand":"Fendt","model":"314 Vario","category":"tractor|hybrid_tractor|electric_tractor",
 "series":"300 Vario",
 "power_hp_rated":140,"power_hp_max":145,"power_kw_rated":103,"power_kw_max":107,   // CV (métricos) y kW; rated=nominal, max=con overboost/potencia máx.
 "power_standard":"ECE R120",
 "engine":{"make":"AGCO Power","model":"49 AWF","cylinders":4,"displacement_l":4.9,"emission_stage":"EU Stage V",
           "egr":null,"aftertreatment":"DOC+SCR","turbo":true,"max_torque_nm":600,"max_torque_rpm":1500,"rated_rpm":2100},
 "hybrid":{"electric_motor_kw":null,"battery_kwh":null,"description":null},   // sólo híbridos/eléctricos
 "transmission":{"type":"CVT|powershift|powerquad|synchro|other","model":"Vario","speeds":"continuous","max_speed_kmh":50,"creeper":null},
 "hydraulics":{"pump_type":null,"flow_lpm":110,"max_pressure_bar":200,"rear_remote_valves_max":4},
 "linkage":{"rear_lift_kg":6000,"front_lift_kg":null,"category":"Cat. III"},
 "pto":{"rear_speeds_rpm":"540/540E/1000","front_pto":null},
 "weight_kg":5700,"wheelbase_mm":2600,"fuel_l":210,"adblue_l":null,
 "tires":{"front":"480/65 R24","rear":"600/65 R34"},
 "cab":{"suspension":null,"air_conditioning":true,"isobus":null,"gps_guidance":null},
 "source":"https://...","notes":"..."}
```
Potencia: CV métricos (hp) y kW tal como los publica el fabricante; si el fabricante sólo da kW, no convertir salvo que lo declare (1 CV = 0,7355 kW; anotar la conversión en `notes`).
