---
title: VSCodeWindow-Objekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 165855fc6f8e63c6c7ad84cb8432419258b7ba4e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322377"
---
# <a name="vscodewindow-object"></a>VSCodeWindow-Objekt
Ein Code-Fenster ist eine spezielle Dokumentfenster, der eine oder mehrere Textansichten, in der Regel enthalten kann die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.

 Aus Sicht der Systemarchitektur wird im Code-Fenster ein Dokumentfenster, das innerhalb eines Fensterrahmens. Konkret wird im Code-Fenster einfach ein Dokumentfenster mit zusätzlichen Funktionen. Im Modus Multiple Document Interface (MDI) ist im Code-Fenster den MDI-Child-Rahmen. Weitere Informationen finden Sie unter [Anpassen von Fenstern des Code mit der legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).

 Die folgende Tabelle enthält die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekt.

|Methode|Beschreibung|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Stellt einen generischen Mechanismus suchen einen Dienst, den ein global eindeutiger Bezeichner (GUID) identifiziert.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Stellt mehrere Document Interface (MDI) untergeordnetes Element, das eine oder mehrere Codeansichten enthält.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Füllt einen Fensterrahmen.|

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Abbildungen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)