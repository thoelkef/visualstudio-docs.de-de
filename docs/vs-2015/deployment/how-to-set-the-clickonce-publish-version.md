---
title: 'Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: d832f28ddbd12bd72d018c841cf114ddae709e38
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523595"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Gewusst wie: Festlegen der ClickOnce-Veröffentlichungsversion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion](https://docs.microsoft.com/visualstudio/deployment/how-to-set-the-clickonce-publish-version).  
  
Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` Eigenschaft bestimmt, ob die Anwendung, die Sie veröffentlichen als Update behandelt wird. Jede Zeitpunktversion erhöht wird, die Anwendung als Update veröffentlicht werden.  
  
 Die `Publish Version` Eigenschaft kann festgelegt werden, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.  
  
> [!NOTE]
>  Es gibt eine Projektoption, die automatisch erhöht wird die `Publish Version` Eigenschaft jedes Mal die Anwendung veröffentlicht wird; diese Option ist standardmäßig aktiviert. Weitere Informationen finden Sie unter [Vorgehensweise: automatisch Erhöhen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>So ändern Sie die Version veröffentlichen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In **Veröffentlichungsversion** Feld, das Erhöhen der **wichtigen**, **kleinere**, **erstellen**, oder **Revision** Version die Nummern.  
  
    > [!NOTE]
    >  Sie sollten niemals eine Versionsnummer verringern; Dies kann zu unvorhersehbaren Updateverhalten führen.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



