---
title: Veröffentlichen auf einer Website
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1236c3057cd209bd5c7c81304a2168704927c506
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "71127932"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Veröffentlichen einer Web-App auf einer Website mithilfe von Visual Studio

Sie können das Tool zum **Veröffentlichen** verwenden, um ASP.NET-, ASP.NET Core-, .NET Core- und Python-Apps über Visual Studio auf einer Website zu veröffentlichen. Für Node.js können Sie zwar gleichen Schritte ausführen, jedoch ist die Benutzeroberfläche anders.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Wenn Sie eine Windows-Desktopanwendung für eine Netzwerkdateifreigabe veröffentlichen müssen, sehen Sie sich den Artikel [Bereitstellen einer Desktopanwendung mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# oder Visual Basic) an. Informationen zu C++/CLI finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), und Informationen zu C/C++ finden Sie unter [Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Veröffentlichen auf einer Website

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie auf **Neues Profil erstellen**.

1. Vergewissern Sie sich im Dialogfeld **Pick a publish target** (Veröffentlichungsziel auswählen), dass **IIS, FTP usw.** ausgewählt ist.

    ![Auswählen von IIS, FTP, usw.](../deployment/media/quickstart-publish-iis-ftp.png "Auswählen von IIS, FTP, usw.")

1. Wählen Sie **Veröffentlichen**. Das Dialogfeld „Profile Publish Settings“ (Profilveröffentlichungseinstellungen) wird geöffnet.

    ![Auswählen eines Ordners](../deployment/media/quickstart-publish-settings-web.png "Auswählen eines Ordners")

1. Geben Sie im Feld **Veröffentlichungsmethode** eine Methode wie z.B. **Web Deploy** oder **FTP** an. Die Einstellungen, die als Nächstes angezeigt werden, entsprechen der Veröffentlichungsmethode. Web Deploy vereinfacht die Bereitstellung von Web-Apps und Websites auf IIS-Servern und muss auf dem Server als Anwendung installiert werden. Verwenden Sie den [Webplattform-Installer](https://www.microsoft.com/web/downloads/platform.aspx) zur Installation.

1. Konfigurieren Sie die erforderlichen Einstellungen für die Veröffentlichungsmethode, und klicken Sie auf **Validate Connection** (Verbindung überprüfen). Wenn der Server oder das Ziel verfügbar sind und Ihre Einstellungen korrekt sind, wird eine Meldung angezeigt, dass die Verbindung überprüft wurde. Dann können Sie veröffentlichen.

    ![Überprüfen der Verbindung](../deployment/media/quickstart-publish-web-deploy.png "Überprüfen der Verbindung")

1. Klicken Sie auf **Einstellungen**, um andere Bereitstellungseinstellungen vorzunehmen, z.B. ob eine Debug- oder Releasekonfiguration bereitgestellt werden soll, und klicken Sie anschließend auf **Speichern**. Wenn Sie remote debuggen, ist die Debugkonfiguration erforderlich.

1. Wenn Sie eine Veröffentlichung durchführen möchten, klicken Sie auf **Veröffentlichen**. Im Ausgabefenster werden der Fortschritt und das Ergebnis der Bereitstellung angezeigt.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie erfahren, wie Sie Visual Studio unter Linux verwenden können, um ein Veröffentlichungsprofil zu erstellen. Sie können ein Veröffentlichungsprofil auch durch das Importieren von Veröffentlichungseinstellungen konfigurieren.

> [!div class="nextstepaction"]
> [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in IIS](tutorial-import-publish-settings-iis.md)
