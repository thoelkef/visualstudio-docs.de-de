---
title: 'Vorgehensweise: Aktualisieren der Status Leiste | Microsoft-Dokumentation'
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
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703148"
---
# <a name="how-to-update-the-status-bar"></a>Vorgehensweise: Aktualisieren der Statusleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **Statusleiste** ist eine Steuerleiste, die sich am unteren Rand vieler Anwendungsfenster befindet, die mindestens eine Status Textzeile oder einen Indikator enthält.  
  
### <a name="to-update-the-status-bar"></a>So aktualisieren Sie die Status Leiste  
  
1. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Sie für jedes einzelne Ansichts Objekt (DocView), das der Editor bereitstellt, z. b. eine Formularansicht und eine Code Ansicht.  
  
2. Wenn die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> , aktualisieren Sie die Informationen in der **Status Leiste** , indem Sie die Methoden von Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > Die IDE ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> nur auf, wenn das Dokument Fenster anfänglich aktiviert ist. Für den verbleibenden Zeitpunkt, an dem das Dokument Fenster aktiv ist, müssen Sie die **Status** leisten Informationen aktualisieren, wenn sich der Zustand des Editors ändert.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Eine **Status Leiste** enthält vier separate Felder:  
  
- Statustext  
  
- Statusleiste  
  
- Animiertes Symbol  
  
- Editor-Informationen  
  
  Weitere Informationen finden Sie unter [Status leisten](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  Die IDE ruft automatisch die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode der-Implementierung auf, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Wenn das Dokument Fenster aktiviert ist.  
  
  Das VSPackage-Implementierer ist für das Aktualisieren des Status Texts in der Statusleiste verantwortlich. Die IDE setzt diese Zeichenfolge auf "Ready" zurück, wenn das Statustextfeld zur Leerlaufzeit auf leeren Text ("") festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Status leisten](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
