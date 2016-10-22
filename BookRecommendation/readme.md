#Book recommender system - Graphlab

The objective of this capstone project is to build a book recomendation system.
There are many tools in python for recomendation Systems. I will be utilizing Graphlab, https://turi.com/learn/userguide/ to build a hybrid recommendation system.
There are usually two methods to build recomendtion systems.

Collaborative filtering based or  Content filtering approach.
Collaborative filtering: relies on the users collaborating to rate an item/product and will only be able to recommend an item if the user is already in the database and his/her preferences/ratings are recorded in the system. similarly a new item in content based approach would not have a rating and thus the system would not be able to make recommendations.

the alternative approach is to use a mix of the two approaches to build a recommendation system that selects the best method to recommend when information is not availiable from the other systems.

The dataset is Amazon books review database, obtained from http://jmcauley.ucsd.edu/data/amazon/ with permission from the authors of Image-based recommendations on styles and substitutes J. McAuley, C. Targett, J. Shi, A. van den Hengel SIGIR, 2015
load the metadata and the reviews files to a dataframe.

def parse(path):

g = gzip.open(path, 'rb')

for l in g:

yield eval(l)

def getDF(path): 
    i = 0 

    df = {}
for d in parse(path):

    df[i] = d
    i += 1
    
return pd.DataFrame.from_dict(df, orient='index') 

booksinfo = getDF('../meta_Books.json.gz')

Sliced and saved the files in Amazon Ec2 server.