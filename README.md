Title: GAM analysis of Fish eggs and larvae (ichthyoplankton) eastern Arabian Sea
# Author: Sonal Rajendra Kalbande 
# Journal: Frontiers in Marine Science
# Year: 2025
# DOI: https://doi.org/10.3389/fmars.2025.1705873
# If you use this code, please cite:
# Kalbande, S.R. et al. (2025). Front. Mar. Sci., 12.


# GAM_fish_Eggs-larvae-analysis-GAM_-ichthyoplankton-eastern-Arabian-Sea
R scripts for GAM analysis used in Kalbande et al. (2025), Frontiers in Marine Science
Supplementary Details: R script for the full Generalized Additive Model (GAM), along with the corresponding 95% confidence intervals.
a) For Fish eggs- GAM- R script
library(mgcv)

R_data <- read.csv("E:/cr46/R_data.csv")

# Data preparation for Gamma family
R_data$FishEgg <- R_data$FishEgg + 0.03

# Model Fitting
gam_log <- gam(FishEgg ~ s(Latitude) + s(WindSpeed) + s(SST) + s(Chl_a) + s(SSS) + s(DO) + s(ZooplanktonBiomass) + s(Silicate) + s(Nitrite) + s(Nitrate) + s(Phosphate),
family = Gamma(link = "log"),
data = R_data)

# Model Output and Diagnostics
summary(gam_log)
gam.check(gam_log)
AIC(gam_log)

b)	For fish larvae-GAM-backwards deletion procedure 

FL-backward

library(mgcv)

R_data <- read.csv("C:/Users/sonal/R_data.csv")

# Data preparation for Gamma family
R_data$FishLarvae <- R_data$FishLarvae + 0.010

# Simplified Model Fitting (Backward Selection Result)
gam_log_simplified <- gam(FishLarvae ~ s(Latitude) + s(WindSpeed) + s(SST) + s(SSS) + s(DO) + s(Nitrate),
family = Gamma(link = "log"),
data = R_data)

# Model Output and Diagnostics
summary(gam_log_simplified)
AIC(gam_log_simplified)
gam.check(gam_log_simplified)


