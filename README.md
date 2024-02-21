# Machine_Learning

## Description

This was a project developed for the Machine Learning course from the MSc in Data Science and Advanced Analytics, at NOVA IMS, regarding hospital readmissions. This project had two goals: 
1. **Binary Classification**: Create a classification model that can accurately predict if a patient will be readmitted to the hospital within 30 days of being discharged. 
2. **Multiclass Classification**: The second objective is to develop a multiclass classifier that predicts the timeframe of a patient’s readmission, with the classes being “No”, “<30 days”, “>30 days”. 
(Note: only models from scikit-learn could be used for this project.)

## Metadata

- _encounter_id_ Unique identifier of the encounter
- _country_ country
- _patient_id_ Identifier of the patient
- _race_ Patient’s race
- _gender_ Patient’s gender
- _age_ Patient’s age bracket
- _weight_ Patient’s weight
- _payer_code_ Code of the health insurance provider (if there is one)
- _outpatient_visits_in_previous_year_ Number of outpatient visits (visits made with the intention of leaving on the same day) the patient made to the hospital in the year preceding the encounter
- _emergency_visits_in_previous_year_ Number of emergency visits the patient made to the hospital in the year preceding the encounter
- _inpatient_visits_in_pre vious_year_ Number of inpatient visits (visits with the intention to stay overnight) the patient made to the hospital in the year preceding the encounter
- _admission_type_ Type of admission of the patient (e.g. Emergency, Urgent, etc...)
- _medical_specialty_ Medical specialty on which the patient was admitted
- _average_pulse_bpm_ Average pulse of the patient during their stay in the hospital in beats per minute
- _discharge_disposition_ Destination given to the patient after being discharged
- _admission_source_ Source of the patient before being admitted in the current encounter
- _length_of_stay_in_hospital_ Number of days between admission and discharge
- _number_lab_tests_ Number of lab tests performed during the encounter
- _non_lab_procedures_ Number of non-lab procedures performed during the encounter
- _number_of_medications_ Number of distinct types of medication administered during the encounter
- _primary_diagnosis_ Primary diagnosis (coded as first three digits of ICD9)
- _secondary_diagnosis_ Secondary diagnosis (first three digits of ICD9)
- _additional_diagnosis_ Additional secondary diagnosis (first three digits of ICD9)
- _number_diagnoses_ Number of diagnoses entered to the system
- _glucose_test_result_ Range of the glucose test results or if the test was not taken. Values: “>200,” “>300,” “normal,” and “none” if not measured
- _a1c_test_result_ Range of the A1C test results or if the test was not taken. Values: “>8” if greater than 8%, “>7” if greater than 7% but less than 8%, “normal” if less than 7%, and “none” if not measured.
- _change_in_meds_during_hospitalization_ Indicates if there was a change in diabetic medications (dosage or generic name). Values: “change” and “no change”
- _prescribed_diabetes_meds_ Yes if patient has diabetes medication perscribed. No otherwise.
- _medication_ List containing all generic names for the medications perscribed to the patient during the encounter. Empty list if no medication was perscribed.
- _readmitted_binary_ Binary target: Yes if patient was readmitted in less than 30 days, No otherwise.
- _readmitted_multiclass_ Multiclass target: “<30 days” if patient was readmitted in less than 30 days after being discharged. “>30 days if patient was readmitted to the hospital but only after more than 30 days after the current discharge. No otherwise.
