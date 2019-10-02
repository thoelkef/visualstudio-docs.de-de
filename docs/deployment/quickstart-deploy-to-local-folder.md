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
ms.openlocfilehash: 862310c8c763ce366798bfacd4f4759d606bb33c
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128213"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Bereitstellen einer App in einem lokalen Ordner mithilfe von Visual Studio

Sie können das Tool zum **Veröffentlichen** verwenden, um ASP.NET-, ASP.NET Core-, .NET Core- und Python-Apps über Visual Studio in einem lokalen Ordner zu veröffentlichen. Für Node.js können Sie zwar gleichen Schritte ausführen, jedoch ist die Benutzeroberfläche anders.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Wenn Sie eine Windows-Desktopanwendung für einen lokalen Ordner veröffentlichen müssen, sehen Sie sich den Artikel [Bereitstellen einer Desktopanwendung mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# oder Visual Basic) an. Informationen zu C++/CLI finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), und Informationen zu C/C++ finden Sie unter [Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Bereitstellen in einem lokalen Ordner

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "Auswahl der Option „Veröffentlichen“")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie auf **Neues Profil erstellen**.

1. Vergewissern Sie sich im Dialogfeld **Pick a publish target** (Veröffentlichungsziel auswählen), dass **Ordner** ausgewählt ist.

    ![Lokalen Ordner als Veröffentlichungsziel auswählen](../deployment/media/quickstart-publish-folder.png "Ordner auswählen")

1. Geben Sie einen Pfad ein, oder klicken Sie auf **Durchsuchen**, um einen lokalen Ordner anzugeben.

1. Wählen Sie **Veröffentlichen**. Dann erstellt Visual Studio das Projekt und veröffentlicht es im angegebenen Ordner. Anschließend wird der Bereich **Veröffentlichen** mit einer Profilübersicht angezeigt.

    ![Eigenschaftenbereich „Veröffentlichen“, in dem eine Profilzusammenfassung angezeigt wird](../deployment/media/quickstart-publish-folder-summary.png)

1. Wenn Sie Bereitstellungseinstellungen konfigurieren möchten, klicken Sie in der Profilübersicht erst auf **Konfigurieren** und anschließend auf die Registerkarte **Einstellungen**.

    ![Profileinstellungen](../deployment/media/quickstart-profile-settings.png "Profile settings")

1. Konfigurieren Sie die Optionen, und legen Sie z.B. fest, ob eine Debug- oder Releasekonfiguration bereitgestellt werden soll, und klicken Sie anschließend auf **Speichern**.

1. Wenn Sie erneut eine Veröffentlichung durchführen möchten, klicken Sie auf **Veröffentlichen**.

Stellen Sie die veröffentlichen Dateien in einer beliebigen Weise bereit. Sie können sie z.B. in ein *ZIP*-Datei packen, einen einfachen Kopierbefehl verwenden, oder sie mit einem Installationspaket Ihrer Wahl bereitstellen.

## <a name="next-steps"></a>Nächste Schritte

- [Bereitstellen einer .NET Core-Anwendung mit dem Tool „Veröffentlichen“](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Packen einer Desktop-App für Microsoft Store (Desktop-Brücke)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Bereitstellen von .NET Framework und Anwendungen](/dotnet/framework/deployment/)
