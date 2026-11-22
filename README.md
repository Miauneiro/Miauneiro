<!-- header -->
<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:06141B,45:13404F,100:A9CC4A&height=230&section=header&text=Jo%C3%A3o%20Manero&fontSize=64&fontColor=ffffff&fontAlignY=36&desc=Data%20engineering%20for%20weather%20and%20climate&descSize=19&descAlignY=58&animation=fadeIn" width="100%" alt="João Manero - Data engineering for weather and climate"/>
</p>

<p align="center">
  <a href="https://github.com/Miauneiro">
    <img src="https://readme-typing-svg.demolab.com?font=Instrument+Sans&weight=600&size=22&duration=2800&pause=900&color=A9CC4A&center=true&vCenter=true&width=720&lines=Data+Engineer+%40+PHAIR-EARTH;Four+climate+apps+shipped+in+six+weeks;From+raw+observations+to+early+warnings;Physics+first%2C+then+the+model" alt="Typing intro"/>
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Lisbon%2C%20Portugal-06141B?style=for-the-badge&logo=googlemaps&logoColor=A9CC4A" alt="Lisbon, Portugal"/>
  <a href="https://www.linkedin.com/in/joão-manero"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="mailto:joaofteixeiramanero@gmail.com"><img src="https://img.shields.io/badge/Email-13404F?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
  <img src="https://img.shields.io/badge/Meteorology-Universidade%20de%20Lisboa-5FB4C9?style=for-the-badge" alt="Meteorology, Universidade de Lisboa"/>
</p>

<br>

> I build the data backbone of a climate-risk company: the pipelines that pull in weather observations, forecasts,
> reanalyses and satellite products, the database that holds them, and the apps that turn them into decisions -
> from a street-level heat map to a warning that arrives before the storm does.

<br>

## Now: the PHAIR-EARTH platform

Since October 2025 I am the Data Engineer at **[PHAIR-EARTH](https://phair-earth.com)** (Physics and AI for a Resilient
Earth), a climate-risk spin-off of the University of Lisbon (Instituto Dom Luiz). In the last months the work grew from one
station pipeline into a **hub-and-spoke platform**: one data hub with several products on top of it. I designed, built and run
the hub and the Warning, Downscaling and Calls apps; Risk and Layers are built by colleagues on the same data.

```mermaid
flowchart LR
    S["Stations, models,<br/>reanalyses, satellites"] --> W["PHAIR Weather and Climate<br/>data hub"]
    W --> WA["PHAIR-Warning<br/>extreme-weather alerts"]
    W --> DS["PHAIR Downscaling<br/>urban climate, deep learning"]
    DS --> WA
    DS --> R["PHAIR-Risk<br/>long-term risk to 2100"]
    DS --> L["PHAIR Layers<br/>surface and atmosphere layers"]
    W --> C["PHAIR-Calls<br/>funding and tenders"]
```

<table>
<tr>
<td width="50%" valign="top">

### PHAIR Weather and Climate
**The single source of data for every other app.**
Station networks (GHCN, ECA&D, Meteostat, IPMA hourly, INMET...), forecasts (GFS, ECMWF IFS and AIFS, ICON, AROME at
~2.5 km, GEFS and ECMWF ensembles), ERA5 and CERRA reanalyses, MODIS land surface temperature, Sentinel-2 NDVI, CMIP6
scenarios and forecast verification. Maps, series, netCDF cut-outs and an API for the other apps.

`PostgreSQL` `FastAPI` `xarray` `netCDF/HDF5` `Leaflet` `Plotly`

</td>
<td width="50%" valign="top">

### PHAIR-Warning
**Extreme-weather alerts, made to measure for each place.**
Compares several forecast models with each location's 30-year climate and with the official thresholds, by
municipality, up to 5 days ahead: heat, cold, rain and wind. Personal places with sector thresholds, plans,
four languages, a desktop app and a phone web app.

`multi-model ensembles` `climatology` `PWA` `Tauri`

</td>
</tr>
<tr>
<td valign="top">

### PHAIR Downscaling
**The climate of the city, street by street.**
Turned our CTO's research deep-learning downscaler (UCDL) into a product: runs, results, catalogue and reports in one app,
GPU-backed, with cached views that make restarts invisible. The base for selling high-resolution data per km² and
for feeding the other products.

`PyTorch` `deep learning` `SLURM` `SQLite`

</td>
<td valign="top">

### PHAIR-Calls
**Funding calls and tenders, already scored.**
Collects public funding and procurement notices (PT/ES), reads the documents and scores each one 0-100 against the
company profile with an LLM, then puts the decision in cards: stack, funnel and sources.

`LLM evaluation` `scraping` `PDF parsing` `scoring`

</td>
</tr>
</table>

**Shared across all apps:** one PHAIR account with multi-factor sign-in and per-app access (with end dates for
contractors), the same design system in light and dark themes, desktop installers for Windows and macOS built by CI,
SemVer releases with changelogs, automated tests and scheduled pipelines running 24/7 on company hardware.

<br>

## The last six months in numbers

<table>
<tr>
<td align="center" width="25%"><h1>4</h1>apps in production<br><sub>Weather, Warning, Downscaling, Calls</sub></td>
<td align="center" width="25%"><h1>320+</h1>commits<br><sub>since mid-October, private repos</sub></td>
<td align="center" width="25%"><h1>25</h1>releases<br><sub>Windows and macOS installers</sub></td>
<td align="center" width="25%"><h1>500+</h1>automated tests<br><sub>across the platform</sub></td>
</tr>
<tr>
<td align="center"><h1>17</h1>data connectors<br><sub>stations, models, warnings</sub></td>
<td align="center"><h1>~68 GB</h1>climate database<br><sub>plus TBs of gridded data</sub></td>
<td align="center"><h1>453</h1>personal weather stations<br><sub>quality-controlled, 5-minute data</sub></td>
<td align="center"><h1>4</h1>languages<br><sub>PT, EN, ES, FR</sub></td>
</tr>
</table>

<br>

## Where it started: crowdsourced stations

The first pipeline at PHAIR-EARTH, still running: **453 personal weather stations** across mainland Portugal,
Madeira and the Azores, at 5-minute resolution - 12x the time resolution and 5.7x the spatial density of the official
network. Statistical and altitude-aware quality control, validation against the national service, urban heat island
analysis and CF-1.8 netCDF4 output (~3.76 M observations, 96.2% completeness over the first 30 days).

<br>

## Open-source projects

| Project | What it does | |
|:--|:--|:--:|
| **[Geophysical Inversion](https://github.com/Miauneiro/geophysical-inversion)** | Gravity-anomaly inversion with a hybrid physics + ML model: 100-1000x faster forward modelling, Monte Carlo inversion with uncertainty | [![Live](https://img.shields.io/badge/live-demo-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://geophysical-inversion.streamlit.app) |
| **[Energy Demand Forecasting](https://github.com/Miauneiro/Energy-Demand-Forecasting)** | 24-hour electricity demand forecasts with a 4-layer LSTM (1.86 M parameters), role-based recommendations | [![Live](https://img.shields.io/badge/live-demo-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://energy-demand-forecasting.streamlit.app) |
| **[Convective Risk Analyzer](https://github.com/Miauneiro/Convective-Risk-Analyzer)** | Atmospheric instability for aviation: CAPE/CIN, Skew-T, risk for 5 aircraft types | [![Live](https://img.shields.io/badge/live-demo-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://convective-risk-analyzer.streamlit.app) |
| **[Föhn Effect Analysis](https://github.com/Miauneiro/Fohen-Effect-Analysis)** | Extreme temperature events from orographic processes, with interactive thermodynamics | [![Live](https://img.shields.io/badge/live-demo-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://fohen-effect-analysis.streamlit.app) |
| **[Ocean Water Masses](https://github.com/Miauneiro/Oceanographic-Water-Mass-Analysis-in-Python)** | CTD profiles, T-S diagrams and Optimum Multiparameter water-mass analysis | [![Live](https://img.shields.io/badge/live-demo-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://oceanographic-water-mass-analysis-in-python.streamlit.app) |

<br>

## Toolbox

<p align="center">
  <img src="https://skillicons.dev/icons?i=py,pytorch,tensorflow,sklearn,postgres,sqlite,fastapi&theme=dark" alt="Python, PyTorch, TensorFlow, scikit-learn, PostgreSQL, SQLite, FastAPI"/><br>
  <img src="https://skillicons.dev/icons?i=rust,tauri,js,html,css,powershell,r,latex&theme=dark" alt="Rust, Tauri, JavaScript, HTML, CSS, PowerShell, R, LaTeX"/><br>
  <img src="https://skillicons.dev/icons?i=git,github,githubactions,linux,windows,vscode&theme=dark" alt="Git, GitHub, GitHub Actions, Linux, Windows, VS Code"/>
</p>

<p align="center"><sub>Scientific stack: xarray, netCDF4, MetPy, gsw, Cartopy, pandas, NumPy, Plotly, Leaflet - and HPC with SLURM.</sub></p>

<br>

## Stats

<p align="center">
  <img height="170" src="https://github-readme-stats.vercel.app/api?username=Miauneiro&show_icons=true&count_private=true&include_all_commits=true&theme=tokyonight&hide_border=true&border_radius=12&title_color=A9CC4A&icon_color=5FB4C9&ring_color=A9CC4A" alt="GitHub stats"/>
  <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Miauneiro&layout=compact&langs_count=8&theme=tokyonight&hide_border=true&border_radius=12&title_color=A9CC4A" alt="Top languages"/>
</p>
<p align="center">
  <img src="https://streak-stats.demolab.com/?user=Miauneiro&theme=tokyonight&hide_border=true&border_radius=12&ring=A9CC4A&fire=E0503F&currStreakLabel=A9CC4A" alt="GitHub streak"/>
</p>

<br>

## How I work

- **Physics first.** A meteorology background means I know why the atmosphere behaves the way it does, which makes
  for better quality control, better features and models that fail less in the places that matter.
- **Ship it, then measure it.** Every app has versions, release notes, tests and installers; every pipeline has
  monitoring. Products are used by real people, not left in notebooks.
- **Autonomous and remote-ready.** Years of remote work (tutoring, and managing an international editorial team across
  time zones) and now full ownership of a company's data platform, end to end.

<br>

<p align="center">
  <a href="https://www.linkedin.com/in/joão-manero"><b>LinkedIn</b></a> ·
  <a href="mailto:joaofteixeiramanero@gmail.com"><b>joaofteixeiramanero@gmail.com</b></a> ·
  <sub>open to collaborations in climate data, forecasting and climate risk</sub>
</p>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:A9CC4A,55:13404F,100:06141B&height=120&section=footer" width="100%" alt=""/>
