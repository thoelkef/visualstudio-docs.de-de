---
title: 'Vorgehensweise: Aktualisieren der Statusleiste | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f1ba62fc5147eb679e6d6a64685b367aafacae4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324798"
---
# <a name="how-to-update-the-status-bar"></a>Vorgehensweise: Aktualisieren der Statusleiste
Die **Statusleiste** ist eine Steuerleiste am unteren Rand der vielen Anwendungsfenster, die eine oder mehrere Textzeilen Status oder Indikatoren enthalten.

## <a name="to-update-the-status-bar"></a>Zum Aktualisieren der Statusleiste

1. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> für jedes einzelne Ansicht-Objekt (DocView-), das der Editor, z. B. eine Formularansicht und eine Codeansicht bereitstellt.

2. Wenn die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, aktualisieren Sie die Informationen in den **Statusleiste** durch Aufrufen der Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.

    > [!NOTE]
    > Die IDE-Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> nur wenn Dokumentfensters anfänglich aktiviert ist. Für den Rest der Zeit, die Ihre Dokumentfenster aktiv ist, müssen Sie aktualisieren die **Statusleiste** Informationen wie den Status der Editor Änderungen.

## <a name="robust-programming"></a>Stabile Programmierung
 Ein **Statusleiste** enthält vier separate Felder:

- Statustext

- Statusanzeige

- Animierte Symbol

- Editorinformationen

  Weitere Informationen finden Sie unter [Statusleisten](/cpp/mfc/status-bars).

  Ruft die IDE automatisch den <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Implementierung, wenn Ihre Dokumentfenster aktiviert wird.

  Die VSPackage-Implementierung ist verantwortlich für den Text in der Statusleiste zu aktualisieren. Die IDE wird diese Zeichenfolge "Bereit" zurückgesetzt, wenn das Statusfeld für den Text auf leere Zeichenfolge festgelegt ist ("") während der Leerlaufzeit.

## <a name="see-also"></a>Siehe auch
- [Statusleisten](/cpp/mfc/status-bars)