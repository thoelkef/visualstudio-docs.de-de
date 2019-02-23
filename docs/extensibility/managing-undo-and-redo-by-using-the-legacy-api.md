---
title: Verwalten von rückgängig machen, und wiederholen Sie die Legacy-API mit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adf6a2405ae3d3408f9cf04199ba05dff9232326
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687795"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Verwalten von zum Rückgängigmachen und wiederherstellen, indem Sie mit der legacy-API
Editoren müssen Rückgängig-Vorgänge unterstützt, mit denen Benutzer ihre letzten Änderungen zurückzusetzen, wenn sie zum Ändern von Code. Die meisten Editoren implementierter [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Rückgängig-Unterstützung, die automatisch von der integrierten Entwicklungsumgebung (IDE) bereitgestellt haben.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Vorgehensweise: Implementieren von Rückgängig-Verwaltung](../extensibility/how-to-implement-undo-management.md) bietet Rückgängig-Funktion für Editoren mit einzelnen oder mehrere Ansichten.

- [Vorgehensweise: Deaktivieren den Rückgängig-Stapel](../extensibility/how-to-clear-the-undo-stack.md) wird beschrieben, wie einen Rückgängig-Stapel zu löschen.

- [Vorgehensweise: Verwenden Sie die verknüpfte rückgängig-Verwaltung](../extensibility/how-to-use-linked-undo-management.md) Incorporates verknüpften rückgängig-Verwaltung in den Editor.

## <a name="reference"></a>Referenz
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Bietet rückgängig-Verwaltung für einen Editor, der mehrere Ansichten unterstützt.
