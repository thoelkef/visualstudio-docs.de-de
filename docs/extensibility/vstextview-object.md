---
title: VSTextView-Objekt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697711"
---
# <a name="vstextview-object"></a>VSTextView-Objekt

Die Textansicht ist ein Fenster, in dem Benutzer den Unicode-Text des Textpuffers anzeigen und bearbeiten können. Im Wesentlichen ist die Ansicht das, was die meisten Benutzer als Editor bezeichnen. Da die Ansicht durch verschiedene Textebenen (Wortumbruch, Umriss von Text usw.) vom Puffer getrennt ist, ist die Ansicht nicht garantiert eine exakte Darstellung des Textes im Puffer. Weitere Informationen zur Textansicht finden Sie [unter Zugreifen auf die Textansicht mithilfe der Legacy-API](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

Die folgende Tabelle zeigt die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Schnittstellen im Objekt.

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Aktiviert die Erstellung zusammengesetzter Aktionen (d. h. Aktionen, die in einer einzigen Rückgängig-/Wiederholungseinheit gruppiert sind).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegenden Methoden zum Verwalten und Zugreifen auf die Ansicht bereit. `IVsTextView`ist nicht sicher eingefädelt.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und verwaltet einen Fensterbereich.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagiert mit Textebenen.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge für die Ansicht aus einem anderen Thread aus.|

## <a name="see-also"></a>Weitere Informationen

- [Zahlen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer-Objekt](../extensibility/vstextbuffer-object.md)
