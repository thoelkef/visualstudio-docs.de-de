---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: ce9a1a2da7397dbc7ce4235391c962cada7d59eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786519"
---
# <a name="live-unit-testing-with-visual-studio"></a>Live Unit Testing mit Visual Studio

Live Unit Testing führt automatisch alle betroffenen Komponententests im Hintergrund aus, und zeigt die Ergebnisse und Code Coverage in der Visual Studio-IDE in Echtzeit an, während Sie eine Anwendung entwickeln. Wenn Sie Ihren Code ändern, bietet Live Unit Testing Feedback dazu, welche Auswirkungen Ihre Änderungen auf vorhandene Tests haben und ob der neue von Ihnen hinzugefügte Code von einem oder mehreren vorhandenen Tests abgedeckt wird. So werden Sie daran erinnert, Komponententests zu schreiben, während Sie Fehler beheben oder neue Funktionen hinzufügen.

> [!NOTE]
> Live Unit Testing steht für C#- und Visual Basic-Projekte zur Verfügung, die auf .NET Core und .NET Framework in der Enterprise-Edition von Visual Studio ausgerichtet sind.

Wenn Sie Live Unit Testing für Ihre Tests verwenden, werden Daten zum Status Ihrer Tests beibehalten. Da bei Live Unit Testing persistente Daten verwendet werden können, bietet es eine überragende Leistung bei der dynamischen Ausführung Ihrer Tests in Bezug auf Codeänderungen.

## <a name="supported-test-frameworks"></a>Unterstützte Testframeworks
Live Unit Testing kann mit den drei gängigen Frameworks für Komponententests verwendet werden, die in der folgenden Tabelle aufgeführt sind. Die unterstützte Mindestversion der Adapter und Frameworks ist ebenfalls in der Tabelle aufgeführt. Die Frameworks für Komponententests sind auf „NuGet.org“ verfügbar.

|Testframework  |Mindestversion des Visual Studio-Adapters  |Mindestversion des Frameworks  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio, Version 2.2.0-beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter, Version 3.5.1 |NUnit, Version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Wenn Sie über ältere, auf MSTest basierende Testprojekte verfügen, die sich auf `Microsoft.VisualStudio.QualityTools.UnitTestFramework` beziehen, und Sie nicht auf die neueren MSTest-NuGet-Pakete umsteigen möchten, sollten Sie mindestens auf Visual Studio 2017 Version 15.4 upgraden.

In einigen Fällen müssen Sie explizit die NuGet-Pakete wiederherstellen, auf die die Projekte in der Projektmappe verweisen, damit Live Unit Testing funktioniert. Hierzu können Sie entweder die Projektmappe explizit erstellen (klicken Sie im obersten Visual Studio-Menü auf **Build** > **Projektmappe neu erstellen**) oder Pakete in der Projektmappe wiederherstellen (klicken Sie mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete wiederherstellen** aus), bevor Sie Live Unit Testing aktivieren.

## <a name="configure-live-unit-testing"></a>Konfigurieren von Live Unit Testing

Sie können Live Unit Testing konfigurieren, indem Sie in der obersten Visual Studio-Menüleiste **Extras** > **Optionen** und anschließend im Dialogfeld **Optionen** im linken Bereich **Live Unit Testing** auswählen.

> [!TIP]
> Nach der Aktivierung von Live Unit Testing (siehe nächster Abschnitt [Starten, Anhalten und Beenden von Live Unit Testing](#start-pause-and-stop-live-unit-testing)) können Sie auch das Dialogfeld **Optionen** öffnen, indem Sie **Test** > **Live Unit Testing** > **Optionen** auswählen.

Die folgende Abbildung zeigt die im Dialogfeld verfügbaren Konfigurationsoptionen für Live Unit Testing:

  ![Bild](./media/lut-options.png)

Die konfigurierbaren Optionen umfassen Folgendes:

- Ob Live Unit Testing angehalten wird, wenn eine Projektmappe erstellt und ein Debugging durchgeführt wird.

- Ob Live Unit Testing angehalten wird, wenn die Akkuleistung des Systems unter einen bestimmten Schwellenwert sinkt.

- Ob Live Unit Testing automatisch ausgeführt wird, wenn eine Projektmappe geöffnet wird.

- Ob das Debugsymbol und die Kommentargenerierung für die XML-Dokumentation aktiviert ist.

- Das Verzeichnis, in dem persistente Daten gespeichert werden sollen.

- Die Fähigkeit, alle persistenten Daten zu löschen. Dies ist hilfreich, wenn sich Live Unit Testing auf unvorhersehbare oder unerwartete Weise verhält, was darauf hinweist, dass die persistenten Daten beschädigt wurden.

- Das Intervall, nach dem eine Zeitüberschreitung für einen Testfall auftritt. Der Standardwert ist 30 Sekunden.

- Die maximale Anzahl der Testläufe, die Live Unit Testing erstellt.

- Die maximale Arbeitsspeichermenge, die Live Unit Testing-Prozesse belegen können.

- Den Umfang an Informationen, der in das Live Unit Testing-Fenster **Ausgabe** geschrieben wird.

   Mögliche Optionen sind: Keine Protokollierung (**Keine**), nur Fehlermeldungen (**Fehler**), Fehler- und Informationsmeldungen (**Info**, die Standardeinstellung) oder alle Details (**Ausführlich**).

   Sie können auch eine ausführlichen Ausgabe im Live Unit Testing-Fenster **Ausgabe** anzeigen, indem Sie einer Umgebungsvariablen auf Benutzerebene mit dem Namen `VS_UTE_DIAGNOSTICS` den Wert „1“ zuweisen und dann Visual Studio neu starten.

   Um detaillierte MSBuild-Protokollmeldungen von Live Unit Testing in einer Datei aufzuzeichnen, legen Sie die `LiveUnitTesting_BuildLog`-Umgebungsvariable auf Benutzerebene auf den Namen der Datei fest, die das Protokoll enthalten soll.

## <a name="start-pause-and-stop-live-unit-testing"></a>Starten, Anhalten und Beenden von Live Unit Testing

Sie aktivieren Live Unit Testing, indem Sie im obersten Visual Studio-Menü auf **Test** > **Live Unit Testing** > **Starten** klicken. Wenn Live Unit Testing aktiviert ist, ändern sich die verfügbaren Optionen im **Live Unit Testing**-Menü von dem einzelnen Element **Starten** zu **Anhalten**, **Beenden** und **Zurücksetzen und bereinigen**.

> [!NOTE]
> Wenn Sie Live Unit Testing in einer Projektmappe starten, die kein Komponententestprojekt enthält, erscheinen zwar die Optionen **Pause**, **Beenden**, und **Bereinigt zurücksetzen** im **Live Unit Testing**-Menü, Live Unit Testing wird jedoch nicht gestartet. Das **Ausgabe**-Fenster zeigt eine Nachricht, die mit „No supported test adapters are referenced by this solution...“(Diese Projektmappe bezieht sich auf keine unterstützten Testadapter...) beginnt.

Sie können Live Unit Testing jederzeit vorübergehend anhalten oder vollständig beenden. Sie könnten sich beispielsweise dann dazu entschließen, wenn Sie gerade ein Refactoring ausführen und wissen, dass die Tests für eine Weile gestört sind. Die drei Menüoptionen sind:

- **Anhalten**: Unterbricht Live Unit Testing vorübergehend.

    Wenn Live Unit Testing angehalten wird, wird die Abdeckungsvisualisierung nicht im Editor dargestellt, aber alle gesammelten Daten bleiben erhalten. Um Live Unit Testing fortzusetzen, wählen Sie im Live Unit Testing-Menü **Weiter** aus. Live Unit Testing führt die notwendigen Schritte aus, um alle Änderungen nachzuholen, die vorgenommen wurden, während Live Unit Testing angehalten war, und aktualisiert die Glyphen entsprechend.

- **Beenden**: Beendet Live Unit Testing vollständig. Live Unit Testing verwirft alle Daten, die gesammelt wurden.

- **Zurücksetzen und bereinigen**: Beendet Live Unit Testing, löscht persistente Daten und startet Live Unit Testing neu.

- **Optionen**: Öffnet das Dialogfeld **Optionen**, das im Abschnitt [Konfigurieren von Live Unit Testing](#configure-live-unit-testing) beschrieben wird.

## <a name="view-coverage-visualization-in-the-editor-as-you-type"></a>Anzeigen der Coverage-Visualisierung im Editor während der Eingabe

Nach der Aktivierung aktualisiert Live Unit Testing alle Codezeilen im Visual Studio-Editor, um Ihnen zu zeigen, ob der Code, den Sie schreiben, von Komponententests abgedeckt ist, und ob die Tests, die ihn abdecken, erfolgreich sind.  Die folgende Abbildung zeigt Codezeilen mit erfolgreichen und fehlgeschlagenen Tests sowie Codezeilen, die nicht durch Tests abgedeckt sind. Zeilen mit einem grünen „✓“ werden nur durch bestandene Tests abgedeckt, Zeilen mit einem roten „x“ werden von einem oder mehreren nicht bestandenen Tests abgedeckt, und Zeilen mit einem blauen „➖“ werden von keinem Test abgedeckt.

  ![Bild](./media/lut-codewindow.png)

Die Abdeckungsvisualisierung von Live Unit Testing wird sofort aktualisiert, wenn Sie Code im Code-Editor ändern. Während der Verarbeitung der Änderungen wird die Visualisierung geändert, um anzugeben, dass die Daten nicht auf dem neuesten Stand sind. Dazu wird ein rundes Uhrensymbol unterhalb der Symbole für erfolgreiche, fehlgeschlagene und nicht abgedeckte Test angezeigt, wie in der folgenden Abbildung dargestellt.

  ![Bild](./media/lut-codeupdating.png)

## <a name="get-information-on-successful-or-failed-tests"></a>Abrufen von Informationen zu erfolgreichen oder fehlgeschlagenen Tests

Wenn Sie den Mauszeiger im Codefenster über das Symbol für erfolgreiche oder fehlgeschlagene Tests bewegen, können Sie sehen, wie viele Tests diese Zeile betreffen. Wenn Sie auf das Symbol klicken, können Sie den Status der einzelnen Tests sehen, wie in der folgenden Abbildung dargestellt wird:

  ![Bild](./media/lut-failedinfo.png)

Neben der Angabe der Namen und Testergebnisse können Sie mithilfe der QuickInfo die Gruppe von Tests erneut ausführen sowie mit dem Debugger ausführen. Wenn Sie einen oder mehrere Tests in der QuickInfo auswählen, können Sie diese Tests auch ausführen oder debuggen. Auf diese Weise können Sie Ihre Tests debuggen, ohne das Codefenster verlassen zu müssen. Wenn der Debugger eine [`Assert`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert)-Methode ausführt, die ein unerwartetes Ergebnis zurückgibt, wird die Programmausführung bei der Überwachung aller eventuell festgelegten Haltepunkte und zusätzlich beim Debuggen angehalten.

Wenn Sie den Mauszeiger über einen nicht bestandenen Test in der QuickInfo bewegen, wird sie erweitert, und es werden zusätzliche Informationen zum jeweiligen Fehler bereitgestellt, wie in der folgenden Abbildung dargestellt wird. Wenn Sie in der QuickInfo auf den nicht bestandenen Test doppelklicken, können Sie direkt zum Test navigieren.

  ![Bild](./media/lut-failedmsg.png)

Wenn Sie zum nicht bestandenen Test navigieren, kennzeichnet Live Unit Testing in der Methodensignatur auch die Tests visuell, die bestanden wurden (angezeigt durch ein halbvolles Becherglas mit einem grünen „✓“), die nicht bestanden wurden (ein halbvolles Becherglas mit einem roten „🞩“) oder die nicht von Live Unit Testing abgedeckt wurden (ein halbvolles Becherglas mit einem blauen „➖“). Methoden, die keine Testmethoden darstellen, sind nicht mit einem Symbol versehen. Die folgende Abbildung zeigt alle vier Arten von Methoden.

  ![Bild](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnostizieren und Beheben von Testfehlern

Über den fehlgeschlagenen Test können Sie problemlos den Produktcode debuggen, ihn bearbeiten und die Entwicklung Ihrer Anwendung fortsetzen. Da Live Unit Testing im Hintergrund ausgeführt wird, müssen Sie Live Unit Testing beim Debuggen, Bearbeiten und Fortsetzen des Zyklus nicht beenden und neu starten.

Beispiel: Der in der obigen Abbildung dargestellte nicht bestandene Test wurde durch die falsche Annahme in der Testmethode verursacht, dass nicht alphabetische Zeichen `true` zurückgeben, wenn sie an die <xref:System.Char.IsLower%2A?displayProperty=fullName>-Methode übergeben werden. Nachdem wir die Testmethode korrigiert haben, stellen wir fest, dass alle Tests bestanden wurden. Währenddessen müssen wir Live Unit Testing nicht anhalten oder beenden.

## <a name="live-unit-testing-and-test-explorer"></a>Live Unit Testing und Test-Explorer

Normalerweise stellt der **Test-Explorer** die Schnittstelle bereit, mit der Sie Tests ausführen und debuggen und Testergebnisse analysieren können. Live Unit Testing ist in den **Test-Explorer** integriert. Wenn Live Unit Testing nicht aktiviert ist oder beendet wurde, zeigt der **Test-Explorer** den Status von Komponententests an, als zuletzt ein Test ausgeführt wurde. Änderungen am Quellcode erfordern, dass Sie die Tests erneut ausführen. Wenn Live Unit Testing dagegen aktiviert ist, wird der Status der Komponententests im **Test-Explorer** sofort aktualisiert. Sie müssen Komponententests nicht mehr explizit ausführen.

> [!NOTE]
> Sie können den **Test-Explorer** öffnen, indem Sie im obersten Visual Studio-Menü auf **Test** > **Windows** > **Test-Explorer** klicken.

Möglicherweise ist Ihnen ausgefallen, dass im **Test-Explorer**-Fenster einige Tests als verblasst angezeigt werden. Beispiel: Wenn Sie Live Unit Testing aktivieren, nachdem Sie ein zuvor gespeichertes Projekt geöffnet haben, ist das **Test-Explorer**-Fenster mit Ausnahme des nicht bestandenen Test verblasst, wie in der folgenden Abbildung gezeigt wird. In diesem Fall hat Live Unit Testing den nicht bestandenen Test erneut ausgeführt, jedoch nicht die erfolgreichen Tests, da die persistenten Daten von Live Unit Testing darauf hinweisen, dass keine Änderungen festgestellt wurden, seitdem die Tests zuletzt erfolgreich ausgeführt wurden.

  ![Bild](media/lut-test-explorer.png)

Sie können alle Tests, die verblasst angezeigt werden, erneut ausführen. Wählen Sie hierfür im **Test-Explorer**-Menü die Option **Alle ausführen** oder **Ausführen**, oder wählen Sie im **Test-Explorer**-Menü einen oder mehrere Tests aus, klicken Sie mit der rechten Maustaste darauf, und wählen Sie im Popupmenü **Ausgewählte Tests ausführen** oder **Ausgewählte Tests debuggen** aus. Tests, die ausgeführt werden, werden oben angezeigt.

Es gibt einige Unterschiede zwischen dem automatischen Ausführen und Aktualisieren der Testergebnisse durch Live Unit Testing und dem expliziten Ausführen von Tests im **Test-Explorer**. Zu diesen Unterschieden zählen Folgende:

- Beim Ausführen oder Debuggen von Tests im Test-Explorer-Fenster werden reguläre Binärdateien ausgeführt. Live Unit Testing führt dagegen instrumentierte Binärdateien aus.
- Live Unit Testing erstellt keine neue Anwendungsdomäne zum Ausführen von Tests, sondern führt Tests mit der Standarddomäne aus. Tests, die über das **Test-Explorer**-Fenster ausgeführt werden, erstellen eine neue Anwendungsdomäne.
- Live Unit Testing führt Tests in allen Testassemblys nacheinander aus. Wenn Sie mehrere Tests im **Test-Explorer**-Fenster ausführen und die Schaltfläche **Tests parallel ausführen** ausgewählt ist, werden Tests parallel ausgeführt.

## <a name="live-unit-testing-and-large-solutions"></a>Live Unit Testing und große Projektmappen

Wenn Ihre Projektmappe mindestens zehn Projekte enthält, zeigt Visual Studio das folgende Dialogfeld an, um Sie zu warnen, dass die dynamische Ausführung einer großen Anzahl von Tests in großen Projekten die Leistung schwerwiegend beeinträchtigen kann, wenn Sie Live Unit Testing starten und keine persistenten Daten vorhanden sind oder wenn Sie im obersten Visual Studio-Menü auf **Test** > **Live Unit Testing** > **Bereinigt zurücksetzen** klicken. Wenn Sie auf **OK** klicken, führt Live Unit Testing alle Tests in der Projektmappe aus. Bei Auswahl von **Abbrechen** können Sie wählen, welche Tests ausgeführt werden. Informationen hierzu finden Sie im folgenden Abschnitt [Einschließen und Ausschließen von Testprojekten und Testmethoden](#include-and-exclude-test-projects-and-test-methods).

 ![Live Unit Testing-Dialogfeld für große Projekte](media/lut-large-project.png)

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Einschließen und Ausschließen von Testprojekten und Testmethoden

Bei Projektmappen mit vielen Testprojekten können Sie steuern, welche Projekte und welche einzelnen Methoden in einem Projekt von Live Unit Testing berücksichtigt werden. Wenn Sie z.B. eine Projektmappe mit Hunderten von Testprojekten haben, können Sie eine bestimmte Reihe von Testprojekten für Live Unit Testing auswählen. Hierfür stehen eine Reihe von Möglichkeiten zur Verfügung, je nachdem, ob Sie alle Tests im Projekt oder in der Projektmappe ausschließen, einen Großteil der Tests ein- oder ausschließen oder einzelne Tests ausschließen möchten. Live Unit Testing speichert den Status für das Einschließen/Ausschließen als Benutzereinstellung, wenn eine Projektmappe geschlossen und erneut geöffnet wird.

**Ausschließen aller Tests in einem Projekt oder einer Projektmappe**

Um die einzelnen Projekte in Komponententests auszuwählen, gehen Sie nach dem Start von Live Unit Testing wie folgt vor:

1. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf die Projektmappe, und wählen Sie **Livetests** > **Ausschließen** aus, um die gesamte Projektmappe auszuschließen.
1. Klicken Sie mit der rechten Maustaste auf jedes Testprojekt, das Sie in die Tests einschließen möchten, und wählen Sie **Livetests** > **Einschließen** aus.

**Ausschließen von einzelnen Tests im Code-Editor-Fenster**

Im Code-Editor-Fenster können Sie einzelne Testmethoden ein- oder ausschließen. Klicken sie im Code-Editor-Fenster mit der rechten Maustaste auf die Signatur der Testmethode. Wählen Sie anschließend **Livetests** > **[die ausgewählte Methode] einschließen**, **Livetests** > **[die ausgewählte Methode] ausschließen** oder **Livetests** > **Alle außer [die ausgewählte Methode] ausschließen** aus, wobei „die ausgewählte Methode“ für den Namen der im Codefenster ausgewählten Methode steht.

**Programmgesteuertes Ausschließen von Tests**

Sie können auch das <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute>-Attribut anwenden, damit Methoden, Klassen oder Strukturen ihre Abdeckung nicht programmgesteuert in Live Unit Testing ausgeschlossen werden.

Mithilfe der folgenden Attribute können Sie ebenfalls einzelne Methoden von Live Unit Testing ausschließen:

- Für xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Für NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Für MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Siehe auch

- [Testtools für Code](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing-Blog](https://go.microsoft.com/fwlink/?linkid=842514)
- [Live-Komponententests – Häufig gestellte Fragen](live-unit-testing-faq.md)
- [Channel 9-Video: Live Unit Testing in Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
