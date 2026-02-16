#import libraries in python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('marketing_campaign_dataset 01.csv')

# Data cleaning: Convert Acquisition_Cost to numeric (remove $ and ,)
df['Acquisition_Cost'] = df['Acquisition_Cost'].replace('[\$,]', '', regex=True).astype(float)

# Convert Date to datetime
df['Date'] = pd.to_datetime(df['Date'], dayfirst=True)

# Basic stats
total_records = len(df)
avg_conversion_rate = df['Conversion_Rate'].mean()
total_acquisition_cost = df['Acquisition_Cost'].sum()
avg_roi = df['ROI'].mean()
avg_engagement = df['Engagement_Score'].mean()

# Performance by Campaign Type
campaign_performance = df.groupby('Campaign_Type').agg({
    'Conversion_Rate': 'mean',
    'Acquisition_Cost': 'sum',
    'ROI': 'mean',
    'Engagement_Score': 'mean',
    'Clicks': 'sum',
    'Impressions': 'sum'
}).sort_values(by='Conversion_Rate', ascending=False)

# Performance by Channel Used
channel_performance = df.groupby('Channel_Used').agg({
    'Conversion_Rate': 'mean',
    'Acquisition_Cost': 'sum',
    'ROI': 'mean',
    'Engagement_Score': 'mean'
}).sort_values(by='ROI', ascending=False)

# Monthly Trends
df['Month'] = df['Date'].dt.to_period('M')
monthly_trends = df.groupby('Month').agg({
    'Conversion_Rate': 'mean',
    'Engagement_Score': 'mean',
    'Acquisition_Cost': 'sum'
}).reset_index()

# Audience Analysis
audience_performance = df.groupby('Target_Audience').agg({
    'Conversion_Rate': 'mean',
    'ROI': 'mean'
}).sort_values(by='Conversion_Rate', ascending=False)

segment_performance = df.groupby('Customer_Segment').agg({
    'Conversion_Rate': 'mean',
    'ROI': 'mean'
}).sort_values(by='Conversion_Rate', ascending=False)

# Monthly Engagement Trend
monthly_engagement = df.groupby('Month')['Engagement_Score'].mean()

print("\nAudience Performance:")
print(audience_performance)
print("\nSegment Performance:")
print(segment_performance)
print("\nMonthly Engagement Trend:")
print(monthly_engagement)

output
Code output
Total Campaigns: 200000
Avg Conversion Rate: 0.0801
Total Acquisition Cost: 2500878608.00
Avg ROI: 5.00
Avg Engagement: 5.49 

Campaign Performance:
               Conversion_Rate  Acquisition_Cost       ROI  Engagement_Score    Clicks  Impressions
Campaign_Type                                                                                      
Influencer            0.080315       502400525.0  5.011068          5.483134  22037657    220769081
Social Media          0.080135       498218100.0  4.991784          5.497878  21955724    219056401
Display               0.080089       500158774.0  5.006551          5.505889  22030979    220074756
Search                0.080021       501911760.0  5.008357          5.487138  22032144    221415139
Email                 0.079788       498189449.0  4.994295          5.499624  21897902    220144927

Channel Performance:
              Conversion_Rate  Acquisition_Cost       ROI  Engagement_Score
Channel_Used                                                               
Facebook             0.079992       410595258.0  5.018699          5.503702
Website              0.080183       416593500.0  5.014167          5.508903
Google Ads           0.080183       418912314.0  5.003141          5.494049
Email                0.080282       420874104.0  4.996487          5.487842
YouTube              0.079889       416778582.0  4.993754          5.484937
Instagram            0.079886       417124850.0  4.988706          5.489039

# Audience Analysis
code output
Audience Performance:
                 Conversion_Rate       ROI
Target_Audience                           
Men 18-24               0.080240  4.982853
Men 25-34               0.080132  5.020627
Women 35-44             0.080102  5.006330
All Ages                0.079975  5.005174
Women 25-34             0.079899  4.997351

Segment Performance:
                     Conversion_Rate       ROI
Customer_Segment                              
Foodies                     0.080257  5.004376
Outdoor Adventurers         0.080180  4.999393
Tech Enthusiasts            0.080168  5.004234
Health & Wellness           0.079945  5.003202
Fashionistas                0.079794  5.000962

Monthly Engagement Trend:
Month
2021-01    5.455321
2021-02    5.503650
2021-03    5.520426
2021-04    5.467214
2021-05    5.529962
2021-06    5.503345
2021-07    5.498470
2021-08    5.472687
2021-09    5.535097
2021-10    5.457441
2021-11    5.457056
2021-12    5.536245
Freq: M, Name: Engagement_Score, dtype: float64


