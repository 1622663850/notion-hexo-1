
一般我们要实现居中设置 HorizontalContentAlignment="Center" VerticalContentAlignment="Center"就可以了， 但是datagrid的DataGridTextColumn中却发现没有HorizontalContentAlignment或者HorizontalAlignment，列中的内容仍然是左对齐，如何处理才能居中呢？


```c#
// 右对齐风格
Style styleRight = new Style(typeof(TextBlock));
Setter setRight = new Setter(TextBlock.HorizontalAlignmentProperty, HorizontalAlignment.Right);styleRight.Setters.Add(setRight);
foreach (DataGridColumn c in yourDataGrid.Columns)
{        DataGridTextColumn tc = c as DataGridTextColumn;
        if (tc != null)        
        {
                tc.ElementStyle = styleRight;
        }
}
```


即只要设置DataGridColumn的ElementStyle就可以了，也可以在xaml中设置


```c#
<Style x:Key="contentCenterStyle"
               TargetType="{x:Type TextBlock}">
            <Setter Property="HorizontalAlignment"
                    Value="Center" />
        </Style>
```


```c#
<DataGridTextColumn Header="代码"
            ElementStyle="{StaticResource contentCenterStyle}"
            Binding="{Binding Name}"></DataGridTextColumn>
```

