# Merging-multiple-Tabs-into-a-single-sheet
This is a code to merge all data in different tabs into one sheet

pip install openpyxl
import os
import pandas as pd
folder = r'C:\Users\Sochi\Downloads\ordersB'
df_total = pd.DataFrame()
files = os.listdir(folder)
files

for file in files:
    if file.endswith('.xlsx'):
        excel_file = pd.ExcelFile(f'{folder}/{file}')
        sheets = excel_file.sheet_names
        for sheet in sheets:
            df = excel_file.parse(sheet_name = sheet)
            df_total = df_total.append(df)
            
df_total.to_excel(r'C:\Users\Sochi\Downloads\ordersB\combined_file.xlsx')

