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
<img width="414" height="96" alt="image" src="https://github.com/user-attachments/assets/0b3c081e-50aa-4e5c-9d87-41335e02cb8c" /> <img width="544" height="97" alt="image" src="https://github.com/user-attachments/assets/24864691-6531-4644-82a6-d7c24925ad2d" />




