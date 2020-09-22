---
title: 'Gewusst wie: Verwenden der verknüpften rückgängig-Verwaltung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840956"
---
# <a name="how-to-use-linked-undo-management"></a>Vorgehensweise: Verwenden der verknüpften Rückgängig-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verknüpftes Rückgängigmachen ermöglicht dem Benutzer das gleichzeitige rückgängig machen derselben Änderungen in mehreren Dateien. Beispielsweise handelt es sich bei gleichzeitigen Textänderungen in mehreren Programmdateien (z. b. eine Header Datei und eine Visual C++ Datei) um eine verknüpfte rückgängig-Transaktion. Die Funktion "verknüpfte rückgängig machen" ist in die Implementierung des rückgängig-Managers der Umgebung integriert, sodass <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> Sie diese Funktion bearbeiten können. Verknüpftes Rückgängigmachen wird von einer übergeordneten Rückgängig-Komponente implementiert, die separate rückgängig-Stapel miteinander verknüpfen kann, um als einzelne Rückgängig-Einheit Die Vorgehensweise für die Verwendung von verknüpftem Rückgängigmachen finden Sie im folgenden Abschnitt.  
  
### <a name="to-use-linked-undo"></a>So verwenden Sie verknüpfte rückgängig  
  
1. Ruft `QueryService` auf `SVsLinkedUndoManager` , um einen Zeiger auf zu erhalten `IVsLinkedUndoTransactionManager` .  
  
2. Erstellen Sie die erste übergeordnete verknüpfte Rückgängig-Einheit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> durch Aufrufen von Dadurch wird der Startpunkt für eine Reihe von rückgängig-Stapeln festgelegt, die in verknüpfte rückgängig-Stapel gruppiert werden. In der- `OpenLinkedUndo` Methode müssen Sie auch angeben, ob die verknüpfte Rückgängig-Aktion strikt oder nicht streng sein soll. Das nicht strikte verknüpfte rückgängig-Verhalten bedeutet, dass einige der Dokumente mit verknüpften rückgängig-gleich geordneten Elementen geschlossen werden können und die anderen verknüpften Rückgängigmachen gleichzeitig auf Ihren Das strikte verknüpfte rückgängig-Verhalten gibt an, dass alle verknüpften gleich geordneten Stapel gleichzeitig rückgängig gemacht werden müssen. Fügen Sie die nachfolgenden verknüpften rückgängig-Stapel durch Aufrufen der [IOleUndoManager:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) -Methode hinzu.  
  
3. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> Sie auf, um alle verknüpften rückgängig-Einheiten als einen Rollback auszuführen.  
  
    > [!NOTE]
    > Zum Implementieren der verknüpften rückgängig-Verwaltung in einem Editor fügen Sie die rückgängig-Verwaltung Weitere Informationen zum Implementieren der verknüpften rückgängig-Verwaltung finden Sie unter Gewusst [wie: Implementieren der rückgängig-Verwaltung](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [Ioleparameentundounit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Vorgehensweise: Implementieren der Rückgängig-Funktion](../extensibility/how-to-implement-undo-management.md)
