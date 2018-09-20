---
title: 'Vorgehensweise: Verwenden Sie die verknüpfte rückgängig-Verwaltung | Microsoft-Dokumentation'
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
ms.openlocfilehash: 255ad8de79b13a74816b2abd28281ac5de6f1932
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370561"
---
# <a name="how-to-use-linked-undo-management"></a>Gewusst wie: verwenden verknüpften rückgängig-Verwaltung
Verknüpfter Rollbackvorgang ermöglicht den Benutzer, die gleichen Änderungen in mehreren Dateien gleichzeitig rückgängig zu machen. Gleichzeitige Text ändert sich auf mehrere Programme, z. B. eine Headerdatei und eine Visual C++-Datei, ist z. B. eine verknüpfte rückgängig-Transaktion. Verknüpften Rückgängig-Funktion ist in der Umgebung-Implementierung von den rückgängig-Manager integriert und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> können Sie diese Funktion zu bearbeiten. Verknüpfter Rollbackvorgang wird von einer übergeordneten Rückgängig-Komponente implementiert, die verknüpft sind separate Rückgängig-Stapel zusammen, um als eine einzelne Rückgängig-Einheit behandelt werden können. Das Verfahren für die Verwendung verknüpften Rollbackvorgang wird im folgenden Abschnitt beschrieben.  
  
## <a name="to-use-linked-undo"></a>Verwenden von verknüpften rückgängig  
  
1.  Rufen Sie `QueryService` auf `SVsLinkedUndoManager` um einen Zeiger auf `IVsLinkedUndoTransactionManager`.  
  
2.  Erstellen Sie das erste übergeordnete verknüpften Rückgängig-Komponente durch Aufrufen von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Hiermit wird den Ausgangspunkt für eine Gruppe von Rückgängig-Stapel in der verknüpften Rückgängig-Stapel gruppiert werden. In der `OpenLinkedUndo` müssen Sie auch festlegen, ob die verknüpfte rückgängig strenge oder außerhalb des strict-Methode. Nicht-strikte verknüpften rückgängig-Verhalten bedeutet, dass einige der Dokumente mit verknüpften rückgängig-nebengeordneten schließen können weiterhin lassen, die das andere verknüpfte gleichgeordnete Elemente, auf deren Stapel rückgängig. Strenge verknüpften rückgängig-Verhalten gibt an, dass alle gleichgeordnetes Element der verknüpften Rückgängig-Stapel rückgängig gemacht werden, zusammen oder überhaupt nicht. Fügen Sie die nachfolgenden verknüpfte Rückgängigmachen von Stapeln durch Aufrufen von [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) Methode.  
  
3.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> einführen alle die verknüpfte Rückgängig-Komponenten als eine.  
  
    > [!NOTE]
    >  Fügen Sie zum Implementieren der verknüpften rückgängig-Verwaltung in einem Editor rückgängig-Verwaltung hinzu. Weitere Informationen zum Implementieren der verknüpften rückgängig-Verwaltung finden Sie unter [Vorgehensweise: Implementieren von Rückgängig-Verwaltung](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Gewusst wie: Implementieren von Rückgängig-Verwaltung](../extensibility/how-to-implement-undo-management.md)