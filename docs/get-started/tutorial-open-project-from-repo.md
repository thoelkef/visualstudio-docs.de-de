---
title: 'Tutorial: Öffnen eines Projekts von einem Repository aus'
description: Hier erfahren Sie, wie Sie ein Projekt mithilfe von Visual Studio in einem Git- oder Azure DevOps-Repository öffnen.
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ad609e9cf6a00a1b966e5d63589592239f215b01
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743028"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Tutorial: Öffnen eines Projekts von einem Repository aus

In diesem Tutorial verwenden Sie Visual Studio, um erstmalig eine Verbindung mit einem Repository herzustellen und dann ein Projekt darin zu öffnen.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Öffnen eines Projekts von einem GitHub-Repository aus

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der oberen Menüleiste auf **Datei** > **Öffnen** > **Aus Quellcodeverwaltung öffnen**.

   Der Bereich **Team Explorer – Verbinden** wird geöffnet.

    ![Team Explorer-Fenster in der Visual Studio-IDE](./media/open-proj-repo-team-explorer.png)

1. Wählen Sie im Abschnitt **Lokale Git-Repositorys** die Option **Klonen** aus.

    ![Auswählen von „Klonen“ im Abschnitt „Lokale Git-Repositorys“](./media/open-proj-repo-local-git-repo-clone.png)

1. Geben oder fügen Sie im Feld ***Geben Sie die URL eines zu klonenden Git ein.*** die URL für Ihr Repository ein, und drücken Sie die **EINGABETASTE**. (Melden Sie sich im Falle einer entsprechenden Aufforderung bei GitHub an.)

   Nach dem Klonen Ihres Repositorys durch Visual Studio wird Team Explorer geschlossen und der Projektmappen-Explorer geöffnet. Die Meldung *Klicken Sie oben auf "Projektmappen und Ordner", um eine Liste mit Projektmappen anzuzeigen.* wird angezeigt. Wählen Sie **Projektmappen und Ordner** aus.

   ![Auswählen von „Projektmappen und Ordner“ im Projektmappen-Explorer](./media/open-proj-repo-github-solutions-folders.png)

1. Ist eine Projektmappendatei verfügbar, wird sie im Flyoutmenü „Projektmappen und Ordner“ angezeigt. Wählen Sie sie aus, und Visual Studio öffnet die Projektmappe.

   ![Auswählen des gewünschten Elements in der Dropdownliste des Projektmappen-Explorers](./media/open-proj-repo-github-solutions-folders-picker.png)

   Enthält das Repository keine Projektmappendatei (insbesondere eine SLN-Datei), wird im Flyoutmenü „Keine Projektmappen gefunden.“ angezeigt. Sie können im Ordnermenü jedoch auf eine beliebige Datei doppelklicken, um sie im Visual Studio-Code-Editor zu öffnen.

### <a name="review-your-work"></a>Überprüfen Ihrer Arbeit

Sehen Sie sich die folgende Animation an, um Ihre Arbeit zu überprüfen, die Sie im Rahmen des vorherigen Abschnitts verrichtet haben.

   ![Animation zum Öffnen eines Projekts in einem GitHub-Repository mithilfe von Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie im Startfenster **Code klonen oder auschecken** aus.

   ![Fenster „Neues Projekt erstellen“ anzeigen](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Geben Sie den Repositoryspeicherort ein, und klicken Sie dann auf **Klonen**.

   ![Ansicht des Fensters „Code klonen oder auschecken“](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio öffnet das Projekt aus dem Repository.

1. Ist eine Projektmappendatei verfügbar, wird sie im Flyoutmenü „Projektmappen und Ordner“ angezeigt. Wählen Sie sie aus, und Visual Studio öffnet die Projektmappe.

   ![Auswählen des gewünschten Elements in der Dropdownliste des Projektmappen-Explorers](./media/open-proj-repo-github-solutions-folders-picker.png)

   Enthält das Repository keine Projektmappendatei (insbesondere eine SLN-Datei), wird im Flyoutmenü „Keine Projektmappen gefunden.“ angezeigt. Sie können im Ordnermenü jedoch auf eine beliebige Datei doppelklicken, um sie im Visual Studio-Code-Editor zu öffnen.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Öffnen eines Projekts von einem Azure DevOps-Repository aus

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der oberen Menüleiste auf **Datei** > **Öffnen** > **Aus Quellcodeverwaltung öffnen**.

   Der Bereich **Team Explorer – Verbinden** wird geöffnet.

    ![Team Explorer-Fenster in der Visual Studio-IDE](./media/open-proj-repo-team-explorer.png)

1. Es gibt zwei Möglichkeiten zum Herstellen einer Verbindung mit dem Azure DevOps-Repository:

      - Wählen Sie im Abschnitt **Anbieter für gehostete Dienste** die Option **Verbinden...** aus.

        ![Abschnitt „Anbieter für gehostete Dienste“ im Team Explorer-Fenster in der Visual Studio-IDE](./media/open-proj-repo-azure-devops.png)

      - Wählen Sie in der Dropdownliste **Verbindungen verwalten** die Option **Verbindung mit einem Projekt herstellen...** aus.

        ![Abschnitt „Verbindungen verwalten“ im Team Explorer-Fenster in der Visual Studio-IDE](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Wählen Sie im Dialogfeld **Verbindung mit einem Projekt herstellen** das Repository, mit dem Sie eine Verbindung herstellen möchten, und anschließend die Option **Klonen** aus.

      ![Dialogfeld „Verbindung mit einem Projekt herstellen“ in Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Die im Listenfeld angezeigten Elemente hängen von den Azure DevOps-Repositorys ab, auf die Sie Zugriff haben.

1. Nach dem Klonen Ihres Repositorys durch Visual Studio wird Team Explorer geschlossen und der Projektmappen-Explorer geöffnet. Die Meldung *Klicken Sie oben auf "Projektmappen und Ordner", um eine Liste mit Projektmappen anzuzeigen.* wird angezeigt. Wählen Sie **Projektmappen und Ordner** aus.

      ![Benachrichtigung „Projektmappen und Ordner“ im Team Explorer in Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Eine Projektmappendatei (insbesondere eine SLN-Datei) wird im Flyoutmenü „Projektmappen und Ordner“ angezeigt. Wählen Sie sie aus, und Visual Studio öffnet die Projektmappe.

   Enthält das Repository keine Projektmappendatei, wird im Flyoutmenü „Keine Projektmappen gefunden.“ angezeigt. Sie können im Ordnermenü jedoch auf eine beliebige Datei doppelklicken, um sie im Visual Studio-Code-Editor zu öffnen.

::: moniker-end

::: moniker range="vs-2019"

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie im Startfenster **Code klonen oder auschecken** aus.

   ![Fenster „Neues Projekt erstellen“ anzeigen](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Klicken Sie im Abschnitt **Repository durchsuchen** auf **Azure DevOps**.

   ![Ansicht des Fensters „Code klonen oder auschecken“](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Melden Sie sich mit Ihrem Konto an, wenn ein Anmeldefenster angezeigt wird.

1. Wählen Sie im Dialogfeld **Verbindung mit einem Projekt herstellen** das Repository, mit dem Sie eine Verbindung herstellen möchten, und anschließend die Option **Klonen** aus.

      ![Dialogfeld „Verbindung mit einem Projekt herstellen“ in Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Die im Listenfeld angezeigten Elemente hängen von den Azure DevOps-Repositorys ab, auf die Sie Zugriff haben.

   Nach Abschluss des Klonvorgangs öffnet Visual Studio den **Team Explorer** und eine Benachrichtigung wird angezeigt.

     ![Das Team Explorer-Fenster in Visual Studio nach dem Klonvorgang](./media/vs-2019/clone-complete-azure-devops.png)

1. Klicken Sie auf den Link **Ordneransicht anzeigen**, um Ihre Ordner und Dateien anzuzeigen.

     ![Der Abschnitt „Projektmappen“ des Team Explorer-Fensters in Visual Studio nach dem Klonvorgang](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio öffnet den **Projektmappen-Explorer**.

1. Klicken Sie auf den Link **Projektmappen und Ordner**, um nach einer zu öffnenden Projektmappendatei (eine SLN-Datei) zu suchen.

      ![Benachrichtigung „Projektmappen und Ordner“ im Team Explorer in Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Wenn Ihr Repository keine Projektmappendatei enthält, wird die Meldung „Keine Projektmappen gefunden“ angezeigt. Sie können im Ordnermenü jedoch auf eine beliebige Datei doppelklicken, um sie im Visual Studio-Code-Editor zu öffnen.

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie mit dem Codieren mit Visual Studio loslegen möchten, können Sie sich die ausführlichen Informationen in einem der folgenden sprachspezifischen Tutorials ansehen:

- [Visual Studio-Tutorials | **C#**](./csharp/index.yml)
- [Visual Studio-Tutorials | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio | **Python**](../python/index.yml)
- [Visual Studio | **JavaScript**, **TypeScript** und **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Siehe auch

- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services: Erste Schritte mit Azure Repos und Visual Studio)
- [Microsoft Learn: Get started with Azure DevOps](/learn/modules/get-started-with-devops/) (Microsoft Learn: Erste Schritte mit Azure DevOps)