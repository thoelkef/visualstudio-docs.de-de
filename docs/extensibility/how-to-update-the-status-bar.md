---
title: 'Vorgehensweise: Aktualisieren der Statusleiste | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 15b207618487fd49516849c591ef80c56b618ce0
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-update-the-status-bar"></a>Vorgehensweise: Aktualisieren der Statusleiste
Die **Statusleiste** ist eine Steuerleiste am unteren Rand des viele Anwendungsfenster, die eine oder mehrere Textzeilen Status oder Indikatoren enthalten.  
  
### <a name="to-update-the-status-bar"></a>Beim Aktualisieren der Statusleiste  
  
1.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>für jede einzelne Ansichtsobjekt (DocView), die der Editor, z. B. eine Formularansicht und eine Codeansicht bereitstellt.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>  
  
2.  Wenn die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, aktualisieren Sie die Informationen in den **Statusleiste** durch Aufrufen der Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> </xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>  
  
    > [!NOTE]
    >  Ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>nur wenn Dokumentfenster anfänglich aktiviert ist.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Für den Rest der Zeit, die Ihre Dokumentfenster aktiv ist, müssen Sie aktualisieren die **Statusleiste** Informationen wie den Status der Editor Änderungen.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Ein **Statusleiste** enthält vier separate Felder:  
  
-   Statustext  
  
-   Statusanzeige  
  
-   Symbol "Animation"  
  
-   Editor-Informationen  
  
 Weitere Informationen finden Sie unter [Statusleisten](/cpp/mfc/status-bars).  
  
 Ruft die IDE automatisch den <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>Methode Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>Implementierung, wenn Ihre Dokumentfenster aktiviert wird.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> </xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>  
  
 Die VSPackage-Implementierung ist verantwortlich für das Aktualisieren des Statustext in der Statusleiste. Die IDE setzt diese Zeichenfolge in "Bereit" zurück, wenn das Statusfeld für den Text auf leere Zeichenfolge festgelegt ist ("") während der Leerlaufzeit.  
  
## <a name="see-also"></a>Siehe auch  
 [Statusleisten](/cpp/mfc/status-bars)
