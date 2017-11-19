---
title: "Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: be66edb3880e8ef91f8fd95d7f11fe465322451f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Gewusst wie: Festlegen der ClickOnce-Veröffentlichungsversion
Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Eigenschaft legt fest, ob die Anwendung, die Sie veröffentlichen als Update behandelt werden. Jedes Mal Version erhöht wird, wird die Anwendung als Update veröffentlicht werden.  
  
 Die `Publish Version` Eigenschaft kann festgelegt werden, auf die **veröffentlichen** auf der Seite der **Projekt-Designer**.  
  
> [!NOTE]
>  Es ist eine Option "Project", die automatisch erhöht wird die `Publish Version` Eigenschaft jedes Mal die Anwendung veröffentlicht wird; diese Option ist standardmäßig aktiviert. Weitere Informationen finden Sie unter [Vorgehensweise: automatisch Erhöhen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>So ändern Sie die Veröffentlichungsversion  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  In **Veröffentlichungsversion** Feld, erhöht die **wichtigen**, **kleinere**, **erstellen**, oder **Revision** Version Zahlen.  
  
    > [!NOTE]
    >  Sie sollten nie eine Versionsnummer verringern; Dies kann unvorhersehbare Updateverhalten daher verursachen.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Vorgehensweise: automatisch Erhöhen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)