---
title: Erstellen neuer Projekte und Projektmappen
description: In diesem Artikel erfahren Sie, wie Sie Projekte und Projektmappen in Visual Studio für Mac erstellen können.
author: conceptdev
ms.author: crdun
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 045d92365501b888e56ce4ae397331e597b5b33a
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820741"
---
# <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts

## <a name="opening-the-project-creation-dialog"></a>Öffnen das Dialogfeld für die Projekterstellung

Es gibt einige Möglichkeiten zum Erstellen eines neuen Projekts in Visual Studio für Mac. Wenn Sie zuerst Visual Studio für Mac öffnen, wird die Willkommensseite angezeigt. Von hier aus können Sie **neu** Dadurch gelangen Sie auf dem Bildschirm "Projekt erstellen".

> [!TIP]
> Darüber hinaus auf der Willkommensseite, können Sie auch öffnen, und suchen Sie nach "," Zuletzt geöffnete Projekte und Projektmappen. Sie können die zuletzt geöffnete Projekte auch öffnen, indem Sie auf der Menüleiste und Auswahl **Datei > neue Lösungen**

![Bildschirm "Willkommen" mit neues Projekt erstellen](media/first-run-project.png)

Wenn Visual Studio für Mac Laden Sie eine Projektmappe bereits geöffnet ist, können Sie eine neue Projektmappe erstellen, indem Sie auf der Menüleiste und Auswahl **Datei > neue Projektmappe**. Erstellen einer neuen Lösung auf diese Weise wird die Projektmappe geschlossen werden, die bereits geladen ist.

## <a name="creating-a-new-project-from-a-template"></a>Erstellen eines neuen Projekts aus einer Vorlage

Die **neues Projekt** Dialogfeld, in der Standardeinstellung zeigt Ihre zuletzt verwendeten Vorlagen, sortiert nach *zuletzt verwendeten*.

Wenn Sie nicht, eine aktuelle Vorlage verwenden möchten, können Sie aus den Kategorien auf der linken Seite des Dialogfelds auswählen. Jede Kategorie enthält mehrere Projektvorlagen für die Sie auswählen. Durch Klicken auf einen Projekttyp klicken, können Sie eine Beschreibung auf der rechten Seite des Bildschirms angezeigt.

![Bildschirm "Neues Projekt"](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Konfigurieren das neue Projekt

Nachdem Sie eine Projektvorlage ausgewählt haben, dauert die folgenden Bildschirmen über alle erforderlichen Konfigurationsschritte zum Einrichten des Projekts; Dies kann eine hängt vom Projekttyp ab.

Alle Projekte erfordern ein neues Projekt sowie einen Speicherort zum Speichern der Dateien. Wenn das Projekt ist Teil einer neuen Lösung, anstatt zu einer vorhandenen Projektmappe hinzufügen, ein Lösungsnamen werden ebenfalls erforderlich.

In dieser Phase können Sie optional auch Quellcodeverwaltungsoptionen für Git konfigurieren. Die folgende Abbildung zeigt ein Beispiel der letzte Konfigurationsschritt für ein .NET Core-Projekt:

![Konfigurieren eines neuen Projekts](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Zusätzliche Projekte hinzufügen zu einer Projektmappe

Sie können zusätzliche Projekte zu einer Projektmappe hinzufügen, indem mit der rechten Maustaste in der Projektmappe im Projektmappenpad, und wählen entweder **hinzufügen > Neues Projekt hinzufügen** oder **hinzufügen > vorhandenes Projekt hinzufügen**.

Hinzufügen eines neuen Projekts führen Sie durch die projekterstellung, siehe [Konfigurieren des neuen Projekts](#configuring-your-new-project).

Wählen ein vorhandenes Projekt hinzufügen, können Sie für ein vorhandenes Projekt auf Ihrem Computer navigieren, und fügen sie der Projektmappe hinzu.

## <a name="see-also"></a>Siehe auch

- [Erstellen von Projektmappen und Projekten (Visual Studio unter Windows)](/visualstudio/ide/creating-solutions-and-projects)