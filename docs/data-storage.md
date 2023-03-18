---
sidebar_position: 10
---
# Data Storage

ErrorDeck uses a database to store all the data. The database is used to store the following data:

- Errors
- Sourcemaps
- Teams
- Projects
- Users
- Invites
- Plans
- Payments
- Webhooks
- API Keys

## Database

ErrorDeck is using PostgreSQL as the database. PostgreSQL is an open-source relational database management system. PostgreSQL is a powerful, open source object-relational database system with over 30 years of active development that has earned it a strong reputation for reliability, feature robustness, and performance.

## Data Storage

ErrorDeck is using Scaleway for data storage for the sourcemaps. Scaleway is a cloud computing platform that offers bare metal servers, virtual servers, object storage, and block storage. Scaleway is a French cloud computing company that was founded in 2013. Scaleway is using only EU servers and it is GDPR compliant. You can read more about the GDPR compliance [here](https://www.scaleway.com/en/gdpr/).

## How Errordeck is taking care of the data

ErrorDeck is taking care of the data by using encryption, both on rest and in transit. Scalingo use AES-XTS-plain64 at rest. They use dm-crypt for that. And we use AES-256-CBC in the database to encrypt tags and context that most likely will contain user data. We also use TLS to encrypt all data in transit.