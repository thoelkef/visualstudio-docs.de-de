---
title: "Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung | Microsoft Docs"
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: e05718d2a00df76d2c78e16c5b4473ab48d43a39
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Gewusst wie: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung
Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung eine Standardwebseite (publish.htm) generiert und zusammen mit der Anwendung veröffentlicht wird. Diese Seite enthält den Namen der Anwendung, einen Link zu der Anwendung und/oder alle vorausgesetzten Komponenten installieren und einen Link zu einem Hilfethema [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Die **Seite "Veröffentlichen"** -Eigenschaft für das Projekt bietet die Möglichkeit, geben Sie einen Namen für die Webseite für Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
 Sobald die Seite "Veröffentlichen" angegeben wurde, wird das nächste Mal veröffentlichen, es an den Veröffentlichungsort kopiert. Es wird nicht überschrieben werden, wenn Sie erneut veröffentlichen. Wenn Sie die Darstellung der Seite anpassen möchten, können Sie dies tun, ohne befürchten, verlieren Ihre Änderungen. Weitere Informationen finden Sie unter [wie: Anpassen der ClickOnce-Standard-Webseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 Die **Seite "Veröffentlichen"** Eigenschaft kann festgelegt werden, der **Veröffentlichungsoptionen** (Dialogfeld), über die **veröffentlichen** Bereich des der **Projekt-Designer**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Eine benutzerdefinierte Website für eine ClickOnce-Anwendung angeben  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie die **veröffentlichen** Bereich.  
  
3.  Klicken Sie auf die **Optionen** die Schaltfläche, um die **Veröffentlichungsoptionen** (Dialogfeld).  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  In der **Veröffentlichungsoptionen** Dialogfeld Feld, stellen Sie sicher, dass die **öffnen Bereitstellungswebseite nach dem Veröffentlichen** Kontrollkästchen (sollte standardmäßig ausgewählt sein).  
  
6.  In der **Bereitstellungswebseite:** Feld Geben Sie den Namen für die Webseite, und klicken Sie dann auf **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Um zu verhindern, dass die Seite "Veröffentlichen" Starten jedes Mal, die Sie veröffentlichen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie die **veröffentlichen** Bereich.  
  
3.  Klicken Sie auf die **Optionen** die Schaltfläche, um die **Veröffentlichungsoptionen** (Dialogfeld).  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  In der **Veröffentlichungsoptionen** deaktivieren Sie im Dialogfeld die **öffnen Bereitstellungswebseite nach dem Veröffentlichen** Kontrollkästchen.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Vorgehensweise: Anpassen der ClickOnce-Standardwebseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)