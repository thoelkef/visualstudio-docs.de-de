---
title: Bereitstellen in einem lokalen Ordner
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 800059dc8d5a3e6ccfb72c588fbb61423a338cba
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036391"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Bereitstellen einer App in einem Ordner mithilfe von Visual Studio

Sie können das Tool zum **Veröffentlichen** verwenden, um ASP.NET-, ASP.NET Core-, .NET Core- und Python-Apps über Visual Studio in einem Ordner zu veröffentlichen. Für Node.js können Sie zwar gleichen Schritte ausführen, jedoch ist die Benutzeroberfläche anders.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Wenn Sie eine Windows-Desktopanwendung für einen Ordner veröffentlichen müssen, sehen Sie sich den Artikel [Bereitstellen einer Desktopanwendung mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# oder Visual Basic) an. Informationen zu C++/CLR finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), und Informationen zu C/C++ finden Sie unter [Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Bereitstellen in einem lokalen Ordner

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird das Fenster **Veröffentlichen** angezeigt. Wählen Sie **Neu**aus.

1. Wählen Sie im Fenster **Veröffentlichen** die Option **Ordner** aus.

    ![Auswählen eines Ordners als Veröffentlichungsziel](../deployment/media/quickstart-publish-folder-new.png "Auswählen eines Ordners")

1. Geben Sie einen Pfad ein, oder klicken Sie auf **Durchsuchen**, um einen Ordner anzugeben.

    ![Angeben des Pfads zum Ordner](../deployment/media/quickstart-publish-folder-path.png "Auswählen eines Ordners")

1. Wählen Sie **Veröffentlichen**. Dann erstellt Visual Studio das Projekt und veröffentlicht es im angegebenen Ordner. Anschließend wird der Bereich **Veröffentlichen** mit einer Profilübersicht angezeigt.

    ![Bereich „Veröffentlichen“ in den Projekteigenschaften mit einer Profilzusammenfassung](../deployment/media/quickstart-publish-folder-summary.png)

1. Wenn Sie Bereitstellungseinstellungen konfigurieren möchten, klicken Sie in der Zusammenfassung des Veröffentlichungsprofils zuerst auf **Bearbeiten** und dann auf die Registerkarte **Einstellungen**.

   Welche Einstellungen Sie sehen, hängt von Ihrem Anwendungstyp ab. Die folgende Abbildung enthält Beispieleinstellungen für eine ASP.NET Core-App.

    ![Profileinstellungen](../deployment/media/quickstart-profile-settings.png "Profileinstellungen")

    Weitere Hilfe zum Auswählen der Einstellungen in .NET finden Sie in den folgenden Themen:

    - [Übersicht über die .NET Core-Anwendungsveröffentlichung](/dotnet/core/deploying/)
    - [.NET Core-RID-Katalog](/dotnet/core/rid-catalog)
    - [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)

1. Konfigurieren Sie die Optionen, und legen Sie z.B. fest, ob eine Debug- oder Releasekonfiguration bereitgestellt werden soll, und klicken Sie anschließend auf **Speichern**.

1. Wenn Sie erneut eine Veröffentlichung durchführen möchten, klicken Sie auf **Veröffentlichen**.

Stellen Sie die veröffentlichen Dateien in einer beliebigen Weise bereit. Sie können sie z.B. in ein *ZIP*-Datei packen, einen einfachen Kopierbefehl verwenden, oder sie mit einem Installationspaket Ihrer Wahl bereitstellen.

## <a name="next-steps"></a>Nächste Schritte

Für .NET-Apps:

- [Bereitstellen einer .NET Core-Anwendung mit dem Tool „Veröffentlichen“](/dotnet/core/deploying/deploy-with-vs)
- [Übersicht über die .NET Core-Anwendungsveröffentlichung](/dotnet/core/deploying/)
- [Bereitstellen von .NET Framework und Anwendungen](/dotnet/framework/deployment/)
