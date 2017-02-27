---
title: "Erweitern Sie den Projektmappen-Explorer-Filter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projektmappen-Explorer erweitern"
  - "Erweiterbarkeit [Visual Studio], Projekte und Projektmappen"
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Erweitern Sie den Projektmappen-Explorer-Filter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können erweitern **Projektmappen\-Explorer** Filterfunktion auf andere Dateien anzuzeigen bzw. auszublenden. Sie können z. B. erstellen ein Filters, der nur C\#\-Factory Klassendateien im zeigt die **Projektmappen\-Explorer**, wie in dieser exemplarischen Vorgehensweise veranschaulicht.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Erstellen Sie ein Projekt der Visual Studio\-Paket  
  
1.  Erstellen Sie ein VSIX\-Projekt namens `FileFilter`. Fügen Sie eine benutzerdefinierten Befehl Elementvorlage mit dem Namen **FileFilter**. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Hinzufügen eines Verweises auf `System.ComponentModel.Composition` und `Microsoft.VisualStudio.Utilities`.  
  
3.  Stellen Sie den Menübefehl auf angezeigt werden die **Projektmappen\-Explorer** Symbolleiste. Öffnen Sie die Datei FileFilterPackage.vsct.  
  
4.  Ändern der `<Button>` Block wie folgt:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### Aktualisieren der Manifestdatei.  
  
1.  Fügen Sie in der Datei "Source.Extension.vsixmanifest" ein Medienobjekt, das MEF\-Komponente ist.  
  
2.  Wählen Sie auf der Registerkarte **Objekte** die Schaltfläche **Neu** aus.  
  
3.  In der **Typ** Feld **Microsoft.VisualStudio.MefComponent**.  
  
4.  In der **Quelle** wählen Sie **ein Projekt in der aktuellen Projektmappe**.  
  
5.  In der **Projekt** Feld **FileFilter**, und wählen Sie dann die **OK** Schaltfläche.  
  
### Fügen Sie den Filtercode  
  
1.  Fügen Sie einige GUIDs in die FileFilterPackageGuids.cs\-Datei:  
  
    ```c#  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Fügen Sie dem FileFilter\-Projekt mit dem Namen FileNameFilter.cs eine Klassendatei hinzu.  
  
3.  Ersetzen Sie den leeren Namespace und der leeren Klasse durch den folgenden Code.  
  
     Die `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Methode nimmt die Auflistung mit der Wurzel der Lösung \(`rootItems`\) und gibt die Auflistung von Elementen, die im Filter eingeschlossen werden.  
  
     Die `ShouldIncludeInFilter` Methode filtert die Elemente in der **Projektmappen\-Explorer** Hierarchie basierend auf der Voraussetzung, dass Sie angeben.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4.  Entfernen Sie in FileFilter.cs Platzierung und Behandlung der Kurzbefehl aus dem FileFilter\-Konstruktor. Das Ergebnis sollte wie folgt aussehen:  
  
    ```c#  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Entfernen Sie die ShowMessageBox\(\)\-Methode.  
  
5.  Ersetzen Sie in FileFilterPackage, Cs den Code in die Initialize\(\)\-Methode durch Folgendes:  
  
    ```c#  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### Testen des Codes  
  
1.  Erstellen Sie das Projekt, und führen Sie es aus. Eine zweite Instanz von Visual Studio wird angezeigt. Dies ist die experimentelle Instanz bezeichnet.  
  
2.  Öffnen Sie in der experimentellen Instanz von Visual Studio ein C\#\-Projekt.  
  
3.  Suchen Sie die Schaltfläche, die Sie auf der Symbolleiste des Projektmappen\-Explorer hinzugefügt. Es sollte die vierte Schaltfläche von links.  
  
4.  Wenn Sie auf die Schaltfläche klicken, alle Dateien herausgefiltert werden sollen, und sollte "alle Elemente aus der Ansicht gefiltert wurden." im Projektmappen\-Explorer.