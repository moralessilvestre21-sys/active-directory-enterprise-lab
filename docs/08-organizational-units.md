# Organizational Units

Organizational Units (OUs) were created to organize Active Directory objects and provide logical targets for administration and Group Policy.

## OU Structure

The following structure was created:

- Employees
  - IT
  - HR
  - Finance
  - Sales
- Workstations
- Servers

CLIENT01 was moved from the default Computers container into the `Workstations` OU.

## Design Decision

Users, workstations, and servers were separated so policies can be applied to specific types of objects without unnecessarily affecting the entire domain.

Department OUs provide additional organization for users and allow department-specific administration or policies in the future.

## Result

The domain now has a structured hierarchy that supports scalable user, computer, and Group Policy management.
