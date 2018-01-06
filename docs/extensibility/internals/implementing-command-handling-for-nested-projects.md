---
title: "Projekte implementieren Befehlsbehandelung für geschachtelte | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4ed9efab34a51bdfaacea1773a33637437b2ced
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementieren von Befehlsbehandelung für geschachtelte-Projekte
Die IDE Befehle, die durchlaufen werden kann übergeben, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> und die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstellen auf geschachtelte Projekte oder übergeordnete Projekte filtern oder überschreiben Sie die Befehle können.  
  
> [!NOTE]
>  Nur Befehle, die normalerweise vom übergeordneten Projekt behandelt können gefiltert werden. Befehle wie **erstellen** und **bereitstellen** von behandelt die IDE kann nicht gefiltert werden.  
  
 Die folgenden Schritte beschreiben den Prozess zum Implementieren der befehlsverarbeitung.  
  
## <a name="procedures"></a>Verfahren  
  
#### <a name="to-implement-command-handling"></a>Um die befehlsverarbeitung zu implementieren  
  
1.  Wenn der Benutzer wählt aus einer geschachtelten Projekts oder eines Knotens in einem geschachtelten Projekt:  
  
    1.  Ruft die IDE die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode.  
  
     - oder -  
  
    1.  Wenn der Befehl in einem Hierarchiefenster wie einen Menübefehl Kontextmenü im Projektmappen-Explorer, stammt die IDE Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> Methode für das Projekt übergeordnete.  
  
2.  Übergeordnetes Projekt kann zu übergebenden Parameter überprüfen `QueryStatus`, wie z. B. `pguidCmdGroup` und `prgCmds`, um zu bestimmen, ob das übergeordnete Projekt die Befehle filtern soll. Wenn das übergeordnete Projekt implementiert wird, um Befehle zu filtern, sollte festgelegt werden:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Übergeordnetes Projekt zurückgeben sollte `S_OK`.  
  
     Wenn übergeordneten Projekts den Befehl nicht gefiltert werden, sollte es nur zurückgeben `S_OK`. In diesem Fall leitet die IDE automatisch den Befehl ab, an das untergeordnete Projekt.  
  
     Übergeordnetes Projekt muss nicht in den Befehl an das untergeordnete Projekt weiterzuleiten. Die IDE führt diese Aufgabe...  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)