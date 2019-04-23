---
title: 'Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: bca76d104550a8607de82c9092f57d43c027e63c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104474"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` Eigenschaft bestimmt, ob die Anwendung, die Sie veröffentlichen als Update behandelt wird. Jede Zeitpunktversion erhöht wird, die Anwendung als Update veröffentlicht werden.  
  
 Die `Publish Version` Eigenschaft kann festgelegt werden, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.  
  
> [!NOTE]
>  Es gibt eine Projektoption, die automatisch erhöht wird die `Publish Version` Eigenschaft jedes Mal die Anwendung veröffentlicht wird; diese Option ist standardmäßig aktiviert. Weitere Informationen finden Sie unter [Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>So ändern Sie die Version veröffentlichen  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. In **Veröffentlichungsversion** Feld, das Erhöhen der **wichtigen**, **kleinere**, **erstellen**, oder **Revision** Version die Nummern.  
  
    > [!NOTE]
    >  Sie sollten niemals eine Versionsnummer verringern; Dies kann zu unvorhersehbaren Updateverhalten führen.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
