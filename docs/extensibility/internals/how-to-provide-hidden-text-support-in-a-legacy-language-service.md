---
title: "Vorgehensweise: unterstützen ausgeblendetem Text in einen Legacy-Sprachdienst | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 664ab99af45e8c449247c5515184293ecb1a469f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Vorgehensweise: unterstützen ausgeblendetem Text in einen Legacy-Sprachdienst
Sie können ausgeblendete Textbereiche neben Gliederungsbereiche erstellen. Ausgeblendeten Text Regionen können es sich um Client gesteuert oder Editor gesteuert und werden verwendet, um einen Bereich der Text vollständig ausblenden. Der Editor zeigt einen ausgeblendeten Bereich als horizontale Linien an. Ein Beispiel hierfür ist, die nur Skript-Ansicht im HTML-Editor.  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-implement-a-hidden-text-region"></a>Implementieren Sie eine Region ausgeblendetem text  
  
1.  Rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Dies gibt einen Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, und übergeben Sie einen Zeiger für einen angegebenen Text-Puffer. Dies bestimmt, ob bereits eine Sitzung für ausgeblendeten Text für den Puffer vorhanden ist.  
  
3.  Wenn bereits eine vorhanden ist, Sie müssen nicht zum Erstellen einer und einen Zeiger auf den vorhandenen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt wird zurückgegeben. Verwenden Sie this-Zeiger, aufzulisten und ausgeblendeten Text Regionen erstellen. Rufen Sie andernfalls <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> zur Erstellung einer Sitzung ausgeblendetem Text für den Puffer.  
  
     Ein Zeiger auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt wird zurückgegeben.  
  
    > [!NOTE]
    >  Beim Aufruf `CreateHiddenTextSession`, Sie können angeben, dass einen Client ausgeblendetem Text (d. h. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Der ausgeblendete Text Client benachrichtigt Sie, wenn ausgeblendeten Texts oder Gliederung erweitert oder werden, durch den Benutzer reduziert ist.  
  
4.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> , fügen Sie einen oder mehrere neue Kontur Regionen zu einem Zeitpunkt angeben der folgenden Informationen in den `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) Parameter:  
  
    1.  Geben Sie den Wert `hrtConcealed` in der `iType` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur, um anzugeben, dass Sie eine ausgeblendete Region, anstatt einen Gliederungsbereich erstellen.  
  
        > [!NOTE]
        >  Wenn verdeckten Regionen ausgeblendet sind, zeigt der Editor automatisch um ausgeblendete Bereiche an, dass ihr Vorhandensein Linien.  
  
    2.  Gibt an, ob der Bereich ist der Client gesteuert oder Editor gesteuert, in der `dwBehavior` Mitglied der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur. Die intelligente Gliederungsmodus Implementierung kann eine Mischung aus Gliederung Editor und der Client gesteuert und Regionen ausgeblendetem Text enthalten.