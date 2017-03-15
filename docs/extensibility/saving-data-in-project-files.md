---
title: "Speichern von Daten in Projektdateien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "in Projektdateien Speichern von Daten [Visual Studio]"
  - "Projektdateien"
  - "Project-Dateien speichern von Daten"
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Speichern von Daten in Projektdateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein Projekt kann untertyp Untertyp spezifisch Daten in der Projektdatei speichern und abrufen.  Das verwaltete Paketframework \(MPF\) stellt zwei Schnittstellen, um diese Aufgabe auszuführen:  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>\-Schnittstelle kann für den Zugriff auf eigenschaftswerten vom **MSBuild**\-Abschnitt der Projektdatei.  Die Methoden, die von <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> bereitgestellt werden, können von jedem Benutzer aufgerufen werden, wenn die Nutzerbedarfe Build zu laden oder verknüpfte Daten zu speichern.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> wird verwendet, um Nicht Build verknüpfte Daten in der Freiform XML beizubehalten.  Die Methoden, die von <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> bereitgestellt werden, werden durch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] immer dann aufgerufen, wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nicht Build verknüpfte Daten in der Projektdatei beibehalten muss.  
  
 Weitere Informationen zum Erstellen eines Builds und Nicht Build verknüpfte Daten finden Sie unter [Beibehalten von Daten in der MSBuild\-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)beibehält.  
  
## Build Speichern und Abrufen von verknüpften Daten  
  
#### So erstellen Sie einen Build zu speichern verknüpfte Daten in der Projektdatei  
  
-   Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>\-Methode auf, um einen vollständigen Pfad der Projektdatei zu speichern.  
  
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
  
#### Um verknüpfte Daten abzurufen Erstellung von der Projektdatei  
  
-   Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A>\-Methode auf, um einen vollständigen Pfad der Projektdatei abzurufen.  
  
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
  
## Nicht Build Speichern und Abrufen von verknüpften Daten  
  
#### Um verknüpfte Daten zu Builds nicht in der Projektdatei speichern  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A>\-Methode, um zu bestimmen, ob ein XML\-Fragment geändert wurde, seit es zuletzt in die aktuelle Datei gespeichert wurden.  
  
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
  
2.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>\-Methode, um XML\-Daten in der Projektdatei zu speichern.  
  
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
  
#### So führen Sie Builds Nicht verknüpfte Daten in der Projektdatei ab  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A>\-Methode, um Eigenschaften für das Projekt Erstellung\-unabhängige und andere Daten zu initialisieren.  Diese Methode wird aufgerufen, wenn keine XML\-Konfigurations von Daten gibt, die in der Projektdatei vorhanden sind.  
  
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
  
2.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>\-Methode, um XML\-Daten aus der Projektdatei zu laden.  
  
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
>  Alle Codebeispiele in diesem Thema bereitgestellt werden, sind Teil eines umfangreicheren Beispiels, [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
## Siehe auch  
 [Beibehalten von Daten in der MSBuild\-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)