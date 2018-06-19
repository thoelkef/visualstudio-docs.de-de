---
title: Speichern von Daten in Projektdateien | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35514385a4ed1d28052ebb21d12ed0b053dd52dc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140176"
---
# <a name="saving-data-in-project-files"></a>Speichern von Daten in Projektdateien
Ein Projektuntertyp kann speichern und Abrufen von untertypspezifischen Daten in der Projektdatei. Das Managed Package Framework (MPF) stellt zwei Schnittstellen, um diese Aufgabe:  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Schnittstelle ermöglicht Zugriff Eigenschaftswerte aus der **MSBuild** Abschnitt der Projektdatei. Die bereitgestellten Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> kann von jedem Benutzer aufgerufen werden, sobald der Benutzer Anforderungen zum Laden und speichern verknüpfte Daten erstellen.  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> wird verwendet, um nicht Build verknüpfte Daten in Freiform-XML beibehalten werden. Die bereitgestellten Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> werden vom aufgerufen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] immer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Build nicht verknüpfte Daten in der Projektdatei beibehalten muss.  
  
 Weitere Informationen zum Build und Build nicht verknüpften Daten persistent zu speichern, finden Sie unter [beibehalten von Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="saving-and-retrieving-build-related-data"></a>Speichern und Abrufen von Build-bezogene Daten  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>Um einen Build speichern-bezogene Daten in der Projektdatei  
  
-   Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> Methode, um einen vollständigen Pfad der Projektdatei zu speichern.  
  
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
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Zum Abrufen von Build-bezogene Daten aus der Projektdatei  
  
-   Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> Methode, um einen vollständigen Pfad der Projektdatei abzurufen.  
  
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
  
## <a name="saving-and-retrieving-non-build-related-data"></a>Speichern und Abrufen von nicht-Build verknüpfte Daten  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>Zum Speichern von nicht-Build-bezogene Daten in der Projektdatei  
  
1.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> Methode, um zu bestimmen, ob ein XML-Fragment geändert wurde, seit dem letzten in die aktuelle Datei gespeichert.  
  
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
  
2.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> Methode, um die XML-Daten in der Projektdatei zu speichern.  
  
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
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Zum Abrufen von nicht-Build-bezogene Daten in der Projektdatei  
  
1.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> Methode, um die Projekteigenschaften für die Erweiterung und andere Daten unabhängig von Build zu initialisieren. Diese Methode wird aufgerufen, wenn es keine XML-Konfigurationsdaten, die in der Projektdatei vorhanden ist.  
  
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
  
2.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> -Methode zum Laden von XML-Daten aus der Projektdatei.  
  
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
>  Alle in diesem Thema bereitgestellten Codebeispiele sind Teil eines umfangreicheren Beispiels in [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)