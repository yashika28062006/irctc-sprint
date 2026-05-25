# AI Feature Specification — Waitlist Confirmation Predictor

## Problem It Solves

Users cannot estimate whether their waitlisted ticket will confirm before journey date.

## Proposed Feature — User Perspective

Users see a “Confirmation Probability” percentage beside waitlisted tickets during booking.

Example:

* WL 12 → 82% confirmation chance

## Model or API Choice

XGBoost prediction model trained on historical railway confirmation patterns.

## Training or Input Data

* Historical PNR data
* Route occupancy trends
* Seasonal demand
* Cancellation patterns
* Festival traffic

## How Output Is Shown to the User

The booking page displays:

* Probability %
* Confidence label
* Suggested alternatives

## Confidence Threshold and Fallback

* Show prediction only above 70% confidence
* Otherwise display:
  “Prediction unavailable currently.”

## Success Metrics

* Reduced unnecessary cancellations
* Increased booking confidence
* Lower support queries

## Limitations and Risks

* Festival seasons may reduce prediction accuracy
* Backend data delays may affect predictions
* Users may over-rely on predictions
