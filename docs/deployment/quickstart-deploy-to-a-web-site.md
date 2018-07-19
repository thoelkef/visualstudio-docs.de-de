---
title: Auf einer Website veröffentlichen
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 036d7549995f79808142c3a0a64e7e5f2075df2c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077502"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Veröffentlichen einer Web-app auf einer Website mit Visual Studio

Sie können die **veröffentlichen** Tool zum Veröffentlichen von ASP.NET, ASP.NET Core, .NET Core und Python-apps auf einer Website aus Visual Studio. Für Node.js die Schritte werden unterstützt, aber die Benutzeroberfläche unterscheidet sich.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>Auf einer Website veröffentlichen

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie **veröffentlichen** (oder verwenden Sie die **erstellen** > **veröffentlichen** Menüelement).

    ![Der Befehl "Veröffentlichen" auf die im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "veröffentlichen wählen")

1. Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** angezeigt. Wählen Sie **neues Profil erstellen**.

1. In der **Veröffentlichungsziel auswählen** Dialogfeld Wählen Sie **IIS, FTP usw**.

    ![Wählen Sie IIS, FTP usw.](../deployment/media/quickstart-publish-iis-ftp.png "wählen Sie IIS, FTP usw..")

1. Wählen Sie **Veröffentlichen**. Das Profil den veröffentlichungseinstellungen wird geöffnet.

    ![Wählen Sie Ordner](../deployment/media/quickstart-publish-settings-web.png "Ordner auswählen")

1. In der **Veröffentlichungsmethode** Feld, wählen Sie eine Methode z. B. **Web Deploy** oder **FTP**. Die Einstellungen, die Sie sehen, entsprechen neben der Veröffentlichungsmethode. Web Deploy vereinfacht die Bereitstellung von Webanwendungen und Websites auf IIS-Server, und muss als eine Anwendung auf dem Server installiert werden. Verwenden der [Webplattform-Installer](https://www.microsoft.com/web/downloads/platform.aspx) installieren.

1. Konfigurieren Sie die erforderliche Einstellungen für die Publish-Methode, und wählen Sie **Verbindung überprüfen**. Wenn die Server oder das Ziel verfügbar ist, und Ihre Einstellungen korrekt sind, wird eine Meldung, die Verbindung wird überprüft, und Sie sind bereit für die Veröffentlichung.

    ![Überprüfen der Verbindung](../deployment/media/quickstart-publish-web-deploy.png "Überprüfen der Verbindung")

1. Wählen Sie **Einstellungen** zum Konfigurieren anderer bereitstellungseinstellungen, z. B. ob Debug- oder Releasekonfiguration Konfiguration bereitstellen, und wählen Sie dann **speichern**. Wenn Sie Remote Debuggen, ist eine Debug-Konfiguration erforderlich.

1. Wählen Sie zum Veröffentlichen **veröffentlichen**. Das Ausgabefenster zeigt Bereitstellungsstatus und die Ergebnisse.

## <a name="next-steps"></a>Nächste Schritte

In dieser schnellstartanleitung haben Sie gelernt, wie Sie Visual Studio verwenden, um ein Veröffentlichungsprofil erstellen. Sie können auch eine Veröffentlichung konfigurieren Profil durch Importieren der veröffentlichungseinstellungen.

> [!div class="nextstepaction"]
> [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in IIS](tutorial-import-publish-settings-iis.md)
