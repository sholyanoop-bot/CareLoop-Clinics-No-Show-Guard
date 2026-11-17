# NoShowGuard – Appointment No-Show Analysis

**Public GitHub Repository:** [Paste your GitHub repository link here]

## 1. Four-part project summary

- **Part 1 – Data preparation:** Cleaned 1,020 original appointment records to 990 usable records, with 218 no-shows (22.0%).
- **Part 2 – SQL analysis:** Appointments booked 31 or more days ahead had a 60.5% no-show rate, compared with 16.2% for appointments booked 1–7 days ahead.
- **Part 3 – Machine learning:** Logistic Regression was selected using training cross-validation (ROC-AUC approximately 0.77); its test ROC-AUC was approximately 0.79.
- **Part 4 – Patient notes:** Analysed 10 follow-up notes, including 9 non-blank notes; 2 of 2 notes classified as forgotten/no reminder had no reminder recorded.

## 2. Business recommendation

The analysis suggests that clinics should focus on reducing missed appointments through timely reminders and follow-up. Of the 990 cleaned appointments, 218 (22.0%) were no-shows. The no-show rate increased to 30.0% for appointments booked 15–30 days ahead and 60.5% for those booked 31 or more days ahead. The selected Logistic Regression model achieved a test ROC-AUC of approximately 0.79, using a 0.35 risk threshold to identify appointments for follow-up. In the ten illustrative patient notes, five appointments had no reminder recorded, and both notes classified as forgotten/no reminder were associated with reminder_sent = No. Clinics could therefore prioritise earlier reminders and follow-up for appointments booked more than 14 days ahead, while using the model to help identify appointments that may need additional attention. The clinic should monitor call capacity and review the results before implementing this approach at scale.

## 3. Model selection

Logistic Regression was selected because it achieved the strongest or comparable training cross-validation ROC-AUC (approximately 0.77) among the models evaluated and performed well on the test set (ROC-AUC approximately 0.79). A probability threshold of 0.35 was selected using out-of-fold training predictions because it improved the balance of precision and recall compared with the default 0.50 threshold. The final test-set evaluation was performed after model selection.

## 4. Limitations

1. The ten patient notes are an illustration and cannot establish the real reasons for missed appointments across all clinics.
2. The data are observational, so associations between appointment characteristics and no-shows do not prove causation.
3. The train/test split is random rather than based on past-to-future dates, so the evaluation may not reflect how the model performs on future appointments.

## 5. Conclusion

NoShowGuard demonstrates how data cleaning, SQL analysis, machine learning and patient-note analysis can help clinics understand appointment no-shows and prioritise follow-up. Further validation using larger datasets and real clinic operations is needed before deployment.