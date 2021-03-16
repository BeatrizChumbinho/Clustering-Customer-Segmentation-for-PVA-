# Clustering/Customer-Segmentation_for_PVA
Paralyzed Veterans of America (PVA) lapsed donors segmentation

Group Project Overview
This dataset was provided by the Paralyzed Veterans of America (PVA). PVA is a non-profit
organization that provides programs and services for US veterans with spinal cord injuries or disease.
With an in-house database of 13 million donors, PVA is also one of the largest direct mail fundraisers in
the United States of America.
Your task is to analyze a sample of the results of one of PVA's recent fundraising appeals, containing 95
412 donors. This mailing was sent to a total of 3.5 million PVA donors who were on the PVA database.
Everyone included in this database made at least one prior donation to PVA.
The mailing included a gift (or "premium") of personalized name & address labels plus an assortment of
10 note cards and envelopes. All of the donors who received this mailing were acquired by PVA through
similar premium-oriented appeals such as this.
One group that is of particular interest to PVA is "Lapsed" donors. These are individuals who made their
last donation to PVA 13 to 24 months ago. They represent an important group to PVA, since the longer
someone goes without donating, the less likely they will be to give again. Therefore, recapturing these
former donors is a critical aspect of PVA's fundraising efforts.As a Data Mining/Analytics Consultant, PVA asked you to develop a Customer Segmentation in such a
way that it will be possible for them to better understand how their donors behave and identify the
different segments of donors/potential donors within their database. You are expected to define, describe
and explain the clusters you choose. Invest time in reasoning how you want to do your clustering, possible
approaches, and advantages or disadvantages of different decisions. Simultaneous, you should briefly
express the marketing approach you recommend for each cluster.




+--------------------------------------------------------------------+
|                PARALYZED VETERANS OF AMERICA (PVA)                 |
|                  DATA DICTIONARY TO ACCOMPANY                      |
+--------------------------------------------------------------------+

Variable                    Description
--------------------------  ------------------------------------------
ODATEDW                     Origin Date. Date of donor's first gift
                            to PVA YYMM format (Year/Month).

OSOURCE                     Origin Source
                            - (Only 1rst 3 bytes are used)
                            - Defaulted to 00000 for conversion
                            - Code indicating which mailing list the
                              donor was originally acquired from
                            - A nominal or symbolic field.

TCODE                       Donor title code
                            000    = _
                            001    = MR.
                            001001 = MESSRS.
                            001002 = MR. & MRS.
                            002    = MRS.
                            002002 = MESDAMES
                            003    = MISS
                            003003 = MISSES
                            004    = DR.
                            004002 = DR. & MRS.
                            004004 = DOCTORS
                            005    = MADAME
                            006    = SERGEANT
                            009    = RABBI
                            010    = PROFESSOR
                            010002 = PROFESSOR & MRS.
                            010010 = PROFESSORS
                            011    = ADMIRAL
                            011002 = ADMIRAL & MRS.
                            012    = GENERAL
                            012002 = GENERAL & MRS.
                            013    = COLONEL
                            013002 = COLONEL & MRS.
                            014    = CAPTAIN
                            014002 = CAPTAIN & MRS.
                            015    = COMMANDER
                            015002 = COMMANDER & MRS.
                            016    = DEAN
                            017    = JUDGE
                            017002 = JUDGE & MRS.
                            018    = MAJOR
                            018002 = MAJOR & MRS.
                            019    = SENATOR
                            020    = GOVERNOR
                            021002 = SERGEANT & MRS.
                            022002 = COLNEL & MRS.
                            024    = LIEUTENANT
                            026    = MONSIGNOR
                            027    = REVEREND
                            028    = MS.
                            028028 = MSS.
                            029    = BISHOP
                            031    = AMBASSADOR
                            031002 = AMBASSADOR & MRS.
                            033    = CANTOR
                            036    = BROTHER
                            037    = SIR
                            038    = COMMODORE
                            040    = FATHER
                            042    = SISTER
                            043    = PRESIDENT
                            044    = MASTER
                            046    = MOTHER
                            047    = CHAPLAIN
                            048    = CORPORAL
                            050    = ELDER
                            056    = MAYOR
                            059002 = LIEUTENANT & MRS.
                            062    = LORD
                            063    = CARDINAL
                            064    = FRIEND
                            065    = FRIENDS
                            068    = ARCHDEACON
                            069    = CANON
                            070    = BISHOP
                            072002 = REVEREND & MRS.
                            073    = PASTOR
                            075    = ARCHBISHOP
                            085    = SPECIALIST
                            087    = PRIVATE
                            089    = SEAMAN
                            090    = AIRMAN
                            091    = JUSTICE
                            092    = MR. JUSTICE
                            100    = M.
                            103    = MLLE.
                            104    = CHANCELLOR
                            106    = REPRESENTATIVE
                            107    = SECRETARY
                            108    = LT. GOVERNOR
                            109    = LIC.
                            111    = SA.
                            114    = DA.
                            116    = SR.
                            117    = SRA.
                            118    = SRTA.
                            120    = YOUR MAJESTY
                            122    = HIS HIGHNESS
                            123    = HER HIGHNESS
                            124    = COUNT
                            125    = LADY
                            126    = PRINCE
                            127    = PRINCESS
                            128    = CHIEF
                            129    = BARON
                            130    = SHEIK
                            131    = PRINCE AND PRINCESS
                            132    = YOUR IMPERIAL MAJEST
                            135    = M. ET MME.
                            210    = PROF.

STATE                       State abbreviation (a nominal/symbolic field)
ZIP                         Zipcode (a nominal/symbolic field)
MAILCODE                    Mail Code
                            " "= Address is OK
                            B = Bad Address

PVASTATE                    EPVA State or PVA State
                            Indicates whether the donor lives in a state
                            served by the organization's EPVA chapter
                            P = PVA State
                            E = EPVA State (Northeastern US)

DOB                         Date of birth (YYMM, Year/Month format.)
NOEXCH                      Do Not Exchange Flag (For list rental)
                            _ = can be exchanged
                            X = do not exchange

RECINHSE                    In House File Flag
                            _ = Not an In House Record
                            X = Donor has given to PVA's In House program

RECP3                       P3 File Flag
                            _ = Not a P3 Record
                            X = Donor has given to PVA's P3 program

RECPGVG                     Planned Giving File Flag
                            _ = Not a Planned Giving Record
                            X = Planned Giving Record

RECSWEEP                    Sweepstakes file flag
                            _ = Not a Sweepstakes Record
                            X = Sweepstakes Record

MDMAUD                      The Major Donor Matrix code
                            The codes describe frequency and amount of
                            giving for donors who have given a $100+
                            gift at any time in their giving history.
                            An RFA (recency/frequency/monetary) field.

                            The (current) concatenated version is a nominal
                            or symbolic field. The individual bytes could separately be
                            used as fields and refer to the following:

                            First byte: Recency of Giving
                              C=Current Donor
                              L=Lapsed Donor
                              I=Inactive Donor
                              D=Dormant Donor

                            2nd byte: Frequency of Giving
                              1=One gift in the period of recency
                              2=Two-Four gifts in the period of recency
                              5=Five+ gifts in the period of recency

                            3rd byte: Amount of Giving
                              L=Less than $100(Low Dollar)
                              C=$100-499(Core)
                              M=$500-999(Major)
                              T=$1,000+(Top)

                            4th byte: Blank/meaningless/filler

                            'X' indicates that the donor is not a major donor.

                            For more information regarding the RFA codes, see
                            the promotion history field definitions.

DOMAIN                      DOMAIN/Cluster code. A nominal or symbolic field.
                            could be broken down by bytes as explained below.

                            1st byte = Urbanicity level of the donor's neighborhood
                              U=Urban
                              C=City
                              S=Suburban
                              T=Town
                              R=Rural

                            2nd byte = Socio-Economic status of the neighborhood
                              1 = Highest SES
                              2 = Average SES
                              3 = Lowest SES (except for Urban communities, where
                                  1 = Highest SES, 2 = Above average SES,
                                  3 = Below average SES, 4 = Lowest SES.)

HOMEOWNR                    Home Owner Flag
                            H = Home owner
                            U = Unknown

CHILD03                     Presence of Children age 0-3
                            B = Both, F = Female, M = Male

CHILD07                     Presence of Childern age 4-7
CHILD12                     Presence of Childern age 8-12
CHILD18                     Presence of Childern age 13-18

NUMCHLD                     NUMBER OF CHILDREN
INCOME                      HOUSEHOLD INCOME
GENDER                      Gender
                            M = Male
                            F = Female
                            U = Unknown
                            J = Joint Account, unknown gender

WEALTH1                     Wealth Rating
HIT                         MOR Flag # HIT (Mail Order Response)
                            Indicates total number of known times the donor has
                            responded to a mail order offer other than PVA's.

--------------------------  -------------------------------------------------
                            The following variables indicate the number of
                            known times the donor has responded to other
                            types of mail order offers.

MBCRAFT                     Buy Craft Hobby
MBGARDEN                    Buy Gardening
MBBOOKS                     Buy Books
MBCOLECT                    Buy Collectables
MAGFAML                     Buy General Family Mags
MAGFEM                      Buy Female Mags
MAGMALE                     Buy Sports Mags
PUBGARDN                    Gardening Pubs
PUBCULIN                    Culinary Pubs
PUBHLTH                     Health Pubs
PUBDOITY                    Do It Yourself Pubs
PUBNEWFN                    News / Finance Pubs
PUBPHOTO                    Photography Pubs
PUBOPP                      Opportunity Seekers Pubs

--------------------------  -------------------------------------------------

DATASRCE                    Source of Overlay Data
                            Indicates which third-party data source the donor
                            matched against
                            1 = MetroMail
                            2 = Polk
                            3 = Both

MALEMILI                    % Males active in the Military
MALEVET                     % Males Veterans
VIETVETS                    % Vietnam Vets
WWIIVETS                    % WWII Vets
LOCALGOV                    % Employed by Local Gov
STATEGOV                    % Employed by State Gov
FEDGOV                      % Employed by Fed Gov

SOLP3                       SOLICIT LIMITATION CODE P3
                               = can be mailed (Default)
                            00 = Do Not Solicit or Mail
                            01 = one solicitation per year
                            02 = two solicitations per year
                            03 = three solicitations per year
                            04 = four solicitations per year
                            05 = five solicitations per year
                            06 = six solicitations per year
                            12 = twelve solicitations per year

SOLIH                       SOLICITATION LIMIT CODE IN HOUSE
                               = can be mailed (Default)
                            00 = Do Not Solicit
                            01 = one solicitation per year
                            02 = two solicitations per year
                            03 = three solicitations per year
                            04 = four solicitations per year
                            05 = five solicitations per year
                            06 = six solicitations per year
                            12 = twelve solicitations per year

MAJOR                       Major ($$) Donor Flag
                            _ = Not a Major Donor
                            X = Major Donor

WEALTH2                     Wealth Rating
                            Wealth rating uses median family income and
                            population statistics from each area to
                            index relative wealth within each state
                            The segments are denoted 0-9, with 9 being
                            the highest income group and zero being the
                            lowest. Each rating has a different meaning
                            within each state.

GEOCODE                     Geo Cluster Code indicating the level geography at which
                            a record matches the census data.
                            A nominal or symbolic field.
                            Blank=No code has been assigned or did not
                            match at any level.

--------------------------  -------------------------------------------------
                            The following variables reflect donor interests,
                            as collected from third-party data sources

COLLECT1                    COLLECTABLE (Y/N)
VETERANS                    VETERANS (Y/N)
BIBLE                       BIBLE READING (Y/N)
CATLG                       SHOP BY CATALOG (Y/N)
HOMEE                       WORK FROM HOME (Y/N)
PETS                        HOUSEHOLD PETS (Y/N)
CDPLAY                      CD PLAYER OWNERS (Y/N)
STEREO                      STEREO/RECORDS/TAPES/CD (Y/N)
PCOWNERS                    HOME PC OWNERS/USERS
PHOTO                       PHOTOGRAPHY (Y/N)
CRAFTS                      CRAFTS (Y/N)
FISHER                      FISHING (Y/N)
GARDENIN                    GARDENING (Y/N)
BOATS                       POWER BOATING (Y/N)
WALKER                      WALK FOR HEALTH (Y/N)
KIDSTUFF                    BUYS CHILDREN'S PRODUCTS (Y/N)
CARDS                       STATIONARY/CARDS BUYER (Y/N)
PLATES                      PLATE COLLECTOR (Y/N)

LIFESRC                     LIFE STYLE DATA SOURCE
                            Indicates source of the lifestyle variables listed
                            above
                            1 = MATCHED ON METRO MAIL ONLY
                            2 = MATCHED ON POLK ONLY
                            3 = MATCHED BOTH MM AND POLK

--------------------------  -------------------------------------------------

PEPSTRFL                    Indicates PEP Star RFA Status
                            blank = Not considered to be a PEP Star
                            'X'   = Has PEP Star RFA Status

--------------------------  -------------------------------------------------

                            The following variables reflect characteristics
                            of the donors neighborhood, as collected from the
                            2010 US Census.

POP901                      Number of Persons
POP902                      Number of Families
POP903                      Number of Households
POP90C1                     Percent Population in Urbanized Area
POP90C2                     Percent Population Outside Urbanized Area
POP90C3                     Percent Population Inside Rural Area
POP90C4                     Percent Male
POP90C5                     Percent Female
ETH1                        Percent White
ETH2                        Percent Black
ETH3                        Percent Native American
ETH4                        Percent Pacific Islander/Asian
ETH5                        Percent Hispanic
ETH6                        Percent Asian Indian
ETH7                        Percent Japanese
ETH8                        Percent Chinese
ETH9                        Percent Philipino
ETH10                       Percent Korean
ETH11                       Percent Vietnamese
ETH12                       Percent Hawaiian
ETH13                       Percent Mexican
ETH14                       Percent Puerto Rican
ETH15                       Percent Cuban
ETH16                       Percent Other Hispanic
AGE901                      Median Age of Population
AGE902                      Median Age of Adults 18 or Older
AGE903                      Median Age of Adults 25 or Older
AGE904                      Average Age of Population
AGE905                      Average Age of Adults >= 18
AGE906                      Average Age of Adults >= 25
AGE907                      Percent Population Under Age 18
CHIL1                       Percent Children Under Age 7
CHIL2                       Percent Children Age 7 - 13
CHIL3                       Percent Children Age 14-17
AGEC1                       Percent Adults Age18-24
AGEC2                       Percent Adults Age 25-34
AGEC3                       Percent Adults Age 35-44
AGEC4                       Percent Adults Age 45-54
AGEC5                       Percent Adults Age 55-64
AGEC6                       Percent Adults Age 65-74
AGEC7                       Percent Adults Age >= 75
CHILC1                      Percent Children Age <=2
CHILC2                      Percent Children Age 3-5
CHILC3                      Percent Children Age 6-11
CHILC4                      Percent Children Age 12-15
CHILC5                      Percent Children Age 16-18
HHAGE1                      Percent Households w/ Person 65+
HHAGE2                      Percent Households w/ Person 65+ Living Alone
HHAGE3                      Percent Households Headed by an Elderly Person Age 65+
HHN1                        Percent 1 Person Households
HHN2                        Percent 2 Person Households
HHN3                        Percent 3 or More Person Households
HHN4                        Percent 4 or More Person Households
HHN5                        Percent 5 or More Person Households
HHN6                        Percent 6 Person Households
MARR1                       Percent Married
MARR2                       Percent Separated or Divorced
MARR3                       Percent Widowed
MARR4                       Percent Never Married
HHP1                        Median Person Per Household
HHP2                        Average Person Per Household
DW1                         Percent Single Unit Structure
DW2                         Percent Detached Single Unit Structure
DW3                         Percent Duplex Structure
DW4                         Percent Multi (2+) Unit Structures
DW5                         Percent 3+ Unit Structures
DW6                         Percent Housing Units in 5+ Unit Structure
DW7                         Percent Group Quarters
DW8                         Percent Institutional Group Quarters
DW9                         Non-Institutional Group Quarters
HV1                         Median Home Value in hundreds
HV2                         Average Home Value in hundreds
HV3                         Median Contract Rent in hundreds
HV4                         Average Contract Rent in hundreds
HU1                         Percent Owner Occupied Housing Units
HU2                         Percent Renter Occupied Housing Units
HU3                         Percent Occupied Housing Units
HU4                         Percent Vacant Housing Units
HU5                         Percent Seasonal/Recreational Vacant Units
HHD1                        Percent Households w/ Related Children
HHD2                        Percent Households w/ Families
HHD3                        Percent Married Couple Families
HHD4                        Percent Married Couples w/ Related Children
HHD5                        Percent Persons in Family Household
HHD6                        Percent Persons in Non-Family Household
HHD7                        Percent Single Parent Households
HHD8                        Percent Male Householder w/ Child
HHD9                        Percent Female Householder w/ Child
HHD10                       Percent Single Male Householder
HHD11                       Percent Single Female Householder
HHD12                       Percent Households w/ Non-Family Living Arrangements
ETHC1                       Percent White < Age 15
ETHC2                       Percent White Age 15 - 59
ETHC3                       Percent White Age 60+
ETHC4                       Percent Black < Age 15
ETHC5                       Percent Black Age 15 - 59
ETHC6                       Percent Black Age 60+
HVP1                        Percent Home Value >= $200,000
HVP2                        Percent Home Value >= $150,000
HVP3                        Percent Home Value >= $100,000
HVP4                        Percent Home Value >= $75,000
HVP5                        Percent Home Value >= $50,000
HVP6                        Percent Home Value >= $300,000
HUR1                        $ 1 or 2 Room Housing Units
HUR2                        Percent >= 6 Room Housing Units
RHP1                        Median Number of Rooms per Housing Unit
RHP2                        Average Number of Rooms per Housing Unit
RHP3                        Median Number of Persons per Housing Unit
RHP4                        Average Number of Persons per Room
HUPA1                       Percent Housing Units w/ 2 thru 9 Units at the Address
HUPA2                       Percent Housing Units w/ >= 10 Units at the Address
HUPA3                       Percent Mobile Homes or Trailers
HUPA4                       Percent Renter Occupied Single Unit Structure
HUPA5                       Percent Renter Occupied, 2 - 4 Units
HUPA6                       Percent Renter Occupied, 5+ Units
HUPA7                       Percent Renter Occupied Mobile Homes or Trailers
RP1                         Percent Renters Paying >= $500 per Month
RP2                         Percent Renters Paying >= $400 per Month
RP3                         Percent Renters Paying >= $300 per Month
RP4                         Percent Renters Paying >= $200 per Month
MSA                         MSA Code
ADI                         ADI Code
DMA                         DMA Code
IC1                         Median Household Income in hundreds
IC2                         Median Family Income in hundreds
IC3                         Average Household Income in hundreds
IC4                         Average Family Income in hundreds
IC5                         Per Capita Income
IC6                         Percent Households w/ Income < $15,000
IC7                         Percent Households w/ Income $15,000 - $24,999
IC8                         Percent Households w/ Income $25,000 - $34,999
IC9                         Percent Households w/ Income $35,000 - $49,999
IC10                        Percent Households w/ Income $50,000 - $74,999
IC11                        Percent Households w/ Income $75,000 - $99,999
IC12                        Percent Households w/ Income $100,000 - $124,999
IC13                        Percent Households w/ Income $125,000 - $149,999
IC14                        Percent Households w/ Income >= $150,000
IC15                        Percent Families w/ Income < $15,000
IC16                        Percent Families w/ Income $15,000 - $24,999
IC17                        Percent Families w/ Income $25,000 - 34,999
IC18                        Percent Families w/ Income $35,000 - $49,999
IC19                        Percent Families w/ Income $50,000 - $74,999
IC20                        Percent Families w/ Income $75,000 - $99,999
IC21                        Percent Families w/ Income $100,000 - $124,999
IC22                        Percent Families w/ Income $125,000 - $149,999
IC23                        Percent Families w/ Income >= $150,000
HHAS1                       Percent Households on Social Security
HHAS2                       Percent Households on Public Assistance
HHAS3                       Percent Households w/ Interest, Rental or Dividend Income
HHAS4                       Percent Persons Below Poverty Level
MC1                         Percent Persons Move in Since 2005
MC2                         Percent Persons in Same House in 2005
MC3                         Percent Persons in Different State/Country in 2005
TPE1                        Percent Driving to Work Alone Car/Truck/Van
TPE2                        Percent Carpooling Car/Truck/Van)
TPE3                        Percent Using Public Transportation
TPE4                        Percent Using Bus/Trolley
TPE5                        Percent Using Railways
TPE6                        Percent Using Taxi/Ferry
TPE7                        Percent Using Motorcycles
TPE8                        Percent Using Other Transportation
TPE9                        Percent Working at Home/No Transportation
PEC1                        Percent Working Outside State of Residence
PEC2                        Percent Working Outside County of Residence in State
TPE10                       Median Travel Time to Work in minutes
TPE11                       Mean Travel Time to Work in minutes
TPE12                       Percent Traveling 60+ Minutes to Work
TPE13                       Percent Traveling 15 - 59 Minutes to Work
LFC1                        Percent Adults in Labor Force
LFC2                        Percent Adult Males in Labor Force
LFC3                        Percent Females in Labor Force
LFC4                        Percent Adult Males Employed
LFC5                        Percent Adult Females Employed
LFC6                        Percent Mothers Employed Married and Single
LFC7                        Percent 2 Parent Earner Families
LFC8                        Percent Single Mother w/ Child in Labor Force
LFC9                        Percent Single Father w/ Child in Labor Force
LFC10                       Percent Families w/ Child w/ no Workers
OCC1                        Percent Professional
OCC2                        Percent Managerial
OCC3                        Percent Technical
OCC4                        Percent Sales
OCC5                        Percent Clerical/Administrative Support
OCC6                        Percent Private Household Service Occ.
OCC7                        Percent Protective Service Occ.
OCC8                        Percent Other Service Occ.
OCC9                        Percent Farmers
OCC10                       Percent Craftsmen, Precision, Repair
OCC11                       Percent Operatives, Machine
OCC12                       Percent Transportation
OCC13                       Percent Laborers, Handlers, Helpers
EIC1                        Percent Employed in Agriculture
EIC2                        Percent Employed in Mining
EIC3                        Percent Employed in Construction
EIC4                        Percent Employed in Manufacturing
EIC5                        Percent Employed in Transportation
EIC6                        Percent Employed in Communications
EIC7                        Percent Employed in Wholesale Trade
EIC8                        Percent Employed in Retail Industry
EIC9                        Percent Employed in Finance, Insurance, Real Estate
EIC10                       Percent Employed in Business and Repair
EIC11                       Percent Employed in Personnal Services
EIC12                       Percent Employed in Entertainment and Recreation
EIC13                       Percent Employed in Health Services
EIC14                       Percent Employed in Educational Services
EIC15                       Percent Employed in Other Professional Services
EIC16                       Percent Employed in Public Administration
OEDC1                       Percent Employed by Local Government
OEDC2                       Percent Employed by State Government
OEDC3                       Percent Employed by Federal Government
OEDC4                       Percent Self Employed
OEDC5                       Percent Private Profit Wage or Salaried Worker
OEDC6                       Percent Private Non-Profit Wage or Salaried Worker
OEDC7                       Percent Unpaid Family Workers
EC1                         Median Years of School Completed by Adults 25+
EC2                         Percent Adults 25+ Grades 0-8
EC3                         Percent Adults 25+ w/ some High School
EC4                         Percent Adults 25+ Completed High School or Equivalency
EC5                         Percent Adults 25+ w/ some College
EC6                         Percent Adults 25+ w/ Associates Degree
EC7                         Percent Adults 25+ w/ Bachelors Degree
EC8                         Percent Adults 25+ Graduate Degree
SEC1                        Percent Persons Enrolled in Private Schools
SEC2                        Percent Persons Enrolled in Public Schools
SEC3                        Percent Persons Enrolled in Preschool
SEC4                        Percent Persons Enrolled in Elementary or High School
SEC5                        Percent Persons in College
AFC1                        Percent Adults in Active Military Service
AFC2                        Percent Males in Active Military Service
AFC3                        Percent Females in Active Military Service
AFC4                        Percent Adult Veterans Age 16+
AFC5                        Percent Male Veterans Age 16+
AFC6                        Percent Female Veterans Age 16+
VC1                         Percent Vietnam Veterans Age 16+
VC2                         Percent Korean Veterans Age 16+
VC3                         Percent WW2 Veterans Age 16+
VC4                         Percent Veterans Serving After May 1995 Only
ANC1                        Percent Dutch Ancestry
ANC2                        Percent English Ancestry
ANC3                        Percent French Ancestry
ANC4                        Percent German Ancestry
ANC5                        Percent Greek Ancestry
ANC6                        Percent Hungarian Ancestry
ANC7                        Percent Irish Ancestry
ANC8                        Percent Italian Ancestry
ANC9                        Percent Norwegian Ancestry
ANC10                       Percent Polish Ancestry
ANC11                       Percent Portuguese Ancestry
ANC12                       Percent Russian Ancestry
ANC13                       Percent Scottish Ancestry
ANC14                       Percent Swedish Ancestry
ANC15                       Percent Ukranian Ancestry
POBC1                       Percent Foreign Born
POBC2                       Percent Born in State of Residence
LSC1                        Percent English Only Speaking
LSC2                        Percent Spanish Speaking
LSC3                        Percent Asian Speaking
LSC4                        Percent Other Language Speaking
VOC1                        Percent Households w/ 1+ Vehicles
VOC2                        Percent Households w/ 2+ Vehicles
VOC3                        Percent Households w/ 3+ Vehicles
HC1                         Percent Median Length of Residence
HC2                         Percent Median Age of Occupied Dwellings in years
HC3                         Percent Owner Occupied Structures Built Since 2009
HC4                         Percent Owner Occupied Structures Built Since 2005
HC5                         Percent Owner Occupied Structures Built Since 2000
HC6                         Percent Owner Occupied Structures Built Since 1990
HC7                         Percent Owner Occupied Structures Built Since 1980
HC8                         Percent Owner Occupied Structures Built Prior to 1860
HC9                         Percent Owner Occupied Condominiums
HC10                        Percent Renter Occupied Condominiums
HC11                        Percent Occupied Housing Units Heated by Utility Gas
HC12                        Percent Occupied Housing Units Heated by Bottled, Tank or LP
HC13                        Percent Occupied Housing Units Heated by Electricity
HC14                        Percent Occupied Housing Units Heated by Fuel Oil
HC15                        Percent Occupied Housing Units Heated by Solar Energy
HC16                        Percent Occupied Housing Units Heated by Coal, Wood, Other
HC17                        Percent Housing Units w/ Public Water Source
HC18                        Percent Housing Units w/ Well Water Source
HC19                        Percent Housing Units w/ Public Sewer Source
HC20                        Percent Housing Units w/ Complete Plumbing Facilities
HC21                        Percent Housing Units w/ Telephones
MHUC1                       Median Homeowner Cost w/ Mortgage per Month dollars
MHUC2                       Median Homeowner Cost w/out Mortgage per Month dollars
AC1                         Percent Adults Age 55-59
AC2                         Percent Adults Age 60-64

--------------------------  -------------------------------------------------

                            The fields listed below are from the promotion history file.

                            PROMOTION CODES:
                            ----------------

                            The following lists the promotion codes and their
                            respective field names (where XXXX refers to ADATE, RFA,
                            RDATE and RAMNT.)

                            '17NK' ==> xxxx_2 (mailing was used to construct
                                               the target fields)
                            '16NK' ==> xxxx_3
                            '16TK' ==> xxxx_4
                            '16SK' ==> xxxx_5
                            '16LL' ==> xxxx_6
                            '16G1' ==> xxxx_7
                            '16GK' ==> xxxx_8
                            '16CC' ==> xxxx_9
                            '16WL' ==> xxxx_10
                            '16X1' ==> xxxx_11
                            '16XK' ==> xxxx_12
                            '15FS' ==> xxxx_13
                            '15NK' ==> xxxx_14
                            '15TK' ==> xxxx_15
                            '15LL' ==> xxxx_16
                            '15G1' ==> xxxx_17
                            '15GK' ==> xxxx_18
                            '15CC' ==> xxxx_19
                            '15WL' ==> xxxx_20
                            '15X1' ==> xxxx_21
                            '15XK' ==> xxxx_22
                            '14FS' ==> xxxx_23
                            '14NK' ==> xxxx_24

                            1st 2 bytes of the code refers to the year of the
                            mailing while 3rd and 4th bytes refer to the
                            following promotion codes/types:

                            LL mailings had labels only
                            WL mailings had labels only
                            CC mailings are calendars with stickers but do
                               not have labels
                            FS mailings are blank cards that fold into
                               thirds with labels
                            NK mailings are blank cards with labels
                            SK mailings are blank cards with labels
                            TK mailings have thank you printed on the
                               outside with labels
                            GK mailings are general greeting cards (an
                               assortment of birthday, sympathy, blank, & get
                               well) with labels
                            XK mailings are Christmas cards with labels
                            X1 mailings have labels and a notepad
                            G1 mailings have labels and a notepad

                            This information could certainly be used to calculate
                            several summary variables that count the number of
                            occurrences of various types of promotions received
                            in the most recent 12-36 months, etc.

                            RFA (RECENCY/FREQUENCY/AMOUNT)
                            ------------------------------

                            The RFA (recency/frequency/amount) status of the
                            donors (as of the promotion dates) is included in the
                            RFA fields.

                            The (current) concatenated version is a nominal
                            or symbolic field. The individual bytes could
                            separately be used as fields and refer to the
                            following:

                            First Byte of code is concerned with RECENCY
                            based on Date of the last Gift

                            F=FIRST TIME DONOR Anyone who has made their
                              first donation in the last 6 months and has
                              made just one donation.

                            N=NEW DONOR Anyone who has made their first
                              donation in the last 12 months and is not a
                              First time donor.  This is everyone who made
                              their first donation 7-12 months ago, or
                              people who made their first donation between
                              0-6 months ago and have made 2 or more
                              donations.

                            A=ACTIVE DONOR Anyone who made their first
                              donation more than 12 months ago and has made
                              a donation in the last 12 months.

                            L=LAPSING DONOR A previous donor who made their
                              last donation between 13-24 months ago.

                            I=INACTIVE DONOR A previous donor who has not
                              made a donation in the last 24 months.  It is
                              people who made a donation 25+ months ago.

                            S=STAR DONOR STAR Donors are individuals who
                              have given to 3 consecutive card mailings.


                            Second Byte of code is concerned with FREQUENCY
                            based on the period of recency.  The period of
                            recency for all groups except L and I is the
                            last 12 months.  For L it is 13-24 months ago,
                            and for I it is 25-36 months ago.  There are
                            four valid frequency codes.

                            1=One gift in the period of recency
                            2=Two gift in the period of recency
                            3=Three gifts in the period of recency
                            4=Four or more gifts in the period of recency

                            Third byte of the code is the Amount of the last
                            gift.

                            A=$0.01  -  $1.99
                            B=$2.00  -  $2.99
                            C=$3.00  -  $4.99
                            D=$5.00  -  $9.99
                            E=$10.00 - $14.99
                            F=$15.00 - $24.99
                            G=$25.00 and above


ADATE_2                     Date the 17NK promotion was mailed
ADATE_3                     Date the 16NK promotion was mailed
ADATE_4                     Date the 16TK promotion was mailed
ADATE_5                     Date the 16SK promotion was mailed
ADATE_6                     Date the 16LL promotion was mailed
ADATE_7                     Date the 16G1 promotion was mailed
ADATE_8                     Date the 16GK promotion was mailed
ADATE_9                     Date the 16CC promotion was mailed
ADATE_10                    Date the 16WL promotion was mailed
ADATE_11                    Date the 16X1 promotion was mailed
ADATE_12                    Date the 16XK promotion was mailed
ADATE_13                    Date the 15FS promotion was mailed
ADATE_14                    Date the 15NK promotion was mailed
ADATE_15                    Date the 15TK promotion was mailed
ADATE_16                    Date the 15LL promotion was mailed
ADATE_17                    Date the 15G1 promotion was mailed
ADATE_18                    Date the 15GK promotion was mailed
ADATE_19                    Date the 15CC promotion was mailed
ADATE_20                    Date the 15WL promotion was mailed
ADATE_21                    Date the 15X1 promotion was mailed
ADATE_22                    Date the 15XK promotion was mailed
ADATE_23                    Date the 14FS promotion was mailed
ADATE_24                    Date the 14NK promotion was mailed

RFA_2                       Donor's RFA status as of 17NK promotion date
RFA_3                       Donor's RFA status as of 16NK promotion date
RFA_4                       Donor's RFA status as of 16TK promotion date
RFA_5                       Donor's RFA status as of 16SK promotion date
RFA_6                       Donor's RFA status as of 16LL promotion date
RFA_7                       Donor's RFA status as of 16G1 promotion date
RFA_8                       Donor's RFA status as of 16GK promotion date
RFA_9                       Donor's RFA status as of 16CC promotion date
RFA_10                      Donor's RFA status as of 16WL promotion date
RFA_11                      Donor's RFA status as of 16X1 promotion date
RFA_12                      Donor's RFA status as of 16XK promotion date
RFA_13                      Donor's RFA status as of 15FS promotion date
RFA_14                      Donor's RFA status as of 15NK promotion date
RFA_15                      Donor's RFA status as of 15TK promotion date
RFA_16                      Donor's RFA status as of 15LL promotion date
RFA_17                      Donor's RFA status as of 15G1 promotion date
RFA_18                      Donor's RFA status as of 15GK promotion date
RFA_19                      Donor's RFA status as of 15CC promotion date
RFA_20                      Donor's RFA status as of 15WL promotion date
RFA_21                      Donor's RFA status as of 15X1 promotion date
RFA_22                      Donor's RFA status as of 15XK promotion date
RFA_23                      Donor's RFA status as of 14FS promotion date
RFA_24                      Donor's RFA status as of 14NK promotion date

--------------------------  -------------------------------------------------
                            The following fields are summary variables from
                            the promotion history file.

CARDPROM                    Lifetime number of card promotions received to
                            date. Card promotions are promotion type FS, GK,
                            TK, SK, NK, XK, UF, UU.
MAXADATE                    Date of the most recent promotion received (in
                            YYMM, Year/Month format)
NUMPROM                     Lifetime number of promotions received to date
CARDPM12                    Number of card promotions received in the last
                            12 months (in terms of calendar months translates
                            into 1603-1702)
NUMPRM12                    Number of promotions received in the last 12
                            months (in terms of calendar months translates
                            into 1603-1702)

--------------------------  -------------------------------------------------
                            The following fields are from the giving history
                            file.

RDATE_3                     Date the gift was received for 16NK
RDATE_4                     Date the gift was received for 16TK
RDATE_5                     Date the gift was received for 16SK
RDATE_6                     Date the gift was received for 16LL
RDATE_7                     Date the gift was received for 16G1
RDATE_8                     Date the gift was received for 16GK
RDATE_9                     Date the gift was received for 16CC
RDATE_10                    Date the gift was received for 16WL
RDATE_11                    Date the gift was received for 16X1
RDATE_12                    Date the gift was received for 16XK
RDATE_13                    Date the gift was received for 15FS
RDATE_14                    Date the gift was received for 15NK
RDATE_15                    Date the gift was received for 15TK
RDATE_16                    Date the gift was received for 15LL
RDATE_17                    Date the gift was received for 15G1
RDATE_18                    Date the gift was received for 15GK
RDATE_19                    Date the gift was received for 15CC
RDATE_20                    Date the gift was received for 15WL
RDATE_21                    Date the gift was received for 15X1
RDATE_22                    Date the gift was received for 15XK
RDATE_23                    Date the gift was received for 14FS
RDATE_24                    Date the gift was received for 14NK

RAMNT_3                     Dollar amount of the gift for 16NK
RAMNT_4                     Dollar amount of the gift for 16TK
RAMNT_5                     Dollar amount of the gift for 16SK
RAMNT_6                     Dollar amount of the gift for 16LL
RAMNT_7                     Dollar amount of the gift for 16G1
RAMNT_8                     Dollar amount of the gift for 16GK
RAMNT_9                     Dollar amount of the gift for 16CC
RAMNT_10                    Dollar amount of the gift for 16WL
RAMNT_11                    Dollar amount of the gift for 16X1
RAMNT_12                    Dollar amount of the gift for 16XK
RAMNT_13                    Dollar amount of the gift for 15FS
RAMNT_14                    Dollar amount of the gift for 15NK
RAMNT_15                    Dollar amount of the gift for 15TK
RAMNT_16                    Dollar amount of the gift for 15LL
RAMNT_17                    Dollar amount of the gift for 15G1
RAMNT_18                    Dollar amount of the gift for 15GK
RAMNT_19                    Dollar amount of the gift for 15CC
RAMNT_20                    Dollar amount of the gift for 15WL
RAMNT_21                    Dollar amount of the gift for 15X1
RAMNT_22                    Dollar amount of the gift for 15XK
RAMNT_23                    Dollar amount of the gift for 14FS
RAMNT_24                    Dollar amount of the gift for 14NK

--------------------------  -------------------------------------------------
                            The following fields are summary variables from
                            the giving history file.

RAMNTALL                    Dollar amount of lifetime gifts to date
NGIFTALL                    Number of lifetime gifts to date
CARDGIFT                    Number of lifetime gifts to card promotions to date
MINRAMNT                    Dollar amount of smallest gift to date
MINRDATE                    Date associated with the smallest gift to date
MAXRAMNT                    Dollar amount of largest gift to date
MAXRDATE                    Date associated with the largest gift to date
LASTGIFT                    Dollar amount of most recent gift
LASTDATE                    Date associated with the most recent gift
FISTDATE                    Date of first gift
NEXTDATE                    Date of second gift
TIMELAG                     Number of months between first and second gift
AVGGIFT                     Average dollar amount of gifts to date

--------------------------  -------------------------------------------------
CONTROLN                    Control number (unique record identifier)

HPHONE_D                    Indicator for presence of a published home
                            phone number

--------------------------  -------------------------------------------------
                            (See the section on RFA for the meaning of the
                            codes)

RFA_2R                      Recency code for RFA_2
RFA_2F                      Frequency code for RFA_2
RFA_2A                      Donation Amount code for RFA_2
MDMAUD_R                    Recency code for MDMAUD
MDMAUD_F                    Frequecy code for MDMAUD
MDMAUD_A                    Donation Amount code for MDMAUD

--------------------------  -------------------------------------------------

GEOCODE2                    County Size Code
