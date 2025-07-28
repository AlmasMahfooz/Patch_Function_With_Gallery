# Patch_Function_With_Gallery
Patch Function With Gallery With SharePoint List as Data Source


Save on Button
--------------
SharePoint List is like below

![Uploading image.png…](https://github.com/AlmasMahfooz/Patch_Function_With_Gallery/blob/main/sharepoint%201.png)

On Screen OnVisible property, fill collection collTempUnits2 with data from SharePoint List.

ClearCollect(collTempUnits2,
ForAll(SharePointListA,
    {RowNumber: RowNumber,
    RowValue:RowValue,
    Title:Title
    })
)
Set Items property to the collection collTempUnits2. In Gallery use Text input for values needs to be updated and set Default property like

ThisItem.RowValue
Set OnChange property of Text Input field as
Patch(collTempUnits2,LookUp(collTempUnits2,Title=ThisItem.Title),{RowValue:TextInput5.Text})

On the OnSelect property of save button insert following code

 ForAll(collTempUnits2,
    With( {collTitle:Title,collRowValue:RowValue}, Patch(SharePointListA,
                         LookUp(SharePointListA,Title=collTitle),
                         {RowValue:collRowValue}
                         )
        )
        )














https://stackoverflow.com/questions/79681739/column-doesnt-exist-but-it-clearly-does-in-collection-and-sharepoint
