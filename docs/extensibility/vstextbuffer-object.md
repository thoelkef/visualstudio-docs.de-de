---
title: VSTextBuffer-Objekt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697726"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer-Objekt
Das Textpufferobjekt stellt einen Strom von Unicode-Text dar, der im Allgemeinen einer Datei zugeordnet ist. Ein <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt kann außerhalb des Kontexts des Kerneditors verwendet werden, wie in einem Assistenten.

 Die folgende Tabelle zeigt `VSTextBuffer`die Schnittstellen von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Iolecommandtarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standard-OLE-Schnittstelle. Wird für die Rückgängig-/Wiederholungsbehandlung im Puffer verwendet.|
|[Ipersistfile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standard-OLE-Schnittstelle.|
|[Ipersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standard-OLE-Schnittstelle.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von Verbindungen -Aktionen (d. h. Aktionen, die in einer einzigen Rückgängig-/Wiederholungseinheit gruppiert sind).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Ermöglicht die Persistenz von Dokumentdaten, die vom Textpuffer verwaltet werden.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Bietet grundlegende Dienstleistungen; von vielen Kunden verwendet werden.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Wird verwendet, um einen Puffer zu durchsuchen.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet Lese- und Schreibfunktionen mithilfe zweidimensionaler Koordinaten. Erbt von `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet Lese- und Schreibfunktionen mithilfe eindimensionaler Koordinaten. Erbt von `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Bietet schnellen, streamorientierten, sequenziellen Zugriff auf Text im Puffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Bietet Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder Moniker des Puffers. Sie können Ihre eigenen Zufallsdaten mit dieser Schnittstelle im Puffer speichern, indem Sie eine GUID erstellen und als Schlüssel verwenden.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt Verbindungspunkte für Ereignisse.|

## <a name="remarks"></a>Bemerkungen
 Die `VSTextBuffer` wird in `QueryInterface` der `IVsTextBuffer`Regel durch einen Aufruf auf gefunden. Weitere Informationen finden Sie unter [Textpuffer](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Zahlen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)
