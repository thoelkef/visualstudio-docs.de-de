---
title: Veröffentlichen in einem Ordner – Visual Studio für Mac
ms.date: 01/22/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac-dev15
ms.openlocfilehash: a71b873a2c853d5b90aea2853d73eb1fe8f6abb6
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55089471"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>Veröffentlichen einer Web-App in einem Ordner mithilfe von Visual Studio für Mac

Sie können das Tool zum Veröffentlichen verwenden, um ASP.NET Core-Apps in einem Ordner zu veröffentlichen.

## <a name="prerequisites"></a>Erforderliche Komponenten

 - [Visual Studio 2017 für Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs4mac2017) installiert mit aktiviertem ASP.NET Core.
 - Ein ASP.NET Core-Projekt. Wenn Sie noch kein Projekt haben, können Sie [ein neues Projekt erstellen](https://docs.microsoft.com/visualstudio/mac/create-new-projects?view=vsmac-2017).

## <a name="publish-to-folder"></a>In Ordner veröffentlichen

Mit Visual Studio für Mac können Sie Ihre ASP.NET Core-Projekte mithilfe des Tools zum Veröffentlichen in einem Ordner veröffentlichen. Nachdem Sie Dateien in einem Ordner veröffentlicht haben, können Sie diese auf Ihren Webserver und somit in eine andere Umgebung verschieben. Wenn Sie eine Veröffentlichung in einem Ordner vornehmen möchten, befolgen Sie die folgenden Schritte:

 1. Klicken Sie im Lösungspad mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**.

    ![Kontextmenü „Veröffentlichen“](media/publish-context-menu.png)

 2. Wenn Sie dieses Projekt bereits veröffentlicht haben, sehen Sie im Menü das Veröffentlichungsprofil. Wählen Sie das Veröffentlichungsprofil aus, um den Veröffentlichungsprozess zu starten.

 3. Wenn Sie das Projekt zum ersten Mal in einem Ordner veröffentlichen möchten, klicken Sie auf **In Ordner veröffentlichen**.

    ![Kontextmenü „In Ordner veröffentlichen“](media/publish-to-folder-context-menu.png)

 4. Das Dialogfeld **In Ordner veröffentlichen** wird angezeigt. In diesem Dialogfeld können Sie den Ordner anpassen, in dem das Projekt veröffentlicht wird. Verwenden Sie dazu die Schaltfläche **Durchsuchen**, oder fügen Sie einen Pfad ein.

 5. Nachdem Sie auf **Veröffentlichen** geklickt haben, geschehen die folgenden Dinge: Zuerst wird ein Veröffentlichungsprofil erstellt. Ein Veröffentlichungsprofil ist eine MSBuild-Datei, die während des Veröffentlichungsprozesses in das Projekt importiert wird. Darin sind die Eigenschaften enthalten, die während des Veröffentlichungsprozesses verwendet werden. Diese Dateien werden in `Properties/PublishProfiles` gespeichert und haben die Erweiterung `.pubxml`. Dann wird der Veröffentlichungsprozess gestartet. Sie können den Fortschritt in der Statusleiste in Visual Studio für Mac überwachen.

    ![IDE-Statusleiste mit Status „Veröffentlichen“](media/publish-to-folder-status-bar.png)

 6. Sobald der Veröffentlichungsvorgang erfolgreich abgeschlossen wurde, wird ein Suchfenster für den Veröffentlichungsordner geöffnet. Nachdem nun ein Veröffentlichungsprofil erstellt wurde, wird es im Kontextmenü „Veröffentlichen“ angezeigt.

    ![Kontextmenü „Veröffentlichen“ mit Ordnerprofil](media/publish-context-menu-with-folder-profile.png)

 7. Wenn Sie das Projekt noch einmal mit den selben Einstellungen veröffentlichen möchten, klicken Sie im Kontextmenü „Veröffentlichen“ auf das Profil.

## <a name="customize-publish-options"></a>Anpassen der Veröffentlichungsoptionen

Wenn Sie den Namen des Veröffentlichungsprofils ändern möchten (dieses wird im Kontextmenü „Veröffentlichen“ angezeigt), können Sie die Veröffentlichungsprofildatei umbenennen. Achten Sie darauf, nicht die Erweiterung der Datei zu ändern (`.puxbml`).

Wenn Sie den Pfad des Veröffentlichungsordner ändern möchten, öffnen Sie das Veröffentlichungsprofil, und bearbeiten Sie den Wert `publishUrl`.

Wenn Sie die verwendete Buildkonfiguration ändern möchten, ändern Sie die Eigenschaft `LastUsedBuildConfiguration` im Veröffentlichungsprofil.