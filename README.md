# Anipang Adoption Competitor Analysis

This project applies propensity-score matching and panel difference-in-differences on weekly data from 849 Android users to examine how adopting the hit game Anipang impacts rival game usage. Using dummy-variable OLS and fixed-effects regressions across ten matched samples, adoption neither significantly reduces time spent on nor the number of rival (non-Kakao) games, nor does it cannibalize usage from competing platforms.

---

## Project Motivation
Understanding how popular mobile games affect user engagement with rival apps helps developers and marketers assess competitive dynamics and inform retention or cross-promotion strategies.

---

## Data Overview
**Dataset:** `kakao_all.csv`  
**Data Type:** Individual-level weekly panel data on app usage count and time (Android devices)  
**Users (N):** 849 Android mobile users  
**Time Period (T):** 2 weeks (July 23 – August 5, 2012)  
- Week 1: Pre-Adoption of Anipang  
- Week 2: Post-Adoption of Anipang  

### Variables

#### User, Time, Treatment
| Variable | Description |
|----------|-------------|
| `panel_id` | User ID |
| `week` | 1 = before Anipang release, 2 = after Anipang release |
| `tg` | 1 = treatment group (Anipang adopters), 0 = control group (non-adopters) |
| `ii` | 1 if user adopted Anipang at/before current week, 0 otherwise |

#### Demographic Profile
| Variable | Description |
|----------|-------------|
| `age` | 1: 7–18, 2: 19–29, 3: 30–39, 4: 40–49, 5: 50–69 |
| `gender` | 1 = Male, 0 = Female |
| `income` | 1: <$1,000, 2: $1,000–3,000, 3: $3,000–5,000, 4: >$5,000 |
| `education` | 1: Elementary–High school, 2: High school grad, 3: Undergrad/grad student, 4: College grad |

#### App Usage Within Kakao Platform
| Variable | Description |
|----------|-------------|
| `log_t_kakao_talk` | Log-transformed usage time of Kakao Talk (seconds) |
| `log_t_kakao_story` | Log-transformed usage time of Kakao Story (excluding Anipang) (seconds) |
| `log_t_kakao_game` | Log-transformed usage time of Kakao Game apps (seconds) |
| `n_kakao_game` | Number of Kakao Game apps used (excluding Anipang) |

#### App Usage Outside Kakao Platform
| Variable | Description |
|----------|-------------|
| `log_t_non_kakao_talk` | Log-transformed usage time of communication apps (seconds) |
| `log_t_non_kakao_story` | Log-transformed usage time of social networking apps (seconds) |
| `log_t_non_kakao_game` | Log-transformed usage time of game apps (seconds) |
| `log_t_non_kakao` | Log-transformed usage time of all non-Kakao apps (seconds) |
| `n_non_kakao_talk` | Number of communication apps used |
| `n_non_kakao_story` | Number of social networking apps used |
| `n_non_kakao_game` | Number of game apps used |
| `n_non_kakao` | Number of all non-Kakao apps used |
| `log_t_anipang` | Log-transformed usage time of Anipang (seconds) |

---

## Analysis Approach
1. Propensity-score matching to balance covariates across adopters and non-adopters  
2. Dummy-variable OLS regressions on matched samples  
3. One-way fixed-effects panel regressions  
4. Interpretation of adoption effects on rival game usage  

---

## Key Findings
- Adoption of Anipang does **not significantly reduce** time spent on or the number of rival non-Kakao games  
- Adoption does **not cannibalize usage** on competing platforms  
- Suggests adoption impacts overall engagement without displacing other games  

---

## Key Methods & Tools
| Category | Details |
|----------|---------|
| Methods  | Propensity Score Matching (PSM), Dummy-Variable Regression, One-Way Fixed-Effects Panel Regression |
| Tools    | RStudio (packages: MatchIt, plm, lmtest, dplyr, ggplot2) |

---

## How to Run
1. Clone the repository:  
```bash
git clone https://github.com/yuki-fang/anipang-adoption-competitor-analysis.git
