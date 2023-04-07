---
layout: default
title: Heat Pump RTU
parent: Measures
grand_parent: Documentation
nav_order: 4
---

![](hvac_hp_rtu.001.png)

**Evaluation Only. Created with Aspose.Words. Copyright 2003-2023 Aspose Pty Ltd.**
## <a name="_toc131683764"></a>**Executive Summary**
Building on the successfully completed effort to calibrate and validate the U.S. Department of Energy’s ResStock™ and ComStock™ models over the past 3 years, the objective of this work is to produce national data sets that empower analysts working for federal, state, utility, city, and manufacturer stakeholders to answer a broad range of analysis questions. 

The goal of this work is to develop energy efficiency, electrification, and demand flexibility end-use load shapes (electricity, gas, propane, or fuel oil) that cover a majority of the high-impact, market-ready (or nearly market-ready) measures. “Measures” refers to energy efficiency variables that can be applied to buildings during modeling.

An *end-use savings shape* is the difference in energy consumption between a baseline building and a building with an energy efficiency, electrification, or demand flexibility measure applied. It results in a timeseries profile that is broken down by end use and fuel (electricity or on-site gas, propane, or fuel oil use) at each time step. 

ComStock is a highly granular, bottom-up model that uses multiple data sources, statistical sampling methods, and advanced building energy simulations to estimate the annual subhourly energy consumption of the commercial building stock across the United States. The baseline model intends to represent the U.S. commercial building stock as it existed in 2018. The methodology and results of the baseline model are discussed in the final technical report of the [End-Use Load Profiles](https://www.nrel.gov/buildings/end-use-load-profiles.html) project.

This documentation focuses on a single end-use savings shape measure—heat pump rooftop units.

The heat pump rooftop units (RTUs) measure replaces gas furnace and electric resistance RTUs with high-efficiency heat pump rooftop units (HP-RTUs). The HP-RTUs are intended to be top-of-the line, including high-efficiency fans and heat pump systems. The fans are variable speed, allowing the HP-RTUs to operate as single-zone variable air volume systems. The heat pumps are also variable speed, allowing for high part load performance. All schedules in the existing RTUs are transferred to the new HP-RTUs for consistency. Furthermore, any energy efficiency features in the existing baseline RTUs such as energy recovery or economizers are also transferred to the new HP-RTUs for consistency. This measure is applicable to approximately 45% of the ComStock floor area.

The HP-RTU measure demonstrates 10.3% total site energy savings (449 trillion British thermal units [TBtu]) for the U.S. commercial building stock modeled in ComStock (Figure 10). The savings are primarily attributed to:

- **42%** stock **heating gas** savings (190 TBtu)
- **−3%** stock **heating electricity** savings (**−**6 TBtu)
- **16%** stock **cooling electricity** savings (109 TBtu)
- **24%** stock **fan electricity** savings (144 TBtu)

The HP-RTU measure demonstrates between 19 and 28 million metric tons (MMT) of greenhouse gas emissions avoided for the three grid electricity scenarios presented, as well as 13 MMT of greenhouse gas emissions avoided for on-site natural gas consumption.





















## **Acknowledgments**
## The authors would like to acknowledge the valuable guidance and input provided by Ryan Meyer, Jon Winkler, Shanti Pless, and Long Engineering.
## **
##
<a name="_toc131925443"></a><a name="_toc131925489"></a><a name="_toc225583134"></a><a name="_toc291051272"></a><a name="_toc291052384"></a><a name="_toc314819176"></a><a name="_toc314823678"></a><a name="_toc352071746"></a>**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**

10

![](hvac_hp_rtu.001.png)
1. ## **Introduction**
This documentation covers “Heat Pump Rooftop Unit” upgrade methodology and briefly discusses key results.  Results can be accessed on the ComStock™ data lake at “[end-use-load-profiles-for-us-building-stock](https://data.openei.org/s3_viewer?bucket=oedi-data-lake&prefix=nrel-pds-building-stock%2Fend-use-load-profiles-for-us-building-stock%2F)” or via the Data Viewer at [comstock.nrel.gov.](https://comstock.nrel.gov/datasets)

|<a name="_toc291051274"></a><a name="_toc291052386"></a><a name="_toc314819178"></a><a name="_toc314823680"></a>**Measure Title**|**Heat Pump Rooftop Units**|
| :- | :- |
|Measure Definition|This measure replaces gas-fired and electric resistance rooftop units (RTUs) with high-efficiency heat pump RTUs (HP-RTUs). The HP-RTUs are assumed to be top-of-the-line with variable-speed compressors and fans allowing for high-performance part load operation. The heat pump is sized to the design cooling load and uses a compressor lockout temperature of 0°F. Supplemental electric resistance heat is used for any additional load. All energy efficiency features in the existing RTUs (energy recovery, demand control ventilation, etc.) as well as operating schedule are transferred to the new HP-RTU system for consistency.|
|Applicability|Buildings that contain gas-fired or electric resistance RTUs. |
|Not Applicable|Buildings that do not contain gas-fired or electric resistance RTUs. Also not applicable to kitchen spaces.|
|Release|EUSS 2023 Release 1|
1. ## **<a name="_toc131683768"></a>Technology Summary**
   1. ### <a name="_toc131683769"></a>**Decarbonizing the U.S. Commercial Building Stock**
Several simultaneous market transformations must occur to decarbonize U.S. energy systems. These include renewable power supply and storage options, widespread adoption of energy efficiency and electric demand flexibility, and ending the burning of on-site fossil fuels such as natural gas, propane, fuel oil, and others. Buildings burn fossil fuels on-site primarily for space heating, water heating, equipment loads, and cooking. The combined on-site natural gas combustion of the residential and commercial sectors is estimated to contribute to 9% of all U.S. carbon dioxide emissions annually [1].

Natural gas is the primary space heating and water heating fuel source for half of all commercial buildings in the United States by number, representing almost 70% of commercial building floor space, with more than half of the natural gas consumed for space heating [2]. In addition to natural gas, almost 10% of commercial buildings report using fuel oils and propane for primary space heating purposes [2]. This leaves only 25% of all commercial buildings currently relying on electricity as their only source for space heating needs [2].
1. ### <a name="_toc131683770"></a>**Heat Pump Rooftop Units As a Decarbonization Pathway**
Many technologies are used to provide space heating in commercial building heating, ventilating, and air conditioning (HVAC) systems. Packaged rooftop units (RTUs) are currently used to heat 37% of commercial buildings in the United States. (representing 50% of the total commercial floor space) [2]. Heat pumps currently provide space heating for only approximately 11% of commercial buildings (representing 15% of the total floor area) [2].

Heat pumps offer a high-performance electric option for commercial building space heating. Their use of electricity for heating enables pathways toward decarbonization, as they deliver space heating 2–4 times more efficiently than electric resistance options. Based on the 2018 Commercial Buildings Energy Consumption Survey (CBECS) data, it is estimated that fewer than 15% of commercial buildings utilize heat pumps for space heating equipment, and when they are in use, they are more commonly found in the warmer southern region of the United States [2]. 

Heat pump technologies are available on the market today to replace existing gas-fired or electric resistance RTU systems. Most manufacturers offer heat pump rooftop units (HP-RTU) with compressors capable of providing 105 kilowatts (kW) or less of cooling capacity (30 tons). There is remarkable opportunity for the growth and widespread adoption of this technology, and expansion of the field will have an extensive impact on electrification efforts.


1. ## <a name="_toc131683771"></a>**ComStock Baseline Approach**
The state of the existing RTUs in the U.S. Department of Energy’s commercial building stock model, ComStock™, is based on a combination of when the buildings were built and how the equipment has been updated over time, described in detail in the “ComStock Documentation” report by the National Renewable Energy Laboratory (NREL) [3]. Equipment performance is assumed to meet the energy code requirements in force at the time and place of installation. For this reason, most of the existing RTUs are modeled as constant air volume with single-speed compressors. This is influential to the results in this analysis because energy savings will be calculated based on the energy performance of the ComStock baseline models versus an updated version of the ComStock baseline that uses the proposed HP-RTUs.

The in-force energy code for the ComStock baseline is shown as a percentage of applicable floor area in Figure 1. Applicable floor area for this analysis includes ComStock buildings with “PSZ-AC with gas coil” and “PSZ-AC with electric coil” HVAC system types (where PSZ-AC stands for packaged single-zone air conditioner). Most ComStock baseline RTUs follow energy code requirements from the early 2000s. Other energy efficiency features such as demand control ventilation, energy recovery, and economizer control are only applied to baseline ComStock RTUs if required by the in-force energy code for the particular model. The ComStock workflow checks the necessary characteristics of each RTU to determine if the feature is required. Similarly, heating, cooling, and fan efficiencies are set based on the in-force code year. For models with the “PSZ-AC with electric coil” HVAC system type, the ComStock baseline will use electric resistance coils with a coefficient of performance (COP) of 1. For models with the “PSZ-AC with gas coil” HVAC system type, the ComStock baseline will use a gas furnace efficiency of generally around 80%.  

![Graphical user interface, application, table

Description automatically generated](hvac_hp_rtu.002.png)

<a name="_ref128139461"></a><a name="_toc131683791"></a>**Figure 1. ComStock baseline in-force energy code followed as a percentage of applicable floor area. Applicable floor area includes ComStock buildings with “PSZ-AC with gas coil” and “PSZ-AC with electric coil” HVAC system types.**
1. ## **<a name="_toc100058849"></a><a name="_toc100827778"></a><a name="_toc131683772"></a>Modeling Approach**
   1. ### <a name="_toc131683773"></a>**Applicability**
The HP-RTU measure is applicable to ComStock models with either gas furnace RTUs (“PSZ-AC with gas coil”) or electric resistance RTUs (“PSZ-AC with electric coil”). This accounts for about 45% of the ComStock floor area (Figure 2). ComStock HVAC distributions are informed by the 2012 CBECS. The methodology for interpreting CBECS data to create HVAC probability distributions for ComStock is discussed in the ComStock documentation [3]. The measure is also not applicable to space types that directly serve kitchens, spaces that are unconditioned, or RTUs with outdoor air ratios above 65% (due to an EnergyPlus® bug with cycling operation). 

![Graphical user interface, application, table

Description automatically generated](hvac_hp_rtu.003.png)

<a name="_ref119239895"></a><a name="_toc131683792"></a>**Figure 2. ComStock HVAC system type prevalence by stock floor area*.***

PTHP stands for packaged terminal heat pump, PVAV stands for packaged variable air volume, DOAS stands for dedicated outdoor air system, and PFP stands for parallel fan-power.
1. ### <a name="_toc131683774"></a>**Technology Specifics Such As Sizing, Performance, Configuration**
   1. #### <a name="_toc131683775"></a>***Heat Pump RTU Modeling***
The HP-RTUs are modeled using the EnergyPlus “AirloopHVAC:UnitarySystem” object [4], [5]. An OpenStudio measure is used in conjunction with the ComStock workflow to modify/remove any applicable RTUs in the ComStock baseline models (“PSZ-AC with gas coil” and “PSZ-AC with electric coil” in Figure 2) and articulate the appropriate HP-RTU objects and settings. Nonapplicable systems are not affected, nor are core operational parameters of systems such as schedules, thermostat set points, unoccupied operation behavior, and design outdoor airflow rates. Furthermore, energy-saving features found in applicable baseline RTUs such as airside heat/energy recovery, economizers, or demand control ventilation are preserved as-is for the new HP-RTU systems. This enables comparability, noting that these features are feasible and available in HP-RTU systems. The modeling details of the HP-RTU system are described further in the following subsections.
1. #### <a name="_toc131683776"></a>***Single-Zone VAV Operation***
The modeled HP-RTUs utilize a single-zone variable air volume (VAV) operation, which varies the supply airflow and discharge air temperature to efficiently maintain zone thermostat set points. As loads increase during heating operation, the supply air temperature is gradually raised until it hits a maximum threshold, and then supply airflow is increased until loads are met. As loads increase during cooling operation, supply air temperature is gradually lowered until it meets a minimum threshold, and the supply airflow is increased until loads are met (Figure 3) [6]. This is generally expected to provide fan energy savings during periods of reduced loads. The minimum supply airflow ratio modeled is 40%, which is common for single-zone RTUs [7]. The exception to the 40% minimum is when higher outdoor airflow rates are required to maintain ASHRAE Standard-62.1 minimum outdoor airflow rates: in these cases, the minimum flow rate to satisfy design outdoor air ventilation rates are modeled [8]. 

![Chart, line chart

Description automatically generated](hvac_hp_rtu.004.png)














<a name="_ref119245653"></a><a name="_toc131683793"></a>**Figure 3. Visual representation of single-zone VAV operation. Image from [10].**
1. #### <a name="_toc131683777"></a>***Cooling Performance*** 
The variable-speed direct expansion (DX) cooling system in the proposed HP-RTUs is modeled using the EnergyPlus “Coil:Cooling:DXMultiSpeed” object using four speeds of cooling [4], [5]. The highest speed (speed 4) represents the cooling performance at rated conditions with the compressor fully loaded. The efficiency values used for this study are based on a 10-ton variable-speed RTU with a full-load COP of 3.6 at rated conditions with an integrated energy efficiency ratio above 17 [9]. Because the EnergyPlus COP input is compressor-only, and therefore removes supply fan energy, the modeling input is adjusted to 4.11 COP using the methodology from the Pacific Northwest National Laboratory’s (PNNL’s) Daikin Rebel study [9]. 

The other speed levels (speeds 1 through 3) represent lower compressor speeds, which would occur when the required load to be met is less than the full capacity of the unit. Each speed corresponds to a fraction of the rated capacity, a rated COP, and a rated airflow. Lower compressor speeds generally show higher COP values, which allow for higher efficiencies during these periods of partial loading. For instance, a PNNL lab testing and modeling study showed 20%–50% annual cooling energy savings for variable-speed RTUs over conventional RTU cooling systems [9]. The capacity fractions and COPs for the different compressor speeds were determined using NREL lab testing data for three variable-speed, central-ducted air-conditioning (AC) systems. Because the testing is based on residential central AC units rather than commercial RTUs, the values derived from the testing are normalized to the rated COP of 4.11 to better represent a commercially available HP-RTU for this study (Table 1) [9]. Variable-speed HP-RTUs are capable of modulating to the specified fractions, but they may not do so in the same manner as the residential units the performance parameters are based on [7].

<a name="_ref127706543"></a><a name="_toc131683811"></a>**Table 1. Multispeed Cooling Coil Performance Parameters** 

Units with high outdoor air fraction may not achieve lower compressor speeds if it violates ventilation requirements.

|**Compressor Speed Level**|**Capacity Fraction of Rated**|**COP Fraction of Rated**|**Applied HP-RTU COP** |**Sensible Heat Ratio Fraction**|
| :- | :- | :- | :- | :- |
|Rated|1\.00|1\.00|4\.11|1\.00|
|4|1\.00|1\.00|4\.11|1\.00|
|3|0\.67|1\.08|4\.44|1\.01|
|2|0\.51|1\.11|4\.56|1\.03|
|1|0\.36|1\.07|4\.40|1\.11|

Five performance curve modifiers are used for modeling the DX multispeed cooling objects. The performance curves were derived from separate work that used NREL lab testing data of three variable-speed, central-ducted AC systems where values representative of the three systems are used. For multispeed objects, these modifier curves are specific to the compressor speed to which they are applied, so each speed will have its own set of curves. They are described as follows:

1. **Energy input ratio (EIR) as a function of part load ratio**—uses the calculated part load ratio to determine an EIR modifier from compressor cycling, which is multiplied against the full-load EIR for the stage (Figure 4). Note that EIR is the inverse of COP, so decreasing the EIR increases the realized efficiency. For the multispeed units modeled in this work, this curve is only used for the lowest compressor speed where cycling losses may occur.
1. **Capacity as a function of temperature**—uses outdoor drybulb and indoor wetbulb temperatures to predict a capacity modifying factor that is multiplied against the rated capacity for each stage (Figure 5). For heat pumps, the available capacity decreases with temperature.
1. **EIR as a function of temperature**—uses outdoor and indoor drybulb temperatures to determine an EIR (1/COP) modifying factor that is multiplied against the rated EIR for each stage for the time step (Figure 6). Note that other modifier functions can also affect the final COP.
1. **Capacity as a function of flow**—modifies capacity based on the determined flow rate for a time step. This curve is not used because capacity is already accounted for in the speed level.
1. **EIR as a function of flow**—modifies EIR based on the determined flow rate for a time step. This curve is not used because the EIR is already accounted for in the speed level.

The cooling performance maps for EIR as a function of part load ratio, COP as a function of temperature, and capacity as a function of temperature are shown Figure 4, Figure 5, and Figure 6, respectively.


![Chart, line chart

Description automatically generated](hvac_hp_rtu.005.jpeg)

<a name="_ref127708273"></a><a name="_toc131683794"></a>**Figure 4. Heating and cooling energy input ratio modifier as a function of part load ratio for all speed levels. This curve primarily captures losses due to part-load cycling at compressor speed 1. This value is divided by the EIR for the time step, which effectively decreases efficiency at lower part load ratios.** 

![Graphical user interface, chart

Description automatically generated](hvac_hp_rtu.006.jpeg)

<a name="_ref121381428"></a><a name="_toc131683795"></a>**Figure 5. Capacity as a function of temperature performance map for the four stages of cooling. This value is multiplied by the nominal capacity for each time step to determine the actual available capacity for the time step.**

![Graphical user interface, chart, radar chart

Description automatically generated](hvac_hp_rtu.007.jpeg)

<a name="_ref121381443"></a><a name="_toc131683796"></a>**Figure 6. COP as a function of temperature performance map for the four stages of cooling. Note that these COP values are for the compressor only—adding in supply fan energy would decrease the values presented.**

1. #### <a name="_toc131683778"></a>***Heat Pump Heating Performance***
The variable-speed heat pump heating in the proposed HP-RTUs is modeled using the EnergyPlus “Coil:Heating:DXMultiSpeed” object using four speeds of heating [4], [5]. This object performs similarly to the “Coil:Cooling:DXMultiSpeed” object described previously. The rated efficiency values used for this study are based on a 10-ton variable-speed RTU with a full-load COP of 3.42 at rated conditions (8.3°C outdoor air temperature entering the condenser and 21.1°C drybulb indoor air temperature entering the coil) [9]. Because the EnergyPlus COP input is compressor-only, and therefore removes supply fan energy, the model input is adjusted to 3.8 COP, using the methodology from PNNL’s study [9]. The parameters for each stage of heating are shown in Table 2. The capacity and COP fractions for each speed level were determined using manufacturer-provided data for a variable-speed, central-ducted, forced-air heat pump system (Table 2). The data are roughly 10 years old but are expected to be a reasonable representation of a variable-speed system. The heating COP increases with lower speed levels, similar to what was described for the cooling COPs. Because the testing is based on residential central heat pump units rather than commercial RTUs, the values derived from the testing are normalized to the rated COP of 3.8 to better represent a commercially available HP-RTU for this study (Table 1) [9]. Variable-speed HP-RTUs are capable of modulating to the specified fractions, but they may not do so in the same manner as the residential units the performance parameters are based on, which emphasizes the need for additional research in this area [7]. The minimum operating temperature for the heat pumps is modeled at −17.8°C, which is the default setting for some manufacturers. The compressor will lock out below this temperature, and only backup heat will be available.

<a name="_ref121384743"></a><a name="_toc131683812"></a>**Table 2. Multispeed Heating Coil Performance Parameters** 

COP values are at rated conditions and vary based on temperature.

|**Compressor Speed Level**|**Capacity Fraction of Rated**|**COP Fraction of Rated**|**Applied HP-RTU COP** |
| :- | :- | :- | :- |
|Rated|1\.00|1\.00|3\.80|
|4|1\.00|1\.00|3\.80|
|3|0\.85|1\.05|3\.98|
|2|0\.48|1\.24|4\.71|
|1|0\.28|1\.45|5\.51|

Similar to the DX multispeed cooling objects, five performance curve modifier types are used for modeling the DX multispeed heating objects. The descriptions of these are discussed in the cooling performance section of this document, with the only difference being that the heating coils use indoor air drybulb temperature instead of indoor air wetbulb temperature, which is used for the cooling coils. The performance curves were derived from manufacturer-provided data for a central-ducted, variable-speed heat pump system. The resulting performance maps for all speed levels are shown in Figure 4, Figure 7, and Figure 8 for EIR as a function of part load ratio, COP, and capacity retention, respectively. As expected with heat pumps, heating COP and capacity generally reduce with outdoor air drybulb temperature.

Heat pump performance maps are especially impactful because of the general reduction of capacity and efficiency at lower outdoor air temperatures where increased heating loads often occur. This study attempts to utilize the best available data, as described previously, because this will notably impact the results. However, it should be emphasized that complete heat pump performance data are still scarce at the time of this study, especially for variable-speed commercial RTUs and low-temperature operation, which limits the understanding of heat pump performance and operation in this analysis. Further research on heat pump performance could increase confidence in heat pump modeling, and this study may be updated as more data become available. 

Comparisons of modeled performance data versus alternative data sources were made, where possible, to validate that the performance data used were reasonable. Table 3 and Table 4 compare some key points on the modeled heat pump performance maps for COP and capacity retention as a function of outdoor air temperature, respectively, with other available data sources for validation. The first data source is for the variable-speed Daikin Rebel HP-RTU, with specification sheet data providing capacity and COP at 8.3°C (rated) and −8.3°C [11]. The second source is a Rheem two-stage HP-RTU with heating performance data at various outdoor air temperatures [10]. The last data source is from a study that performed lab testing on a Carrier cold climate variable-speed HP-RTU, which provides COP values at various outdoor air temperatures [11]. 

The modeled HP-RTU outperforms the capacity retention of the reference units by 5% to 9%, with the largest difference occurring with the Rheem unit at −17.8°C (Table 3). For COP retention, the modeled HP-RTU outperforms the reference units by 3% to 14%, with the largest difference occurring with the Rheem unit at −17.8°C (Table 4). Although there are some notable differences between the modeled and reference unit performance, and the modeled HP-RTU outperforms the reference units in all cases, these comparisons still suggest the modeled HP-RTU performance is reasonably appropriate compared to other available data, especially considering they are different units from different data sources. Note that no alternative data sources were found for comparing part-load performance or the impacts of cycling on variable-speed heat pump units, further emphasizing the need for more research in this space to increase modeling confidence.

![Chart

Description automatically generated](hvac_hp_rtu.008.jpeg)

<a name="_ref121388760"></a><a name="_toc131683797"></a>**Figure 7. COP as a function of temperature performance map for the four stages of heating. Note that these COP values are for the compressor only—adding in supply fan energy would decrease the values presented.**

![Chart, calendar

Description automatically generated](hvac_hp_rtu.009.jpeg)

<a name="_ref121388769"></a><a name="_toc131683798"></a>**Figure 8. Capacity as a function of temperature performance map for the four stages of heating. This value is multiplied by the nominal capacity for each time step to determine the actual available capacity for the time step.**



<a name="_ref121388710"></a><a name="_toc131683813"></a>**Table 3. Capacity Retention As a Function of Outdoor Air Temperature Comparison for Daikin Rebel, Rheem Renaissance, and the Modeled HP-RTU Performance Curves** 

|**Reference Temperature, °C**|**8.3°C**|**−8.3°C**|**−17.8°C**|
| :- | :- | :- | :- |
**This document was truncated here because it was created in the Evaluation Mode.**
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
