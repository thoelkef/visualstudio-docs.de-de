---
title: Erweitern den Projektmappen-Explorer-Filter | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef9439d9cebfa8b80b214e52d077ab1f770d4750
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047319"
---
# <a name="extend-the-solution-explorer-filter"></a>Erweitern Sie den Projektmappen-Explorer-filter
Sie können die erweitern **Projektmappen-Explorer** Funktionen ein- oder Ausblenden von verschiedenen Dateien zu filtern. Sie können z. B. erstellen ein Filters, der nur C#-Factory Klassendateien in zeigt die **Projektmappen-Explorer**, wie Sie diese exemplarische Vorgehensweise veranschaulicht.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Erstellen Sie ein Visual Studio-paketprojekt

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `FileFilter`. Hinzufügen eine benutzerdefinierten Befehls-Elementvorlage, die mit dem Namen **"FileFilter"**. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Hinzufügen eines Verweises auf `System.ComponentModel.Composition` und `Microsoft.VisualStudio.Utilities`.

3. Stellen Sie den Menübefehl angezeigt werden die **Projektmappen-Explorer** Symbolleiste. Öffnen der *FileFilterPackage.vsct* Datei.

4. Ändern der `<Button>` Block, um die folgenden:

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

1. In der *"Source.Extension.vsixmanifest"* Datei, fügen Sie ein Medienobjekt, das MEF-Komponente ist.

2. Auf der **Assets** Registerkarte die **neu** Schaltfläche.

3. In der **Typ** Feld, und wählen Sie **Microsoft.VisualStudio.MefComponent**.

4. In der **Quelle** Feld, und wählen Sie **ein Projekt in der aktuellen Projektmappe**.

5. In der **Projekt** Feld, und wählen Sie **"FileFilter"**, und wählen Sie dann die **OK** Schaltfläche.

### <a name="add-the-filter-code"></a>Fügen Sie den Filtercode

1. Fügen Sie einige GUIDs, die die *FileFilterPackageGuids.cs* Datei:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Fügen Sie eine Klassendatei zum Projekt mit dem Namen "FileFilter" *FileNameFilter.cs*.

3. Ersetzen Sie den leeren Namespace und die leere Klasse mit dem folgenden Code.

     Die `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Methode nimmt die Sammlung mit den Stamm der Projektmappe (`rootItems`) und gibt die Auflistung von Elementen, die im Filter eingeschlossen werden.

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

4. In *FileFilter.cs*, entfernen Sie die Platzierung von Befehl und Verarbeitung von Code aus dem "FileFilter"-Konstruktor. Das Ergebnis sollte wie folgt aussehen:

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

     Entfernen Sie die `ShowMessageBox()` -Methode.

5. In *FileFilterPackage.cs*, ersetzen Sie den Code in die `Initialize()` -Methode durch Folgendes:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Testen des Codes

1. Erstellen Sie das Projekt, und führen Sie es aus. Eine zweite Instanz von Visual Studio wird geöffnet. Dies ist die experimentelle Instanz bezeichnet.

2. Öffnen Sie in der experimentellen Instanz von Visual Studio eine c#-Projekt ein.

3. Suchen Sie die Schaltfläche Sie hinzugefügt haben, auf die **Projektmappen-Explorer** Symbolleiste. Es sollte die vierte Schaltfläche von links sein.

4. Wenn Sie auf die Schaltfläche klicken, alle Dateien herausgefiltert werden sollten und sollte **wurden alle Elemente aus der Ansicht gefiltert.** in der **Projektmappen-Explorer**.