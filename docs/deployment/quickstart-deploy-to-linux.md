---
title: Veröffentlichen Sie in App Service unter Linux
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: aa4afce6ef50284f1f966054e805b55c86f4daaf
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341747"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Veröffentlichen einer ASP.NET Core-app in App Service unter Linux mithilfe von Visual Studio

Sie können die **veröffentlichen** Tool zum Veröffentlichen von ASP.NET Core-apps in Azure App Service unter Linux.

Bereitstellung in App Service unter Linux über die **veröffentlichen** Tool erfordert Visual Studio 2017 Version 15.7.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Veröffentlichen Sie in App Service unter Linux

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie **veröffentlichen** (oder verwenden Sie die **erstellen** > **veröffentlichen** Menüelement).

    ![Der Befehl "Veröffentlichen" auf die im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "veröffentlichen wählen")

1. Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** Bereich angezeigt wird, in der Groß-/Kleinschreibung wählen **neues Profil erstellen**.

1. In der **Veröffentlichungsziel** Dialogfeld wählen **App Service Linux**.

    ![Wählen Sie Azure App Service](../deployment/media/quickstart-publish-linux.png "Azure App Service auswählen")

1. Wählen Sie **Veröffentlichen**. Die **App Service erstellen** Dialogfeld wird angezeigt. Sie Azure-Konto melden Sie an, wenn erforderlich, und klicken Sie dann auf die Standardeinstellungen für app Service über die Felder aufzufüllen

    ![Erstellen von App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "Azure App Service erstellen")

1. Wählen Sie **Erstellen** aus. Visual Studio die app zu Azure App Service bereitgestellt wird und die Web-app in Ihrem Browser lädt. Die Projekteigenschaften **veröffentlichen** Bereich werden die Website-URL und andere Details.

    ![Veröffentlichen Sie die im Eigenschaftenbereich mit einem Profil Statusübersicht](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

In den vorherigen Schritten haben Sie Azure-Ressourcen in einer Ressourcengruppe erstellt. Wenn Sie nicht auf diese Ressourcen in der Zukunft zu benötigen, können Sie sie löschen, indem Sie die Ressourcengruppe löschen.
Wählen Sie im linken Menü im Azure-Portal **Ressourcengruppen** und wählen Sie dann **MyResourceGroup**.
Klicken Sie auf der Seite der Ressourcengruppe stellen Sie sicher, dass die Ressourcen aufgelisteten sind, die Sie löschen möchten.
Wählen Sie **löschen**, Typ **MyResourceGroup** in das Textfeld ein, und wählen Sie dann **löschen**.

## <a name="next-steps"></a>Nächste Schritte

In dieser schnellstartanleitung haben Sie gelernt, wie Sie Visual Studio verwenden, um ein Veröffentlichungsprofil für die Bereitstellung in App Service unter Linux zu erstellen. Sie sollten Weitere Informationen zur Veröffentlichung in Linux mit Azure.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
