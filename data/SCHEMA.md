# Esquema de datos técnicos (data/tech/<marca>.json)

Archivo = array JSON de máquinas. Una entrada por máquina (modelo base/versión estándar).
Regla de oro: NUNCA inventar ni estimar. Si un dato no está en la fuente → null. Cada entrada lleva `source` (URL oficial o ruta del PDF local + página) y `notes` con la configuración a la que se refieren las cifras (zapatas, pluma/brazo, neta/bruta, etc.).

```json
{
 "brand": "Hyundai", "model": "R220LC-9A", "category": "excavator|mini_excavator|wheel_loader|skid_steer|compact_track_loader",
 "equivalent_to": ["ZE225GN"],            // modelos Zoomlion de clase equivalente (peso/potencia)
 "weight_kg": 22760,
 "engine": {"make":"Cummins","model":"B6.7","displacement_l":6.7,"cylinders":6,
            "power_kw_net":117,"power_kw_gross":124,"rpm":1950,
            "emission_stage":"EU Stage V",
            "egr": true,                     // true/false/null: válvula EGR
            "aftertreatment":"DOC+DPF+SCR"}, // lo que publique el fabricante; null si no consta
 "hydraulics": {"pump_type":"2 bombas pistones axiales variable","pump_flow_lpm":"2x212",   // texto: caudal por bomba tal como lo publica el fabricante (L/min)
                "pump_flow_total_lpm":424,"system_pressure_bar":350,"aux_flow_lpm":null},
 "performance": {"bucket_dig_force_kn":153,"arm_dig_force_kn":108,"swing_speed_rpm":11,
                 "travel_speed_kmh":5.5,"gradeability_pct":70,
                 "max_dig_depth_mm":6010,"max_reach_mm":9330,"max_dump_height_mm":6700,
                 "bucket_capacity_m3":1.0,
                 "breakout_force_kn":null,"rated_operating_capacity_kg":null,"tipping_load_kg":null},   // las 3 últimas para cargadoras / skid steer
 "capacities": {"fuel_l":400,"hydraulic_tank_l":160},
 "cab": {"rops_fops":true,"air_conditioning":true},
 "source": "https://...", "notes": "..."
}
```
Para cargadoras de ruedas y skid steers rellenar lo aplicable (bucket_capacity, breakout_force_kn, tipping_load_kg, rated_operating_capacity_kg, aux_flow_lpm) y dejar null lo que no aplica.
