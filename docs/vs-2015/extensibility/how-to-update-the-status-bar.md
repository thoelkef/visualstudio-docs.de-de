---
title: 'Vorgehensweise: Aktualisieren der Statusleiste | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d34642bd805469283ad22d6b40054596ed00a9e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441562"
---
# <a name="how-to-update-the-status-bar"></a>Vorgehensweise: Aktualisieren der Statusleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **Statusleiste** ist eine Steuerleiste am unteren Rand der vielen Anwendungsfenster, die eine oder mehrere Textzeilen Status oder Indikatoren enthalten.  
  
### <a name="to-update-the-status-bar"></a>Zum Aktualisieren der Statusleiste  
  
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
  
  Weitere Informationen finden Sie unter [Statusleisten](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  Ruft die IDE automatisch den <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Implementierung, wenn Ihre Dokumentfenster aktiviert wird.  
  
  Die VSPackage-Implementierung ist verantwortlich für den Text in der Statusleiste zu aktualisieren. Die IDE wird diese Zeichenfolge "Bereit" zurückgesetzt, wenn das Statusfeld für den Text auf leere Zeichenfolge festgelegt ist ("") während der Leerlaufzeit.  
  
## <a name="see-also"></a>Siehe auch  
 [Statusleisten](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
