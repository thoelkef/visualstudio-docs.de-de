---
title: 'Tutorial: Öffnen eines Projekts von einem Repository aus'
description: Hier erfahren Sie, wie Sie ein Projekt mithilfe von Visual Studio in einem Git- oder Azure DevOps-Repository öffnen.
ms.custom: get-started
ms.date: 03/13/2019
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
ms.openlocfilehash: f017e0ef3d7b76ba4d5de18ecab614f030b07501
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070073"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Tutorial: Öffnen eines Projekts von einem Repository aus

In diesem Tutorial verwenden Sie Visual Studio, um erstmalig eine Verbindung mit einem Repository herzustellen und dann ein Projekt darin zu öffnen.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) kostenlos herunterladen.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Öffnen eines Projekts von einem GitHub-Repository aus

1. Öffnen Sie Visual Studio 2017.

1. Wählen Sie auf der oberen Menüleiste **Datei** > **Öffnen** > **Aus Quellcodeverwaltung öffnen** aus.

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

## <a name="open-a-project-from-an-azure-devops-repo"></a>Öffnen eines Projekts von einem Azure DevOps-Repository aus

1. Öffnen Sie Visual Studio 2017.

1. Wählen Sie auf der oberen Menüleiste **Datei** > **Öffnen** > **Aus Quellcodeverwaltung öffnen** aus.

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
  
## <a name="next-steps"></a>Nächste Schritte

Wenn Sie mit dem Codieren mit Visual Studio loslegen möchten, können Sie sich die ausführlichen Informationen in einem der folgenden sprachspezifischen Tutorials ansehen:

- [Visual Studio-Tutorials | **C#**](./csharp/index.yml)
- [Visual Studio-Tutorials | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio | **C++**](/cpp/get-started/)
- [Visual Studio | **Python**](/visualstudio/python/)
- [Visual Studio | **JavaScript**, **TypeScript** und **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Siehe auch

- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services: Erste Schritte mit Azure Repos und Visual Studio)
- [Microsoft Learn: Get started with Azure DevOps](/learn/modules/get-started-with-devops/) (Microsoft Learn: Erste Schritte mit Azure DevOps)