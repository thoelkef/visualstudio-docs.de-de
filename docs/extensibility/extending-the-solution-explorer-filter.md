---
title: Erweitern den Projektmappen-Explorer-Filter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 890c3572bf556b92481be204f947b62e6d596264
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-solution-explorer-filter"></a>Erweitern Sie den Projektmappen-Explorer-Filter
Sie können erweitern **Projektmappen-Explorer** Funktionen zum ein- oder Ausblenden von anderen Dateien zu filtern. Sie können z. B. erstellen ein Filters, der nur C#-Factory Klassendateien in zeigt den **Projektmappen-Explorer**, wie diese exemplarische Vorgehensweise veranschaulicht.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-visual-studio-package-project"></a>Erstellen Sie ein Projekt der Visual Studio-Paket  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `FileFilter`. Fügen Sie eine Elementvorlage für benutzerdefinierte Befehl mit dem Namen **FileFilter**. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Hinzufügen eines Verweises auf `System.ComponentModel.Composition` und `Microsoft.VisualStudio.Utilities`.  
  
3.  Stellen Sie den Menübefehl auf angezeigt werden die **Projektmappen-Explorer** Symbolleiste. Öffnen Sie die FileFilterPackage.vsct-Datei.  
  
4.  Ändern der `<Button>` Block, der dem folgenden:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>Aktualisieren der Manifestdatei  
  
1.  Fügen Sie ein Medienobjekt, das eine MEF-Komponente ist in der Datei "Source.Extension.vsixmanifest" hinzu.  
  
2.  Auf der **Bestand** Registerkarte, und wählen Sie die **neu** Schaltfläche.  
  
3.  In der **Typ** Feld **Microsoft.VisualStudio.MefComponent**.  
  
4.  In der **Quelle** Feld **ein Projekt in der aktuellen Projektmappe**.  
  
5.  In der **Projekt** Feld **FileFilter**, und wählen Sie dann die **OK** Schaltfläche.  
  
### <a name="add-the-filter-code"></a>Fügen Sie den Filtercode  
  
1.  Fügen Sie einige GUIDs in die FileFilterPackageGuids.cs-Datei ein:  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Fügen Sie dem FileFilter-Projekt mit dem Namen FileNameFilter.cs eine Klassendatei hinzu.  
  
3.  Ersetzen Sie den leeren Namespace und die leere Klasse ist mit den folgenden Code.  
  
     Die `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Methode nimmt die Sammlung mit dem Stammverzeichnis der Projektmappe (`rootItems`) und gibt die Auflistung von Elementen, die im Filter eingeschlossen sein.  
  
     Die `ShouldIncludeInFilter` Methode filtert die Elemente in der **Projektmappen-Explorer** Hierarchie basierend auf der Bedingung, dass Sie angeben.  
  
    ```csharp  
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
  
4.  Entfernen Sie in FileFilter.cs den Befehl Platzierung und Behandeln von Code aus dem FileFilter-Konstruktor. Das Ergebnis sollte wie folgt aussehen:  
  
    ```csharp  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Entfernen Sie die ShowMessageBox()-Methode.  
  
5.  Ersetzen Sie in FileFilterPackage, Cs den Code in die Initialize()-Methode wie folgt aus:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>Testen des Codes  
  
1.  Erstellen Sie das Projekt, und führen Sie es aus. Eine zweite Instanz von Visual Studio wird geöffnet. Dies ist die experimentelle Instanz aufgerufen.  
  
2.  Öffnen Sie in der experimentellen Instanz von Visual Studio ein c#-Projekt.  
  
3.  Suchen Sie nach der Schaltfläche, die Sie auf der Symbolleiste Projektmappen-Explorer hinzugefügt. Es sollte die vierte Schaltfläche von links.  
  
4.  Wenn Sie die Schaltfläche klicken, sollten alle Dateien herausgefiltert werden, und sehen Sie "alle Elemente aus der Ansicht gefiltert wurden." im Projektmappen-Explorer.