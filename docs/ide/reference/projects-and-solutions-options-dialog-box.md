---
title: Projekte und Projektmappen, Dialogfeld "Optionen"
ms.date: 07/14/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad43a125074240cb6dfb3c8f2c40750b803ac322
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "57867812"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>Projekte und Projektmappen, Dialogfeld „Optionen“

Legt das Visual Studio-Verhalten im Zusammenhang mit Projekten und Projektmappen fest. Klicken Sie zum Zugriff auf diese Optionen auf **Extras** > **Optionen**, erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.

Die Standardpfade für Projekt- und Vorlagenordner werden über die Registerkarte **Speicherorte** im gleichen Dialogfeld festgelegt.

## <a name="general-page"></a>Seite „Allgemein“

Die folgenden Optionen sind auf der Seite **Allgemein** verfügbar.

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>Fehlerliste bei Buildfertigstellung mit Fehlern immer anzeigen

Öffnet das Fenster **Fehlerliste** nachdem der Build fertig gestellt ist nur dann, wenn ein Projekt nicht erstellt werden konnte. Hier werden während des Buildvorgangs aufgetretene Fehler angezeigt. Wenn diese Option deaktiviert ist, treten die Fehler weiterhin auf, aber das Fenster wird nicht geöffnet, wenn der Build abgeschlossen ist. Diese Option ist standardmäßig aktiviert.

### <a name="track-active-item-in-solution-explorer"></a>Aktives Element im Projektmappen-Explorer überwachen

Bei Auswahl dieser Option wird der **Projektmappen-Explorer** automatisch geöffnet, und das aktive Element ist ausgewählt. Das ausgewählte Element ändert sich beim Arbeiten mit unterschiedlichen Dateien in einem Projekt oder einer Projektmappe bzw. mit verschiedenen Komponenten in einem Designer. Wenn diese Option deaktiviert ist, ändert sich die Auswahl im **Projektmappen-Explorer** nicht automatisch. Diese Option ist standardmäßig aktiviert.

### <a name="show-advanced-build-configurations"></a>Erweiterte Buildkonfigurationen anzeigen

Wenn diese Option ausgewählt ist, werden die Optionen für die Buildkonfiguration im Dialogfeld **Projekt-Eigenschaftenseiten** und im Dialogfeld **Projektmappen-Eigenschaftenseiten** angezeigt. Wenn diese Option deaktiviert ist, werden die Optionen für die Buildkonfiguration nicht im Dialogfeld **Projekt-Eigenschaftenseiten** und **Projektmappen-Eigenschaftenseiten** für Visual Basic- und C#-Projekte angezeigt, die eine Konfiguration oder beide Konfigurationen (Debug und Release) enthalten. Wenn ein Projekt eine benutzerdefinierte Konfiguration hat, werden die Optionen für die Buildkonfiguration angezeigt.

Wenn diese Option deaktiviert ist, werden die Befehle im Menü **Erstellen**, z.B. **Projektmappe erstellen**, **Projektmappe neu erstellen** und **Projektmappe bereinigen**, für die Releasekonfiguration ausgeführt, und die Befehle im Menü **Debuggen**, z.B. **Debuggen starten** und **Starten ohne Debugging**, werden für die Debugkonfiguration ausgeführt.

### <a name="always-show-solution"></a>Projektmappe immer anzeigen

Bei Auswahl dieser Option werden die Projektmappe und alle Befehle, die für Projektmappen ausgeführt werden, immer in der IDE angezeigt. Wenn diese Option deaktiviert ist, werden alle Projekte als eigenständige Projekte erstellt, und Sie können die Projektmappe im Projektmappen-Explorer oder Befehle, die für Projektmappen ausgeführt werden, in der IDE nicht sehen, wenn die Projektmappe nur ein Projekt enthält.

::: moniker range="vs-2017"

### <a name="save-new-projects-when-created"></a>Neue Projekte beim Erstellen speichern

Bei Auswahl dieser Option können Sie einen Speicherort für das Projekt im Dialogfeld **Neues Projekt** festlegen. Wenn diese Option deaktiviert ist, werden alle neuen Projekte als temporäre Projekte erstellt. Bei der Arbeit mit temporären Projekten können Sie ein Projekt erstellen und damit experimentieren, ohne einen Speicherort angeben zu müssen.

::: moniker-end

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>Benutzer bei nicht vertrauenswürdigem Projektspeicherort warnen

Wenn Sie versuchen, ein neues Projekt zu erstellen oder ein vorhandenes Projekt an einem Speicherort zu öffnen, der nicht vollständig vertrauenswürdig ist (z. B. auf einem UNC-Pfad oder HTTP-Pfad), wird eine Meldung angezeigt. Verwenden Sie diese Option, um anzugeben, ob die Meldung jedes Mal angezeigt wird, wenn Sie versuchen, ein Projekt an einem Speicherort zu erstellen oder zu öffnen, der nicht vollständig vertrauenswürdig ist.

### <a name="show-output-window-when-build-starts"></a>Ausgabefenster bei Buildbeginn anzeigen

Zeigt zu Beginn der Projektmappenerstellung automatisch das [Ausgabefenster](../../ide/reference/output-window.md) in der IDE an.

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Beim Umbenennen von Dateien zum symbolischen Umbenennen auffordern

Wenn diese Option aktiviert ist, werden Sie in einer Meldung gefragt, ob Visual Studio alle im Projekt enthaltenen Verweise auf das Codeelement umbenennen soll.

### <a name="prompt-before-moving-files-to-a-new-location"></a>Vor dem Verschieben von Dateien an einen neuen Speicherort fragen

Wenn diese Option aktiviert ist, zeigt Visual Studio ein Bestätigungsmeldungsfeld an, bevor die Speicherorte von Dateien durch Aktionen im **Projektmappen-Explorer** verändert werden.

### <a name="reopen-documents-on-solution-load"></a>Dokumente beim Laden der Projektmappe erneut öffnen

**Eingeführt in Visual Studio 2017 Version 15.8**

Wenn diese Option aktiviert ist, werden die Dokumente, die beim letzten Schließen dieser Projektmappe noch geöffnet waren, automatisch geöffnet, wenn die Projektmappe geöffnet wird.

Das erneute Öffnen von bestimmten Dateitypen oder Designern kann das Laden von Projektmappen verzögern. Deaktivieren Sie diese Option, um die [Leistung beim Laden von Projektmappen](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) zu verbessern, wenn Sie den vorherigen Kontext der Projektmappe nicht wiederherstellen möchten.

## <a name="locations-page"></a>Seite „Speicherorte“

Die folgenden Optionen sind auf der Seite **Speicherorte** verfügbar.

### <a name="projects-location"></a>Speicherort der Projekte

Legt den Standardspeicherort fest, an dem neue Projekte und Projektmappenordner von Visual Studio erstellt werden. Verschiedene Dialogfelder verwenden auch den in dieser Option festgelegten Speicherort als Ausgangspunkt für Ordner. So verwendet z.B. das Dialogfeld **Projekt öffnen** diesen Speicherort für die Verknüpfung **Meine Projekte**.

### <a name="user-project-templates-location"></a>Speicherort von Benutzerprojektvorlagen

Gibt den Standardspeicherort an, der vom Dialogfeld **Neues Projekt** verwendet wird, um die Liste **Meine Vorlagen** zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

### <a name="user-item-templates-location"></a>Speicherort von Benutzerelementvorlagen

Legt den Standardspeicherort fest, der vom Dialogfeld **Neues Element hinzufügen** verwendet wird, um die Liste **Meine Vorlagen** zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Siehe auch

- [Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Dialogfeld „Optionen“, Projekte und Projektmappen, Webprojekte](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
