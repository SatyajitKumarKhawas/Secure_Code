# Seperation of Duties (SoD) Conflict Detection

## Overview
This script analyzes role-based access control (RBAC) data to detect Separation of Duties (SoD) conflicts. It maps entitlements, privileges, roles, and users to generate a conflict report highlighting violations based on predefined SoD rules.

## Features
- Loads data from multiple Excel sheets containing entitlements, privileges, role hierarchies, user-role mappings, and SoD rules.
- Maps entitlements to privileges, privileges to roles, and users to roles.
- Detects conflicts where a user has entitlements that violate SoD rules.
- Generates an Excel report highlighting conflicts.

## Prerequisites
Ensure you have the following installed:
- Python 3.x
- Pandas (`pip install pandas`)
- OpenPyXL (`pip install openpyxl`)

## File Structure
The script expects the following input files in the `D:\Python_Project\securecode\` directory:
- `SOD_Ruleset.xlsx` (Sheets: `ENTITLEMENT_MST`, `SOD_MASTER`)
- `XX_7_PVLGS_MASTER_RPT.xlsx`
- `XX_6_PVLG_TO_ROLE_RELATION_RPT.xlsx`
- `XX_5_ROLE_TO_ROLE_HIER_RPT.xlsx`
- `XX_3_USER_ROLE_MAPPING_RPT.xlsx`
- `XX_2_USER_DETAILS_RPT.xlsx`
- `XX_4_ROLE_MASTER_DETAILS_RPT.xlsx`

## Installation & Usage
1. Clone the repository or copy the script.
2. Install dependencies using:
   ```sh
   pip install pandas openpyxl
   ```
3. Run the script:
   ```sh
   python script.py
   ```
4. The output will be saved as `Conflict_Report.xlsx` in the current directory.

## Functions
### `load_data()`
Loads data from multiple Excel sheets and returns DataFrames.

### `map_user_details(user_details)`
Maps `USER_ID` to `USER_DISPLAY_NAME`.

### `map_role_details(role_details)`
Maps `ROLE_ID` to `ROLE_NAME`.

### `map_entitlements_to_privileges(entitlements, privileges)`
Maps access points to entitlements.

### `map_privileges_to_roles(privilege_roles)`
Maps privileges to roles.

### `map_users_to_roles(user_roles)`
Maps users to their assigned roles.

### `detect_conflicts(user_roles, privilege_roles, entitlement_mapping, sod_rules, user_map, role_map)`
Checks for SoD conflicts based on entitlements assigned to users via roles.

### `generate_conflict_report(conflicts)`
Creates an Excel file containing all detected conflicts.

## Notes
- Ensure the file paths and sheet names match your dataset.
- If any files are missing or have different column names, modify the script accordingly.

## Troubleshooting
- **FileNotFoundError**: Ensure all required files exist in the specified directory.
- **KeyError**: Verify column names in the Excel sheets match those used in the script.
- **Incorrect Output**: Check if privilege codes and entitlements are formatted correctly.

## License
This project is open-source. You may modify and distribute it as needed.

