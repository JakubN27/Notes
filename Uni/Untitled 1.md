## 3️⃣ User Flow

### a) Customer (Ticket Buyer) Flow

1. Student visits the DuPulse event page after Fixr sells out.
    
2. Selects ticket type and quantity.
    
3. Proceeds to **Stripe Checkout** for payment.
    
4. On successful payment:
    
    - Ticket is created in Supabase.
        
    - Unique QR code generated and emailed/available for download.
        
5. Student shows QR code at the event for entry.
    

### b) Door / Bouncer Flow

1. Organiser opens **DuPulse scanner web page** on a phone or tablet.
    
2. Scans QR code using device camera.
    
3. System queries Supabase:
    
    - If valid and unscanned → mark as scanned, display ✅
        
    - If invalid or already scanned → display ❌
        
4. Optional: multiple scanners at different entry points synchronized in real-time.
    

---

## 4️⃣ Fixr System Considerations

- Most clubs use the **Fixr Organiser app** on iOS/Android for ticket scanning.
    
- **Proprietary Fixr scanners are rare** at university events.
    
- Fixr QR codes are only compatible with their own app; **no public API exists** for integration.
    
- Therefore, DuPulse **must operate an independent QR scanning system**:
    
    - Web-based scanner on a smartphone or tablet.
        
    - Independent ticket validation logic.
        
- Operationally, this means:
    
    - DuPulse acts as a **parallel ticketing system** to Fixr.
        
    - Staff can use separate devices for Fixr and DuPulse tickets.
        
    - No conflict exists with Fixr scanning; DuPulse tickets are just scanned on a second device.
        

---

## 5️⃣ Advantages to Clubs (Pitch Perspective)

- **Exclusive second drop**: Sell tickets after Fixr sells out, capturing extra revenue.
    
- **Direct revenue & lower fees**: Stripe payments reduce fees compared to Fixr.
    
- **Data & analytics**: Full access to ticket sales, scanned attendees, and basic conversions.
    
- **Web-based scanner**: No app install needed, works on any device.
    
- **Campus ecosystem integration**: Directly connects students, societies, and events within DuPulse.
    
- **Flexible & iterative**: Changes or new features can be implemented quickly, unlike Fixr’s closed system.