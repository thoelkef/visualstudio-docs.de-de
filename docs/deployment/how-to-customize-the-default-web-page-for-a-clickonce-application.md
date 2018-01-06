---
title: "Vorgehensweise: Anpassen der Standardwebseite für eine ClickOnce-Anwendung | Microsoft Docs"
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
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: "14"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 4927a5909ba4b09e796d52d81cc9821a5a9c4820
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Gewusst wie: Anpassen der Standardwebseite für eine ClickOnce-Anwendung
Wenn Sie eine ClickOnce-Anwendung im Web zu veröffentlichen, wird eine Webseite automatisch generiert und zusammen mit der Anwendung veröffentlicht. Die Standardseite enthält den Namen der Anwendung und Links, um die Anwendung installieren, Installieren der erforderlichen Komponenten oder zugreifen auf die Hilfe auf MSDN.  
  
> [!NOTE]
>  Die tatsächliche Links, die Sie auf der Seite finden Sie unter abhängig sind, auf dem Computer, auf dem die Seite angezeigt wird, und welche erforderlichen Komponenten, die Sie einschließen.  
  
 Der Standardname für die Webseite lautet Publish.htm. Sie können den Namen im Ändern der **Projekt-Designer**. Weitere Informationen finden Sie unter [wie: Angeben einer Seite "Veröffentlichen" für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Nur, wenn eine neuere Version erkannt wird, wird die Publish.htm (Webseite) veröffentlicht.  
  
> [!NOTE]
>  Änderungen, die Sie, um vornehmen Ihre **veröffentlichen** Einstellungen wirken sich nicht auf der Seite "Publish.htm" mit einer Ausnahme: Wenn Sie hinzufügen oder Entfernen von Komponenten nach dem anfänglich veröffentlichen, die Liste der erforderlichen Komponenten werden nicht mehr genau. Sie müssen den Text für die erforderliche Verknüpfung entsprechend die Änderungen zu bearbeiten.  
  
### <a name="to-customize-the-publish-web-page"></a>Anpassen der Seite "Web veröffentlichen"  
  
1.  Veröffentlichen Sie die ClickOnce-Anwendung auf eine Webadresse ein. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Öffnen Sie auf dem Webserver die Publish.htm-Datei in Visual Web Designer oder einem anderen HTML-Editor ein.  
  
3.  Passen Sie die Seite wie gewünscht, und speichern Sie sie.  
  
4.  Dies ist optional. Um zu verhindern, dass Visual Studio Ihre benutzerdefinierten veröffentlichte Webseite überschreiben, deaktivieren Sie **generieren automatisch Bereitstellungswebseite nach jeder Veröffentlichung** im Dialogfeld Veröffentlichungsoptionen.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Gewusst wie: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)