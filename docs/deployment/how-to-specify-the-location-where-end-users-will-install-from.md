---
title: 'Vorgehensweise: Angeben des Speicher Orts für die Installation durch Endbenutzer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e28ad8353858b35fc1c4e83f0511a58b4162dc9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85381937"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Vorgehensweise: Angeben des Speicherorts für die Installation durch Endbenutzer
Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ist der Speicherort, an dem Benutzer die Anwendung herunterladen und installieren, nicht notwendigerweise der Speicherort, an dem Sie die Anwendung anfänglich veröffentlichen. Beispielsweise kann ein Entwickler in einigen Organisationen eine Anwendung auf einem Stagingserver veröffentlichen, und dann würde ein Administrator die Anwendung auf einen Webserver verschieben.

In diesem Fall können Sie die- `Installation URL` Eigenschaft verwenden, um den Webserver anzugeben, auf dem Benutzer die Anwendung herunterladen. Dies ist erforderlich, damit das Anwendungs Manifest weiß, wo nach Updates gesucht werden soll.

Die- `Installation URL` Eigenschaft kann auf der Seite **veröffentlichen** des Projekt- **Designers**festgelegt werden.

> [!NOTE]
> Die- `Installation URL` Eigenschaft kann auch mit dem **PublishWizard**festgelegt werden. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>So geben Sie eine Installations-URL an

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Geben Sie im Feld Installations-URL den Installations Speicherort unter Verwendung einer voll qualifizierten URL im Format ein `https://www.contoso.com/ApplicationName` , oder verwenden Sie einen UNC-Pfad im Format `\Server\ApplicationName` .

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)