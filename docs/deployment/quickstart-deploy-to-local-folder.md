---
title: Bereitstellen in einem lokalen Ordner
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781912"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Bereitstellen einer app in einen lokalen Ordner, die mithilfe von Visual Studio

Sie können die **veröffentlichen** Tool zum Veröffentlichen von ASP.NET, ASP.NET Core, .NET Core und Python-apps in einen lokalen Ordner aus Visual Studio. Für Node.js die Schritte werden unterstützt, aber die Benutzeroberfläche unterscheidet sich.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Bereitstellen in einem lokalen Ordner

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie **veröffentlichen** (oder verwenden Sie die **erstellen** > **veröffentlichen** Menüelement).

    ![Der Befehl "Veröffentlichen" auf die im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "veröffentlichen wählen")

1. Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** angezeigt. Wählen Sie **neues Profil erstellen**.

1. In der **Veröffentlichungsziel** Dialogfeld wählen **Ordner**.

    ![Wählen Sie die lokalen Ordner als ein veröffentlichen-Taget](../deployment/media/quickstart-publish-folder.png "Ordner auswählen")

1. Geben Sie einen Pfad ein, oder wählen Sie **Durchsuchen** an einen lokalen Ordner.

1. Wählen Sie **Veröffentlichen**. Visual Studio das Projekt wird erstellt und veröffentlicht es für den angegebenen Ordner. Die Projekteigenschaften **veröffentlichen** Bereich angezeigt wird, ein Profil Zusammenfassung angezeigt.

    ![Veröffentlichen Sie die im Eigenschaftenbereich mit einem Profil Statusübersicht](../deployment/media/quickstart-publish-folder-summary.png)

1. Wählen Sie zum Konfigurieren von bereitstellungseinstellungen **konfigurieren** im Profil für Zusammenfassung, und wählen die **Einstellungen** Registerkarte.

    ![-Profileinstellungen](../deployment/media/quickstart-profile-settings.png "-profileinstellungen")

1. Konfigurieren Sie Optionen wie z. B., ob Debug- oder Releasekonfiguration Konfiguration bereitstellen, und wählen Sie dann **speichern**.

1. Wählen Sie zum erneuten Veröffentlichen **veröffentlichen**.

Stellen Sie die veröffentlichen Dateien in einer beliebigen Weise bereit. Sie können z. B. Verpacken in eine *ZIP* Datei, einen einfachen Kopierbefehl verwenden oder mit jedem Installationspaket Ihrer Wahl bereitstellen.

## <a name="next-steps"></a>Nächste Schritte

- [Bereitstellen einer .NET Core-Anwendung mit dem Tool „Veröffentlichen“](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Packen einer Desktop-App für Microsoft Store (Desktop-Brücke)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Bereitstellen, die .NET Framework und Anwendungen](/dotnet/framework/deployment/)
