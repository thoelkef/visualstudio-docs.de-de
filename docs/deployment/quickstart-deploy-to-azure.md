---
title: Veröffentlichen in Azure App Service
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
- azure
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341689"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Veröffentlichen einer Web-app in Azure App Service mithilfe von Visual Studio

Sie können die **veröffentlichen** Tool zum Veröffentlichen von ASP.NET, ASP.NET Core, Node.js und .NET Core-apps in Azure App Service oder Azure App Service Linux (mit Containern). Führen Sie die Schritte für Python-apps auf [Python – in Azure App Service veröffentlichen](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie **veröffentlichen** (oder verwenden Sie die **erstellen** > **veröffentlichen** Menüelement).

    ![Der Befehl "Veröffentlichen" auf die im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "veröffentlichen wählen")

1. Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** Bereich angezeigt wird, in der Groß-/Kleinschreibung wählen **neues Profil erstellen**.

1. In der **Veröffentlichungsziel** Dialogfeld wählen **App Service**.

    ![Wählen Sie Azure App Service](../deployment/media/quickstart-publish-azure.png "Azure App Service auswählen")

1. Wählen Sie **Veröffentlichen**. Die **App Service erstellen** Dialogfeld wird angezeigt. Sie Azure-Konto melden Sie an, wenn erforderlich, und klicken Sie dann auf die Standardeinstellungen für app Service über die Felder aufzufüllen

    ![Erstellen von App Service](../deployment/media/quickstart-publish-settings-app-service.png "Azure App Service erstellen")

1. Wählen Sie **Erstellen** aus. Visual Studio die app zu Azure App Service bereitgestellt wird und die Web-app in Ihrem Browser lädt. Die Projekteigenschaften **veröffentlichen** Bereich werden die Website-URL und andere Details.

    ![Veröffentlichen Sie die im Eigenschaftenbereich mit einem Profil Statusübersicht](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

In den vorherigen Schritten haben Sie Azure-Ressourcen in einer Ressourcengruppe erstellt. Wenn Sie nicht auf diese Ressourcen in der Zukunft zu benötigen, können Sie sie löschen, indem Sie die Ressourcengruppe löschen.
Wählen Sie im linken Menü im Azure-Portal **Ressourcengruppen** und wählen Sie dann **MyResourceGroup**.
Klicken Sie auf der Seite der Ressourcengruppe stellen Sie sicher, dass die Ressourcen aufgelisteten sind, die Sie löschen möchten.
Wählen Sie **löschen**, Typ **MyResourceGroup** in das Textfeld ein, und wählen Sie dann **löschen**.

## <a name="next-steps"></a>Nächste Schritte

In dieser schnellstartanleitung haben Sie gelernt, wie Sie Visual Studio verwenden, um ein Veröffentlichungsprofil für die Bereitstellung in Azure erstellen. Sie können auch eine Veröffentlichung konfigurieren Profil durch Importieren der veröffentlichungseinstellungen von Azure App Service.

> [!div class="nextstepaction"]
> [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in Azure](tutorial-import-publish-settings-azure.md)
