# SEIRify_
SEIRify is a simple, interactive, and user-friendly R Shiny application designed for post-outbreak analysis of community-level infectious disease data. SEIRify allows users to fit SEIR-based models, visualize the disease trajectories in compartments, and generate estimates of critical model parameters through an accessible web interface. 

# Installation

This application is available as a shiny application downloadable at https://github.com/ACHANGWA/SEIRify. R was chosen as the computing platform because it is free, open source, and runs on any modern operating system so the application can be broadly available as possible.

To install and run the shiny app locally on your computer you will need to first install R, it is also suggested that you install Rstudio. For detailed instructions for installing the R and R studio, visit the respective links https://cran.r-project.org/bin/windows/base/ and https://posit.co/download/rstudio-desktop

# About page

Upon initially loading the application, users will see the “About” icon at the top right side of the application. This page provides an overview of the methods employed within the dashboard, including model specification, forecasting, and details of the available evaluation statistics. 

# Explore model's page

The Explore models page serves as the starting point for using the SEIRify dashboard (Figure 1), including specifying the scenario of interest (Simulated Scenario Only versus Simulated and Real Scenario compared), compartmental model type (SI, SIR, and SEIR), inputting disease parameters based on selected models (transmission rate, exposure rate and recovery rate) and inputting the population parameters (Total population, initial susceptible, exposed, infected and recovered). After selecting all necessary options and clicking the “Run model simulation” button, the resulting models fit and display the appropriate model visualizations and model parameters on this page. Note that each time any input is changed, the “Run model simulation” button has to be clicked again. Note that if options have not been specified and processed, the dashboard will remain blank (Figure 1). The model parameter window displays the key inputs and estimated parameters used in the simulation, allowing users to verify the correctness of the model setup.
The Comparison window provides model outputs of the real versus simulated scenarios. These include key epidemiological metrics, such as the reduction in total infections, the reduction in outbreak duration (in days), the reduction in peak size, the delayed epidemic start (in days), and the delay in the timing of the peak (in days). For each metric, the window displays the point estimate along with its 95% confidence interval (CI).
<img width="975" height="489" alt="image" src="https://github.com/user-attachments/assets/1a241a87-7f25-433e-817b-f8583ebd5529" />
Figure 1. A screenshot of the Explore models page after initially loading the dashboard.
Users primarily interact with the dashboard’s sidebars, where details related to the population, scenario specifications, and all model parameters must be entered. Once selected, the user can then click “Run model simulation” to obtain the output. The SEIRify dashboard was developed using R-Shiny. 
The Demographics window shows a summary of all the variables of the uploaded dataset. Numeric variables are summarized as means and standard deviations, while categorical variables are presented as counts and percentages. 
<img width="975" height="149" alt="image" src="https://github.com/user-attachments/assets/95c01f7f-068d-4f28-b864-ec7f9c7beb97" />
Figure 2. A screenshot of the Demographics tab 

# The scenarios

SEIRify allows users to explore two types of scenarios, the simulated scenario and the real versus simulated scenario. To activate each scenario, the toggle must be switched on for the simulated scenario and off for the real versus simulated scenario (Figure 2). In the simulated scenario, the model generates plots and model parameters for each compartment based only on user-defined parameters, including population size, transmission rate, recovery rate, and simulation duration. This mode is useful for examining hypothetical situations. In the real versus simulated scenario, users are expected to upload an outbreak dataset, and the model compares simulated epidemic curves with the observed data
<img width="967" height="98" alt="image" src="https://github.com/user-attachments/assets/004f11a2-d303-4417-98f4-d96f7eb004ee" />
Figure 3. A screenshot showing how to activate both the simulated scenario only and the real versus simulated scenario

# The input data

In SEIRify, users can upload their own outbreak datasets in CSV format using the “Choose CSV File” option for the ‘real versus simulated scenario’ ONLY. For users who do not have a dataset, a mock dataset can be downloaded directly from the interface at the bottom left corner (‘Download Mock Data’). Note that this is a dummy dataset for demonstration. The input data must follow a structured format with specific variables. The uploaded dataset must have the following required variables and format;

-	date_of_exposure: the date when an individual was exposed to infection in YYY-MM-DD format.
-	date_of_onset: the date when symptoms or infection onset occurred in YYY-MM-DD format.
-	Any other demographic or disease-related required variable (Figure 3).
<img width="940" height="665" alt="image" src="https://github.com/user-attachments/assets/c8d23022-1a3b-45cc-80fe-68210f66d6af" />
Figure 4. Screenshot of the data CSV file

# The models
The current version of SEIRify provides users with the opportunity to model three different compartmental models (Figure 4):
-	Susceptible (S) – Infectious (I): SI Model
In SI models, individuals who become infected remain infectious for life, as infection does not confer immunity. Thus, people never leave the infectious state. This structure is suitable for modeling lifelong infections such as HIV or herpes virus. The key parameter is the transmission rate (β), which represents the probability of disease transmission between a susceptible and an infectious individual per contact per unit time.
<img width="446" height="152" alt="image" src="https://github.com/user-attachments/assets/fb9a9e40-04bc-41ad-9325-96467302c47f" />

-	Susceptible (S) – Infectious (I) – Recovered (R): SIR Model
In SIR models, infected individuals eventually recover and move into the recovered class, where they are assumed to be immune. The two main parameters are the transmission rate (β) and the recovery rate (α), with α defined as the reciprocal of the mean infectious period (1/mean infectious period).
<img width="577" height="133" alt="image" src="https://github.com/user-attachments/assets/7b7cd445-8074-4952-9e22-7ec31cce8377" />

-	Susceptible (S) – Exposed (E) – Infectious (I) – Recovered (R): SEIR Model
The SEIR model adds an exposed class to capture the incubation period during which individuals are infected but not yet infectious. This model is widely used for acute infectious diseases with a latent stage. Parameters required for this model include the transmission rate (β), the progression rate (k) from exposed to infectious (defined as the reciprocal of the incubation period, 1/incubation period), and the recovery rate (α) (1/mean infectious period).
<img width="590" height="91" alt="image" src="https://github.com/user-attachments/assets/70359ba1-2160-4d8a-9fd5-23ede1532dd0" />

<img width="346" height="188" alt="image" src="https://github.com/user-attachments/assets/40357e87-2b21-4f72-9efa-ab0d34cec00f" />

Figure 5. Screenshot displaying the compartmental models in SEIRify

Depending on the user’s interest, SEIRify provides the option to visualize the dynamics of individual model compartments separately. By selecting “Show compartments separately”, users can isolate and plot the trajectory of a chosen compartment (e.g., susceptible, exposed, infected, or recovered). In addition, the interface allows the display of confidence intervals for either the simulated scenario, the real scenario, or both, with selectable levels (95%, 90%, 75%, or 50%). This functionality enables more detailed exploration of compartment-specific dynamics and facilitates comparison between real and simulated outcomes

<img width="480" height="587" alt="image" src="https://github.com/user-attachments/assets/74bf2a09-359b-48bb-9fcd-b1452826d686" />

Figure 6. Screenshot showing selection of the ‘show compartment separately’ icon and its specificities

# The population 

In SEIRify, users are required to specify the total population (N) for which the simulation will be performed. Once this value is entered, the system automatically adjusts the counts for the initial susceptible and initial infected populations according to the user’s input. This setup reflects the epidemiological principle that an outbreak typically begins with an index case and subsequently spreads to susceptible individuals in the community. Users must also provide the simulation duration (days), which determines the time horizon of the epidemic projection in the simulated scenario. For the real versus simulated scenario, however, the epidemic duration is determined by the range of dates present in the uploaded dataset. An additional optional input allows users to define the total population size in the real versus simulated scenario, enabling estimation of the uninfected population as the difference between the total community population and the number of infected individuals recorded in the uploaded dataset.

<img width="387" height="588" alt="image" src="https://github.com/user-attachments/assets/1eec29cf-fec7-4b95-8d1e-9105d82f5a68" />

Figure 7. A screenshot of the population input fields showing the initial conditions and simulation duration for the outbreak model


# The epidemiological parameters

Based on the selected model, users are required to specify the appropriate epidemiological parameters. These include the transmission rate (β), defined as the probability of infection per contact per unit time; the progression rate (k) from exposed to infectious, which is the reciprocal of the incubation period (1/incubation period); and the recovery rate (α), defined as the reciprocal of the mean infectious period (1/mean infectious period). In SEIRify, these parameters are adjusted interactively by moving the corresponding toggles on the interface, allowing users to explore different epidemic trajectories under varying assumptions of disease transmissibility, latency, and recovery.


# Output

SEIRify provides multiple options for accessing and exporting model outputs. Visual results are displayed in the Model Visualization window, where epidemic dynamics can be plotted by compartment for both simulated and real scenarios. These plots can be downloaded directly as PNG images or PDF documents for reporting and presentations. In addition, the underlying model parameters are displayed in the Model Parameters window, with the option to export the data in CSV, Excel, or PDF formats. Similarly, the Comparison window summarizes key performance metrics between simulated and real scenarios (reduced duration, delayed start, reduced infections, reduced peak, or delayed peak), which can also be downloaded in the same formats. 

# Application specifications 

To ensure broad accessibility, SEIRify was developed as a web-based application that can be accessed through a standard internet browser without the need for specialized software installation. The framework was built on RStudio Shiny. The epidemic models were implemented as R scripts, with each model encapsulated in a dedicated R function and invoked by the server-side script (server.R) of the Shiny application. This design maintained a clear separation between the user interface and computational components, allowing model code to be modified independently of the application interface.  The SEIRify application was developed using several packages to support its functionality. The shiny, shinyWidgets, and shinyjs packages provide the core framework for building the interactive dashboard and extending functionality. flexdashboard was used to structure the user interface, while highcharter supported interactive visualizations, complementing the built-in plotting features. For epidemiological modeling, deSolve was employed to solve systems of ordinary differential equations, and EpiEstim was used for estimating time-varying reproduction numbers. Data cleaning and management were facilitated by tidyverse, tidyr, data.table, and janitor, with DT enabling interactive tabular displays. lubridate was used for handling dates and times, which are central to epidemic datasets. Font management and customization of visual outputs were achieved through extrafont, extrafontdb, systemfonts, and sysfonts. 
Below are the epidemiological parameters for some selected infectious diseases. These parameters can be used for both the simulated scenario only and the real versus simulated scenario.

<table>
  <thead>
    <tr>
      <th rowspan="2">Parameter</th>
      <th colspan="6">Infectious Disease</th>
    </tr>
    <tr>
      <th>COVID-19</th>
      <th>Influenza A</th>
      <th>Measles</th>
      <th>Pertussis</th>
      <th>Ebola</th>
      <th>mpox</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Transmission rate per day – β</strong></td>
      <td>Wild<br>0.21–0.28<br><br>Omicron<br>1.14–2.0</td>
      <td>1.8</td>
      <td>1.7–2.6</td>
      <td>0.2–0.5</td>
      <td>0.2 to 0.3</td>
      <td>0.01 to 0.1</td>
    </tr>
    <tr>
      <td><strong>Exposure rate – σ (1/Incubation Period)</strong></td>
      <td>0.21 (1/4.6 days)</td>
      <td>0.5 (1/2 days)</td>
      <td>0.08 (1/13 days)</td>
      <td>1/7–1/10</td>
      <td>1/2–1/21</td>
      <td>1/10</td>
    </tr>
    <tr>
      <td><strong>Recovery rate – γ (1/duration of infectiousness)</strong></td>
      <td>0.1–0.2<br>(≈ 1/5–10 days)</td>
      <td>0.2<br>(1/5 days)</td>
      <td>0.1–0.14<br>(1/7–10 days)</td>
      <td>0.071</td>
      <td>1/6–1/16</td>
      <td>0.05</td>
    </tr>
  </tbody>
</table>

# Case study 1: Simulated Scenario ONLY - Influenza A 

To demonstrate the simulated functionality of SEIRify, we modeled an influenza A outbreak in a hypothetical community of 100 individuals over a 30-day period using the SEIR compartmental model. At the start of the simulation, the population was initialized with 99 susceptible, 1 infected, 0 exposed, and 0 recovered individuals, reflecting the introduction of a single index case into an otherwise susceptible population. 

<img width="466" height="864" alt="image" src="https://github.com/user-attachments/assets/d14bdbd3-b77b-448e-aa4d-ac04141064d2" />

Figure 8. Screenshot showing initial input of population parameters

The model parameters were specified as follows: transmission rate (β) of 1.8 per contact per unit time, exposure rate (σ) of 0.5 (corresponding to an average incubation period of 2 days), and recovery rate (γ) of 0.24 (corresponding to an average infectious period of approximately 4 days). These parameter values represent plausible ranges for influenza A transmission dynamics as published in the empirical literature [].

<img width="623" height="500" alt="image" src="https://github.com/user-attachments/assets/2c796078-fd2c-4602-9095-39bcbb925b85" />
Figure 9. Screenshot showing initial input of transmission parameters

# The outputs
# Visualization

After selecting the “show compartment separately” option, we visualized each compartment individually to better understand the dynamics of the simulated outbreak. Visual plots for each compartment downloaded from SEIRify are shown below.

# The susceptible (S) compartment 

The susceptible population declined rapidly over the 30-day simulation period. Beginning with 99 susceptible individuals at the onset of the epidemic, the curve shows an accelerated decrease between days 5 and 10 as exposure and transmission intensified. By approximately day 12, the number of susceptible individuals dropped close to zero, indicating that nearly the entire population had transitioned to exposed or infected compartments.

<img width="797" height="532" alt="image" src="https://github.com/user-attachments/assets/cee4419e-0566-4b31-b3c9-c9809bdc92bf" />

Figure 10. Output for the simulated scenario S compartment


# The Exposed (E) compartment 

The exposed population followed a bell-shaped trajectory during the 30-day simulation. Starting at zero, the number of exposed individuals rose steadily as susceptibles became infected but had not yet developed symptoms. The curve peaked around day 8, with approximately 28 individuals in the exposed state, reflecting the maximum buildup of latent infections. After the peak, the exposed population declined sharply as individuals transitioned into the infectious compartment. By day 20, the exposed compartment had nearly returned to zero, indicating depletion of the latent pool as the epidemic progressed.

<img width="726" height="484" alt="image" src="https://github.com/user-attachments/assets/8a311506-c1e8-4ff1-b2d6-37cd2997049a" />

Figure 11. Output for the simulated scenario E compartment

# The Infected (I) compartment 

Beginning with a single index case, the number of infected individuals increased gradually in the first few days, followed by a sharp rise as transmission accelerated. The curve peaked around day 10, with nearly 38 individuals simultaneously infectious, representing the maximum burden of active cases in the community. After this peak, the number of infected individuals declined steadily as recoveries outpaced new infections.
<img width="525" height="350" alt="image" src="https://github.com/user-attachments/assets/d642a737-319c-454e-a1d4-0a7d1d9ce868" />
Figure 12. Output for the simulated scenario I compartment

# The Recovered (R) compartment 









