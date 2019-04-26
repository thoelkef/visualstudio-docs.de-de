---
title: Festlegen mehrerer Startprojekte in Visual Studio für Mac
description: In diesem Artikel wird beschrieben, wie Sie festlegen, dass mehrere Projekte beim Ausführen oder Debuggen gestartet werden.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: a4a4f2f4fd4ce6cd88d11979a21e4e9184adfca8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988469"
---
# <a name="how-to-set-multiple-startup-projects"></a>Vorgehensweise: Festlegen mehrerer Startprojekte

In Visual Studio für Mac können Sie festlegen, ob mehr als ein Projekt beim Debuggen oder Ausführen der Projektmappe gestartet werden soll.

## <a name="to-set-multiple-startup-projects"></a>So legen Sie mehrere Startprojekte fest

1. Klicken Sie im **Lösungspad** auf die entsprechende Projektmappe (der oberste Knoten).

2. Öffnen Sie das Kontextmenü des Projektmappenknotens (Rechtsklick), und klicken Sie anschließend auf **Startprojekte festlegen...**.

   ![„Startprojekte festlegen...“ im Kontextmenü](media/startup-proj-ctx-menu.png)

3. Das Dialogfeld **Laufzeitkonfiguration für Projektmappe erstellen** wird angezeigt. Über dieses Dialogfeld wird eine neue Laufzeitkonfiguration für die Projektmappe erstellt. Sie können diese beliebig benennen. Der Standardname ist `Multiple Projects`.

   ![Dialogfeld „Laufzeitkonfiguration für Projektmappe erstellen“](media/create-sln-run-config.png)

4. Klicken Sie auf **Laufzeitkonfiguration erstellen**. Das Dialogfeld **Projektmappenoptionen** wird geöffnet. Hierbei ist die neue Laufzeitkonfiguration für die Projektmappe ausgewählt.

   ![Dialogfeld „Projektmappenoptionen“](media/sln-options-run-config-multi-projects.png)

5. Wählen Sie die Projekte aus, die Sie beim Debuggen oder Ausführen Ihrer Anwendung über Visual Studio für Mac starten möchten.

   ![Dialogfeld „Projektmappenoptionen“ mit konfigurierter Laufzeitkonfiguration](media/sln-options-run-config-multi-projects-configured.png)

6. Klicken Sie auf **OK**. Das Dialogfeld wird geschlossen, und die neue Laufzeitkonfiguration für die Projektmappe wird als aktive Laufzeitkonfiguration festgelegt.

   ![Projektmappe mit mehreren Projekten, die beim Debuggen oder Ausführen gestartet werden sollen](media/startup-project-configured.png) Sie werden feststellen, dass zwei Projekte für den Start konfiguriert wurden, da beide Projekte im **Lösungspad** **fettgedruckt** dargestellt werden. In der Symbolleiste wurde die neue Laufzeitkonfiguration als aktuelle Laufzeitkonfiguration für die Projektmappe konfiguriert.

## <a name="next-steps"></a>Nächste Schritte

- [Kompilieren und Generieren in Visual Studio für Mac](compiling-and-building.md)
- [Grundlagen der Buildkonfiguration](configurations.md)