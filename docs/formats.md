# File formats

`PStomo` has 3 basic input files (in addition to the parameter file and the initial/starting model):

1. __station file__: contains station coordinates in cartesian (flat Earth) projection
2. __source file__: contains origin time and hypocenter of sources (earthquakes and/or controlled) in cartesian projection
3. __arrival time file__: contains arrival times of P (and S) waves sorted by recording station

Although it is not necessary, we follow this convention for naming the input files:

- all files have a `.in` extension
- all files begin with a common prefix, which is a short identifier of the project or region 
  (e.g. ``ice`` for Iceland or ``ncal`` for Northern California)
- station file has the ``_stat``suffix (e.g. ``ice_stat.in``)
- source file has the ``_src``suffix (e.g. ``ice_src.in``)
- arrival time file has the ``_tt``suffix (e.g. ``ice_tt.in``)

Since we often have many more sources than stations, to reduce computing time inside `PStomo` 
travel times are calculated from the stations. Therefore the concept of source and receiver is
reversed inside the code.

## Station list

A station file contains lines with the following columns (one for each station):

```
STATION_ID X Y Z MAX_DISTANCE NUMBER_ARRIVAL_TIMES USE_STATION FLAG STATION_CODE
```

- `STATION_ID` = numerical station ID __(not passed to main)__
- `X` = x coordinate in km
- `Y` = y coordinate in km
- `Z` = z coordinate in km (negative if above sea level)
- `MAX_DISTANCE` = distance (km) to furthest source recorded by this station __(not passed to main)__
- `NUMBER_ARRIVAL_TIMES` = number of arrival times for this station
- `USE_STATION` = use flag: 0 use, 1 do not use __(WARNING: opposite to standard true/false convention)__
- `FLAG` = additional flag __(not passed to main)__
- `STATION_CODE` = alphanumeric station code __(not passed to main)__

```
    0  -33.59028   -4.31897   -0.79400  116.72459  1225    0    0 CADE
    1  -42.17252   12.75307   -1.16000  150.92570   854    0    0 CBOL
    2  -20.12271    2.41153   -2.21000  101.10428  2142    0    0 CCAN
    3  -26.79712    2.82335   -2.06400   94.74211  1168    0    0 CCHO
    4  -15.59873    9.43089   -2.10300  109.41433   827    0    0 CDIE
    5  -33.25449   10.47509   -1.62600  111.62872   962    0    0 CDOS
    6  -18.92852   12.64890   -2.11000  108.85104   762    0    0 CFOR
```

## Source locations

A source file contains lines with the following columns (one for each source):

```
SOURCE_ID YYMMDD HHMM SS.FF... X Y Z MAGNITUDE EVENT_TYPE EVENT_GROUP_ID FLAG
```

- `SOURCE_ID` = source number/ID (usually starts at 0 but not required?)
- `YYMMDD` = origin time year, month, and day for this source __(WARNING: two-digit year)__
- `HHMM` = origin time hour and minute for this source
- `SS.FF...` = origin time seconds and fractionary part (variable precision)
- `X` = x coordinate in km
- `Y` = y coordinate in km
- `Z` = z coordinate/focal depth in km (negative if above sea level)
- `MAGNITUDE` = event magnitude
- `EVENT_TYPE` = 0 for earthquakes, 1 for explosions (controlled source)
- `EVENT_GROUP_ID` = event group ID this source belongs to (if no event groups `SOURCE_ID = EVENT_GROUP_ID`)
- `FLAG` = __(passed to main but apparently not used)__

```
     0 040628 0342 29.90   -29.3320     9.4560     0.0000   1.90      0      0      0
     1 040628 0423 48.20   -29.9220     9.0140     0.0000   1.90      0      1      0
     2 040629 2125 53.40   -16.4760    13.3100     0.0000   2.70      0      2      0
     3 040706 1855 57.60   -28.3670     2.8040     0.0000   1.70      0      3      0
     4 040716 2152  3.70   -34.7100    15.7880    24.5000   1.60      0      4      0
     5 040725 0059 41.60   -29.5290     9.2350     0.0000   1.80      0      5      0
     6 040727 0514 10.60   -22.9390    18.6410    16.4000   2.40      0      6      0
     7 040727 0514 44.40   -27.5580    13.5530     5.1000   2.60      0      7      0
     8 040727 0531 10.50   -28.0430    15.2170     8.4000   1.80      0      8      0
     9 040727 1747 38.80   -30.6180     5.6910     0.0000   1.40      0      9      0
    10 040728 0029 27.00   -28.6480     9.0110     0.0000   1.60      0     10      0
    11 040730 1111 51.00   -29.1360     9.6770     0.0000   2.50      0     11      0
```

## Arrival times

The arrival time file contains two types of lines:

### Station line

The arrival time file must begin with a station line and must contain exactly as many station lines
as stations listed in the station file (and in the same order).

```
STATION_CODE NUMBER_ARRIVAL_TIMES
```

- `STATION_CODE` = station code __(program does not check that it coincides with code in station file)__
- `NUMBER_ARRIVAL_TIMES` = number of arrival times for this station (this exact same of number of
   arrival time lines must follow this station line)

### Arrival time line
```
SOURCE_ID YYMMDD HHMM P_SECOND P_WEIGHT P_USE S_SECOND S_WEIGHT S_USE
```

- `SOURCE_ID` = source ID in source file this arrival time belongs to
- `YYMMDD` = year, month and day of arrival time __(WARNING: two-digit year)__
- `HHMM` = hour and minute of arrival time
- `P_SECOND` = second of P-wave arrival time
- `P_WEIGHT` = weight of P-wave arrival time (HYPO71 convention: 0 = full weigth, > 3 = do not use)
- `P_USE` = flag for using this P phase: 0 = use, > 0 do not use __(WARNING: opposite to standard true/false convention)__
- `S_SECOND` = second of S-wave arrival time (can be greater than 60 s if S arrival time does not occur in same minute as P arrival time).
   If S phase is not present then `S_SECOND = 0.0` and `S_WEIGHT = S_USE = 9`.
- `S_WEIGHT` = weight of S-wave arrival time (HYPO71 convention: 0 = full weigth, > 3 = do not use)
- `S_USE` = flag for using this S phase: 0 = use, > 0 do not use __(WARNING: opposite to standard true/false convention)__

Although the station file lists `STATION_ID` and `STATION_CODE`, these values are not used nor
checked against the values in the arrival time file. Instead the program assumes
that the stations in the arrival time file appear in exactly the same order as in the station file.

However `NUMBER_ARRIVAL_TIMES` in the arrival time file and in the station file must be the same,
and is verified by the program.

```
CADE   1225
     371 170401 1657   10.550   1   0   17.120   2   0
     372 170406 2350    7.840   1   0    9.660   2   0
     373 170408 0846   17.160   1   0    0.000   9   9
     374 170623 2148   26.150   1   0   28.430   2   0
     375 170410 0101   14.790   1   0   20.740   2   0
     378 170421 0450   26.430   1   0   33.150   2   0
     379 170422 1416   25.160   1   0   30.520   2   0
     380 170423 1932   12.340   1   0   14.430   2   0
     381 170424 0201   31.170   1   0   32.550   2   0
     386 170513 0126   30.780   1   0   33.070   2   0
     389 170523 0029   22.760   1   0   24.840   2   0
     .
     .
     .
    2223 200406 2219   54.000   1   0   55.910   2   0
    2224 200407 0335   37.460   1   0   42.790   2   0
    2225 200407 2359   52.180   1   0   53.150   2   0
    2226 200408 0612   20.060   1   0   25.330   2   0
CBOL   854
     330 160803 2230   50.560   1   0   57.750   2   0
     331 160831 0734   26.290   1   0   34.960   2   0
     332 160927 2347   53.610   1   0   61.520   2   0
     335 161003 1340   49.230   1   0   58.740   2   0
     .
     .
     .
```

## Velocity model

## Ray coverage

## Output travel times
