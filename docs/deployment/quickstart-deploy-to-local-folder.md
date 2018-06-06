---
title: Bereitstellen in einen lokalen Ordner - Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 05/08/2018
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
ms.openlocfilehash: 016538bded47a5186294c161cc7f310b26818d15
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764218"
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Bereitstellen einer Web-app oder .NET Core-app in einen lokalen Ordner mit dem Visual Studio Publish-tool

Sie können die **veröffentlichen** Tool zum Veröffentlichen der app in einen lokalen Ordner. 

Diese Schritte gelten für ASP.NET, ASP.NET Core .NET Core und Python-apps in Visual Studio. Für Node.js die Schritte werden unterstützt, aber die Benutzeroberfläche unterscheidet sich.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 installiert haben und die. **NET Desktopentwicklung** Arbeitslast und die. **NET Core** arbeitsauslastung.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **.NET Core**, und wählen Sie dann im mittleren Bereich **Konsolen-App (.NET Core)**.

1. Geben Sie einen Namen wie **MyLocalApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

## <a name="deploy-to-a-local-folder"></a>Bereitstellen in einem lokalen Ordner

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**.

    ![Wählen Sie veröffentlichen](../deployment/media/quickstart-publish.png "wählen veröffentlichen")

1. Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil erstellen**.

1. In der **Veröffentlichungsziel auswählen** Dialogfeld Wählen Sie **Ordner**.

    ![Wählen Sie die Ordner](../deployment/media/quickstart-publish-folder.png "Ordner auswählen")

1. Geben Sie einen Pfad, oder klicken Sie auf **Durchsuchen** , um einen lokalen Ordner zu suchen.

1. Klicken Sie auf **Veröffentlichen**.

    Visual Studio das Projekt erstellt und veröffentlicht sie in den angegebenen Ordner.

    Klicken Sie im Bereich veröffentlichen wird einem Profil.

1. Klicken Sie zum Konfigurieren von bereitstellungseinstellungen auf **Einstellungen** im Profil Zusammenfassung.

    ![Einstellungen für Profil](../deployment/media/quickstart-profile-settings.png "Einstellungen Profil") 

1. Optionen konfigurieren, beispielsweise, ob eine Debug- oder Releasekonfiguration Konfiguration bereitzustellen, und klicken Sie dann auf **speichern**.

1. Um erneut zu veröffentlichen, klicken Sie auf **veröffentlichen**.

Stellen Sie die veröffentlichen Dateien in einer beliebigen Weise bereit. Sie können z. B. in einer Zipdatei Verpacken, verwenden Sie einen Befehl einfaches Kopieren oder alle Installationspaket Ihrer Wahl bereitstellen.

## <a name="next-steps"></a>Nächste Schritte

- [Bereitstellen einer .NET Core-Anwendung mit dem Tool „Veröffentlichen“](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Packen einer Desktop-App für Microsoft Store (Desktop-Brücke)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Bereitstellen von .NET Framework und Anwendungen...](/dotnet/framework/deployment/)
