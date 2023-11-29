# policy-reasoner
Implements the famous policy reasoner, known as `checker` in Brane terminology. Builds on top of reasoners like [eFLINT](https://gitlab.com/eflint) and meant to be queried by [Brane](https://github.com/epi-project/brane).


# Needed FIXES

Install diesel CLI
- `cargo install diesel_cli --no-default-features --feature sqlite`

Run diesel migration
- `cd lib/policy`
- `diesel migration run --database-url data/policy.db`

Add active policy (requires `sqlite3` client)
- `sqlite3 ./data/policy.db`
- \[OLD DONT USE ANYMORE\] `INSERT INTO policies VALUES(1,'Dit is een omschrijving','Dit is een versie omschrijving','Bas Kloosterman',1698255086939846,readfile('./lib/reasonerconn/examples/example-policy-content.json')); INSERT INTO active_version VALUES(1,'2023-10-31 20:14:39.669660','Bas Kloosterman');`
- ```
  INSERT INTO policies VALUES(1,'Dit is een omschrijving','Dit is een versie omschrijving','Bas Kloosterman',1698255086939846,'[{"reasoner":"eflint","reasoner_version":"0.1.0","content":[]}]');
  INSERT INTO active_version VALUES(1,'2023-10-31 20:14:39.669660','Bas Kloosterman');
  ```
- Ctrl+D

// TODO: Check if needed
go eFlint server
- struct.go:156 remove omitempty json tag // of niet require empty array
- naming:
    - +user(HospitalA). -> +user(Hospitala).
    - Exists task, dataset' : ... -> Exists task, dataset2 :
- projection:
    - recipient.user == user => (recipient.user) == user
- negation:
