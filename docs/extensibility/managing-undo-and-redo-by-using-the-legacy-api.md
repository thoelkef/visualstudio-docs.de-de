---
title: Rückgängig machen und wiederholen Sie über die Legacy-API verwalten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93bb65fa9865c5ca7386925d2c145f2acbc0993a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Verwalten von rückgängig und wiederholen, über die Legacy-API
Editoren müssen Rückgängig-Vorgängen unterstützen, mit denen Benutzer ihre zuletzt vorgenommenen Änderungen umzukehren, wenn sie den Code ändern. Die meisten unter implementierten Editoren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] können Rückgängig-Unterstützung, die automatisch von der integrierten Entwicklungsumgebung (IDE) bereitgestellt haben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Implementieren von Rückgängig-Management](../extensibility/how-to-implement-undo-management.md)  
 Bietet rückgängig Editoren mit einzelnen oder mehrere Ansichten.  
  
 [Vorgehensweise: Deaktivieren der Rückgängig-Stapel](../extensibility/how-to-clear-the-undo-stack.md)  
 Beschreibt, wie einen Rückgängig-Stapel gelöscht.  
  
 [Vorgehensweise: Verwenden Sie die verknüpfter Rollbackvorgang Verwaltung](../extensibility/how-to-use-linked-undo-management.md)  
 Verknüpfter Rollbackvorgang Management integriert in den Editor.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Ermöglicht die rückgängig-Verwaltung für einen Editor, der mehrere Ansichten unterstützt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte