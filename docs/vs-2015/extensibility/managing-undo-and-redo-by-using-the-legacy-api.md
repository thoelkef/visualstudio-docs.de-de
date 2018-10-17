---
title: Verwalten von rückgängig machen, und wiederholen Sie die Legacy-API mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb2ff049635d75608114be380c9697faf0585725
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177891"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Verwalten von Rückgängigmachen und Wiederherstellen mithilfe der Legacy-API
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

