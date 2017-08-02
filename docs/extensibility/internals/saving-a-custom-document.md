---
title: "Speichern ein benutzerdefiniertes Dokument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Persistenz, benutzerdefinierte Dokumente speichern"
  - "Projekte [Visual Studio SDK] benutzerdefinierte Dokumente speichern"
  - "Editoren [Visual Studio SDK] benutzerdefinierte Dokumente speichern"
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Speichern ein benutzerdefiniertes Dokument
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Umgebung behandelt **Save**, **Save As**und **Save All** Befehle.  Wenn ein Benutzer auf **Speichern**klickt, wird **Speichern unter**, **oder Alles speichern** auf dem **Datei** Menü oder die Projektmappe mit dem Ergebnis einer Alle speichern, der folgende Prozess verwendet wird.  
  
 ![Speichern im Kunden&#45;Editor](~/docs/extensibility/internals/media/private.gif "Private")  
Speichern, Speichern unter, und speichern Sie alle Befehls Klassenbehandlung für einen benutzerdefinierten Editor  
  
 Dieser Vorgang wird in den folgenden Schritten einzeln aufgeführt:  
  
1.  Für die **Speichern** und **Speichern unter** Befehle verwendet die Umgebung den <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Dienst, um das aktive Dokumentfenster und somit bestimmen, welche Elemente gespeichert werden sollen.  Sobald das aktive Dokumentfenster bekannt ist, durchsucht die Umgebung den Hierarchien zeiger\- und Elementbezeichner \(itemID\) für das Dokument in der Tabelle Dokumente.  Weitere Informationen finden Sie unter [Dokumenttabelle der ausgeführten](../../extensibility/internals/running-document-table.md).  
  
     Für den Befehl Alle speichern, die Umgebung verwendet die Informationen in der Tabelle der Dokumente, um die Liste aller Elemente zu kompilieren, um zu speichern.  
  
2.  Wenn die Projektmappe <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> einen Aufruf empfängt, wird sie durch den Satz von ausgewählten Elementen durch \(d. h. die Mehrfachauswahl verfügbar gemacht <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> vom Dienst\).  
  
3.  Bei jedem Element in der Auswahl, wird die Projektmappe den Zeiger Hierarchien, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>\-Methode aufrufen, um zu bestimmen, ob der Menü Speichern aktiviert werden soll.  Wenn eine oder mehrere Elemente geändert wurden, ist der Befehl Speichern aktiviert.  Wenn die Hierarchie einen standardmäßigen Editor verwendet, delegiert die Hierarchie Abfragen für geänderten Status in den Editor, indem sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>\-Methode aufruft.  
  
4.  Bei jedem ausgewählten Element, das geändert wurde, wird die Projektmappe den Zeiger Hierarchien, um die Hierarchien auf den entsprechenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>\-Methode aufrufen.  
  
     Im Fall eines benutzerdefinierten Editors ist die Kommunikation zwischen Dokumenten und das angegebene Channeldatenobjekt dem Projekt privat.  Daher werden alle besonderen Aspekte Dauerhaftigkeit zwischen diesen beiden Objekten behandelt.  
  
    > [!NOTE]
    >  Wenn Sie implementieren, sind Sie Persistenz, ist die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>\-Methode aufrufen, um Zeit zu sparen.  Die überprüft diese Methode, um sicherzustellen, dass es sicher ist, die Datei zu speichern \(z. B. die Datei nicht schreibgeschützt\).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)