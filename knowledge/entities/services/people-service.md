# People Service

- **Repo:** finos/traderX
- **Directory:** people-service/
- **Tech:** .NET Core
- **Port:** 18089
- **Type:** REST API

## Purpose

Manages users in the system and associates them with accounts. Returns information about a person by logonId or employeeId, supports searching by logonId or fullName, and validates whether a logonId or employeeId can be associated to a valid person.

## Connections

- **Inbound:** [[web-front-end]] (REST/HTTP), [[account-service]] (REST/HTTP — validate people for account association)
- **Outbound:** User Directory (LDAP — external user lookup)

## API

- Swagger UI: `/swagger`
- Example: `/People/GetPerson?LogonId=user01`

## Sources

- Code: https://github.com/finos/traderX/tree/main/people-service
- Last synced: 2026-04-01
