---
title: "Verwalten von R&#252;ckg&#228;ngigmachen und wiederholen, mit der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - rückgängig management"
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Verwalten von R&#252;ckg&#228;ngigmachen und wiederholen, mit der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editoren müssen Rückgängig\-Vorgänge unterstützt, mit denen Benutzer ihre letzte Änderungen rückgängig zu machen, wenn sie den Code ändern. Die meisten Editoren implementiert unter [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] können Rückgängig\-Unterstützung, die automatisch von der integrierten Entwicklungsumgebung \(IDE\) bereitgestellt haben.  
  
## In diesem Abschnitt  
 [Gewusst wie: Implementieren von Rückgängig\-Management](../extensibility/how-to-implement-undo-management.md)  
 Stellt Rückgängig\-Funktion für Editoren mit einzelnen oder mehreren Ansichten bereit.  
  
 [Gewusst wie: deaktivieren den Rückgängig\-Stapel](../extensibility/how-to-clear-the-undo-stack.md)  
 Beschreibt, wie einen Rückgängig\-Stapel zu löschen.  
  
 [Gewusst wie: Verwenden Sie die verknüpften Verwaltung](../extensibility/how-to-use-linked-undo-management.md)  
 Fügen verknüpften Management in Editor.  
  
## Referenz  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Ermöglicht die rückgängig\-Verwaltung für einen Editor, der mehrere Ansichten unterstützt.  
  
## Verwandte Abschnitte