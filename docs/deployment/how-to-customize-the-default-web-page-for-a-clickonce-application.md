---
title: Anpassen der Standardwebseite für ClickOnce-Anwendung
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66d304be4e2435b6ec1ecafe8aeb473b83fa1033
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263333"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Vorgehensweise: Anpassen der Standardwebseite für eine ClickOnce-Anwendung
Wenn Sie eine ClickOnce-Anwendung im Web veröffentlichen, eine Webseite automatisch generiert und zusammen mit der Anwendung veröffentlicht. Die Standardseite enthält den Namen der Anwendung und Links zu die Anwendung zu installieren, Installieren der erforderlichen Komponenten oder zugreifen auf die Hilfe auf MSDN.

> [!NOTE]
> Die tatsächliche Links, die Sie auf der Seite finden Sie abhängig sind, auf dem Computer, die, in dem die Seite angezeigt wird, und welche erforderlichen Komponenten, die Sie einbeziehen.

 Der Standardname für die Webseite ist *Publish.htm*; Sie können den Namen im Ändern der **Projekt-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 Die *Publish.htm* Webseite wird veröffentlicht, nur dann, wenn eine neuere Version erkannt wird.

> [!NOTE]
> Änderungen, die Sie, um vornehmen Ihre **veröffentlichen** Einstellungen wirken sich nicht die *Publish.htm* Seite mit einer Ausnahme: Wenn Sie hinzufügen oder entfernen Voraussetzungen, nachdem Sie ursprünglich veröffentlicht haben, wird die Liste der Komponenten nicht mehr genau sein. Sie müssen den Text für die erforderliche Verknüpfung zu den Änderungen entsprechend bearbeiten.

### <a name="to-customize-the-publish-web-page"></a>Anpassen der Seite "Web veröffentlichen"

1. Veröffentlichen Sie die ClickOnce-Anwendung auf eine Webadresse ein. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Öffnen Sie auf dem Webserver, der *Publish.htm* -Datei in Visual Web Designer oder einem anderen HTML-Editor.

3. Anpassen der Seite nach Bedarf, und speichern Sie sie.

4. Dies ist optional. Um zu verhindern, dass Visual Studio überschreiben Ihrer Webseite angepasste veröffentlichen, deaktivieren Sie **generieren automatisch Bereitstellungswebseite nach jeder veröffentlichen** in die **Veröffentlichungsoptionen** Dialogfeld.

## <a name="see-also"></a>Siehe auch
- [ClickOnce security and deployment (ClickOnce-Sicherheit und -Bereitstellung)](../deployment/clickonce-security-and-deployment.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)