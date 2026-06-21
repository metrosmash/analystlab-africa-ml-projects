# Titanic Survival Prediction API

## Project Title
Titanic Simulation — Survival Prediction API

## Model Description
The dataset used was the Titanic dataset, building on feature engineering work from week 3. Further feature engineering was applied to the data, which was then used to train a **Logistic Regression** model with `max_iter=500`. The model achieved a score of **0.80**. No further fine-tuning was done.

## Input Features

| # | Feature | Type | Description |
|---|---------------|-------|-------------|
| 1 | `Age` | float | Age of the character |
| 2 | `is_female` | int | Is the character female or not |
| 3 | `is_alone` | int | Is the character alone or not |
| 4 | `Embarked_Q` | int | Did the character embark from Queenstown |
| 5 | `Embarked_S` | int | Did the character embark from Southampton |
| 6 | `title_Master.` | int | Did the character hold the title of Master |
| 7 | `title_Miss.` | int | Did the character hold the title of Miss |
| 8 | `title_Mlle.` | int | Did the character hold the title of Mlle (Mademoiselle) |
| 9 | `title_Mr.` | int | Did the character hold the title of Mr |
| 10 | `title_Mrs.` | int | Did the character hold the title of Mrs |
| 11 | `title_Rev.` | int | Did the character hold the title of Reverend |
| 12 | `title_Unknown` | int | Unknown character title |
| 13 | `family_bin_1` | int | Did the character have a family/spouse with them, amounting to 2 or 3 |
| 14 | `family_bin_2` | int | Did the character have a large family with them, amounting from 4 to 10 |
| 15 | `Pclass_2` | int | Did the character pay for 2nd class |
| 16 | `Pclass_3` | int | Did the character pay for 3rd class |

## Example Request
Say there is a man aged 24 who boarded the ship alone. He was in 3rd class because he had no money, and he embarked from the port of Southampton.

We click the appropriate buttons in the web interface, then click the **"Check if they survived"** button.

## Example Response
We are then given a percentage chance of survival for the character we created:

```
Your Character has 6.7% Chance of Surviving!
```

## How to Run the API

1. Clone or download the project folder.
2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```
3. Run the app:
   ```
   python -m main
   ```
4. This starts a web interface. Open your browser and navigate to:
   ```
   http://127.0.0.1:5000
   ```
5. Fill in the character's details in the form and click **"Check if they survived"** to get the prediction.
