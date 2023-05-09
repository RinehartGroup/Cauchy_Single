# [Cauchy_Single](https://github.com/RinehartGroup/Cauchy_Single/blob/main/Cauchy_Single.ipynb)

<a href="https://zenodo.org/badge/latestdoi/638608500"><img src="https://zenodo.org/badge/638608500.svg" alt="DOI"></a>

`Cauchy_Single` is a Jupyter Notebook for the fitting of magnetization curves to a single Cauchy distribution

## Requirements
- `numpy`
- `scipy`
- `pandas`
- `lmfit`
- `os`
- `glob`

## Importing data
`Cauchy_Single` imports a .csv with headers of temperature (`Temp`), magnetic field in Tesla (`Field`), magnetic moment (`Moment_emu`), magnetic moment per gram (`Moment_emu_g`), and a corrected magnetic field in Tesla (`Field_True`)
- Note: Due to slight remnant fields in the SQUID magnetometer, `Field` is converted to `Field_True` through a measurement of the Pd standard, described previously in [Quantum Design Application Note 1500-021](https://qdusa.com/siteDocs/appNotes/1500-021.pdf)

## Selecting and manipulating data
- `Cauchy_Single` will automatically select the forward sweep of the magnetization curve, then interpolate to generate 10,000 equally spaced points, preventing emphasis of the fit to any specific region.

## Fit parameters
The modified Cauchy distribution consists of four parameters with initial guesses and reasonable bounds:
- Chi_linear (`Xp`): linear contribution due to paramagnetic/diamagnetic signal(s)
- Gamma (`gamma`): sharpness of magnetization curve
- Coercive field (`Hc`): offset in field (x-axis)
- Saturation magnetization (`Ms`): scaling factor in emu/g

## Output
- Plot of interpolated magnetization curve with Cauchy fit to curve
- Derivative of Cauchy fit (dMdH vs. H)

## Usage
- Change directories for finding files and saving purposes
- Ensure reasonable initial guesses for fit

## Notes
- To reach the correct susceptibility unit (cm<sup>3</sup>/g), ensure that the dMdH values are divided by 10,000, as the native unit for magnetic field in this code is in Tesla, not Oerstead.
