---
title: "Gewusst wie: Verwenden Sie die verkn&#252;pften Verwaltung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - verknüpften management"
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Gewusst wie: Verwenden Sie die verkn&#252;pften Verwaltung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Linked rückgängig machen kann der Benutzer die gleichen Änderungen gleichzeitig in mehreren Dateien rückgängig zu machen.  Zum Beispiel ändert simultaner Text über mehrere Programmdateien, z. B. eine Headerdatei und eine Visual verknüpft ist, C\+\+\-Datei Transaktion rückgängig gemacht.  Linked rückgängig Funktion wird in die Implementierung der Umgebung des managers Rückgängig und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> können Sie diese Funktion bearbeiten.  Rückgängig Linked wird implementiert von einer übergeordneten Rückgängigeinheit, die als einzelne Rückgängigeinheit zu behandelnden Rückgängig\-Stapel separaten, die das Verknüpfen kann.  Die Prozedur für die verknüpfte Anwendung einzeln rückgängig machen wird im folgenden Abschnitt aufgelistet.  
  
### Verwenden Sie die Option Rückgängig zur verknüpften  
  
1.  Rufen Sie `QueryService` auf `SVsLinkedUndoManager` auf, um einen Zeiger auf `IVsLinkedUndoTransactionManager`zu gelangen.  
  
2.  Erstellen Sie die ursprüngliche übergeordnetes Element verknüpfte Rückgängigeinheit durch Aufrufen von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>.  Dies legt den Ausgangspunkt für eine Gruppe fest in verknüpften zu gruppierende Rückgängig\-Stapel Rückgängigstapel.  In der `OpenLinkedUndo`\-Methode müssen Sie auch angeben, ob Sie den Befehl Rückgängig aus, um verknüpfte strikt oder Nicht STRICT sein soll.  Verknüpfte Nicht\-STRICT rückgängig machen Verhalten impliziert, dass einige Dokumente mit Joins gleichgeordnete Elemente können dem anderen verknüpft sein und dennoch schließen, nebengeordnete Elemente auf ihren Stapeln Undo Command rückgängig zu machen.  Ein streng verknüpftes Rollback gibt an, dass alle verknüpften nebengeordneten Stapel zusammen rückgängig gemacht werden müssen.  Fügen Sie die folgenden verknüpften Rückgängig\-Stapel hinzu, indem Sie [IOleUndoManager::Hinzufügen](http://msdn.microsoft.com/library/windows/desktop/ms680135)\-Methode aufrufen.  
  
3.  Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> , um alle verknüpften Rückgängigeinheiten als Steuerelement zurücksetzen.  
  
    > [!NOTE]
    >  Zum Implementieren der zugehörigen Rückgängigmachen Verwaltung in einem Editor rückgängig machen, fügen Administration.  Weitere Informationen zur Implementierung bezieht Rückgängigmachen Verwaltung finden [Gewusst wie: Implementieren Sie zum Rückgängigmachen Verwaltung](../extensibility/how-to-implement-undo-management.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Gewusst wie: Implementieren von Rückgängig\-Management](../extensibility/how-to-implement-undo-management.md)