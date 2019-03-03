## Can you predict which water pumps are faulty?

Using data from Taarifa and the Tanzanian Ministry of Water, the goal of the Kaggle competition was to predict which water pumps were functional, which needed repairs, and those which didn’t work at all.
Predict one of these three classes based on a number of variables about what kind of pump is operating, when it was installed, and how it is managed.
A smart understanding of which waterpoints will fail can improve maintenance operations and ensure that clean, potable water is available to communities across Tanzania.

Kaggle competition or not, all data modeling project should start with a baseline model, so that subsequent model can compare with.

### Begin project by establishing Baseline metrics.
#### Method 1: Majority baseline by value_counts. Random chance predictions have
54% functional well pump.
38% non-functional pump.
7% repairable.

```python
df_label.status_group.value_counts(normalize=True)
functional                 0.543081
non functional             0.384242
functional needs repair    0.072677
Name: status_group, dtype: float64
```
