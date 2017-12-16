---
title: Bereitstellen in einen lokalen Ordner - Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c8696e7ffb4120bae12538a03b77d62c0d091a7
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Bereitstellen einer Web-app oder .NET Core-app in einen lokalen Ordner mit dem Visual Studio Publish-tool

Sie können die **veröffentlichen** Tool zum Veröffentlichen der app in einen lokalen Ordner. 

Diese Schritte gelten für ASP.NET, ASP.NET Core .NET Core und Python-apps in Visual Studio. Für Node.js die Schritte werden unterstützt, aber die Benutzeroberfläche unterscheidet sich.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Wählen Sie in Visual Studio **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **.NET Core**, und wählen Sie dann im mittleren Bereich **Konsolen-App (.NET Core)**.

1. Geben Sie einen Namen wie **MyLocalApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt das Projekt.

## <a name="deploy-to-a-local-folder"></a>Bereitstellen Sie auf einem lokalen Ordner

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Projekts, und wählen Sie **veröffentlichen**.

    ![Wählen Sie veröffentlichen](../deployment/media/quickstart-publish.png "wählen veröffentlichen")

1. In der **veröffentlichen** Bereich auswählen **Ordner**.

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

- [Bereitstellen einer .NET Core-Anwendung mit dem Tool veröffentlichen](https://docs.microsoft.com/en-us/dotnet/core/deploying/deploy-with-vs)
- [Verpacken einer desktop-app für Microsoft Store (Desktop Bridge)](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (.NET) [Bereitstellen von .NET Framework und Anwendungen](https://docs.microsoft.com/en-us/dotnet/framework/deployment/)
