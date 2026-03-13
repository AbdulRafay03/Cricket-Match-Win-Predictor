
# Cricket Match Win Predictor

This project analyzes ball-by-ball data from ODI cricket matches to extract insightful features and build a machine learning-based win prediction system. It uses historical match data to train two models:

### Approach

1. **Pre-Match Predictor**
   This model uses pre-match features such as teams, venue, and toss outcome to predict the *expected winner* before the match begins. It is trained on historical matches and captures general team strengths and situational context.

2. **Ball-by-Ball Predictor**
   The second model takes the *expected winner* as an input and dynamically updates the win probability after every ball using real-time match data. This model is trained on delivery-level data and adapts to the changing match situation.

---

### Project Structure

* `Creating Dataset.py`: Parses raw JSON files and generates delivery-level data with engineered features.
* `Datafiles/`: Directory containing raw match JSON files.
* `Dataset/`: Processed and feature-rich dataset ready for training or inference.
* `Models/`: Contains `.pkl` files for trained LightGBM models with high accuracy.
* `WinPredictionNotebook.ipynb`: Interactive notebook for training models or running inference.

---

### Extracted Features

The following features are extracted and computed from the match data:

| Feature                                            | Description                                                      |
| -------------------------------------------------- | ---------------------------------------------------------------- |
| `match_id`                                         | Unique identifier for each match                                 |
| `inning`                                           | 1 if batting first, 2 if chasing                                 |
| `batting_team`, `bowling_team`                     | Teams involved in the delivery                                   |
| `over`, `ball_in_over`                             | Ball position within the match                                   |
| `batter`, `bowler`                                 | Names of players                                                 |
| `runs_off_bat`, `extras`, `total_runs`             | Breakdown of each delivery                                       |
| `is_wicket`, `wicket_type`, `player_out`           | Wicket-related info                                              |
| `current_score`, `wickets_lost`, `balls_bowled`    | Current match state                                              |
| `run_rate`                                         | Current run rate                                                 |
| `target_runs`, `runs_remaining`, `balls_remaining` | Target-based stats for chasing team                              |
| `required_run_rate`                                | Required run rate to win                                         |
| `pressure_index`                                   | Categorical metric: High, Medium, Low pressure                   |
| `projected_score`                                  | Projected score based on current rate                            |
| `partnership_runs`                                 | Runs added by current batting pair                               |
| `run_rate_vs_required_diff`                        | Current RR minus required RR                                     |
| `comparative_rr`                                   | Difference between team and opponent run rates in second innings |

---

### How to Use

1. Place raw JSON files in the `Datafiles/` directory.
2. Run `Creating Dataset.py` to parse and generate the processed dataset.
3. Train the models or run inference using the notebook (`WinPredictionNotebook.ipynb`).
4. Trained models are available in the `Models/` folder.

---

### Applications

* Predict match outcomes dynamically during a live match.
* Analyze momentum shifts through run rate trends.
* Evaluate pressure scenarios and turning points in the match.
* Provide real-time insights for broadcasters or viewers.

---

### Requirements

* Python 3.8+
* pandas
* scikit-learn
* lightgbm

Install dependencies using:

```bash
pip install -r requirements.txt
```

---

Let me know if you'd like a `requirements.txt` or a sample output visualization section added.
