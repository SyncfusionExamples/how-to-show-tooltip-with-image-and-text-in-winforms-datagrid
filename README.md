# How to Show ToolTip with Image and Text in WinForms DataGrid?

This sample illustrates that how to show ToolTip with image and text in [WinForms DataGrid](https://www.syncfusion.com/winforms-ui-controls/datagrid) (SfDataGrid).

By default, the Tooltip for grid cells will be loaded with `CellValue` text. To add image in tooltip with existing text, the `ToolTipOpening` event can be used. In that event, the `ToolTipInfo` for the items can be updated with image.

```C#
//Event subscription
this.sfDataGrid1.ToolTipOpening += SfDataGrid1_ToolTipOpening;

//Event customization
private void SfDataGrid1_ToolTipOpening(object sender, ToolTipOpeningEventArgs e)
{
    var record = e.Record as OrderInfo;

    e.ToolTipInfo.Items.AddRange(new ToolTipItem[] { toolTipItem1, toolTipItem2 });

    var recordIndex = this.sfDataGrid1.TableControl.ResolveToRowIndex(record);

    if (e.RowIndex == recordIndex)
    {
        if (record.CustomerID == "FRANS")
        {
            e.ToolTipInfo.Items[1].Text = "FRANS";                        
            e.ToolTipInfo.Items[0].Image = Image.FromFile(@"../../Images/FRANS.png");
        }
    }
}
```

![DataGrid showing Tooltip with Image and Text](TooltipWithImageAndText.png)