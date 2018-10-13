---
title: Umbenennen von Knoten in der Projekthierarchie (C++) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 5b86096834b2a841b3fe35e1045bc3897bb7667f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203761"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Umbenennen von Knoten in der Projekthierarchie (C++)
Sie können einem projekthierarchienknoten für den Ordner umbenennen, mit dem HierUtil7-Projekt-Framework für nicht verwalteten C++. Weitere Informationen finden Sie unter [HierUtil7 Beispiel](http://msdn.microsoft.com/en-us/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Erweitern den Knoten "Standorthierarchie"  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Erweitern den Knoten "Standorthierarchie", und benennen Sie den Ordner  
  
1.  Wählen Sie den Knoten "Standorthierarchie", indem Sie mit dem folgenden Verfahren:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` ist der Container der Hierarchie entspricht, zu dem Ordner und `EXPF_SelectItem` stammt aus dem <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> Enumeration. Die `GUID_MacroExplorer` ist eine GUID-Konstante, die in Vsshell.idl definiert und ist ein Beispiel für `rguidPersistenceSlot` in die Funktionssignatur der `ExtExpand`in Hu_node.h definiert.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Sie finden die Hu_node.h-Datei im Ordner \<installationsstamms > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2.  Benennen Sie den Ordner, von dem Befehl Umbenennen durch Buchen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` ist eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Zeiger: `<IVsUIShell>``srpVsUIShell`. `guiVSStd97` ist ein eindeutiger Bezeichner der Befehlsgruppe, zu dem der Befehl `cmdidRename` gehört, im Vsshlids.h definiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekttypen](../extensibility/internals/creating-project-types.md)   
 [VSSDK-Beispiele](../misc/vssdk-samples.md)