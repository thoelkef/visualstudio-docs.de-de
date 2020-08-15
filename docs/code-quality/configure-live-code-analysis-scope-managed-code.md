---
title: Konfigurieren des Gültigkeits Bereichs der Live Code Analyse für verwalteten Code
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6df882d50d0c1d052191246605af856743ffdf3d
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249192"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Gewusst wie: Konfigurieren des Gültigkeits Bereichs der Live-Code Analyse für verwalteten Code

## <a name="what-is-live-code-analysis-for-managed-code"></a>Was ist "Live Code Analyse" für verwalteten Code?
Visual Studio führt eine Reihe von Live-Code Analysen aus, die auch als *Hintergrundanalyse*bezeichnet werden, während Sie Quelldateien im Editor bearbeiten. Einige davon sind minimal Analysen für eine akzeptable Visual Studio-IDE-Bearbeitungsumgebung. Einige davon sind für eine verbesserte Reaktionsfähigkeit von IDE-Features vorgesehen. Ein Teil davon besteht darin, zusätzliche IDE-Funktionen wie Diagnose-und Code Korrekturen von Roslyn-Analyzern zu aktivieren. Basierend auf der-Funktionalität können diese Analysen wie folgt gruppiert werden:

- **Hintergrund Berechnung der Diagnose**: Analyse zum Berechnen von Fehlern, Warnungen und Vorschlägen in den Quelldateien. Diese Diagnosen werden als Einträge in der Fehlerliste und als Wellenlinien im Editor angezeigt. Sie können in zwei Kategorien eingeteilt werden:
  - C#-und Visual Basic-Compilerdiagnose
  - Roslyn Analyzer-Diagnose, die Folgendes umfasst:

    - Integrierte IDE-Analysen für Vorschläge im Codestil und
    - Drittanbieter-Analyzer-Pakete, die für Projekte in der aktuellen Projekt Mappe [installiert](./install-roslyn-analyzers.md) werden.

- **Weitere Hintergrundanalysen**: Analyse zur Verbesserung der Reaktionsfähigkeit und Visual Studio-Interaktion für IDE-Features. Beispiele für derartige Analysen:
  - Hintergrundverarbeitung von geöffneten Dateien.
  - Hintergrund Kompilierung von Projekten mit geöffneten Dateien zum Erkennen von Symbolen, um die Reaktionsfähigkeit bestimmter IDE-Features zu verbessern.
  - Die Syntax und Symbol Caches werden aufgebaut.
  - Die Designer Zuordnung für Quelldateien (z. b. Formulare, Steuerelemente usw.) wird erkannt.

## <a name="default-analysis-scope"></a>Standardanalyse Bereich

Standardmäßig wird die Live Code Analyse für die Hintergrund Berechnung der Diagnose für alle Dateien ausgeführt, die in Visual Studio _geöffnet_ werden. Einige der oben erwähnten _Hintergrundanalysen_ werden für alle Projekte ausgeführt, die über mindestens eine geöffnete Datei verfügen. Während einige Hintergrundanalysen für die gesamte Projekt Mappe ausgeführt werden.

## <a name="custom-analysis-scope"></a>Benutzerdefinierter Analysebereich

Der Standardbereich jeder Hintergrundanalyse wurde optimiert, um die optimale Benutzerfreundlichkeit, die Funktionalität und die Leistung für die meisten Kunden Szenarien und-Lösungen zu optimieren. Es gibt jedoch Fälle, in denen Kunden diesen Bereich möglicherweise anpassen möchten, um die Hintergrundanalyse zu verringern oder zu erhöhen. Beispiel:

- Energiesparmodus: Wenn Benutzer auf Laptop Akku Betrieb sind, möchten Sie möglicherweise den Energieverbrauch für eine längere Akkulaufzeit minimieren. In diesem Szenario möchten Sie die Hintergrundanalyse minimieren.
- Bedarfs gesteuerte Code Analyse: Wenn Benutzer die Live Analyzer-Ausführung ausschalten und die Code Analyse bei Bedarf manuell ausführen möchten, sollten Sie die Hintergrundanalyse minimieren. Weitere Informationen finden [Sie unter Gewusst wie: Manuelles Ausführen der Code Analyse bei Bedarf](./how-to-run-code-analysis-manually-for-managed-code.md).
- Vollständige projektmappenanalyse: Wenn Benutzer immer alle Diagnosen in allen Dateien in der Projekt Mappe sehen möchten, unabhängig davon, ob Sie im Editor geöffnet sind oder nicht. In diesem Szenario möchten Sie den Bereich der Hintergrundanalyse für die gesamte Projekt Mappe maximieren.

Ab Visual Studio 2019 Version 16,5 können Benutzer den Umfang der gesamten Live-Code Analyse, einschließlich der Diagnose Berechnung, für c#-und Visual Basic-Projekte explizit anpassen. Folgende Analysebereiche sind verfügbar:

- **Aktuelles Dokument**: minimiert den Gültigkeitsbereich der Live-Code Analyse, sodass er nur für die aktuelle oder sichtbare Datei im Editor ausgeführt wird.
- **Geöffnete Dokumente**: Standard-Live Code Analysebereich, wie im obigen Abschnitt beschrieben.
- **Gesamte Lösung**: maximiert den Gültigkeitsbereich für die Live-Code Analyse, der für alle Dateien und Projekte in der gesamten Projekt Mappe ausgeführt werden soll.

Sie können einen der oben genannten benutzerdefinierten Analysebereiche im Dialogfeld Extras Optionen auswählen, indem Sie die folgenden Schritte ausführen:

1. Um das Dialogfeld **Optionen** zu öffnen **, wählen Sie**in der Menüleiste von Visual Studio Extras  >  **Optionen**aus.

2. Wählen Sie im Dialogfeld **Optionen die Option** **Text-Editor**  >  **c#** oder **Basic**  >  **erweitert**aus.

3. Wählen Sie den gewünschten Bereich für die **Hintergrundanalyse** aus, um den Analysebereich anzupassen. Wählen Sie **OK** aus, wenn Sie fertig sind.

![Analysebereich.](./media/background-analysis-scope.png)

> [!NOTE]
> Vor Visual Studio 2019 Version 16,5 können Benutzer den Analysebereich für die Diagnose Berechnung an die gesamte Projekt Mappe anpassen, indem Sie das Kontrollkästchen **vollständige projektmappenanalyse aktivieren** **unter Extras**  >  **Optionen**  >  **Text-Editor**  >  **c#** oder **einfache**  >  Registerkarte "**erweitert** " verwenden. Es gibt keine Unterstützung für das Minimieren des Bereichs der Hintergrundanalyse in früheren Visual Studio-Versionen.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Live Code Analysebereich automatisch minimieren

Wenn Visual Studio feststellt, dass die Verfügbarkeit von 200 MB oder weniger System Arbeitsspeicher zur Verfügung steht, wird der Gültigkeitsbereich für die Live-Code Analyse automatisch in "Aktuelles Dokument" minimiert. In diesem Fall wird eine Warnung angezeigt, die Sie darüber informiert, dass Visual Studio einige Features deaktiviert hat. Mit einer Schaltfläche können Sie bei Bedarf wieder zum vorherigen Analysebereich wechseln.

![Warnungs Text Minimierung des Analyse Bereichs](./media/fsa_alert.png)

## <a name="see-also"></a>Weitere Informationen

- [Automatisches Anhalten von Features](./automatic-feature-suspension.md)
- [Funktions Anforderung für den Energiesparmodus](https://github.com/dotnet/roslyn/issues/38429)
