# Group Policy

Group Policy was implemented to centrally manage workstation settings and user restrictions within the domain.

## Configuration

- Opened Group Policy Management on DC01.
- Created a workstation-focused Group Policy Object (GPO).
- Linked the GPO to the `Workstations` OU.
- Configured a policy restricting access to Control Panel and Windows Settings.
- Used `gpupdate /force` to refresh Group Policy on CLIENT01.
- Used `gpresult` to verify policy processing and scope.

## Policy Scope

During testing, the Control Panel restriction was configured under **User Configuration** while the GPO was linked to the `Workstations` OU.

This demonstrated an important Group Policy concept: computer and user settings are processed according to the Active Directory objects within the applicable scope.

## Validation

Policy behavior was tested directly on CLIENT01 and verified using Group Policy reporting tools.

## Result

The lab demonstrates centralized configuration management and practical understanding of GPO linking, scope, inheritance, and policy processing.
