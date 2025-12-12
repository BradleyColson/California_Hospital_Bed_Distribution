# California_Hospital_Bed_Distribution
California Hospital Bed Distribution

- [Overview](#overview)
- [Data_Description](#Data_Description)
- [Key_Insights](#Key_Insights)
https://public.tableau.com/app/profile/bradley.colson/viz/CaliforniaHospitalBedDistribution/CaliforniaHospitalBedDistribution


<img width="1366" height="768" alt="CA_Hospital" src="https://github.com/user-attachments/assets/c62d7600-16f9-40ab-a0f3-8cd9a1144915" />

# Overview

Investigating the hospital bed distribution in California

# Data_Description

10800 + rows. Data cleaned out commas that interfered with MySQL import wizard.

# Key_Insights

The distribution of healthcare capacity in California is seen to be concentrated in major metropolitan areas, leading to obvious disparities between urban centers and rural counties. 

The overall bed capacity is dominated by Skilled Nursing Facilities (SNFs), which cater to long-term care rather than critical acute emergencies.

Key Finding: Over 56% of total beds are non-acute (SNFs, Residential, etc.) or are in facilities with no specified Emergency Room services. This structure makes the state vulnerable to acute care surges, particularly in lesser populated regions.

1. How are Hospital Beds Distributed? (SQL Analysis)
   
A. Geographic Concentration (The 80/20 Rule in Health Care)

The top 10 most populous counties account for a disproportionately high number of beds, leaving rural areas severely resource-poor.

County Name Total Beds Facility Count Avg Beds/Facility
Los Angeles 63,537 615 103.3
San Diego 16,597 125 132.8
Orange 14,570 113 128.9
San Bernardino 9,631 86 112.0
Riverside 9,321 96 97.1
Santa Clara 9,221 68 135.6

The Bed Deserts: The bottom counties demonstrate critical scarcity:
County Name | Total Beds | Facility Count |

Mono | 17 | 1 |
Mariposa | 34 | 1 |
Trinity | 38 | 1 |
Sierra | 39 | 1 |

B. Distribution by Facility Type
The largest portion of licensed capacity is for long-term care, not intensive medical care.
License Category Description Total Beds Avg Beds
Skilled Nursing Facility 109,362 101.1
General Acute Care Hospital 84,271 185.6
Acute Psychiatric Hospital 4,260 101.4

Acute Bed Gap: While General Acute Care Hospitals are typically larger (Avg 185 beds), the sheer volume of Skilled Nursing Beds (109k) means the state's infrastructure focus is on long-term maintenance rather than high-volume acute surge capacity.

C. Emergency Service Capability
The majority of bed inventory is disconnected from emergency services:
ER Service Level Description Total Beds 

Not Applicable 117,315
Emergency - Basic 66,810
Emergency - Comprehensive 4,708


2. Business Suggestion or Solution
The core business challenge is maximizing the utility of the existing, highly centralized bed capacity while guaranteeing minimum service levels in resource-scarce rural areas.
Strategic Recommendation: Hybrid Capacity Model
The state should move toward a Hybrid Capacity Model that uses technology and regulation to bridge the geographic and service-level gaps.
Mandate and Subsidize Tele-Acute Care in Rural Areas:
Action: Require the single-facility counties (like Mono, Mariposa, Trinity) to implement 24/7 Tele-ICU and Tele-Stroke/Tele-Trauma partnerships with major urban hubs (LA, San Diego).

Goal: This effectively grants rural patients access to specialist expertise without requiring resource-intensive on-site staff, immediately upgrading the quality of the 17-39 existing beds from basic stabilization to effective mid-level acute care.
Establish SNF/Acute Conversion Protocols:
Action: Create a tiered classification system for the 109,362 Skilled Nursing Facility (SNF) beds, identifying which ones meet minimum structural standards (e.g., oxygen lines, power redundancy) to be rapidly converted to Sub-Acute Flex Wards during a declared statewide public health emergency.
Goal: This turns the large SNF capacity into a controllable, rapid-deployment surge capacity, preventing the General Acute Care Hospitals from being immediately overwhelmed during a crisis.

Invest in Regional Behavioral Health Centers:
Action: The large average size of Acute Psychiatric Hospitals (Avg 101 beds) suggests institutional, centralized care. Shift funding and licensing towards establishing smaller, 20-30 bed, community-based Psychiatric Health Facilities in mid-sized counties (e.g., Fresno, Alameda).
Goal: Decentralizing mental health care improves local access, reduces the strain on patients and families traveling long distances, and integrates behavioral health more seamlessly into regional service networks.






