---
title: "Veröffentlichen einer Website - Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e324869eb90cd60cba68d9ed7b2e3fdb1ebb588d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Veröffentlichen Sie eine Web-app oder eine .NET Core-app zu einer Website mit dem Visual Studio Publish-tool

Sie können die **veröffentlichen** Tool ASP.NET-Apps auf einer Website veröffentlichen.

Diese Schritte gelten für ASP.NET, ASP.NET Core .NET Core und Python-apps in Visual Studio. Für Node.js die Schritte werden unterstützt, aber die Benutzeroberfläche unterscheidet sich.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung ((.NET Framework)**oder (nur c#) **ASP.NET-Webanwendung für Core**, und klicken Sie dann auf **OK**.

1. Wählen Sie **MVC**, stellen Sie sicher, dass **keine Authentifizierung** ausgewählt ist, und klicken Sie dann auf **OK**.

1. Geben Sie einen Namen wie **MyWebApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie **erstellen > Projektmappe** zum Erstellen des Projekts.

## <a name="publish-to-a-web-site"></a>Veröffentlichen einer Website

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**.

    ![Wählen Sie veröffentlichen](../deployment/media/quickstart-publish-aspnet.png "wählen veröffentlichen")

1. In der **veröffentlichen** Bereich auswählen **IIS, FTP usw.**.

    ![Wählen Sie IIS, FTP usw.](../deployment/media/quickstart-publish-iis-ftp.png "wählen Sie IIS, FTP usw.")

1. Klicken Sie auf **Veröffentlichen**.

    Das Profil die veröffentlichungseinstellungen ein Dialogfeld geöffnet.

    ![Wählen Sie die Ordner](../deployment/media/quickstart-publish-settings-web.png "Ordner auswählen")

1. In der **Veröffentlichungsmethode** Feld, und wählen Sie eine Methode wie z. B. **Web Deploy** oder **FTP**.

    Die Einstellungen, die Sie sehen, als Nächstes die publishing-Methode entsprechen.

1. Konfigurieren Sie die erforderliche Einstellungen für die Veröffentlichungsmethode, und klicken Sie auf **Validate Connection**.

    Wenn der Server oder das Ziel verfügbar ist, und Ihre Einstellungen korrekt sind, sehen Sie eine Meldung, die die Verbindung weist darauf hin überprüft wird und Sie bereit sind, veröffentlichen.

    ![Überprüfen der Verbindung](../deployment/media/quickstart-publish-web-deploy.png "Überprüfen der Verbindung")

1. Wenn Sie andere Einstellungen konfigurieren möchten, klicken Sie auf **Einstellungen**.

    Sie können Optionen konfigurieren, beispielsweise, ob eine Debug- oder Releasekonfiguration Konfiguration bereitzustellen, und klicken Sie dann auf **speichern**. Wenn Sie Remotedebuggen ist eine Debug-Konfiguration erforderlich.

1. Klicken Sie zum Veröffentlichen auf **veröffentlichen**.

    Das Ausgabefenster zeigt Bereitstellungsstatus sowie die Ergebnisse.

## <a name="next-steps"></a>Nächste Schritte

- [Bereitstellen von ASP.NET in IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)
