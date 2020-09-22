---
title: Speichern von Daten in Projektdateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc671963854e4fa0c2af763de5000fac82a839b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841151"
---
# <a name="saving-data-in-project-files"></a>Speichern von Daten in Projektdateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit einem Projekt Untertyp können Untertypen spezifische Daten in der Projektdatei gespeichert und abgerufen werden. Das Managed Package Framework (MPF) stellt zwei Schnittstellen zum Ausführen dieser Aufgabe bereit:  
  
- Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Schnittstelle ermöglicht den Zugriff auf Eigenschaftswerte aus dem **MSBuild** -Abschnitt der Projektdatei. Die von bereitgestellten Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> können von jedem Benutzer aufgerufen werden, wenn der Benutzer buildbezogene Daten laden oder speichern muss.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Wird verwendet, um nicht-Build-bezogene Daten in frei Form-XML beizubehalten. Die von bereitgestellten Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> werden von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aufgerufen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , wenn nicht auf Builds bezogene Daten in der Projektdatei beibehalten werden müssen.  
  
  Weitere Informationen zum Beibehalten von Build-und nicht-Build-bezogenen Daten finden Sie unter [persistente Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="saving-and-retrieving-build-related-data"></a>Speichern und Abrufen von verknüpften Daten  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>So speichern Sie verknüpfte Daten in der Projektdatei  
  
- Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> Methode auf, um einen vollständigen Pfad der Projektdatei zu speichern.  
  
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
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>So rufen Sie verknüpfte Daten aus der Projektdatei ab  
  
- Rufen Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> Methode auf, um einen vollständigen Pfad der Projektdatei abzurufen.  
  
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
  
## <a name="saving-and-retrieving-non-build-related-data"></a>Speichern und Abrufen von Daten, die nicht im Build zusammenhängen  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>So speichern Sie Daten, die nicht im Build zusammenhängen, in der Projektdatei  
  
1. Implementieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> Methode, um zu bestimmen, ob sich ein XML-Fragment geändert hat, seit es zuletzt in der aktuellen Datei gespeichert wurde.  
  
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
  
2. Implementieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> Methode, um die XML-Daten in der Projektdatei zu speichern.  
  
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
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>So rufen Sie nicht-Build-bezogene Daten in der Projektdatei ab  
  
1. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> Sie die-Methode, um die Eigenschaften der Projekt Erweiterung und andere buildunabhängige Daten zu initialisieren. Diese Methode wird aufgerufen, wenn in der Projektdatei keine XML-Konfigurationsdaten vorhanden sind.  
  
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
  
2. Implementieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> Methode, um die XML-Daten aus der Projektdatei zu laden.  
  
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
> Alle in diesem Thema enthaltenen Codebeispiele sind Teile eines größeren Beispiels, [VSSDK](../misc/vssdk-samples.md)-Beispiele.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
