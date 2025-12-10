🚨 Attack Severity Ranking using Learning-to-Rank Algorithms
📌 Project Overview

This project focuses on ranking network intrusion attacks by their criticality using Learning-to-Rank (LTR) techniques.
Rather than simply classifying attacks, the goal is to prioritize which attacks are most severe, helping security analysts focus on high-impact threats first.

The model is trained on CICIDS 2017 network traffic data, filtered to include only attack samples. Each data point represents a network flow, and the system learns how to assign higher scores to more critical attacks, producing a ranked list of alerts.

The final output is:

Ranked attack alerts

Top-priority attack type

Score distributions and ranking comparisons across algorithms

🧠 Algorithms Used

The project implements and compares three Learning-to-Rank algorithms using LightGBM:

1️⃣ RankNet

RankNet is a pairwise ranking algorithm that learns to predict which of two samples should be ranked higher.

Optimizes relative ordering instead of absolute labels

Uses a neural network–inspired loss function

Good baseline for ranking intrusion alerts

Why used:
To establish a fundamental ranking model and benchmark performance.

2️⃣ LambdaRank

LambdaRank improves on RankNet by directly optimizing ranking metrics such as NDCG (Normalized Discounted Cumulative Gain).

Uses “lambda gradients” instead of standard loss gradients

Better aligns learning with ranking quality

More effective for prioritization problems

Why used:
To improve ranking quality and better emphasize top-ranked attacks.

3️⃣ LambdaMART (DART)

LambdaMART combines LambdaRank + Gradient Boosted Decision Trees.

In this project:

Uses DART (Dropouts meet Multiple Additive Regression Trees)

Reduces overfitting

Produces more stable rankings

Why used:
To achieve the best ranking performance while handling complex feature interactions in network traffic data.

📊 Output & Evaluation

Each algorithm produces:

A ranked list of attack samples

A top-priority attack type based on the highest score

Score distributions and rank-vs-score visualizations

Training time comparison

Ranking quality is evaluated using NDCG, emphasizing accurate prioritization of severe attacks.

✅ Key Takeaway

This project demonstrates that Learning-to-Rank models are more effective than traditional classification when the objective is attack prioritization rather than detection alone.
Among the tested methods, LambdaMART (DART) provides the most robust and reliable ranking for real-world intrusion detection systems.
