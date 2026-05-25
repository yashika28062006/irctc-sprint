# Impact vs Effort Matrix

|             | Low Effort                       | High Effort                       |
| ----------- | -------------------------------- | --------------------------------- |
| High Impact | Search Filters, Refund Dashboard | Tatkal Queue, AI WL Predictor     |
| Low Impact  | Mobile Layout Improvements       | Seat Selection Sync, UPI Tracking |

---

# Placement Justifications

## Tatkal Queue — High Impact / High Effort

Affects millions of users daily during Tatkal booking hours. Requires backend queue infrastructure, WebSocket updates, and session management redesign. This should be prioritized as a major platform project.

## Search Filters — High Impact / Low Effort

Filter persistence affects almost all train search users. Requires mostly frontend session handling and minimal backend work. This is an ideal quick-win improvement.

## Seat Selection Sync — Low Impact / High Effort

Affects a smaller subset of users but requires backend synchronization updates. Changes booking state management significantly.

## UPI Tracking — Low Impact / High Effort

Payment tracking improves trust but requires payment gateway integrations and live callback handling.

## Mobile Layout — Low Impact / Low Effort

Responsive redesign mainly affects frontend CSS and layout handling.

## Refund Dashboard — High Impact / Low Effort

Clear refund visibility reduces support load and user confusion. Mostly dashboard and status aggregation work.

---

# Recommended Sprint Order

1. Search Filters
2. Refund Dashboard
3. Mobile Layout
4. Tatkal Queue
5. Seat Selection Sync
6. UPI Tracking
