---
title: Veröffentlichen in Azure App Service
ms.date: 06/22/2018
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 3bad335fe9781cbd039f17a1a78c51bfa63775d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970642"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Veröffentlichen einer Web-App in Azure App Service mit Visual Studio

Sie können mit dem Tool **Veröffentlichen** in Azure App Service oder Azure App Service Linux (mit Containern) ASP.NET-, ASP.NET Core-, Node.js- und .NET Core-Apps veröffentlichen. Führen Sie für Python-Apps die Schritte unter [Python – Veröffentlichen in Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) aus.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "Auswahl der Option „Veröffentlichen“")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie in diesem Fall auf **Neues Profil erstellen**.

1. Wählen Sie im Dialogfeld **Veröffentlichungsziel auswählen** den Eintrag **App Service** aus.

    ![Auswahl von Azure App Service](../deployment/media/quickstart-publish-azure.png "Choose Azure App Service")

1. Wählen Sie **Veröffentlichen**. Das Dialogfeld **App Service erstellen** wird angezeigt. Melden Sie sich ggf. mit Ihrem Azure-Konto an. Anschließend werden die Felder mit den Standardeinstellungen für App Service aufgefüllt.

    ![App Service erstellen](../deployment/media/quickstart-publish-settings-app-service.png "Azure App Service erstellen")

1. Wählen Sie **Erstellen** aus. Visual Studio stellt die App in Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen. Im Bereich **Veröffentlichen** werden in den Projekteigenschaften die Website-URL und andere Details angezeigt.

    ![Bereich „Veröffentlichen“ in den Projekteigenschaften mit einer Profilzusammenfassung](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

In den vorherigen Schritten haben Sie bereits in einer Ressourcengruppe Azure-Ressourcen erstellt. Wenn Sie sich sicher sind, dass Sie diese Ressourcen in Zukunft nicht mehr benötigen, können Sie sie löschen, indem Sie die Ressourcengruppe entfernen.
Wählen Sie links im Azure-Portal **Ressourcengruppen** und anschließend **myResourceGroup** aus.
Vergewissern Sie sich, dass es sich bei den auf der Seite „Ressourcengruppe“ aufgeführten Ressourcen wirklich um die Ressourcen handelt, die gelöscht werden sollen.
Klicken Sie auf **Löschen**, geben Sie **myResourceGroup** in das Textfeld ein, und klicken Sie anschließend erneut auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie gelernt, wie Sie mithilfe von Visual Studio ein Veröffentlichungsprofil für die Bereitstellung in Azure erstellen. Sie können ein Veröffentlichungsprofil auch durch das Importieren von Veröffentlichungseinstellungen über Azure App Service konfigurieren.

> [!div class="nextstepaction"]
> [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in Azure](tutorial-import-publish-settings-azure.md)
