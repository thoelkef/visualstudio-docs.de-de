---
title: "Umbenennen von Knoten in der Projekthierarchie (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HierUtil7-Beispiel [Visual Studio SDK], Projektknoten umbenennen"
  - "Projektknoten, in HierUtil7 Beispiel umbenennen"
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Umbenennen von Knoten in der Projekthierarchie (C++)
Sie können einen Projektordner Knoten hierarchien umbenennen, indem Sie das Framework für HierUtil7 des Projekts nicht verwaltetes C\+\+ verwenden.  Weitere Informationen finden Sie unter [HierUtil7 Sample](http://msdn.microsoft.com/de-de/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## Ruft den Hierarchieknoten erweitern  
  
#### Um den Hierarchieknoten erweitern und den Ordner umbenennen  
  
1.  Wählen Sie den Hierarchieknoten aus, indem Sie die folgende Methode verwenden:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` ist der Ordner entsprechend dem Dienstcontainer Hierarchien und `EXPF_SelectItem` wird von der <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS>\-Enumeration.  `GUID_MacroExplorer` ist eine GUID\-Konstante, die in Vsshell.idl definiert und ist ein Beispiel für `rguidPersistenceSlot` in der Funktionssignatur von `ExtExpand`, definiert in Hu\_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Sie können die Hu\_node.h\-Datei im Ordner \\ Programme \\ \<installation root\> 8.0 \\ EnvSDK Partner Common \\ \\ hierutil7 suchen:  
  
2.  Benennen Sie den Ordner, indem Sie den Befehl Umbenennen verwenden, indem Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>senden  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` ist ein Zeiger <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> : `<IVsUIShell>``srpVsUIShell`.  `guiVSStd97` ist ein eindeutiger Bezeichner der Befehlsgruppe, die der Befehl `cmdidRename` gehört, definiert in Vsshlids.h.  
  
## Siehe auch  
 [Erstellen von Projekttypen](../extensibility/internals/creating-project-types.md)   
 [VSSDK\-Beispiele](../misc/vssdk-samples.md)