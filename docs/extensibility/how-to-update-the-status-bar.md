---
title: 'Vorgehensweise: Aktualisieren der Statusleiste | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 76801810aafa3bd4048776ca38385ad1cf508d94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-the-status-bar"></a>Vorgehensweise: Aktualisieren der Statusleiste
Die **Statusleiste** ist eine Steuerleiste am unteren Rand des viele Anwendungsfenster, die eine oder mehrere Textzeilen Status oder Indikatoren enthalten.  
  
### <a name="to-update-the-status-bar"></a>Beim Aktualisieren der Statusleiste  
  
1.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> für jede einzelne Ansichtsobjekt (DocView), die der Editor, z. B. eine Formularansicht und eine Codeansicht bereitstellt.  
  
2.  Wenn die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, aktualisieren Sie die Informationen in den **Statusleiste** durch Aufrufen der Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> nur wenn Dokumentfenster anfänglich aktiviert ist. Für den Rest der Zeit, die Ihre Dokumentfenster aktiv ist, müssen Sie aktualisieren die **Statusleiste** Informationen wie den Status der Editor Änderungen.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Ein **Statusleiste** enthält vier separate Felder:  
  
-   Statustext  
  
-   Statusanzeige  
  
-   Symbol "Animation"  
  
-   Editor-Informationen  
  
 Weitere Informationen finden Sie unter [Statusleisten](/cpp/mfc/status-bars).  
  
 Ruft die IDE automatisch den <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Implementierung, wenn Ihre Dokumentfenster aktiviert wird.  
  
 Die VSPackage-Implementierung ist verantwortlich für das Aktualisieren des Statustext in der Statusleiste. Die IDE setzt diese Zeichenfolge in "Bereit" zurück, wenn das Statusfeld für den Text auf leere Zeichenfolge festgelegt ist ("") während der Leerlaufzeit.  
  
## <a name="see-also"></a>Siehe auch  
 [Statusleisten](/cpp/mfc/status-bars)