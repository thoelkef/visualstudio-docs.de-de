---
title: Verwalten von rückgängig machen, und wiederholen Sie die Legacy-API mit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ccb49abc1251b489807efcb4d7e9ce89b25dcd16
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842696"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Verwalten von zum Rückgängigmachen und wiederherstellen, indem Sie mit der legacy-API
Editoren müssen Rückgängig-Vorgänge unterstützt, mit denen Benutzer ihre letzten Änderungen zurückzusetzen, wenn sie zum Ändern von Code. Die meisten Editoren implementierter [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Rückgängig-Unterstützung, die automatisch von der integrierten Entwicklungsumgebung (IDE) bereitgestellt haben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Implementieren von Rückgängig-Verwaltung](../extensibility/how-to-implement-undo-management.md)  
 Bietet Rückgängig-Funktion für Editoren mit einzelnen oder mehreren Ansichten an.  
  
 [Vorgehensweise: Deaktivieren des Rückgängig-Stapels](../extensibility/how-to-clear-the-undo-stack.md)  
 Beschreibt, wie einen Rückgängig-Stapel gelöscht.  
  
 [Vorgehensweise: Verwenden Sie die verknüpfte rückgängig-Verwaltung](../extensibility/how-to-use-linked-undo-management.md)  
 Enthält verknüpfte rückgängig-Verwaltung in den Editor.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Bietet rückgängig-Verwaltung für einen Editor, der mehrere Ansichten unterstützt.  
