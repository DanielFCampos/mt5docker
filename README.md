# MetaTrader 5 for dockerized application

A simple package to enable Python connection to MT5 on docker.

This package is a fork from [mt5linux](https://github.com/lucas-campagna/mt5linux) updated to work on Python 3.13+.

The package uses [wine](https://www.winehq.org), [rpyc](https://github.com/tomerfiliba-org/rpyc) to allow using [MetaTrader5](https://pypi.org/project/MetaTrader5) towards a dockerized MT5 application.

## Installation

- MetraTrader5 
Please refer to [MetaTrader5-Docker](https://github.com/gmag11/MetaTrader5-Docker) to dockerize your MT5.

- Python connection
To install use UV on remote github `uv add "mt5docker @ git+https://github.com/DanielFCampos/mt5docker"`

## How To Use

1. Start your docker container running MetaTrader5.

2. For UI experience, just start your browser pointing to `http://<your ip address>:3000`.

3. For programmatic use, make your scripts/notebooks as you did with MetaTrader5:
```python
# import the package
from mt5docker import MetaTrader5
# connect to the server
mt5 = MetaTrader5(
    # host = 'localhost' (default)
    # port = 8001        (default)
) 
# use as you learned from: https://www.mql5.com/en/docs/integration/python_metatrader5/
mt5.initialize(
    # login=1234567890 (no default)
    # password="your-password" (no default)
    # server="server-name" (no default)
)
# initialization may not need login/pwd/svr info if MT5 instance is already configured
mt5.terminal_info()
mt5.copy_rates_from_pos('VALE3', mt5.TIMEFRAME_M1, 0, 1000)
# ...
# don't forget to shutdown
mt5.shutdown()
```
