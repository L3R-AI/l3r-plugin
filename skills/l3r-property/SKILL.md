---
name: l3r-property
description: Answer questions about one US property, parcel or site with the L3R connector. Use when the user asks what is at an address, its parcel number, building facts, zoning, natural hazards, flood or wetlands, Census figures for the area, what is nearby, its electric or gas utility, data center projects near it, or about a power plant, grid operator or coal shipments.
---

# Using L3R

L3R's tools are read-only and answer for one property, facility or area at a time.

## Pick the tool

Use the tool that answers the question asked. Call another only when the user asks for more.

| Question | Tool |
|---|---|
| What is at an address or parcel number: type, buildings, year built, parcel, PROP- key | `lookup_property` |
| Population, income, home value, rent for the area | `census_for_area` |
| Zoning district, or what a district such as RS-3 in Tulsa allows | `zoning_for_property` |
| FEMA hazard ratings, EPA cleanup sites within a mile | `hazards_for_property` |
| Nearest water, roads, rail, airports, power plants, renewables, schools, broadband, EV charging | `nearby_for_property` (set `topics` to what was asked) |
| Flood zone, wetlands, protected areas, contamination, slope, sewer for a lot | `site_screen_for_property` |
| Grid, electric utility, retail supplier, gas utility | `energy_service_for_property` |
| Data center projects from official records | `data_center_projects` |
| A power plant, airport, port, water system, school, hospital or mine by name or ID | `lookup_facility` |
| A plant's generation and fuel history | `energy_plant_history` |
| A state's electricity prices, sales and emissions | `electricity_state_profile` |
| A grid operator's hourly demand and fuel mix | `grid_demand_mix` |
| Power flows between grid operators | `grid_interchange` |
| Coal shipped from mines to a plant | `coal_shipments` |
| Congressional, state legislative and school districts | `districts_for_property` |
| What L3R covers for a county, a state or the US | `coverage_for_county` |
| Ranked lists: power plants by state, county or metro area, FEMA risk-ranked Census tracts, strategic seaports | `list_reference_data` |

## Rules

- **One per call.** Give one address, parcel number or ID per call. L3R never lists properties, searches an area for them or answers in bulk. If the user gives several properties, tell them it answers one at a time.
- **Show the card.** Each result's text is a Markdown card. Show it nearly as is. Keep its source line, any Census or FEMA notice, and its closing line about Athena.
- **Don't recompute.** Use the numbers as returned. Don't convert, total, round or derive new figures from them.
- **Maps.** `lookup_property` returns a map of the lot with a `Map:` link; show the image. The other property tools give only the `Map:` link; pass `map: true` only when the user asks to see the map again.
- **Use the PROP- key.** When the user asks more about a property already looked up, give its `PROP-` key as `property_key` rather than the address.
- **Missing means not held.** A value L3R leaves out, or lists under `not_held`, is one L3R doesn't hold. Never say it doesn't exist, and never estimate it.
- **Zoning is not a determination.** Overlays, variances and recorded restrictions are not applied. Say so when zoning matters to a decision.
- **Ambiguous results.** On `AMBIGUOUS`, show the candidates and ask which one, or ask for the county, ZIP or unit.
- **Permits, rights and municipal code** are not in these tools. Point the user to Athena at 3drights.com.
- **No owners, values or sales.** L3R doesn't return them.
- **Answer in the user's language.** Keep addresses, parcel numbers, permit names and form names in English as written, since those are what the city uses.
