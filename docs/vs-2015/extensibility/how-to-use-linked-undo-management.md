---
title: 'Vorgehensweise: Verwenden Sie die verknüpfte rückgängig-Verwaltung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e64d65376a85b9cbc9af525117e017c56f7b851
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523609"
---
# <a name="how-to-use-linked-undo-management"></a>Vorgehensweise: Verwenden Sie die verknüpfte rückgängig-Verwaltung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: verwenden verknüpften rückgängig-Verwaltung](https://docs.microsoft.com/visualstudio/extensibility/how-to-use-linked-undo-management).  
  
Verknüpfter Rollbackvorgang ermöglicht den Benutzer, die gleichen Änderungen in mehreren Dateien gleichzeitig rückgängig zu machen. Gleichzeitige Text ändert sich auf mehrere Programme, z. B. eine Headerdatei und eine Visual C++-Datei, ist z. B. eine verknüpfte rückgängig-Transaktion. Verknüpften Rückgängig-Funktion ist in der Umgebung-Implementierung von den rückgängig-Manager integriert und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> können Sie diese Funktion zu bearbeiten. Verknüpfter Rollbackvorgang wird von einer übergeordneten Rückgängig-Komponente implementiert, die verknüpft sind separate Rückgängig-Stapel zusammen, um als eine einzelne Rückgängig-Einheit behandelt werden können. Das Verfahren für die Verwendung verknüpften Rollbackvorgang wird im folgenden Abschnitt beschrieben.  
  
### <a name="to-use-linked-undo"></a>Verwenden von verknüpften rückgängig  
  
1.  Rufen Sie `QueryService` auf `SVsLinkedUndoManager` um einen Zeiger auf `IVsLinkedUndoTransactionManager`.  
  
2.  Erstellen Sie das erste übergeordnete verknüpften Rückgängig-Komponente durch Aufrufen von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Hiermit wird den Ausgangspunkt für eine Gruppe von Rückgängig-Stapel in der verknüpften Rückgängig-Stapel gruppiert werden. In der `OpenLinkedUndo` müssen Sie auch festlegen, ob die verknüpfte rückgängig strenge oder außerhalb des strict-Methode. Nicht-strikte verknüpften rückgängig-Verhalten bedeutet, dass einige der Dokumente mit verknüpften rückgängig-nebengeordneten schließen können weiterhin lassen, die das andere verknüpfte gleichgeordnete Elemente, auf deren Stapel rückgängig. Strenge verknüpften rückgängig-Verhalten gibt an, dass alle gleichgeordnetes Element der verknüpften Rückgängig-Stapel rückgängig gemacht werden, zusammen oder überhaupt nicht. Fügen Sie die nachfolgenden verknüpfte Rückgängigmachen von Stapeln durch Aufrufen von [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) Methode.  
  
3.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> einführen alle die verknüpfte Rückgängig-Komponenten als eine.  
  
    > [!NOTE]
    >  Fügen Sie zum Implementieren der verknüpften rückgängig-Verwaltung in einem Editor rückgängig-Verwaltung hinzu. Weitere Informationen zum Implementieren der verknüpften rückgängig-Verwaltung finden Sie unter [Vorgehensweise: Implementieren rückgängig-Verwaltung](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Vorgehensweise: Implementieren der Rückgängig-Funktion](../extensibility/how-to-implement-undo-management.md)

