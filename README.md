# Databricks-Assignment_Synapx
Assignment





Gold layer ER model preview: 
                    ┌───────────────────┐
                    │    dim_patient    │
                    │-------------------│
                    │ patient_key (PK)  │
                    │ patient_id        │
                    │ gender            │
                    │ birth_date        │
                    │ city              │
                    │ state             │
                    │ country           │
                    │ ...               │
                    └─────────┬─────────┘
                              │
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
┌───────▼────────┐   ┌────────▼────────┐   ┌────────▼────────┐
│ fact_encounter │   │ fact_condition  │   │ fact_observation│
│----------------│   │-----------------│   │-----------------│
│ encounter_key  │   │ condition_id    │   │ observation_id  │
│ patient_key FK │   │ patient_key FK  │   │ patient_key FK  │
│ status         │   │ encounter_key FK│   │ encounter_key FK│
│ period_start   │   │ condition_text  │   │ value_quantity  │
│ period_end     │   │ is_current      │   │ loinc_code      │
└────────┬───────┘   └────────┬────────┘   └────────┬────────┘
         │                    │                     │
         └──────────────┬─────┴──────────────┬──────┘
                        │                    │
                  ┌─────▼─────────┐
                  │ dim_encounter │
                  │---------------│
                  │ encounter_key │
                  │ encounter_id  │
                  │ organization  │
                  └───────────────┘
