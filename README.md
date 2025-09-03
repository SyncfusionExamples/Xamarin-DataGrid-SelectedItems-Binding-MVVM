# How to bind and control the selected items on SfDataGrid using the MVVM pattern.

This article demonstrates how to bind and control the selected items on SfDataGrid.

To achieve this, a bindable SelectedItems property is exposed in the ViewModel. This property remains synchronized with the grid’s current selection and also updates the grid when its value changes from the ViewModel, ensuring two-way communication between the UI and the data layer.

## Xaml#:

```xml
<sfgrid:SfDataGrid x:Name="dataGrid"
                    ItemsSource="{Binding State}" 
                    NavigationMode="Cell"
                    ColumnSizer="Auto"
                    SelectedItems="{Binding SelectedItems}"
                    SelectionMode="Multiple"
                    AutoGenerateColumns="True">

</sfgrid:SfDataGrid>
```

## C#:

```C#
class ViewModel : INotifyPropertyChanged
{
    public ObservableCollection<object> SelectedItems
    {

        get
        {
            return selectedItems;
        }
        set
        {
            selectedItems = value;OnPropertyChanged(nameof(SelectedItems));
        }
    }
}
```