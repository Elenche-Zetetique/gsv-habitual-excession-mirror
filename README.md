# GSV Habitual Excession

**GSV (General Systems Versioning) Habitual Excession** is an Ansible-based automation system designed to process and update personal documents with structured workflows. It operates in two modes: `test` for debugging and `prod` for production logging.

## Features

- Automates document processing tasks using Ansible.
- Supports `test` mode for debugging without persistent logs.
- Supports `prod` mode with structured logging in `info.log`.
- Uses Ansible tags to control execution modes.

## Requirements

- Ansible installed on the system.
- Inventory file (`hosts`) configured with the target machines.

## Usage
### ReadWatchLog

Processes files defined in ReadWatchLog (s. [ReadWatchLog](https://github.com/Elenche-Zetetique/readwatchlog-mirror))

Run the playbook in **test mode** (prints debug messages, no logs written):

```sh
ansible-playbook readwatchlog.yml -i inventory/hosts --tags "test"
```

Run the playbook in **prod mode** (records logs in `info.log`):

```sh
ansible-playbook readwatchlog.yml -i inventory/hosts --tags "prod"
```

## Logging

- **Test Mode**: Outputs messages to the terminal for debugging.
- **Prod Mode**: Writes important steps to `info.log` for tracking and to `error.log` for errors.

## Structure

```
GSV-Habitual-Excession/
│
├── playbooks/
│   └── readwatchlog.yml # Main playbook for processing documents of ReadWatchLog-format
│
├── inventory/
│   ├── hosts             # Inventory file
│   └── logs/
│       ├── info.log      # Production info-log file
│       └── error.log     # Production error-log file
│
├── roles/
│   └── readwatchlog/
│       └── tasks/
│           ├── main.yml
│           ├── operation.yml
│           ├── postprocessing.yml
│           ├── preprocessing.yml
│           ├── prod.yml
│           └── test.yml
│
└── README.md
```

## Future Plans
- Expand playbooks for additional document management tasks.
- Implement more granular logging and reporting.
- Introduce role-based structuring for better maintainability.

## License
This project is licensed under the [**Creative Commons Attribution-NonCommercial 4.0 (CC BY-NC 4.0)**](https://creativecommons.org/licenses/by-nc/4.0/legalcode.en) license.

### Summary:
- You are **free to use, modify, and share** this software **for non-commercial purposes**.
- **Commercial use is strictly prohibited**.
- No warranties or liability: The author is **not responsible** for any issues arising from use.

## Authors
Maintained by [**Elenche Zetetique**](https://elenche-zetetique.com/).