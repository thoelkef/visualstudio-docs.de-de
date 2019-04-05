---
title: 'Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d779e364f5cbe7bc4b90e0a77ab3fb825a7b6c2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960083"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung, Ändern der `Publish Version` -Eigenschaft bewirkt, dass die Anwendung als Update veröffentlicht werden. Standardmäßig Visual Studio automatisch inkrementiert die `Revision` Anzahl von der `Publish Version` jedes Mal veröffentlichen Sie die Anwendung.  
  
 Sie können dieses Verhalten deaktivieren, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>So deaktivieren Sie automatisch Inkrementieren der Veröffentlichungsversion  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  In der **Veröffentlichungsversion** deaktivieren Sie im Abschnitt der **Revisionsnummer automatisch mit jeder Veröffentlichung erhöhen** Kontrollkästchen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
