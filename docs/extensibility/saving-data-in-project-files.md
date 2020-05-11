---
title: Speichern von Daten in Projektdateien | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fd6cfaa450bc268665ae0f58109c99002da6152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701352"
---
# <a name="save-data-in-project-files"></a>Speichern von Daten in Projektdateien
Ein Projektuntertyp kann subtypspezifische Daten in der Projektdatei speichern und abrufen. Das Managed Package Framework (MPF) stellt zwei Schnittstellen bereit, um diese Aufgabe zu erfüllen:

- Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Schnittstelle ermöglicht den Zugriff auf Eigenschaftswerte aus dem **MSBuild-Abschnitt** der Projektdatei. Die von <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> ihnen bereitgestellten Methoden können von jedem Benutzer aufgerufen werden, wenn der Benutzer buildbezogene Daten laden oder speichern muss.

- Der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> wird verwendet, um nicht buildbezogene Daten in Freiform-XML beizubehalten. Die von <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> ihnen bereitgestellten Methoden werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aufgerufen, wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es erforderlich ist, nicht buildbezogene Daten in der Projektdatei beizubehalten.

  Weitere Informationen zum Beibehalten von Build- und nicht buildbezogenen Daten finden Sie unter Speichern von [Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Speichern und Abrufen von buildbezogenen Daten

### <a name="to-save-a-build-related-data-in-the-project-file"></a>So speichern Sie Builddaten in der Projektdatei

- Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> Sie die Methode auf, um einen vollständigen Pfad der Projektdatei zu speichern.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>So rufen Sie buildbezogene Daten aus der Projektdatei ab

- Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> Sie die Methode auf, um einen vollständigen Pfad der Projektdatei abzurufen.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>Speichern und Abrufen nicht buildbezogener Daten

### <a name="to-save-non-build-related-data-in-the-project-file"></a>So speichern Sie nicht buildbezogene Daten in der Projektdatei

1. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> Sie die Methode, um zu bestimmen, ob sich ein XML-Fragment seit dem letzten Speichern in der aktuellen Datei geändert hat.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> Sie die Methode zum Speichern der XML-Daten in der Projektdatei.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>So rufen Sie nicht buildbezogene Daten in der Projektdatei ab

1. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> Sie die Methode, um die Projekterweiterungseigenschaften und andere buildunabhängige Daten zu initialisieren. Diese Methode wird aufgerufen, wenn keine XML-Konfigurationsdaten in der Projektdatei vorhanden sind.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> Sie die Methode zum Laden der XML-Daten aus der Projektdatei.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> Alle in diesem Thema bereitgestellten Codebeispiele sind Teile eines größeren Beispiels in [VSSDK-Beispielen](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Weitere Informationen
- [Beibehalten von Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
