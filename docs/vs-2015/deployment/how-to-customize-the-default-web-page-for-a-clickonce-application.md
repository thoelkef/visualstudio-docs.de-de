---
title: 'Vorgehensweise: Anpassen der Standard Webseite für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840831"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Gewusst wie: Anpassen der Standardwebseite für eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine ClickOnce-Anwendung im Web veröffentlicht wird, wird automatisch eine Webseite generiert und zusammen mit der Anwendung veröffentlicht. Die Standardseite enthält den Namen der Anwendung und Links zum Installieren der Anwendung, Installieren der erforderlichen Komponenten oder zugreifen auf die Hilfe auf MSDN.  
  
> [!NOTE]
> Die tatsächlichen Links, die auf der Seite angezeigt werden, hängen von dem Computer ab, auf dem die Seite angezeigt wird, und von den Voraussetzungen, die Sie einschließen.  
  
 Der Standardname für die Webseite ist Publish.htm. der Name kann im **Projekt-Designer**geändert werden. Weitere Informationen finden Sie unter Gewusst [wie: Angeben einer Veröffentlichungs Seite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Die Publish.htm Webseite wird nur veröffentlicht, wenn eine neuere Version erkannt wird.  
  
> [!NOTE]
> Änderungen, die Sie an Ihren **Veröffentlichungs** Einstellungen vornehmen, wirken sich nicht auf die Publish.htm Seite aus, mit einer Ausnahme: Wenn Sie nach der ersten Veröffentlichung erforderliche Komponenten hinzufügen oder entfernen, ist die Liste der Voraussetzungen nicht mehr korrekt. Sie müssen den Text für den erforderlichen Link bearbeiten, um die Änderungen widerzuspiegeln.  
  
### <a name="to-customize-the-publish-web-page"></a>So passen Sie die Webseite zum Veröffentlichen an  
  
1. Veröffentlichen Sie Ihre ClickOnce-Anwendung an einem Webspeicherort. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2. Öffnen Sie auf dem Webserver die Datei Publish.htm im Visual Web Designer oder einem anderen HTML-Editor.  
  
3. Passen Sie die Seite wie gewünscht an, und speichern Sie Sie.  
  
4. (Optional) Um zu verhindern, dass Visual Studio die angepasste Veröffentlichungs Webseite überschreibt, deaktivieren Sie im Dialogfeld Veröffentlichungs Optionen die Option **Bereitstellung automatisch generieren nach jeder Veröffentlichung** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Sicherheit und-Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Gewusst wie: Angeben einer Veröffentlichungs Seite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
