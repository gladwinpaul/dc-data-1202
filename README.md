# dc-data-1202
## data 1202 assignment 5
The python code attached is created as a part of assignment 4 of course DATA -  1202 - Data Analysis Tools for Analytics 
- The library used is pandas
- The database used is 'youtube_dataset.csv'
- The dataset have special characters. So I modified data set loading query with encoding parameter.To identify the suitable codec I used the following command:
                   
                   with open('youtube_dataset.csv') as f:                     
                     print(f.encoding
                     
- The modified data loading query was: 

                raw_df=pd.read_csv('./youtube_dataset.csv', encoding='cp1252')
                raw_df.head()
 
- To view Data Types, use the query
 
               raw_df.info()
 - to display channel type as list,use
 
            list(raw_df.channeltype.unique())    
 - The first 1000 entries are selected using iloc command. The tailor made function is named as slice_data. The slice_data receive data frame and number of rows and return the values in those rows.
    
          def slice_data (df, number_of_rows):
          return df.iloc[:number_of_rows]
          first_1000 = slice_data(raw_df, 1000)
- The length of extracted data is verified using:
 
          print(len(first_1000))
- The channel type distribution is calculated using a custom made function named dist. A for loop is used inside the function to calculate the count of channel distribution using a common query.
        
        channel_dist = {}
          def dist(t):
          for x in t:
        channel_dist[x] = channel_dist.get(x,0) + 1
        distrubition = dist(first_1000.channeltype)

- The newly created data frame file is saved as CSV using to_csv() code and load the same using new_df_1000 = pd.read_csv code.
    
       first_1000.to_csv(r'E:/Users/SYS/Documents/youtube1000.csv', index = False)
        new_df_1000 = pd.read_csv('E:/Users/SYS/Documents/youtube1000.csv')
       new_df_1000.head(10)
