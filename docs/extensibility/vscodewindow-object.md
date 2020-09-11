---
title: Vscodewindow-Objekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d319dfd0f44646f911a01a157a92fc2e5596e492
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012398"
---
# <a name="vscodewindow-object"></a>Vscodewindow-Objekt
Ein Code Fenster ist ein spezielles Dokument Fenster, das mindestens eine Textansicht enthalten kann, in der Regel das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.

 In der Architektur ist das Code Fenster ein Dokument Fenster, das sich innerhalb eines Fensterrahmens befindet. Funktionell ist das Code Fenster einfach ein Dokument Fenster mit zusätzlichen Features. Im MDI-Modus (Multiple Document Interface) ist das Code Fenster der untergeordnete MDI-Frame. Weitere Informationen finden Sie unter [Anpassen von Code Fenstern mit der Legacy-API](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015).

 In der folgenden Tabelle sind die Schnittstellen des- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekts enthalten.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Stellt einen generischen Zugriffs Mechanismus bereit, um einen Dienst zu suchen, den eine Globally Unique Identifier (GUID) identifiziert.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Stellt ein untergeordnetes Multiple Document Interface (MDI)-Element dar, das mindestens eine Code Ansicht enthält.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Füllt einen Fensterrahmen.|

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Abbildungen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)