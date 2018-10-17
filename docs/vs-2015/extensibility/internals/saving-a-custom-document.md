---
title: Speichern eines benutzerdefinierten Dokuments | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1402dd3ed2acf6c4801953c59f14d2454b95c01d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235728"
---
# <a name="saving-a-custom-document"></a>Speichern eines benutzerdefinierten Dokuments
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Umgebungshandles der **speichern**, **speichern**, und **Alles speichern** Befehle. Wenn ein Benutzer klickt **speichern**, **speichern**, **oder speichern Sie alle** auf die **Datei** Menü oder schließt die Projektmappe, wodurch alle speichern, die folgenden erfolgt.  
  
 ![Speichern im Kunden-Editor](../../extensibility/internals/media/private.gif "Private")  
Speichern Sie, speichern unter, und speichern Sie alle Klassenbehandlung für einen benutzerdefinierten Editor-Befehl  
  
 Dieser Prozess wird in den folgenden Schritten beschrieben:  
  
1.  Für die **speichern** und **speichern** Befehle, die Umgebung verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service, um zu bestimmen, das das aktive Fenster, und somit welche Elemente gespeichert werden soll. Nachdem das aktive Dokumentfenster bekannt ist, sucht die Umgebung für das Dokument in der ausgeführten Dokumententabelle Hierarchie Zeiger und Elementbezeichner (Element-ID). Weitere Informationen finden Sie unter [Running Document Table](../../extensibility/internals/running-document-table.md).  
  
     Für den Befehl Alle speichern verwendet die Umgebung die Informationen in der ausgeführten Dokumententabelle, kompilieren Sie die Liste der zu speichernden alle Elemente.  
  
2.  Wenn die Lösung empfängt eine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufrufen, wird der Satz von ausgewählten Elementen durchlaufen (, also die Mehrfachauswahl von verfügbar gemacht werden die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Service).  
  
3.  Die Lösung verwendet für jedes Element in der Auswahl den Hierarchie Zeiger aufrufen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Methode, um zu bestimmen, ob der Kontextmenübefehl von "Speichern" aktiviert werden soll. Wenn ein oder mehrere Elemente geändert werden, ist der Befehl "Speichern" aktiviert. Wenn die Hierarchie ein standard-Editors verwendet wird, klicken Sie dann die Hierarchie-Delegaten, die für Abfragen dirty-Status in den Editor durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> Methode.  
  
4.  Für jedes ausgewählte Element, das geändert wurde, verwendet die Lösung den Hierarchie Zeiger zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Methode auf die entsprechenden Hierarchien.  
  
     Bei einem benutzerdefinierten Editor ist die Kommunikation zwischen das dokumentendatenobjekt und das Projekt privat. Daher werden speziellen persistenzaspekte zwischen diesen beiden Objekten behandelt.  
  
    > [!NOTE]
    >  Wenn Sie Ihre eigenen Persistenz implementieren, müssen Sie unbedingt Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Methode, um Zeit zu sparen. Diese Methode überprüft, um sicherzustellen, dass sie zum Speichern der Datei sicher ist (z. B. die Datei ist nicht schreibgeschützt).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)

