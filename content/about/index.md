---
title: "Rohan Chadha"
## description: "Some things about me"
---
**Some things about me:**
* Grew up in Amritsar
* Graduated from NIT Jalandhar + IIFT
* Early career in software engineering, later turned PM.
* I love movies & I like doing hard things
* Currently self-learning vibe coding & piano

**Here's where I've worked so far 👇**:
* Product & Data @ shiksha.com (160 Cr revenue, 500M+ annual visits)
* Product & Growth @ zingbus - YC'21 ($70M intercity bus travel aggregator)
* Software Engineer @ Capgemini (Wealth Mgmt/Payments)

## Infoedge - shiksha.com (1 year)
* Shiksha is India's leading education guidance platform 
    * 500 Mn+ annual vists
    * 1 Mn+ App Downloads
* We provide comprehensive college and course selection guidance to students
* I  take care of **User Growth** & **Engagement** charter at shiksha
* I still work here. so can't talk about much else rn 😁


## Zingbus - YC'21 (2 years 8 months)
* zingbus - an **asset-light** & **SOP-heavy** business. 
* It partners with small and medium size bus fleet operators.
* Aggregates this supply under zingbus brands - plus, maxx, valuebus (kinda like OYO does with hotels)
* Fleet Operator takes complete ownership of - maintenance, staffing, compliance, etc
* zingbus takes care of demand side of the equation
* Gets demand through **OTAs** (redbus, mmt, abhibus), its **[B2C app](https://play.google.com/store/apps/details?id=com.zingbusbtoc.zingbus)** (1M+ downloads) & **B2B platform** (focused towards Travel Agents)
* Also completely owns network/schedule planning, training crew, inventory pricing, marketing, CX experience 

On to things I built while I was there 👇


### Apr 2023 - Nov 2024 (Product Manager)

I was leading the whole product pipeline at this point. I had 4 direct reports (1 designer & 3 APMs)

* zingprime - Loyalty Pass inclusive of below benefits
    * On-Time Guarantee (if your bus is >45 mins late at your destination or pickup point, 50% refund coupon)
    * Additional 5% discount
    * Free Travel Insurance
    * Better Refund & Cancellation Policy
    * Was used heavily for Customer Acquisition. Free zingprime on App Install.
    * We'd much rather prefer a customer directly book & repeat through our app rather than from OTA (coz 14% Take Rate)
* Curated Marketplace (Partner Buses)
    * We had decent traffic on consumer app & huge Travel Agent network but only 300 buses on the road connecting 500 cities
    * We weren't servicing a lot of the routes the users & travel agents were searching for (resulting in zero result pages)
    * Enter Curated Marketplace - Sell non-zingbus branded supply on our platform
    * Got this inventory via GDS intergations with Bitla, Mantis, Abhibus (These are Amadeus/Sabre equivalents for Bus Travel)
* Demand-generation (B2C, B2B)
    * Automated Price Drops (rule based) - On route X to Y, if trip start time is in < 4 hrs & occupancy < 50%, set price to minSupplyPrice
    * Send outbound calls to Travel Agents who work on these routes
    * Send tf rates to Travel Agents who work on these routes
* Multi Modal Product for offbeat destinations
    * Book a **cab+bus+cab** journey via zingbus. All legs of the journey booked through zingbus & managed via zingbus.
        * Shared cab from Gurgaon to Delhi (Wait at zingbus lounge)
        * Delhi to Aut in a bus
        * Shared cab from Aut to Jibhi
    * Built the whole back-office for this 
        * Inventory Creation & Pricing
        * Crew Assignment & Crew update (cab+bus+cab)
        * CX Communication layer (whatsapp, sms, email, notifications)
        * Crew App (support for multi-modal trips)
* [Supply Portal](https://www.zingbus.com/operator) - Bus Fleet Owner & Admin
    * Payout & Settlement reports
    * Supply Audit reports
    * Crew report cards
    * Onboard & manage supply
    * Occupancy Analytics
    * Customer Feedback & Report card

* Dynamic Pricing Product (B2B/B2C)
    * Get signals (routes, occupancy, prices) from open marketplace platforms (OTAs, GDS APIs)
    * Defined rules in Internal systems that govern zingbus seta prices based on these signals
<!---
* Valuebus - Demand Aggregation & Dynamic Supply Matching product
* Spin The Wheel
    * Reactivation
* Rapido Partnership 
* CRM/User Journeys (through MoEngage & Clevertap)
* Reactivation Campaigns
* Referral Program 
-->


### Apr 2022 - Mar 2023 (Associate Product Manager - I)
* Crew App - [zingbus Marshal App](https://play.google.com/store/apps/details?id=com.zingbus.zingbusmarshalapp)
    * Automated incentive + salary credit in wallet
        * Driver can see exact breakdown of incentive & salaries (for every task and trip completion)
        * Extract wallet amount directly into Personal bank account (using Razorpay payouts)
    * Nudges -> Next passengers to call, Upcoming pickups/Drops
    * CX Dashboard - Intelligent Alerts
* ***Crew App - Rating Collection for OTA bookings***
    * **Problem** - Most people will only rate your service on OTAs if they have a bad exp.
    * By virtue of this, your service rating will keep falling unless you have promoters on OTA
    * zingbus incentivised crew to get the cx to rate us on OTA after trip completion (by calling. masked calls ofc)
    * Crew could track these tasks, its progress, linked incentive directly from the app
* Implemented WhatsApp chatbot using freshdesk bot builder
    * Resolved 70% of incoming chat volume
    * Decreased First Response Time by 83%

<!---   
* Checkout Revamp - Save Passenger Info in profile so it could be used again in future bookings
* Ancilliaries Product Integrations - 
    * Insurance
    * CO2 neutralize
    * Free Cancellations
* Incident Management
    * Maksed Call Intelligence
* Bus Live Tracking Product
    * Self Help Page
-->
* Intelligent Crew Assignment on trips
* Led integrations
    * Optimized PG costs - onboarded PayTM, PhonePe & Razorpay
    * Juspay for logic based routing & downtime protection
    * Mixpanel for event tracking
    * Singular for Attribution
    * Decentro for KYCs
    * Razorpay X for Crew payouts
    * Clevertap for Customer Engagement & Retention campaigns
    * Customer Glu - Gamification campaigns
    * Bimaplan - Travel Insurance Provider
    * Clime.io - Carbon Neutralization initiative

