---
title: 'Vorgehensweise: Anpassen der Standardwebseite für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ec63fe5ae4b99252321b86b44066c46842a0851
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433892"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Vorgehensweise: Anpassen der Standardwebseite für eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine ClickOnce-Anwendung im Web veröffentlichen, eine Webseite automatisch generiert und zusammen mit der Anwendung veröffentlicht. Die Standardseite enthält den Namen der Anwendung und Links zu die Anwendung zu installieren, Installieren der erforderlichen Komponenten oder zugreifen auf die Hilfe auf MSDN.  
  
> [!NOTE]
> Die tatsächliche Links, die Sie auf der Seite finden Sie abhängig sind, auf dem Computer, die, in dem die Seite angezeigt wird, und welche erforderlichen Komponenten, die Sie einbeziehen.  
  
 Der Standardname für die Webseite lautet Publish.htm. Sie können den Namen im Ändern der **Projekt-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Nur dann, wenn eine neuere Version erkannt wird, wird die Publish.htm (Webseite) veröffentlicht.  
  
> [!NOTE]
> Änderungen, die Sie, um vornehmen Ihre **veröffentlichen** Einstellungen wirken sich nicht auf der Seite "Publish.htm", mit einer Ausnahme: Wenn Sie hinzufügen oder entfernen Voraussetzungen, nachdem Sie ursprünglich veröffentlicht, die Liste der erforderlichen Komponenten werden nicht mehr korrekt. Sie müssen den Text für die erforderliche Verknüpfung zu den Änderungen entsprechend bearbeiten.  
  
### <a name="to-customize-the-publish-web-page"></a>Anpassen der Seite "Web veröffentlichen"  
  
1. Veröffentlichen Sie die ClickOnce-Anwendung auf eine Webadresse ein. Weitere Informationen finden Sie unter [Vorgehensweise: Publish a ClickOnce Application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2. Öffnen Sie auf dem Webserver der Publish.htm-Datei in Visual Web Designer oder einem anderen HTML-Editor ein.  
  
3. Anpassen der Seite nach Bedarf, und speichern Sie sie.  
  
4. Dies ist optional. Um zu verhindern, dass Visual Studio überschreiben Ihrer Webseite angepasste veröffentlichen, deaktivieren Sie **generieren automatisch Bereitstellungswebseite nach jeder veröffentlichen** im Dialogfeld "Veröffentlichungsoptionen".  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
