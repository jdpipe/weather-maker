# weather-maker
TMY3/EPW weather data file creation tool

This utility processes publicly available Bureau of Meteorology
weather and solar radiation data into a TMY3 or EPW format file
suitable for tools such as SAM and EnergyPlus. In addition, it
attempts to clean up the data to produce a high quality weather data
file.

Usage: `weather-maker.py [-h] [--version] [--grids GRIDS] [-l LATLONG LATLONG]
                        [-i I] -y YEAR --st ST [--name NAME] --hm-data HM_DATA
                        --hm-details HM_DETAILS [--tz TZ] -o OUT
                        [--format FORMAT] [-v]`

Please file bug reports at https://github.com/bje-/weather-maker/issues

Example usage
-------------

To download and make the script accessible from the terminal, use:

```
cd ~
git clone https://github.com/jdpipe/weather-maker.git
cd weather-maker
chmod +x weather-maker.py
export PATH=$PATH:~/weather-maker
export PYTHONPATH=$PYTHONPATH:~/weather-maker
```

Assuming the data files are located on a hard drive located at `/media/$USER/TOSHIBA EXT`, and assuming the ground-station weather data is located in a subfolder called `WA`, the following command should process a TMY file for 'Karratha Aero' station, which is number 004083. Note that the `--hm-data` parameter requires the name of the data file for this weather station, and the 'StdDet' file is the one containing metadata for all of the weather stations that we have. It is somewhat redundant to have to specify both the station number (`004083`) as well as the data file (`--hm-data`), it seems.

```
cd "/media/$USER/TOSHIBA EXT"
cd WA
weather-maker.py --grids /media/john/TOSHIBA\ EXT/ --hm-data HM01X_Data_004083_999999998721462.txt --hm-details HM01X_StnDet_999999998721462.txt -y 1995 --st 004083 -o ~/mytmy-karratha.txt
```

When we run this, we are still getting some errors, which need to be investigated.

