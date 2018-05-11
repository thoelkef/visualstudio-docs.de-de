---
title: Veröffentlichen in Azure App Service - Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/22/2017
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
ms.openlocfilehash: c5c172ff3ec3033b50815efdb0b4ee293853ab1e
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Veröffentlichen Sie eine ASP.NET oder ASP.NET Core-app in Azure App Service mithilfe von Visual Studio

Sie können die **veröffentlichen** Tool zum Veröffentlichen von ASP.NET, ASP.NET Core, Python, Node.js und .NET Core-apps in Azure App Service.

Wenn Sie nicht bereits über ein Azure-Konto verfügen, können Sie [registrieren Sie sich hier](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 installiert haben und die **ASP.NET** und **.NET Framework** Entwicklungsaufwand. Für eine .NET Core-app müssen Sie auch die **.NET Core** arbeitsauslastung.

    Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich entweder **ASP.NET-Webanwendung ((.NET Framework)** oder (nur c#) **ASP.NET-Webanwendung für Core**, und klicken Sie dann auf **OK**.

1. Wählen Sie **MVC** (oder wählen Sie **Webanwendung (Model-View-Controller)** für .NET Core), stellen Sie sicher, dass **keine Authentifizierung** ausgewählt ist, und klicken Sie dann auf **OK** .

1. Geben Sie einen Namen wie **MyWebApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

1. Wählen Sie **erstellen > Projektmappe** zum Erstellen des Projekts.

## <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**.

    ![Wählen Sie veröffentlichen](../deployment/media/quickstart-publish-aspnet.png "wählen veröffentlichen")

1. Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil erstellen**.

1. In der **Veröffentlichungsziel auswählen** Dialogfeld Wählen Sie **Anwendungsdienst**.

    ![Wählen Sie die Azure App Service](../deployment/media/quickstart-publish-azure.png "-Azure App Service auswählen")

1. Klicken Sie auf **Veröffentlichen**.

    Die **Anwendungsdienst erstellen** Dialogfeld wird angezeigt.

    ![Erstellen des Anwendungsdienst](../deployment/media/quickstart-publish-settings-app-service.png "-Azure App Service erstellen")
    
1. Wenn Sie in Visual Studio nicht angemeldet sind, melden Sie sich, und klicken Sie dann die app Service-Standardeinstellungen füllen Sie die Felder.

    Das Profil die veröffentlichungseinstellungen ein Dialogfeld geöffnet.

    ![Wählen Sie die Ordner](../deployment/media/quickstart-publish-settings-web.png "Ordner auswählen")

    In diesem Dialogfeld können Sie wählen Sie das Abonnement verwendeten, wählen oder erstellen ein Azure-Ressourcengruppe usw.

1. Klicken Sie auf **Erstellen**.

    Visual Studio die app bereitgestellt wird, um Ihren Azure App Service, und die Web-app in Ihrem Browser lädt.

    In der Zusammenfassung der **veröffentlichen** Bereich finden Sie unter der Website-URL für den neuen Azure-App-Dienst.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie gelernt, wie Sie Visual Studio verwenden, um ein Veröffentlichungsprofil für die Bereitstellung in Azure zu erstellen. Sie können auch eine Veröffentlichung konfigurieren Profil durch Importieren von veröffentlichungseinstellungen aus Azure App Service.

> [!div class="nextstepaction"]
> [Importieren von veröffentlichungseinstellungen und in Azure bereitstellen](tutorial-import-publish-settings-azure.md)
