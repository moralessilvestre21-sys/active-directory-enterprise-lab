# Users and Groups

Active Directory users and security groups were created to practice centralized identity and access management.

## Configuration

- Created domain user accounts inside the appropriate department OUs.
- Created security groups for organizational access.
- Added users to groups based on their department or role.
- Practiced modifying group membership when a user's role changed.
- Used group membership instead of assigning permissions directly to individual users.

## Example

The domain account `ajohnson` was used to authenticate to CLIENT01 and verify that domain authentication was functioning correctly.

A department transfer scenario was also tested by removing a user from their previous security group and assigning them to the appropriate new group.

## Design Principle

Group-based access simplifies administration because permissions can be managed according to job role rather than repeatedly configured for individual accounts.

## Result

The environment demonstrates basic identity lifecycle and role-based access management using Active Directory users and security groups.
