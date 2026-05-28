# itm8-bicep-shared-abbr-locations

Shared Bicep module that provides helper functions for mapping Azure region names to their standardized abbreviations. These abbreviations are intended for use in resource naming conventions, particularly for backup vault and geo-related naming.

## Version

`0.1.0`

## Overview

This module exports three user-defined functions that resolve Azure location names (both canonical slug form, e.g. `westeurope`, and display name form, e.g. `West Europe`) to short geo-code abbreviations (e.g. `we`).

## Exported Functions

### `getLocationAbbreviation(location string) string`

Returns the abbreviation for a given Azure location. If the location is not found in the mapping, it returns `'unknown'`.

```bicep
var abbr = getLocationAbbreviation('westeurope') // 'we'
var abbr = getLocationAbbreviation('West Europe') // 'we'
var abbr = getLocationAbbreviation('unknownregion') // 'unknown'
```

### `getAllLocationAbbreviations() object`

Returns the full mapping object of all supported Azure locations to their abbreviations.

```bicep
var allMappings = getAllLocationAbbreviations()
```

### `hasLocationAbbreviation(location string) bool`

Returns `true` if the given location has a known abbreviation, otherwise `false`.

```bicep
var known = hasLocationAbbreviation('northeurope') // true
var known = hasLocationAbbreviation('unknownregion') // false
```

## Usage

Reference this module using the Bicep registry:

```bicep
import { getLocationAbbreviation, hasLocationAbbreviation, getAllLocationAbbreviations } from 'br:itm8crpweiacbicep001-fvdzezaff2hwcgcj.azurecr.io/itm8-bicep-shared-abbr-locations:0.1'

var locationAbbr = getLocationAbbreviation(location)
```

## Supported Locations

The module covers all major Azure regions, including both slug and display name variants:

| Display Name          | Slug                  | Abbreviation      |
|-----------------------|-----------------------|-------------------|
| Australia Central     | australiacentral      | acl               |
| Australia East        | australiaeast         | ae                |
| Brazil South          | brazilsouth           | brs               |
| Canada Central        | canadacentral         | cnc               |
| Central US            | centralus             | cus               |
| East Asia             | eastasia              | ea                |
| East US               | eastus                | eus               |
| East US 2             | eastus2               | eus2              |
| France Central        | francecentral         | frc               |
| Germany West Central  | germanywestcentral    | gwc               |
| Japan East            | japaneast             | jpe               |
| Korea Central         | koreacentral          | krc               |
| North Europe          | northeurope           | ne                |
| Norway East           | norwayeast            | nwe               |
| Poland Central        | polandcentral         | plc               |
| South Africa North    | southafricanorth      | san               |
| South Central US      | southcentralus        | scus              |
| Southeast Asia        | southeastasia         | sea               |
| Spain Central         | spaincentral          | esc               |
| Sweden Central        | swedencentral         | sdc               |
| Switzerland North     | switzerlandnorth      | szn               |
| UAE North             | uaenorth              | uan               |
| UK South              | uksouth               | uks               |
| West Europe           | westeurope            | we                |
| West US               | westus                | wus               |
| West US 2             | westus2               | wus2              |
| West US 3             | westus3               | wus3              |

> Reference: https://learn.microsoft.com/en-us/azure/backup/scripts/geo-code-list

> For the full list of all supported regions, refer to [main.bicep](./main.bicep).

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).
