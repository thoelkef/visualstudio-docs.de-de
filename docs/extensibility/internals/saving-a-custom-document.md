---
title: Speichern eines Dokuments benutzerdefinierte | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3cd6f5f45736a7b2578bc9df80a8472d3b50c3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="saving-a-custom-document"></a>Speichern eine benutzerdefinierte Dokumenteigenschaften
Umgebungshandles der **speichern**, **speichern unter**, und **alle speichern** Befehle. Wenn ein Benutzer klickt **speichern**, **speichern unter**, **oder alle speichern** auf die **Datei** Menü oder schließt die Projektmappe, wodurch alle speichern, die folgenden erfolgt.  
  
 ![Kunden-Editor speichern](../../extensibility/internals/media/private.gif "Private")  
Speichern Sie, speichern unter, und speichern Sie alle befehlsbehandelung für einen benutzerdefinierten editor  
  
 Dabei werden in den folgenden Schritten beschrieben:  
  
1.  Für die **speichern** und **speichern unter** Befehle, die Umgebung verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service, um zu bestimmen, das aktive Fenster, und daher welche Elemente gespeichert werden soll. Nachdem das aktive Fenster bekannt ist, sucht die Umgebung für das Dokument in der Dokumenttabelle der ausgeführten Hierarchie Zeiger und Element-ID (ItemID). Weitere Informationen finden Sie unter [Document-Tabelle ausgeführt](../../extensibility/internals/running-document-table.md).  
  
     Für den Befehl Alle speichern verwendet die Umgebung die Informationen in der Dokumenttabelle der ausgeführten, kompilieren Sie die Liste aller Elemente zu speichern.  
  
2.  Wenn empfängt die Lösung eine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufrufen, wird die Gruppe von ausgewählten Elementen durchlaufen (d. h. die Mehrfachauswahl von verfügbar gemacht werden die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Service).  
  
3.  Für jedes Element in der Auswahl, die Lösung den Hierarchie-Zeiger aufrufen, verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Methode, um zu bestimmen, ob der Menübefehl speichern aktiviert werden soll. Wenn ein oder mehrere Elemente geändert werden, ist die Befehls "Speichern" aktiviert. Wenn die Hierarchie ein standard-Editors verwendet wird, klicken Sie dann die Hierarchie-Delegaten, die für Abfragen modifizierte Status in den Editor durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> Methode.  
  
4.  Für jedes ausgewählte Element, das geändert wurde, verwendet die Lösung den Hierarchie-Zeiger zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> -Methode für die entsprechenden Hierarchien.  
  
     Im Falle eines benutzerdefinierten Editors ist die Kommunikation zwischen dem dokumentdatenobjekt und dem Projekt privat. Daher werden speziellen Persistenz Bedenken zwischen diesen beiden Objekten behandelt.  
  
    > [!NOTE]
    >  Wenn Sie eine eigene Persistenz implementieren, aufrufen werden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Methode, um Zeit zu sparen. Diese Methode überprüft, um sicherzustellen, dass die Datei gespeichert werden kann (z. B. die Datei ist nicht schreibgeschützt).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)