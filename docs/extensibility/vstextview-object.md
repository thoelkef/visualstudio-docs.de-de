---
title: VSTextView-Objekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab54fce0271438f89ec66b4fc5d8db1ebe21634f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721419"
---
# <a name="vstextview-object"></a>VSTextView-Objekt
Die Textansicht ist ein Fenster, das ermöglicht Benutzern das Anzeigen und bearbeiten den Unicode-Text des Textpuffers. Im Wesentlichen ist die Ansicht, was die meisten Benutzer als Editor bezeichnet. Da die Ansicht aus dem Puffer von verschiedenen Textebenen (Zeilenumbruch, Gliederung, Text usw.) getrennt ist, wird die Sicht nicht garantiert eine genaue Darstellung des Texts im Puffer. Weitere Informationen zu der Textansicht, finden Sie unter [zugreifen auf TheText Ansicht mit der legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

 Die folgende Tabelle zeigt die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.

|Interface|Beschreibung|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von verbundaktionen (d. h. Aktionen, die in einer einzelnen Rückgängig-/Wiederholen-Einheit gruppiert sind).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegende Methoden für die Verwaltung und den Zugriff auf die Ansicht bereit. `IVsTextView` ist nicht sicher Thread.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und verwaltet einen Fensterbereich.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interaktion mit Textebenen.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge für die Sicht von einem anderen Thread.|

## <a name="see-also"></a>Siehe auch
- [Abbildungen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer-Objekt](../extensibility/vstextbuffer-object.md)
- [Zugreifen auf TheText Ansicht mit der legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)