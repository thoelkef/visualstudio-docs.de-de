---
title: Umbenennen von Knoten der Projekt Hierarchie (C++) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686589"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Umbenennen von Knoten in der Projekthierarchie (C++)
Sie können einen Projektordner Hierarchie Knoten mithilfe des HierUtil7-Projekt Frameworks für nicht verwaltete C++ umbenennen. Weitere Informationen finden Sie unter [HierUtil7 Sample](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Erweitern des Hierarchie Knotens  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>So erweitern Sie den Hierarchie Knoten und benennen den Ordner um  
  
1. Wählen Sie den Hierarchie Knoten mithilfe der folgenden Methode aus:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` der Hierarchie Container, der dem Ordner entspricht und `EXPF_SelectItem` von der- <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> Enumeration ist. `GUID_MacroExplorer`Ist eine GUID-Konstante, die in vsshell. idl definiert ist, und ist ein Beispiel für `rguidPersistenceSlot` in der Funktions Signatur von `ExtExpand` , definiert in Hu_node. h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Sie finden die Datei "Hu_node. h" im Ordner " \<installation root> \programme\vsip 8.0 \ envsdk\common\hierutil7":  
  
2. Benennen Sie den Ordner um, indem Sie den Befehl zum Umbenennen mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` ist ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Zeiger: `<IVsUIShell>``srpVsUIShell` . `guiVSStd97` ein eindeutiger Bezeichner der Befehlsgruppe, zu der der Befehl `cmdidRename` gehört, der in vsshlids. h definiert ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Projekttypen](../extensibility/internals/creating-project-types.md)   
 [VSSDK-Beispiele](../misc/vssdk-samples.md)