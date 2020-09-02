---
title: Verwalten von Rückgängigmachen und wiederholen mithilfe der Legacy-API | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194371"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Verwalten von Vorgängen zum Rückgängigmachen und Wiederherstellen mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editoren müssen rückgängig-Vorgänge unterstützen, mit denen Benutzer ihre aktuellen Änderungen umkehren können, wenn Sie Code ändern. Die meisten Editoren, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] die unter und implementiert werden, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] können von der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) automatisch Rückgängigmachen  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Implementieren der Rückgängig-Funktion](../extensibility/how-to-implement-undo-management.md)  
 Stellt die Rückgängig-Funktion für Editoren mit einzelnen oder mehreren Ansichten bereit.  
  
 [Vorgehensweise: Leeren des Stapels zum Rückgängigmachen](../extensibility/how-to-clear-the-undo-stack.md)  
 Beschreibt, wie ein Rückgängig-Stapel gelöscht wird.  
  
 [Vorgehensweise: Verwenden der verknüpften Rückgängig-Funktion](../extensibility/how-to-use-linked-undo-management.md)  
 Integriert verknüpfte rückgängig-Verwaltung in Ihren Editor.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Bietet Rückgängig-Verwaltung für einen Editor, der mehrere Ansichten unterstützt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte
