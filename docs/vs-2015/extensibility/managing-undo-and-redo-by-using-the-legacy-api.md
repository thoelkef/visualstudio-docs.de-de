---
title: Verwalten von rückgängig machen, und wiederholen Sie die Legacy-API mit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194371"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Verwalten von Vorgängen zum Rückgängigmachen und Wiederherstellen mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editoren müssen Rückgängig-Vorgänge unterstützt, mit denen Benutzer ihre letzten Änderungen zurückzusetzen, wenn sie zum Ändern von Code. Die meisten Editoren implementierter [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Rückgängig-Unterstützung, die automatisch von der integrierten Entwicklungsumgebung (IDE) bereitgestellt haben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Implementieren der Rückgängig-Funktion](../extensibility/how-to-implement-undo-management.md)  
 Bietet Rückgängig-Funktion für Editoren mit einzelnen oder mehreren Ansichten an.  
  
 [Vorgehensweise: Leeren des Stapels zum Rückgängigmachen](../extensibility/how-to-clear-the-undo-stack.md)  
 Beschreibt, wie einen Rückgängig-Stapel gelöscht.  
  
 [Vorgehensweise: Verwenden der verknüpften Rückgängig-Funktion](../extensibility/how-to-use-linked-undo-management.md)  
 Enthält verknüpfte rückgängig-Verwaltung in den Editor.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Bietet rückgängig-Verwaltung für einen Editor, der mehrere Ansichten unterstützt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte
