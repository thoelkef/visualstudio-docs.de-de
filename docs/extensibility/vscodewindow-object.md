---
title: VSCodeWindow-Objekt | Microsoft Docs
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
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697954"
---
# <a name="vscodewindow-object"></a>VSCodeWindow-Objekt
Ein Codefenster ist ein spezielles Dokumentfenster, das eine <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oder mehrere Textansichten, in der Regel das Objekt, enthalten kann.

 Architektonisch ist das Codefenster ein Dokumentfenster, das sich innerhalb eines Fensterrahmens befindet. Funktionell ist das Codefenster einfach ein Dokumentfenster mit zusätzlichen Funktionen. Im MDI-Modus (Multiple Document Interface) ist das Codefenster der untergeordnete MDI-Frame. Weitere Informationen finden Sie unter [Anpassen von Codefenstern mithilfe der Legacy-API](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 Die folgende Tabelle enthält die <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Schnittstellen im Objekt.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Stellt einen generischen Zugriffsmechanismus bereit, um einen Dienst zu finden, den ein GLOBAL eindeutiger Bezeichner (GUID) identifiziert.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Stellt ein untergeordnetes Element für die Multi document Interface (MDI) dar, das eine oder mehrere Codeansichten enthält.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Füllt einen Fensterrahmen.|

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Zahlen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)
