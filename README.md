# test-ec.py
print('hello les camarades')

# téléchargement des infos
import pandas as pandas
df = pd.read_csv("/content/Pakistan_Largest_Ecommerce_Dataset.csv") 
df.head()
df.info()

# effacer les lignes vides
df.drop(df.iloc[:, 21:], inplace = True, axis = 1) 
df.info()

# pourcentage des NAs par colonne
print (df.item_id.isna(.sum()))
for colonne in df.coloumns:
    print("le pourcentage des NAs dans la colonne", colonne, "est", (df1[colonne].isna().sum())*100/(df.shape[0]))

df.dropna(inplace=True)
df.info()




# visialisation de la correlation entre les différentes varibles

import seaborn as sns
import matplotlib.pyplot as plt 

sns.heatmap(corr_df, annot=True)
plt.show()



    
# colonne status
df['status'].value_counts().index


df['status'].value_count(normalize=True).plot(kind='bar')



# colonne item_id = numéro id de la commande. 
#le type ne doit pas être int parce que ce n'est pas une variable quantitive
# transformer le type en string (ou objet)


df["item_id"] = df["item_id"].astype(str)
df["item_id"] = df["item_id"].str.replace('.0', '')
df["item_id"].dtype



#modifier le type de la colonne created_at en date 

df['created_at'] = pd.to_datetime(df['created_at'])
df['created_at'].dtype
df.head(2)


#modifier le type de la colonne Working Date en date ainsi que Customer Since
df['Working Date'] = pd.to_datetime(df['Working Date'])
df['Working Date'].dtype
df['Customer Since'] = pd.to_datetime(df['Customer Since'])
df.head(2)



df.duplicated().sum(axis = 0)




df["sku"].value_counts()


df["price"].plot()

plt.boxplot([df["price"])

df["order_amount"] = df["price"]*df["qty_ordered"]







#fig, ax = plt.subplots(figsize=(12, 10))
order = list(df['grand_total'].groupby(df['category_name_1']).agg('sum').sort_values(ascending=False).index)


g = sns.catplot(x='grand_total', y='category_name_1',data=df, estimator=sum, ci=0, kind="bar", order=order, col='status',palette='summer')
#g.axes(shape=(24,12))
g.set_xlabels("Grand Total Of Sales")
g.set_ylabels("Category")
plt.show()
