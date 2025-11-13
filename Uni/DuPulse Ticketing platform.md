## 1. Feature Overview

Objective:  
Develop a ticketing system integrated with DuPulse that allows clubs to sell an overflow batch of event tickets after Fixr sells out, positioning DuPulse as the “exclusive second drop” ticket platform.

Goal:

- Sell up to 40% of event tickets per event through DuPulse.
    
- Provide seamless customer checkout, QR validation at the door, and basic analytics for organisers.
    
- Maintain independence from Fixr due to lack of public API and proprietary QR scanner system.
    

---

## 2. Development Process

a) Core Components

1. Ticket Listings
    
    - Backend: tickets table linked to events. Stores ticket type, quantity, price, Stripe product ID.
        
    - Frontend: Ticket purchase page integrated with DuPulse’s event pages.
        
2. Payment Integration
    
    - Use Stripe Checkout for secure payments.
        
    - Backend handles session creation and webhook for successful payment.
        
    - Purchases logged in Supabase, each assigned a unique QR code (UUID).
        
3. QR Code Generation
    
    - Each purchased ticket generates a unique QR code pointing to a DuPulse validation endpoint.
        
    - QR codes can be printed or displayed digitally on users’ phones.
        
4. Door Scanning / Validation
    
    - Web-based QR scanner accessible on any smartphone or tablet.
        
    - Scans QR codes, validates them against Supabase, and marks tickets as “scanned” to prevent reuse.
        
    - Displays instant green/red confirmation to bouncers or organisers.
        
5. Organizer Dashboard
    
    - Displays ticket sales, revenue, scanned status, and attendee lists.
        
    - Optional export of CSV for reporting.
        
6. Analytics
    
    - Tracks ticket views, purchases, and scanning events.
        
    - Provides organisers with conversion rates and attendance metrics.
        

---

b) Development Bottlenecks and Difficulties

|Challenge|Difficulty|Mitigation / Notes|
|---|---|---|
|Stripe Integration and Payouts|Medium|Stripe Connect is optional; for MVP, funds can be collected via Stripe and paid out manually. Webhook reliability must be tested carefully.|
|QR Validation at Door|Medium|Must be fast and reliable; offline fallback needed if venue Wi-Fi is poor. Multi-scanner concurrency must be handled.|
|Fixr Integration Limitations|High|Fixr has no public API and their QR codes only work in their app. You cannot integrate directly, requiring DuPulse to generate its own QR codes.|
|Operational Trust|Medium|Clubs must trust a parallel QR system at the door. Requires training, test QR validation, and clear instructions.|
|Offline / Low-Light Scenarios|Low-Medium|QR scanning must handle low-light conditions and optionally allow offline validation.|
|Security / Fraud Prevention|Medium|Each QR can only be used once; optionally include buyer ID verification for high-value events.|

---

## 3. User Flow

a) Customer (Ticket Buyer) Flow

1. Student visits the DuPulse event page after Fixr sells out.
    
2. Selects ticket type and quantity.
    
3. Proceeds to Stripe Checkout for payment.
    
4. On successful payment:
    
    - Ticket is created in Supabase.
        
    - Unique QR code generated and emailed or available for download.
        
5. Student shows QR code at the event for entry.
    

b) Door / Bouncer Flow

1. Organiser opens DuPulse scanner web page on a phone or tablet.
    
2. Scans QR code using device camera.
    
3. System queries Supabase:
    
    - If valid and unscanned, mark as scanned, display confirmation.
        
    - If invalid or already scanned, display rejection.
        
4. Optional: multiple scanners at different entry points synchronized in real-time.
    

---

## 4. Fixr System Considerations

- Most clubs use the Fixr Organiser app on iOS or Android for ticket scanning.
    
- Proprietary Fixr scanners are rare at university events.
    
- Fixr QR codes are only compatible with their own app; no public API exists for integration.
    
- Therefore, DuPulse must operate an independent QR scanning system:
    
    - Web-based scanner on a smartphone or tablet.
        
    - Independent ticket validation logic.
        
- Operationally, this means:
    
    - DuPulse acts as a parallel ticketing system to Fixr.
        
    - Staff can use separate devices for Fixr and DuPulse tickets.
        
    - No conflict exists with Fixr scanning; DuPulse tickets are just scanned on a second device.
        

---

## 5. Advantages to Clubs

- Exclusive second drop: Sell tickets after Fixr sells out, capturing extra revenue.
    
- Direct revenue and lower fees: Stripe payments reduce fees compared to Fixr.
    
- Data and analytics: Full access to ticket sales, scanned attendees, and basic conversions.
    
- Web-based scanner: No app install needed, works on any device.
    
- Campus ecosystem integration: Directly connects students, societies, and events within DuPulse.
    
- Flexible and iterative: Changes or new features can be implemented quickly, unlike Fixr’s closed system.
    

---

## 6. Technical Feasibility

- Supabase backend can handle tickets, purchases, and validation.
    
- Stripe provides payment processing with minimal integration overhead.
    
- QR scanning via web browser is a mature, reliable solution.
    
- Development effort for MVP: approximately one week for a single developer.
    
- Long-term enhancements: Stripe Connect for automatic payouts, multi-event scanning, offline scanning support, and richer analytics.
    

---

## 7. Conclusion

DuPulse ticketing is technically feasible, operationally compatible, and strategically valuable as a club overflow solution.

Key considerations:

- Must use independent QR codes due to Fixr’s closed system.
    
- Clubs must use a web-based scanner or a second device alongside their existing Fixr app.
    
- Main development risks involve Stripe integration, QR scanning reliability at the door, and offline fallback scenarios.
    

Once implemented, this feature can serve as a pilot for exclusive drops, giving DuPulse a foothold in event ticketing beyond its current event management capabilities.

---
