# Heroes of Pymoli  
This is a demonstartion of the Heroes of Pymoli where I am using Python in Jupyter Notebook

Heroes Of Pymoli Data Analysis
Of the 1163 active players, the vast majority are male (84%). There also exists, a smaller, but notable proportion of female players (14%).

Our peak age demographic falls between 20-24 (44.8%) with secondary groups falling between 15-19 (18.60%) and 25-29 (13.4%).

Note
Instructions have been included for each segment. You do not have to follow them exactly, but they are included to help you think through the steps.
In [27]:
# Dependencies and Setup
import pandas as pd
import numpy as np

# File to Load (Remember to Change These)
file_to_load = "purchase_data.csv"

# Read Purchasing File and store into Pandas data frame
purchase_data_df = pd.read_csv(file_to_load)

purchase_data_df.head()
Out[27]:
Purchase ID	SN	Age	Gender	Item ID	Item Name	Price
0	0	Lisim78	20	Male	108	Extraction, Quickblade Of Trembling Hands	3.53
1	1	Lisovynya38	40	Male	143	Frenzied Scimitar	1.56
2	2	Ithergue48	24	Male	92	Final Critic	4.88
3	3	Chamassasya86	24	Male	100	Blindscythe	3.27
4	4	Iskosia90	23	Male	131	Fury	1.44
Player Count
Display the total number of players
In [28]:
total = len(purchase_data_df["Purchase ID"].unique())
print("Total Number of Players: ", total)
Total Number of Players:  780
Purchasing Analysis (Total)
Run basic calculations to obtain number of unique items, average price, etc.
Create a summary data frame to hold the results
Optional: give the displayed data cleaner formatting
Display the summary data frame
In [29]:
number_of_unique_items = len(purchase_data_df["Item Name"].unique())
print(number_of_unique_items)

avg_purch_price = purchase_data_df["Price"].mean()
print(avg_purch_price)

total_num_purchase = purchase_data_df["Price"].sum()
print(total_num_purchase)

total_revenue = total_num_purchase * total
print(total_revenue)

summary_table = pd.DataFrame({"Number of Unique Items": number_of_unique_items ,
                              "Average Purchase Price":[avg_purch_price],
                              "Total Number of Purchases": [total_num_purchase],
                              "Total Revenue": [total_revenue]})
summary_table
179
3.050987179487176
2379.77
1856220.6
Out[29]:
Number of Unique Items	Average Purchase Price	Total Number of Purchases	Total Revenue
0	179	3.050987	2379.77	1856220.6
Gender Demographics
Percentage and Count of Male Players
Percentage and Count of Female Players
Percentage and Count of Other / Non-Disclosed
In [38]:
#clean_df = purchase_data_df.copy()
#clean_df

#sq = purchase_data_df.columns = ['Purchase ID', 'Gender']
#sq.head(2)
#s = purchase_data_df.keywords
#counts = s.value_counts()
#percent = s.value_counts(normalize=True)
#percent100 = s.value_counts(normalize=True).mul(100).round(1).astype(str) + '%'





#
#e_col_gender =['Purchase ID', 'Gender']
#df_ec_gender = purchase_data_df[e_col_gender]
#df_ec_gender.head()

#pm = purchase_data_df.groupby('Gender')
#pm.head()

#usa_ufo_df = clean_df.loc[clean_df["Gender"] == "Male", :]
#usa_ufo_df.head()

#state_counts = usa_ufo_df["Purchase ID"].value_counts()
#state_counts.head()

#usa_ufo_df = clean_df.loc[clean_df["Gender"] == "Female", :]
#usa_ufo_df.head()
Out[38]:
Purchase ID	SN	Age	Gender	Item ID	Item Name	Price
0	0	Lisim78	20	Male	108	Extraction, Quickblade Of Trembling Hands	3.53
1	1	Lisovynya38	40	Male	143	Frenzied Scimitar	1.56
2	2	Ithergue48	24	Male	92	Final Critic	4.88
3	3	Chamassasya86	24	Male	100	Blindscythe	3.27
4	4	Iskosia90	23	Male	131	Fury	1.44
5	5	Yalae81	22	Male	81	Dreamkiss	3.61
6	6	Itheria73	36	Male	169	Interrogator, Blood Blade of the Queen	2.18
7	7	Iskjaskst81	20	Male	162	Abyssal Shard	2.67
8	8	Undjask33	22	Male	21	Souleater	1.10
9	9	Chanosian48	35	Other / Non-Disclosed	136	Ghastly Adamantite Protector	3.58
10	10	Inguron55	23	Male	95	Singed Onyx Warscythe	4.74
11	11	Haisrisuir60	23	Male	162	Abyssal Shard	2.67
12	12	Saelaephos52	21	Male	116	Renewed Skeletal Katana	4.18
13	13	Assjaskan73	22	Male	4	Bloodlord's Fetish	1.70
14	14	Saesrideu94	35	Male	165	Bone Crushing Silver Skewer	4.86
15	15	Lisassa64	21	Female	98	Deadline, Voice Of Subtlety	2.89
16	16	Lisirra25	20	Male	40	Second Chance	2.52
17	17	Zontibe81	21	Male	161	Devine	1.76
18	18	Reunasu60	22	Female	82	Nirvana	4.90
19	19	Chamalo71	30	Male	89	Blazefury, Protector of Delusions	4.64
20	20	Iathenudil29	20	Male	57	Despair, Favor of Due Diligence	4.60
21	21	Phiarithdeu40	20	Male	168	Sun Strike, Jaws of Twisted Visions	1.48
22	22	Siarithria38	38	Other / Non-Disclosed	24	Warped Fetish	3.81
23	23	Eyrian71	40	Male	151	Severance	3.40
24	24	Siala43	30	Male	141	Persuasion	3.19
25	25	Lisirra87	29	Male	178	Oathbreaker, Last Hope of the Breaking Storm	4.23
26	26	Lirtossa84	11	Male	71	Demise	1.61
27	27	Eusri44	7	Male	96	Blood-Forged Skeletal Spine	3.09
28	28	Aela59	21	Male	119	Stormbringer, Dark Blade of Ending Misery	4.32
29	29	Tyida79	24	Male	37	Shadow Strike, Glory of Ending Hope	3.16
...	...	...	...	...	...	...	...
750	750	Iljask75	22	Male	167	Malice, Legacy of the Queen	3.61
751	751	Lisjaskan36	11	Male	180	Stormcaller	3.36
752	752	Mindjasksya61	17	Male	112	Worldbreaker	2.60
753	753	Frichirranya75	36	Male	178	Oathbreaker, Last Hope of the Breaking Storm	4.23
754	754	Pheosurllorin41	23	Female	79	Alpha, Oath of Zeal	4.05
755	755	Raesty92	12	Male	76	Haunted Bronzed Bludgeon	3.15
756	756	Ilast79	20	Male	73	Ritual Mace	2.05
757	757	Eratiel90	18	Male	57	Despair, Favor of Due Diligence	4.60
758	758	Iral74	21	Male	182	Toothpick	4.03
759	759	Tyaelorap29	25	Male	72	Winter's Bite	3.77
760	760	Aithelis62	21	Male	44	Bonecarvin Battle Axe	2.38
761	761	Assim27	45	Male	17	Lazarus, Terror of the Earth	1.70
762	762	Asur53	26	Male	110	Suspension	1.44
763	763	Lassilsala30	21	Male	85	Malificent Bag	1.75
764	764	Saedaiphos46	18	Male	113	Solitude's Reaver	4.07
765	765	Irith83	18	Male	130	Alpha	2.07
766	766	Aelastirin39	23	Male	58	Freak's Bite, Favor of Holy Might	4.14
767	767	Ilmol66	8	Female	92	Final Critic	4.88
768	768	Assassasta79	38	Male	92	Final Critic	4.88
769	769	Ilosian36	15	Male	145	Fiery Glass Crusader	4.58
770	770	Lirtosia63	34	Male	12	Dawne	1.02
771	771	Iskossasda43	16	Male	25	Hero Cane	4.35
772	772	Asur53	26	Male	136	Ghastly Adamantite Protector	3.58
773	773	Hala31	21	Male	19	Pursuit, Cudgel of Necromancy	1.02
774	774	Jiskjask80	11	Male	101	Final Critic	4.19
775	775	Aethedru70	21	Female	60	Wolf	3.54
776	776	Iral74	21	Male	164	Exiled Doomblade	1.63
777	777	Yathecal72	20	Male	67	Celeste, Incarnation of the Corrupted	3.46
778	778	Sisur91	7	Male	101	Final Critic	4.19
779	779	Ennrian78	24	Male	50	Dawn	4.60
780 rows × 7 columns

In [33]:
#p_group_by = df_ec_gender.groupby(['Gender'])
#group_gen = df_ec_gender.count()
#p_group_by = group_gen.groupby(['Gender'])
#percent_gen = group_gen/total * 100
#percent_gen
#summary_table_2 = pd.DataFrame({"Count of Players":[group_gen], "Percentage of Gender":[percent_gen]})
#summary_table_2
#sum_gen
Purchasing Analysis (Gender)
Run basic calculations to obtain purchase count, avg. purchase price, avg. purchase total per person etc. by gender
Create a summary data frame to hold the results
Optional: give the displayed data cleaner formatting
Display the summary data frame
In [26]:
purch_count = purchase_data_df['Purchase ID'].count()
print(purch_count)
purch_ave = purchase_data_df['Price'].mean()
print(purch_ave)
purch_total_val = purchase_data_df["Price"].sum()
print(purch_total_val)
purch_ave_price_gender = purchase_data_df['Price'].mean()
print(purch_ave_price_gender)
780
3.050987179487176
2379.77
3.050987179487176
