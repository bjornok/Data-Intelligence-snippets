### Using Python operator to find column names from SLT operator

SLT Operator V2 delivers a JSON structure in the data.attributes variable.

Check SAP blog [SAP Data Intelligence(3.1-2010) : CSV as Target using SLT Connector Operator](https://blogs.sap.com/2021/02/19/sap-data-intelligence3.1-2010-csv-as-target-using-slt-connector-operator/) for details


```python
def on_input(inData):
    
    data = StringIO(inData.body)
    
    attr = inData.attributes
    
    ABAPKEY = attr['ABAP']
    col= []
    for columnname in ABAPKEY['Fields']:
        col.append(columnname['Name'])
    df = pd.read_csv(data, index_col=False, names=col)
    df_csv = df.to_csv(index=False, header = True)
    
    api.send("output", api.Message(attributes={}, body=df_csv))

api.set_port_callback( "input1", on_input)
```
