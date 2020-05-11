---
title: Konfigurieren des Livecodeanalysebereichs für verwalteten Code
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432090"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Gewusst wie: Konfigurieren des Livecodeanalysebereichs für verwalteten Code

## <a name="what-is-live-code-analysis-for-managed-code"></a>Was ist "Live-Codeanalyse" für verwalteten Code?
Visual Studio führt eine Reihe von Live-Code-Analysen aus, die auch als *Hintergrundanalyse*bezeichnet werden, während Sie Quelldateien im Editor bearbeiten. Ein Teil davon ist für eine akzeptable Visual Studio-IDE-Bearbeitung erforderlich. Ein Teil davon dient zur verbesserten Reaktionsfähigkeit von IDE-Funktionen. Während einige davon zusätzliche IDE-Funktionen aktivieren sollen, z. B. Diagnose- und Codekorrekturen von Roslyn-Analysatoren. Basierend auf der Funktionalität können diese Analysen wie folgt gruppiert werden:

- **Hintergrundberechnung der Diagnose**: Analyse zum Berechnen von Fehlern, Warnungen und Vorschlägen in Quelldateien. Diese Diagnosen werden als Einträge in der Fehlerliste und als Wellenschimmer im Editor angezeigt. Sie können in zwei Kategorien eingeteilt werden:
    - Compilerdiagnose für C- und Visual Basic-Compiler
    - Roslyn-Analyzer-Diagnose, die Folgendes umfasst:

        - Integrierte IDE-Analysatoren für Codestilvorschläge und
        - Analysepakete von Drittanbietern, die für Projekte in der aktuellen Projektmappe [installiert](./install-roslyn-analyzers.md) sind.

- **Weitere Hintergrundanalysen**: Analyse zur Verbesserung der Reaktionsfähigkeit und Visual Studio-Interaktion für IDE-Features. Einige Beispiele für solche Analysen sind:
    - Hintergrundanalyse geöffneter Dateien.
    - Hintergrundkompilierung von Projekten mit geöffneten Dateien, um Symbole für eine verbesserte Reaktionsfähigkeit bestimmter IDE-Funktionen zu realisieren.
    - Erstellen von Syntax- und Symbolcaches.
    - Erkennen der Designerzuordnung für Quelldateien, z. B. Formulare, Steuerelemente usw.

## <a name="default-analysis-scope"></a>Standardanalysebereich

Standardmäßig wird die Livecodeanalyse für die Hintergrundberechnung der Diagnose für alle Dateien ausgeführt, die in Visual Studio _geöffnet_ werden. Nur wenige der oben genannten _Hintergrundanalysen_ führen für alle Projekte aus, die mindestens eine offene Datei haben. Während nur wenige Hintergrundanalysen für die gesamte Lösung ausgeführt werden.

## <a name="custom-analysis-scope"></a>Benutzerdefinierter Analysebereich

Der Standardbereich jeder Hintergrundanalyse wurde für die optimale Benutzerfreundlichkeit, Funktionalität und Leistung für die meisten Kundenszenarien und -lösungen optimiert. Es gibt jedoch Fälle, in denen Kunden diesen Bereich anpassen möchten, um die Hintergrundanalyse zu verringern oder zu erhöhen. Beispiel:

- Energiesparmodus: Wenn Benutzer mit Laptop-Akku laufen, möchten sie möglicherweise den Stromverbrauch für eine längere Akkulaufzeit minimieren. In diesem Szenario möchten sie die Hintergrundanalyse minimieren.
- Bedarfsbezogene Codeanalyse: Wenn Benutzer die Ausführung von Live-Analyzer lieber deaktivieren und die Codeanalyse bei Bedarf manuell ausführen, möchten sie die Hintergrundanalyse minimieren. Weitere Informationen [finden Sie unter Gewusst wie: Manuell ausführen der Codeanalyse bei Bedarf](./how-to-run-code-analysis-manually-for-managed-code.md).
- Vollständige Lösungsanalyse: Wenn Benutzer immer alle Diagnosen in allen Dateien in der Lösung sehen möchten, unabhängig davon, ob sie im Editor geöffnet sind oder nicht. In diesem Szenario möchten sie den Hintergrundanalysebereich für die gesamte Lösung maximieren.

Ab Visual Studio 2019 Version 16.5 können Benutzer den Umfang aller Livecodeanalysen, einschließlich der Diagnoseberechnung, explizit für C-Und Visual Basic-Projekte anpassen. Verfügbare Analysebereiche sind:

- **Aktuelles Dokument**: Minimiert den Livecodeanalysebereich, um nur für die aktuelle oder sichtbare Datei im Editor ausgeführt zu werden.
- **Öffnen von Dokumenten**: Standard-Livecodeanalysebereich, wie im obigen Abschnitt beschrieben.
- **Gesamtlösung**: Maximiert den Live-Code-Analysebereich, um für alle Dateien und Projekte in der gesamten Projektmappe ausgeführt zu werden.

Sie können einen der oben genannten benutzerdefinierten Analysebereiche im Dialogfeld Tools-Optionen auswählen, indem Sie die folgenden Schritte ausführen:

1. Um das Dialogfeld **Optionen zu** öffnen, wählen Sie in der Menüleiste in Visual Studio**Extras-Optionen** **Tools** > aus.

2. Wählen Sie im Dialogfeld **Optionen** die Option **Texteditor** > **C-** oder **Basic** > **Advanced aus.**

3. Wählen Sie den gewünschten **Hintergrundanalysebereich** aus, um den Analysebereich anzupassen. Wählen Sie **OK,** wenn Sie fertig sind.

![Analysebereich.](./media/background-analysis-scope.png)

> [!NOTE]
> Vor Visual Studio 2019 Version 16.5 können Benutzer den Analysebereich für die Diagnoseberechnung mithilfe des **Kontrollkästchens Vollständige Lösungsanalyse** aktivieren auf der Registerkarte > **Tools-Optionen** > **Texteditor** > **C-** oder **Basic** > **Advanced** an die gesamte Lösung anpassen. **Tools** Es gibt keine Unterstützung, um den Hintergrundanalysebereich in früheren Visual Studio-Versionen zu minimieren.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Automatische Minimierung des Livecode-Analysebereichs

Wenn Visual Studio erkennt, dass 200 MB oder weniger Systemspeicher verfügbar sind, wird der Livecodeanalysebereich automatisch auf "Aktuelles Dokument" minimiert. In diesem Fall wird eine Warnung angezeigt, die Sie darüber informiert, dass Visual Studio einige Features deaktiviert hat. Mit einer Schaltfläche können Sie bei Bedarf zurück zum vorherigen Analysebereich wechseln.

![Warnungstext minimiert Denkumfang](./media/fsa_alert.png)

## <a name="see-also"></a>Weitere Informationen

- [Automatisches Anhalten von Features](./automatic-feature-suspension.md)
- [Power-Save-Modus-Feature-Anforderung](https://github.com/dotnet/roslyn/issues/38429)
