# Pandas
```python
#import pandas as pd
```

---
## Settings

#### interface
```python
pd.get_option()
pd.set_option()
pd.reset_option()
pd.describe_option()
pd.option_context()
```

#### usage
必须匹配单一setting值，否则抛出exception
```python
pd.get_option("display.max_rows")
pd.set_option("display.max_rows",101)
```

#### setting option
* display.max_rows
* display.max_columns
* 