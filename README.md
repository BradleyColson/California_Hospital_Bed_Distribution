# California_Hospital_Bed_Distribution
California Hospital Bed Distribution

- [Overview](#overview)
- [Data Description](#DataDescription)
- [Key Insights](#KeyInsights)
- [Data Limitations](#DataLimitations)
- [Technical SQL Details](#TechnicalSQLDetails)
  
https://public.tableau.com/app/profile/bradley.colson/viz/CaliforniaHospitalBedDistribution/CaliforniaHospitalBedDistribution

<img width="999" height="799" alt="How are California Hospital Beds Distributed_" src="https://github.com/user-attachments/assets/3065c895-95d1-41b9-a101-f79190db9841" />


# Overview

Investigating the hospital bed distribution in California

# Data Description

10800 + rows. Data consists of Facility Level Description, County, Total Number of Beds, ER Service Level, License Type, and License Category

# Key Insights

The distribution of hospital bed capacity in California is concentrated in major metropolitan areas, leading to obvious capacity between urban centers and rural counties. 

The overall bed capacity is dominated by Skilled Nursing Facilities (SNFs), which cater to long-term care rather than critical acute emergencies.

Key Finding: Over 56% of total beds are non-acute (SNFs, Residential, etc.) or are in facilities with no specified Emergency Room services. This structure makes the state vulnerable to acute care surges, particularly in lesser populated regions.


Geographic Distribution (Top 3 Counties)
Business Insight: Los Angeles is the dominant hub with nearly 4x the capacity of San Diego.


Top 3 Results:

Los Angeles: 64,642 Beds (615 Facilities)
San Diego: 16,597 Beds (125 Facilities)
Orange: 14,570 Beds (113 Facilities)


The Bed Deserts: The bottom counties demonstrate critical scarcity:
County Name | Total Beds | Facility Count |

Mono | 17 | 1 |
Mariposa | 34 | 1 |
Trinity | 38 | 1 |
Sierra | 39 | 1 |

B. Distribution by Facility Type
The largest portion of licensed capacity is for long-term care, not intensive medical care.
License Category Description Total Beds Avg Beds
Skilled Nursing Facility     109,362    101.1
General Acute Care Hospital   84,271    185.6
Acute Psychiatric Hospital     4,260    101.4

Acute Bed Gap: While General Acute Care Hospitals are typically larger (Avg 185 beds), the sheer volume of Skilled Nursing Beds (109k) means the state's infrastructure focus is on long-term maintenance rather than high-volume acute surge capacity.

The "Bed Deserts" (Bottom 3 Counties)
Business Insight: Rural counties are critically underserved. Mono County has only 1 facility with 17 beds.

Key Findings: Mono (17), Mariposa (34), Trinity (38), Sierra (39).


Facility Type Distribution
Business Insight: The majority of beds are in Skilled Nursing, not Acute Hospitals.

Results:
Skilled Nursing Facility: 109,362 Beds (Avg size: 101)
General Acute Care Hospital: 84,271 Beds (Avg size: 185)
Acute Psychiatric Hospital: 4,260 Beds (Avg size: 101)


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


# DataLimitations

The MYSQL Wizard was only importing 1862 rows of approx 10800 rows. I found that commas in the Total_Number_Beds column was being misread. I used a simple find replace to replace every comma with a space.

# Technical_SQL_Details

A. Geographic Distribution (Top 3 Counties)
Business Insight: Los Angeles is the dominant hub with nearly 4x the capacity of San Diego.
SQL
SELECT
	COUNTY_NAME,
	SUM(TOTAL_NUMBER_BEDS) as Total_Beds,
	COUNT(*) as Facility_Count,
	AVG((TOTAL_NUMBER_BEDS as Avg_Beds_Per_Facility
FROM California_healthcare_cleanc
GROUP BY COUNTY_NAME
ORDER BY Total_Beds DESC
LIMIT 10;
Top 3 Results:
Los Angeles: 64,642 Beds (615 Facilities)
San Diego: 16,597 Beds (125 Facilities)
Orange: 14,570 Beds (113 Facilities)

Business Insight: Rural counties are critically underserved. Mono County has only 1 facility with 17 beds.
SQL
SELECT
	COUNTY_NAME,
	SUM(TOTAL_NUMBER_BEDS)  as Total_Beds
FROM California_healthcare_cleanc
GROUP BY COUNTY_NAME
ORDER BY Total_Beds ASC
LIMIT 10;
Key Findings: Mono (17), Mariposa (34), Trinity (38), Sierra (39).

Facility Type Distribution
Business Insight: The majority of beds are in Skilled Nursing, not Acute Hospitals.
SQL
SELECT
    LICENSE_CATEGORY_DESC,
	SUM(TOTAL_NUMBER_BEDS) as Total_Beds,
	AVG(TOTAL_NUMBER_BEDS) as Avg_Size
FROM healthcare_cleanc
GROUP BY LICENSE_CATEGORY_DESC
ORDER BY Total_Beds DESC;
Results:
Skilled Nursing Facility: 109,362 Beds (Avg size: 101)
General Acute Care Hospital: 84,271 Beds (Avg size: 185)
Acute Psychiatric Hospital: 4,260 Beds (Avg size: 101)

Emergency Room Correlation
Business Insight: Most beds (117k+) are in facilities marked "Not Applicable" for ER service (likely Nursing Homes), confirming that most bed capacity is non-emergency.
SQL
SELECT
    ER_SERVICE_LEVEL_DESC,
	SUM(TOTAL_NUMBER_BEDS) as Total_Beds
FROM California_healthcare_cleanc
GROUP BY ER_SERVICE_LEVEL_DESC
ORDER BY Total_Beds DESC;
Results:
Not Applicable: 117,231
Emergency Basic: 66,810
None : 11,255






