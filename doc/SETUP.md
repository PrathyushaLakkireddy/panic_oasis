# Setting up PANIC

PANIC requires its own setup process, involving three main parts, each of which generates its own respective config file:

- Linking up any of the optional features that you set up (`config/user_config_main.ini`)
- Providing a list of nodes that you wish to monitor (`config/user_config_nodes.ini`)
- Providing a list of GitHub repositories that you wish to monitor (`config/user_config_repos.ini`)

All of these steps are packaged into one setup process which is started up by running:
```bash
pipenv sync
pipenv run python run_setup.py
# If multiple versions of Python are installed, the python executable may be `python3.6`, `python3.7`, etc.
```

Alternatively, you can take a look at the three `config/example_***.ini` files and perform the config file generation manually by copying the three example config files to the ones listed above and replacing the example pieces of information with actual ones.

The setup process is guided by instructions which we highly recommend that you read. The setup of any optional feature that was not set up in the previous section can be skipped. For convenience, any yes/no question can be answered with a *yes* just by pressing *ENTER*.

Lastly, note that if you wish to change some configurations and run the setup process again, it will detect the config files and will not simply overwrite the current configurations.

**IMPORTANT NOTE** : The `node_name` inside the `user_config_nodes.ini` file must be the same as that of the node name given in the setup of the Oasis API Server.

## Advanced Configuration

If you had a look in the `config/` folder, you may have seen the `config/internal_config_*.ini` files. There is no setup process for the internal configurations because you do not have to modify them.

The **main internal configuration file** (`config/internal_config_main.ini`) defines values that are less likely to require changing. However, we encourage more advanced users to experiment with different configurations if the consequences of any changes are realised and acknowledged beforehand.

This file consists of values such as:
- Which files to use for logging, and the logging level
- Which Redis databases to use (10 and 11 by default)
- Which Redis keys to use to store values in Redis
- Timeout setting for certain temporary Redis keys
- Data collection periods for each of the monitor types
- Alert frequency and severity modifiers (by time intervals and boundaries)
- Link to use for the `/validators` Telegram command.

The **alerts internal configuration file** (`config/internal_config_alerts.ini`) lists all possible alerts and alert severities, allowing the user to disable specific alerts or even a whole alert severity by setting the respective key from `True` to `False`.
<!-- TODO: add more info once config UI is usable -->

---
[Back to alerter installation page](INSTALL_AND_RUN.md)