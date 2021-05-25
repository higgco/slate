# Data Dictionary


Higg assessments contain a large amount of data. The FEM export has over 4000 columns for each assessment. Defining every indicator is beyond the scope of this API documentation. 

Instead, we define a dictionary of the most commonly used attributes to help with common operations. For indicators outside of this list, consult your local Higg expert for more information.

FSLM data definitions currently follow the SLCP Output Key dictionary.

BRM data definitions are being finalized as of the drafting of this document.

Once the FSLM Scoring Pilot is complete, this data dictionary will be enhanced to show the new Higg specific fields that are available.

## Dictionary

Field | Notes | Type
---------- | ------- | -------
surveyid | Unique ID for this module line |  STRING
version | Version of survey (ex: fem2017, fem2018, fem2019, fem2020, fslm, brm2019, brm2020) | STRING
groupid | Account ID of module owner | | STRING
groupname | Account name of module owner |  STRING
SAC_Id | Higg ID of module owner |  STRING
ParentCompany | Parent company (if any) of assessment owner |  STRING
users | Semi-colon delimited list of account users for this account |  STRING
posted | Indicates posted status of this module | BOOLEAN
verified | Indicates if this is an FEM or vFEM | BOOLEAN
related_rfi_answer | If verified == true, indicates the self-assessment ID that created this verified assessment |  STRING
scores | if 'scores' is in includes, a new scores key will be returned. See 'Scores' for more information
ghg | if 'ghg' is in includes, a new 'ghg' key will be returned. See 'GHG' for more information
usage | if 'usage' is in includes, a new 'usage' key will be returened. See 'Resource Usage' for more information
sitecountry | Facility country from the Facility profile |  STRING
sipindustrysector | Sector this facility operates in ex: ‘Footwear’ | STRING
sipfacilitytype | Type of facility. Ex: ‘Printing or Dyeing’ |  STRING
sipfacilityprocesseschem | Facility Chemical Processes. Ex: ‘Raw Material Storage’ | STRING
sipfacilityprocessesmaterials | Facility Material Processes. Ex: ‘Extrusion’ | STRING
sipfacilityprocessespkg | Facility Packaging Processes. Ex: ‘Cutting’| STRING
sipfacilityprocessesprintdye | Facility Print & Dye Processes. Ex: ‘Sublimation’ | STRING
sipfacilityprocessessew | Facility Sewing Processes. Ex: ‘Cutting’| STRING
sipfacilityprocessestrim | Facility Trim Process. Ex: ‘Casting’| STRING
sipfulltimeemployees | Employee count (pre-determined ranges): Ex: ‘501-1000’ | INTEGER
siparttimeemployees | Employee count (pre-determined ranges): Ex: ‘501-1000’ | INTEGER
sipfacilityannualprodvolunits | Unit of product, single selection, ‘Kilogram’, ‘Meter’, ‘Sq Yard’| STRING
sipmaterialtypes | Material Types. Ex: ‘Foams’ | STRING
sipmaterialbarriers | Material Types: Barriers. Ex: ‘Microporus Coating’| STRING
sipmaterialfoams | Material Types: Foams. Ex: ‘Polyethylene (PE) foam’| STRING
sipmaterialinsulation | Material Types: Insulation. Ex: ‘Sheep Wool Insulation’| STRING
sipmaterialleather | Material Types: Leather. Ex: ‘Goat Leather’| STRING
sipmaterialplastics | Material Types: Plastic. Ex: ‘Polyester Plastic’| STRING
sipmaterialmetals | Material Types: Metals. Ex: ‘Brass’| STRING
sipmaterialrubbers | Material Types: Rubbers. Ex: ‘Isoprene Rubber (IR)’| STRING
sipmaterialsynthleather | Material Types: Synthetic Leather. Ex: ‘Polyurethane (PU)’| STRING
sipmaterialtextiles | Material Types: Textiles. Ex: ‘Carbon fiber fabric’| STRING
sipmaterialwoodbased | Material Types: Wood. Ex: ‘Cork’ |  STRING
score.total | Total Higg score for this module | FLOAT
ems.score | Total score in EMS section | FLOAT
ems.level1 | Level 1 score in EMS section | FLOAT
ems.level2 | Level 2 score in EMS section | FLOAT
ems.level3 | Level 3 score in EMS section | FLOAT
energy.score | Total score for Energy section | FLOAT
energy.level1 | Level 1 score in Energy section | FLOAT
energy.level2 | Level 2 score in Energy section | FLOAT
waste.level1 | Level 1 score in Waste | FLOAT
waste.level2 | Level 2 score in Waste | FLOAT
waste.level3 | Level 3 score in Waste | FLOAT
water.score | Total score in Water Use section | FLOAT
water.level1 | Level 1 score in Water Use | FLOAT
water.level2 | Level 2 score in Water Use | FLOAT
water.level3 | Level 3 score in Water Use | FLOAT
air.score | Total score in Air Emissions section | FLOAT
air.level1 | Level 1 score in Air Emissions | FLOAT
airs.level2 | Level 2 score in Air Emissions | FLOAT
airs.level3 | Level 3 score in Air Emissions | FLOAT
chemicals.score | Total score in Chemicals Management section | FLOAT
chemicals.level1 | Level 1 score in Chemicals | FLOAT
chemicals.level2 | Level 2 score in Chemicals | FLOAT
chemicals.level3 | Level 3 score in Chemicals | FLOAT
*air.applicability | Selected applicability path for Air| STRING
*water.applicability | Selected applicability path for Water| STRING
*ems.applicability | Selected applicability path EMS| STRING
*wastewater.applicability | Selected applicability path for Wastewater| STRING
*waste.applicability | Selected applicability path for Waste| STRING
*chemicals.applicability | Selected applicability path for Chemicals| STRING
verificationDetails | if 'verificationDetails' is in includes the whole verification details will be reutrned. See 'Verification Details' for more informations | STRING
## Applicabilities

To be updated soon.