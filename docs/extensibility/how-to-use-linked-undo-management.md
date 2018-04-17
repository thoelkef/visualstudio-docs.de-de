---
title: 'Vorgehensweise: Verwenden Sie die Verwaltung von verknüpfter Rollbackvorgang | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 24e39bd0bde922dbe761bc9de176d43161bb985d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-linked-undo-management"></a>Vorgehensweise: Verwenden Sie die verknüpfter Rollbackvorgang Verwaltung
Verknüpfter Rollbackvorgang ermöglicht dem Benutzer, die gleichen Änderungen in mehreren Dateien gleichzeitig rückgängig zu machen. Gleichzeitige Text ändert sich über mehrere Programmdateien, z. B. eine Headerdatei und eine Visual C++-Datei ist beispielsweise ein verknüpfter Rollbackvorgang-Transaktion. Verknüpfter Rollbackvorgang-Funktion ist in der Umgebung Implementierung der Rollback-Manager integriert und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> können Sie diese Funktion zu bearbeiten. Verknüpfter Rollbackvorgang wird von einem übergeordneten Rückgängig-Komponente implementiert, die verknüpft sind separate Rückgängig-Stapel zusammen, um als einen einzelnen Rückgängig-Komponente behandelt werden können. Das Verfahren für die Verwendung verknüpften Rollbackvorgang werden im folgenden Abschnitt beschrieben.  
  
### <a name="to-use-linked-undo"></a>Verknüpften Rollbackvorgang verwenden  
  
1.  Rufen Sie `QueryService` auf `SVsLinkedUndoManager` um einen Zeiger auf `IVsLinkedUndoTransactionManager`.  
  
2.  Erstellen Sie die ursprüngliche übergeordnete verknüpfter Rollbackvorgang Einheit durch Aufrufen von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Dies legt den Ausgangspunkt für eine Reihe von Rückgängig-Stapel in verknüpften Rückgängig-Stapel gruppiert werden. In der `OpenLinkedUndo` Methode müssen Sie auch angeben, ob Sie die verknüpften Rollbackvorgang strict oder außerhalb des strict-sein soll. Nicht strict verknüpfter Rollbackvorgang Verhalten bedeutet, dass können einige der Dokumente mit verknüpfter Rollbackvorgang gleichgeordnete Elemente schließen lassen, die andere verknüpfte, rückgängig weiterhin gleichgeordnete Elemente, auf deren Stapel. Strict verknüpfter Rollbackvorgang Verhalten gibt an, dass alle verknüpften nebengeordneten Stapel zusammen oder überhaupt nicht rückgängig gemacht werden. Fügen Sie die nachfolgenden verknüpft Rückgängig Stapel durch den Aufruf [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) Methode.  
  
3.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> auf Ausführen, Sichern Sie alle Einheiten verknüpfter Rollbackvorgang als eine.  
  
    > [!NOTE]
    >  Fügen Sie zum Implementieren der verknüpfter Rollbackvorgang-Verwaltung in einem Editor rückgängig-Verwaltung hinzu. Weitere Informationen zum Implementieren von verknüpfter Rollbackvorgang Management finden Sie unter [Vorgehensweise: Implementieren rückgängig Management](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Vorgehensweise: Implementieren von Rückgängig-Management](../extensibility/how-to-implement-undo-management.md)