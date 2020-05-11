---
title: Veröffentlichen in Azure App Service
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 4bbff0c2d149afddc355afe5f6c93e9d0aea54c0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806914"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Veröffentlichen einer Web-App in Azure App Service mit Visual Studio

Mithilfe einer der folgenden Methoden können Sie ASP.NET-, ASP.NET Core, Node.js und .NET Core-Apps in Azure App Service oder Azure App Service Linux (mit Containern) veröffentlichen.

* Verwenden Sie Azure DevOps mit [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops) für die kontinuierliche (oder automatisierte) Bereitstellung von Apps.

* Verwenden Sie für die einmalige (oder manuelle) Bereitstellung von Apps das Tool zum **Veröffentlichen** in Visual Studio, um ASP.NET-, ASP.NET Core, Node.js und .NET Core-Apps in Azure App Service oder Azure App Service Linux (mit Containern) bereitzustellen. Führen Sie für Python-Apps die Schritte unter [Python – Veröffentlichen in Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) aus.

In diesem Artikel wird beschrieben, wie Sie das Tool zum **Veröffentlichen** für die einmalige Bereitstellung verwenden.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie in diesem Fall auf **Neues Profil erstellen**.

1. Wählen Sie im Dialogfeld **Veröffentlichungsziel auswählen** den Eintrag **App Service** aus.

    ![Azure App Service auswählen](../deployment/media/quickstart-publish-azure.png "Azure App Service auswählen")

1. Wählen Sie **Veröffentlichen**. Das Dialogfeld **App Service erstellen** wird angezeigt. Melden Sie sich ggf. mit Ihrem Azure-Konto an. Anschließend werden die Felder mit den Standardeinstellungen für App Service aufgefüllt.

    ![App Service erstellen](../deployment/media/quickstart-publish-settings-app-service.png "Azure App Service auswählen")

1. Klicken Sie auf **Erstellen**. Visual Studio stellt die App in Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen. Im Bereich **Veröffentlichen** werden in den Projekteigenschaften die Website-URL und andere Details angezeigt.

    ![Eigenschaftenbereich „Veröffentlichen“, in dem eine Profilzusammenfassung angezeigt wird](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

In den vorherigen Schritten haben Sie Azure-Ressourcen in einer Ressourcengruppe erstellt. Wenn Sie diese Ressourcen in Zukunft nicht mehr benötigen, können Sie sie löschen, indem Sie die Ressourcengruppe löschen.
Klicken Sie im Azure-Portal im Menü auf der linken Seite auf **Ressourcengruppen** und dann auf **myResourceGroup**.
Stellen Sie auf der Seite der Ressourcengruppe sicher, dass die Ressourcen aufgelistet sind, die Sie löschen möchten.
Wählen Sie **Löschen** aus, geben Sie im Textfeld **myResourceGroup** ein, und wählen Sie dann **Löschen** aus.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie gelernt, wie Sie mithilfe von Visual Studio ein Veröffentlichungsprofil für die Bereitstellung in Azure erstellen. Sie können ein Veröffentlichungsprofil auch durch das Importieren von Veröffentlichungseinstellungen über Azure App Service konfigurieren.

> [!div class="nextstepaction"]
> [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in Azure](tutorial-import-publish-settings-azure.md)
