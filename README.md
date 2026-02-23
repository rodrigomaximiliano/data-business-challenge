iFood Data Analyst Challenge

Comprehensive analysis of the iFood customer dataset including segmentation, predictive modeling, and campaign investment optimization recommendations.

Objective

The pilot campaign sent to 2,205 customers generated a profit of -2,952 MU — meaning money was lost by contacting everyone indiscriminately.

This challenge aims to answer:

Who are our customers and how do they behave?

Can we segment them into actionable groups?

Can we predict who will respond to the next campaign to make it profitable?

How do we translate data insights into creative and budget decisions?

Dataset

2,205 customers, 39 variables

No missing values — analysis-ready dataset

Includes spending behavior, purchase channels, previous campaign history, demographics, and target variable Response

Contact cost: 3 MU | Revenue per response: 11 MU

Project Structure
data-business-analyst-challenge/
├── data/
│   └── ifood_df.csv
├── analysis.ipynb
├── eda_perfil_respuesta.png
├── eda_canales.png
├── elbow.png
├── segmentos.png
├── feature_importance.png
├── campaign_performance.png
├── README_ES.md
├── README_EN.md
└── requirements.txt
Methodology
1. EDA — Responder Profile

Median profile comparison between responders and non-responders:

Responders have 28% higher income ($64k vs $50k)

Spend 3.5x more ($960 vs $275)

Accepted at least 1 previous campaign — past behavior predicts future behavior

Use web and catalog channels more frequently — digitally active customers

Non-responders rely more on discounts — price-driven, not premium customers

2. Segmentation using K-Means (k=4)
Segment	Customers	Median Income	Median Spend	CTR	ROAS	Decision
⭐ Champions	236	$80,137	$1,537	49%	1.79	🟢 Scale
💰 High Value	805	$65,704	$896	13%	0.48	🟡 Review creative
🌱 Recently Active	589	$35,860	$58	15%	0.55	🟡 Adjust offer
😴 Dormant	575	$36,732	$62	4%	0.16	🔴 Pause
3. Predictive Model — Random Forest

A Random Forest classifier was trained with class_weight='balanced' to predict customer response probability.

Top Important Features:

Customer_Days — customer tenure

Recency — days since last purchase

AcceptedCmpOverall — campaign acceptance history

MntMeatProducts, MntTotal — spending level

Business impact (test set):

	Contacts	Profit
Mass campaign	441	-586 MU
Model-driven targeting	26	+120 MU
Improvement	-94% contacts	+706 MU
4. Concept × Trigger × Persona × Format × Hook Matrix

Translation of data insights into creative strategy per segment:

	Champions	High Value	Recently Active	Dormant
Concept	Exclusivity / Premium	Perceived value	Frequency / Habit	—
Trigger	Accepted 2+ past campaigns	High income, low conversion	Frequent buyer, low ticket	ROAS 0.16, unprofitable
Persona	Premium, $1,537 spend, digital	High purchasing power	Recent customer, low spend	Inactive
Format	Catalog / Personalized Email	Display / Direct offer	Push / Volume discount	—
Hook	"Exclusive access, just for you"	"At this price, today only"	"Complete your basket"	—
Investment Recommendations

🟢 Champions → Scale. Only segment with positive ROAS (1.79). CPA of just $6.

🔴 Dormant → Pause. CPA $69 for $11 revenue. Guaranteed loss.

🟡 High Value → Do not pause — optimize creative. They have purchasing power but current messaging underperforms.

🟡 Recently Active → Adjust offer. High frequency, low ticket size. Campaign misaligned with customer profile.

Technologies Used

Python 3.12

pandas, numpy

matplotlib, seaborn

scikit-learn (KMeans, RandomForestClassifier)

Jupyter Notebook

How to Reproduce the Analysis
git clone https://github.com/rodrigomaximiliano/data-business-challenge
cd data-business-challenge
python -m venv venv
venv\Scripts\activate        # Windows
pip install -r requirements.txt
jupyter notebook analysis.ipynb
Conclusion

A mass campaign is not optimal when only 15% of customers respond.

By combining segmentation and predictive modeling, it is possible to:

Reduce contact volume by 94%

Move from losses to positive profit

Make informed decisions about message, format, and hook per customer segment

Data-driven targeting turns marketing from cost center into profit engine.