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

## <a name="opening-the-project-creation-dialog"></a>Öffnen des Dialogfelds für die Projekterstellung

Es gibt verschiedene Möglichkeiten, ein neues Projekt in Visual Studio für Mac zu erstellen. Wenn Sie Visual Studio für Mac erstmalig öffnen, wird die Willkommensseite angezeigt. Hier können Sie die Option **Neu** auswählen. Anschließend gelangen Sie zum Bildschirm für die Projekterstellung.

> [!TIP]
> Darüber hinaus können Sie auf der Willkommensseite auch aktuelle Projekte und Projektmappen öffnen und nach ihnen suchen. Sie können auch aktuelle Projekte öffnen, indem Sie in der Menüleiste **Datei > Aktuelle Projektmappen** wählen.

![Willkommensseite mit der Option zum Erstellen eines neuen Projekts](media/first-run-project.png)

Wenn Visual Studio für Mac bereits mit einer geladenen Lösung geöffnet ist, können Sie eine neue Projektmappe erstellen, indem Sie in der Menüleiste **Datei > Neue Projektmappe** auswählen. Wenn Sie auf diese Weise eine neue Projektmappe erstellen, wird die bereits geladene geschlossen.

## <a name="creating-a-new-project-from-a-template"></a>Erstellen eines neuen Projekts aus einer Vorlage

Das Dialogfeld **Neues Projekt** zeigt standardmäßig Ihre zuletzt verwendeten Vorlagen sortiert nach den *zuletzt verwendeten* Vorlagen an.

Wenn Sie keine aktuelle Vorlage verwenden möchten, können Sie eine andere aus den Kategorien auf der linken Seite des Dialogfelds auswählen. Jede Kategorie enthält mehrere Projektvorlagen, aus denen Sie auswählen können. Wenn Sie auf einen Projekttyp klicken, wird auf der rechten Seite des Bildschirms eine Beschreibung angezeigt.

![Bildschirm „Neues Projekt“](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Konfigurieren des neuen Projekts

Nachdem Sie sich für eine Projektvorlage entschieden haben, werden Sie auf den folgenden Bildschirmen durch alle Konfigurationsschritte geführt, die für die Einrichtung des Projekts erforderlich sind; diese können je nach Projekttyp variieren.

Für alle Projekte ist ein neues Projekt sowie ein Speicherort für die Dateien erforderlich. Wenn das Projekt Teil einer neuen Projektmappe ist, wird auch ein Projektmappenname benötigt, anstatt es zu einer bestehenden Projektmappe hinzuzufügen.

Optional können Sie in diesem Schritt auch Optionen für die Git-Quellcodeverwaltung konfigurieren. Das folgende Bild zeigt ein Beispiel für den letzten Konfigurationsschritt für ein .NET Core-Projekt:

![Konfigurieren eines neuen Projekts](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Hinzufügen weiterer Projekte zu einer Projektmappe

Sie können weitere Projekte zu einer Projektmappe hinzufügen, indem Sie mit der rechten Maustaste auf die Projektmappe im Lösungspad klicken und entweder **Hinzufügen > Neues Projekt hinzufügen** oder **Hinzufügen > Vorhandenes Projekt hinzufügen** auswählen.

Wenn Sie ein neues Projekt hinzufügen, werden Sie durch die Erstellung eines neuen Projekts geleitet, wie in [Konfigurieren des neuen Projekts](#configuring-your-new-project) gezeigt.

Wenn Sie ein vorhandenes Projekt hinzufügen möchten, können Sie auf Ihrem Computer nach einem bestehenden Projekt suchen und es der Projektmappe hinzufügen.

## <a name="see-also"></a>Siehe auch

- [Erstellen von Projektmappen und Projekten (Visual Studio unter Windows)](/visualstudio/ide/creating-solutions-and-projects)