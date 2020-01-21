---
title: Analysieren der Speicherauslastung für .NET-Objekte | Microsoft-Dokumentation
ms.date: 12/9/2019
ms.topic: conceptual
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9518ffd618a6d82505feca33b37b5151a3a9f961
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886761"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analysieren der Speicherauslastung mithilfe des .NET-Tools für die Objektzuordnung

Mithilfe des .NET-Tools für die Objektzuordnung können Sie sehen, wie viel Arbeitsspeicher Ihre App insgesamt belegt und bei welchen Codepfaden der Bedarf am höchsten ist.

Nachdem Sie das Tool ausgeführt haben, werden Ihnen die Funktionsausführungspfade angezeigt, bei denen Objekte zugewiesen werden. So können Sie die Wurzel der Aufrufstruktur identifizieren, bei der der Speicherbedarf am größten ist.

## <a name="setup"></a>Setup

1. Öffnen Sie den Leistungs-Profiler (**ALT + F2**) in Visual Studio.
2.  Aktivieren Sie das Kontrollkästchen **Nachverfolgung der .NET-Objektzuordnung**.

![Diagnosehub](../profiling/media/diaghub.png "Diagnosehub")

> [!NOTE]
> Standardmäßig wird das Startprojekt als **Analyseziel** ausgewählt. Sie können aber auch einen laufenden Prozess, eine ausführbare Datei, eine laufende App und installierte Apps analysieren lassen. Klicken Sie dazu auf das Dropdownmenü **Ziel ändern**, und wählen Sie aus den verfügbaren Optionen aus.

   Das Tool für die .NET-Objektzuordnung bietet aktuell nicht die Möglichkeit, ausführbare Dateien über das Dropdownmenü auszuwählen. Sie müssen das EXE-Projektsystem durchlaufen, um das Tool verwenden zu können. Schließen Sie dazu zuerst die aktuelle Projektmappe (**Datei** -> **Projektmappe schließen**), und wählen Sie dann unter **Datei** -> **Projekt oder Projektmappe öffnen** Ihre EXE-Datei aus.

![Analyseziel](../profiling/media/analysistarget.png "Analyseziel")

3. Klicken Sie auf die Schaltfläche **Start**, um das Tool auszuführen.

![Sammlung beenden](../profiling/media/stopcollection.png "Sammlung beenden")

4. Nachdem das Tool gestartet wurde, durchlaufen Sie das gewünschte Szenario in Ihrer App. Drücken Sie anschließend auf **Sammlung beenden**, oder schließen Sie Ihre App, um sich Ihre Daten anzeigen zu lassen.
5. Klicken Sie auf die Registerkarte **Allocation** (Zuordnung). Die Anzeige auf Ihrem Bildschirm sollte nun ungefähr so aussehen.

![Speicherbelegung](../profiling/media/allocation.png "Zuordnung")

Herzlichen Glückwunsch! Sie können jetzt die Speicherbelegung der Objekte analysieren.

## <a name="understand-your-data"></a>Erläuterungen zu den Daten

### <a name="collection"></a>Auflistung

![Auflistung](../profiling/media/collection.png "Auflistung")

In der Sammlungsansicht können Sie sehen, wie viele Objekte während der Garbage Collection gesammelt und wie viele davon beibehalten wurden. Hier finden Sie auch zwei Kreisdiagramme, mit denen diese Informationen für die einzelnen Typen grafisch dargestellt werden.

- In der Spalte **Collected** (Gesammelt) wird die Anzahl der Objekte angezeigt, die vom Garbage Collector erfasst wurden.
- Die Spalte **Survived** (Verblieben) zeigt, wie viele Objekte nach der Ausführung des Garbage Collectors noch vorhanden waren.

### <a name="allocation"></a>Zuordnung

![Zuordnung erweitert](../profiling/media/allocationexpanded.png "Zuordnung erweitert")

Die Ansicht „Allocation“ (Zuordnung) ermöglicht es Ihnen, zu sehen, welche Objekte wie viel Arbeitsspeicher belegen und wo sie gespeichert sind.

- In der Spalte **Name** sind verschiedene Klassen und Strukturen aufgeführt, die Arbeitsspeicher belegen. Jedes Element in der Spalte ist ein Knoten, der erweitert werden kann, wenn es innerhalb dieser Kategorie Elemente gibt, die Arbeitsspeicher belegen. (nur in der Ansicht **Allocation** (Zuordnung) verfügbar)
- In der Spalte **Total (Allocations)** ((Gesamt-)Zuordnungen) wird die Anzahl der Objekte eines bestimmten Zuordnungstyps angezeigt, die Arbeitsspeicher belegen. (In den Ansichten **Allocation** (Zuordnung), **Aufrufstruktur** und **Funktionen** verfügbar)
- In der Spalte **Self (Allocations)** ((Selbst-)Zuordnungen) wird die Anzahl der Objekte in einem einzelnen Element angezeigt, das Arbeitsspeicher belegt. (In den Ansichten **Allocation** (Zuordnung), **Aufrufstruktur** und **Funktionen** verfügbar)
- Alle drei Spalten sind sortierbar. Bei der Spalte **Name** erfolgt die Sortierung entweder alphabetisch vorwärts oder rückwärts. Bei den Spalten **Total (Allocations)** ((Gesamt-)Zuordnungen) und **Self (Allocations)** ((Selbst-)Zuordnungen) können Sie sich die Zahlen aufsteigend oder absteigend sortiert anzeigen lassen.
- Die Spalten **Total Size (Bytes)** (Gesamtgröße (Byte)) und **Self Size (Bytes)** (Automatische Größe (Byte)) sind standardmäßig nicht aktiviert. Um diese zu aktivieren, klicken Sie mit der rechten Maustaste auf **Name**, **Total (Allocations)** ((Gesamt-)Zuordnungen) oder auf **Self (Allocations)** ((Selbst-)Zuordnungen) und dann auf die Optionen **Total Size (Bytes)** (Gesamtgröße (Byte)) und **Self Size** (Automatische Größe (Byte)), um sie dem Diagramm hinzuzufügen. Die beiden Spalten ähneln **Total (Allocations)** ((Gesamt-)Zuordnungen) und **Self (Allocations)** ((Selbst-)Zuordnungen) mit der Ausnahme, dass anstelle der Anzahl der Objekte, die Arbeitsspeicher belegen, die Gesamtgröße des Arbeitsspeichers in Byte angezeigt wird, den diese Objekte belegen. [Nur in der Ansicht „Allocation“ (Zuordnung) verfügbar]

### <a name="call-tree"></a>Aufrufstruktur

![Aufrufstruktur](../profiling/media/calltree.png "Aufrufstruktur")

Mit der Ansicht **Aufrufstruktur** können Sie sich die Funktionsausführungspfade anzeigen lassen, die Objekte enthalten, die viel Arbeitsspeicher belegen.

- Die Spalte **Funktionsname** zeigt basierend auf der Ebene des Knotens, den Sie überprüfen, den Prozess oder den Namen einer Funktion an, die Objekte enthält, die Arbeitsspeicher belegen.
- In den Spalten **Total (Allocations)** ((Gesamt-)Zuordnungen) und **Self (Allocations)** ((Selbst-)Zuordnungen) werden dieselben Informationen angezeigt wie in der Ansicht **Allocations** (Zuordnungen).
- Die Spalte **Modulname** zeigt das Modul an, das die aufrufende Funktion oder den aufrufenden Prozess enthält.

![Langsamster Pfad](../profiling/media/hotpath.png "Langsamster Pfad")

- Wenn Sie auf die Schaltfläche **Langsamsten Pfad erweitern** klicken, wird ein Funktionsausführungspfad hervorgehoben, der viele Objekte enthält, die Arbeitsspeicher belegen. Der Algorithmus startet bei einem vom Benutzer ausgewählten Knoten, hebt den Pfad der meisten Zuordnungen hervor und hilft dem Benutzer bei der Untersuchung.
- Die Schaltfläche **Langsamsten Pfad anzeigen** aktiviert oder deaktiviert das Flammensymbol, das zeigt, welche Knoten Teil des **langsamsten Pfads** sind.

### <a name="functions"></a>Funktionen

![Funktionen](../profiling/media/functions.png "Funktionen")

Mit der Ansicht **Funktionen** können Sie sich Prozesse, Module und Funktionen anzeigen lassen, die Arbeitsspeicher belegen.

- In der Spalte **Name** werden Prozesse als Knoten der obersten Ebene angezeigt. Unterhalb der Prozesse befinden sich die Module und darunter die Funktionen.
- In den Spalten **Total (Allocations)** ((Gesamt-)Zuordnungen) und **Self (Allocations)** ((Selbst-)Zuordnungen) werden dieselben Informationen angezeigt wie in der Ansicht **Allocations** (Zuordnungen).

Die Ansichten **Allocation** (Zuordnung), **Aufrufstruktur** und **Funktionen** enthalten alle die Optionen **Nur eigenen Code anzeigen**, **Show Native Code** (Nativen Code anzeigen) und **Suchen**:

![Filterleiste](../profiling/media/filterbar.png "Filterleiste")

- **Nur eigenen Code anzeigen**: Damit der Benutzer sich auf seinen Code konzentrieren kann, werden Systeme, Frameworks und anderer nicht vom Benutzer stammender Code hinter Frames ( **[External Code]** ) verborgen. Weitere Informationen finden Sie unter [Funktion „Nur eigenen Code anzeigen“ verwenden, um nur eigenen Code zu debuggen](../debugger/just-my-code.md).
- **Show Native Code** (Nativen Code anzeigen): Mit dieser Option wird im Analyseziel vorhandener native Code angezeigt, einschließlich Code, der nicht vom Benutzer stammt.
- Im **Filterfeld** können Sie einen Parameter eingeben, nach dem in den Spalten **Name** oder **Funktionsname** gesucht werden soll. Wenn Sie hier etwas eingeben, werden nur die Typen angezeigt, die eine entsprechende Zeichenfolge enthalten.
