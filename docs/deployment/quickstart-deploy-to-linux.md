---
title: Veröffentlichen in App Service unter Linux
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 1e05862aa57c24bfa8f17d551762054278dd6e52
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806871"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Veröffentlichen einer ASP.NET Core-App in Azure App Service mit Visual Studio unter Linux

Ab Version 15.7 von Visual Studio 2017 können Sie ASP.NET Core-Apps in Azure App Service Linux (mit Containern) mithilfe einer der folgenden Methoden veröffentlichen.

* Verwenden Sie Azure DevOps mit [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops) für die kontinuierliche (oder automatisierte) Bereitstellung von Apps.

* Verwenden Sie für die einmalige (oder manuelle) Bereitstellung von Apps das Tool zum **Veröffentlichen** in Visual Studio, um ASP.NET Core-Apps in App Service für Linux (mit Containern) zu veröffentlichen.

In diesem Artikel wird beschrieben, wie Sie das Tool zum **Veröffentlichen** für die einmalige Bereitstellung verwenden.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Veröffentlichen in App Service unter Linux

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie in diesem Fall auf **Neues Profil erstellen**.

1. Vergewissern Sie sich im Dialogfeld **Pick a publish target** (Veröffentlichungsziel auswählen), dass **App Service Linux** ausgewählt ist.

    ![Azure App Service auswählen](../deployment/media/quickstart-publish-linux.png "Azure App Service auswählen")

1. Wählen Sie **Veröffentlichen**. Das Dialogfeld **App Service erstellen** wird angezeigt. Melden Sie sich ggf. mit Ihrem Azure-Konto an. Anschließend werden die Felder mit den Standardeinstellungen für App Service aufgefüllt.

    ![App Service erstellen](../deployment/media/quickstart-publish-settings-app-service-linux.png "Azure App Service auswählen")

1. Klicken Sie auf **Erstellen**. Visual Studio stellt die App in Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen. Im Bereich **Veröffentlichen** werden in den Projekteigenschaften die Website-URL und andere Details angezeigt.

    ![Eigenschaftenbereich „Veröffentlichen“, in dem eine Profilzusammenfassung angezeigt wird](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

In den vorherigen Schritten haben Sie Azure-Ressourcen in einer Ressourcengruppe erstellt. Wenn Sie diese Ressourcen in Zukunft nicht mehr benötigen, können Sie sie löschen, indem Sie die Ressourcengruppe löschen.
Klicken Sie im Azure-Portal im Menü auf der linken Seite auf **Ressourcengruppen** und dann auf **myResourceGroup**.
Stellen Sie auf der Seite der Ressourcengruppe sicher, dass die Ressourcen aufgelistet sind, die Sie löschen möchten.
Wählen Sie **Löschen** aus, geben Sie im Textfeld **myResourceGroup** ein, und wählen Sie dann **Löschen** aus.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie erfahren, wie Sie Visual Studio unter Linux verwenden können, um ein Veröffentlichungsprofil für die Bereitstellung in App Service zu erstellen. Möglicherweise benötigen Sie weitere Informationen zum Veröffentlichen mit Azure unter Linux.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
