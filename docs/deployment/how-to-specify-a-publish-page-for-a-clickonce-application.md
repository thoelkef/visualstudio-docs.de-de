---
title: 'Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9878c3aa3f7ca7ae2a1606e3dd455731c0d9876b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917756"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung
Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung eine Standardwebseite (publish.htm) generiert und zusammen mit der Anwendung veröffentlicht wird. Diese Seite enthält den Namen der Anwendung, einen Link zum Installieren der Anwendung und/oder alle erforderlichen Komponenten und einen Link zu einem Hilfethema [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Die **Seite "Veröffentlichen"** Eigenschaft für das Projekt können Sie einen Namen für die Webseite für angeben Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
 Nachdem die Seite "Veröffentlichen" angegeben wurde, wird das nächste Mal, die, das Sie veröffentlichen, das Sie an den Veröffentlichungsort kopiert. Es wird nicht überschrieben werden, wenn Sie erneut veröffentlichen. Wenn Sie die Darstellung der Seite anpassen möchten, können Sie dafür ohne sich Gedanken, verlieren Ihre Änderungen. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen der ClickOnce-Standardwebseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 Die **Seite "Veröffentlichen"** Eigenschaft kann festgelegt werden, der **Veröffentlichungsoptionen** klicken Sie im Dialogfeld aus zugegriffen werden kann die **veröffentlichen** im Bereich der **Projekt-Designer**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Um eine benutzerdefinierte Webseite für eine ClickOnce-Anwendung anzugeben.  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie die **veröffentlichen** Bereich.  
  
3.  Klicken Sie auf die **Optionen** die Schaltfläche, um die **Veröffentlichungsoptionen** Dialogfeld.  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  In der **Veröffentlichungsoptionen** Dialogfeld Feld, stellen Sie sicher, dass die **lichen Bereitstellungswebseite nach dem Veröffentlichen** das Kontrollkästchen aktiviert ist (es sollte standardmäßig ausgewählt).  
  
6.  In der **Bereitstellungswebseite** , geben Sie den Namen für Ihre Webseite, und klicken Sie dann auf **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Um zu verhindern, dass die Seite "Veröffentlichen" Starten jedes Mal, wenn Sie veröffentlichen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie die **veröffentlichen** Bereich.  
  
3.  Klicken Sie auf die **Optionen** die Schaltfläche, um die **Veröffentlichungsoptionen** Dialogfeld.  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  In der **Veröffentlichungsoptionen** Dialogfeld das Kontrollkästchen der **lichen Bereitstellungswebseite nach dem Veröffentlichen** Kontrollkästchen.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Vorgehensweise: Anpassen der ClickOnce-Standardwebseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)