---
title: Erweitern des Lösungs-Explorer-Filters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711568"
---
# <a name="extend-the-solution-explorer-filter"></a>Erweitern des Projektmappen-Explorer-Filters
Sie können die **Filterfunktionalität des Projektmappen-Explorers** erweitern, um verschiedene Dateien ein- oder auszublenden. Sie können z. B. einen Filter erstellen, der nur Factorydateien der C-Klasse im **Projektmappen-Explorer**anzeigt, wie diese exemplarische Vorgehensweise veranschaulicht.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Erstellen eines Visual Studio-Paketprojekts

1. Erstellen Sie ein `FileFilter`VSIX-Projekt mit dem Namen . Fügen Sie eine benutzerdefinierte Befehlselementvorlage mit dem Namen **FileFilter**hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Fügen Sie `System.ComponentModel.Composition` einen `Microsoft.VisualStudio.Utilities`Verweis auf und hinzu.

3. Lassen Sie den Menübefehl auf der Symbolleiste des **Projektmappen-Explorers** anzeigen. Öffnen Sie die Datei *FileFilterPackage.vsct.*

4. Ändern `<Button>` Sie den Block in Folgendes:

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

1. Fügen Sie in der Datei *source.extension.vsixmanifest* ein Asset hinzu, das eine MEF-Komponente ist.

2. Wählen Sie auf der Registerkarte **Assets** die Schaltfläche **Neu** aus.

3. Wählen Sie im Feld **Typ** **Microsoft.VisualStudio.MefComponent**aus.

4. Wählen Sie im Feld **Quelle** **ein Projekt in der aktuellen Projektmappe**aus.

5. Wählen Sie im Feld **Projekt** **FileFilter**aus, und wählen Sie dann die Schaltfläche **OK** aus.

### <a name="add-the-filter-code"></a>Hinzufügen des Filtercodes

1. Fügen Sie der *FileFilterPackageGuids.cs* Datei einige GUIDs hinzu:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Fügen Sie dem FileFilter-Projekt mit dem Namen *FileNameFilter.cs*eine Klassendatei hinzu.

3. Ersetzen Sie den leeren Namespace und die leere Klasse durch den folgenden Code.

     Die `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Methode nimmt die Auflistung, die`rootItems`den Stamm der Lösung ( ) enthält, und gibt die Auflistung der Elemente zurück, die in den Filter eingeschlossen werden sollen.

     Die `ShouldIncludeInFilter` Methode filtert die Elemente in der **Projektmappen-Explorer-Hierarchie** basierend auf der angegebenen Bedingung.

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

4. Entfernen *Sie in FileFilter.cs*die Befehlsplatzierung und den Handhabungscode aus dem FileFilter-Konstruktor. Das Ergebnis sollte wie folgt aussehen:

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

     Entfernen `ShowMessageBox()` Sie auch die Methode.

5. Ersetzen Sie in *FileFilterPackage.cs* `Initialize()` den Code in der Methode durch Folgendes:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Testen Ihres Codes

1. Erstellen Sie das Projekt, und führen Sie es aus. Eine zweite Instanz von Visual Studio wird geöffnet. Dies wird als experimentelle Instanz bezeichnet.

2. Öffnen Sie in der experimentellen Instanz von Visual Studio ein C-Projekt.

3. Suchen Sie nach der Schaltfläche, die Sie auf der Symbolleiste des **Projektmappen-Explorers** hinzugefügt haben. Es sollte der vierte Knopf von links sein.

4. Wenn Sie auf die Schaltfläche klicken, sollten alle Dateien herausgefiltert werden, und Sie sollten sehen, dass **alle Elemente aus der Ansicht gefiltert wurden.** im **Projektmappen-Explorer**.
