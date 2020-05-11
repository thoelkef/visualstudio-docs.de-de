---
title: Animationen für Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698609"
---
# <a name="animations-for-visual-studio"></a>Animationen für Visual Studio
## <a name="animation-fundamentals"></a>Animationsgrundlagen

### <a name="animation-best-practices-in-visual-studio"></a>Bewährte Methoden für Animationen in Visual Studio
Befolgen Sie diese Regeln, um konsistente und benutzerfreundliche Animationsstile in der Visual Studio-IDE sicherzustellen.

- **Seien Sie selektiv.** Beschränken Sie Animationen auf Solche, die bestimmten Zwecken dienen.

- **Timing und Geschwindigkeit sind wichtig,** um sicherzustellen, dass sich Übergänge schnell und natürlich anfühlen:

  - Schließen Sie animierte Übergänge innerhalb einer halben Sekunde (500 Millisekunden) ab.

  - Animationen, die häufig auftreten würden, müssen schnell genug sein, damit sie den Workflow des Benutzers nicht unterbrechen. Sehen Sie sich die Animation in einer Schleife an und passen Sie das Timing an, bis es sich richtig anfühlt.

  - Animationen sollten nicht so schnell oder verwirrend sein, dass sie schwer zu verstehen sind, aber nicht so langsam, dass es einen ungeduldig macht, damit der Übergang beendet wird.

  - Verwenden Sie variables Timing, um die Bedeutung hervorzuheben. Wenn Sie z. B. durch eine Sequenz von Elementen in einem Klassendiagramm navigieren, beschleunigen Sie Übergänge zwischen Elementen, um sich dann auf wichtige Elemente zu konzentrieren.

- **Verwenden Sie allmähliche nicht-lineare Lockerung** von einem Zustand zum anderen, so dass ein Gefühl der Ruhe und natürliche Bewegung.

- Wenn möglich, **verwenden Sie eine subtile Animation auf der Maus,** um interaktive Elemente unter der Maus anzuzeigen.

- Wenn Sie sich in Ihren Features stark auf Animationen verlassen, stellen Sie eine Möglichkeit bereit, sie lokal (für alle Ihre Funktionen) als Option im Dialogfeld **Tools > Optionen** **zu deaktivieren.**

- **Es sollte jeweils nur eine Animation erfolgen** und nur eine Information vermitteln. Mehr als ein Objekt, das sich bewegt oder versucht, mehrere Dinge zu vermitteln, kann verwirrend sein.

- **Subtilität ist wichtig.** In den meisten Fällen muss Animation nicht die Aufmerksamkeit des Benutzers verlangen, um seinem Zweck zu dienen. Subtile Änderungen in Timing, Sequenzierung und Verhalten können die Wahrnehmung erheblich beeinflussen und den Unterschied zwischen einer effektiven und ineffektiven Animation ausmachen.

- Wenn Sie Animationen verwenden, um auf etwas aufmerksam zu machen, **stellen Sie sicher, dass es sich lohnt, den**Gedankengang des Benutzers zu unterbrechen.

- **Beim Anzeigen von Fortschritt oder Status** durch Animation:

  - Beenden Sie die Anzeige von Fortschrittsbewegungen, wenn der zugrunde liegende Prozess nicht vorankommt.

  - Unterscheiden Sie unbestimmte Prozesse von bestimmten Prozessen.

  - Stellen Sie sicher, dass eine Animation über identifizierbare Abschluss- und Fehlerzustände verfügt.

  - Minimieren Sie die Verwendung von Effektanimationen, die den Status anzeigen, und stellen Sie sicher, dass sie einen echten Wert haben, indem Sie zusätzliche Informationen über die tatsächliche Verwendung bereitstellen. Beispiele hierfür sind vorübergehende Statusänderungen und Notfälle

#### <a name="animation-donts"></a>Animation don'ts:

- Verwenden Sie keine kleinen Bewegungen (Bewegung auf kleinem Grundriss). Bevorzugen Sie Fades und Änderungen gegenüber bewegten Objekten.

- Verwenden Sie keine Animationen, die über eine große Fläche von Bildschirmimmobilien stattfinden. Unabhängig von der Größe lenkt dieser Animationsstil den Benutzer ab.

- Verwenden Sie keine Animationen, die nichts mit dem Objekt zu tun haben, auf das sich der Benutzer derzeit konzentriert oder mit dem er interagiert.

- Verwenden Sie keine Animationen, die eine Benutzerinteraktion erfordern, um den Status zurückzusetzen, z. B. den Benutzer zwingen, auf eine blinkende Benachrichtigung zu reagieren, damit sie nicht mehr blinkt. Die Interaktion mit ihnen sollte in irgendeiner Weise ausreichen, um sie zu entlassen.

Weitere Informationen zu Anwendungen für diese bewährten Methoden finden Sie unter [Animationsmuster](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Animationsmetriken

- Das System sollte sichtbar auf Benutzergesten in weniger als 10 Millisekunden reagieren.

- Animierte Übergänge sollten nicht länger als 500 Millisekunden dauern.

- Eine Möglichkeit, Übergänge zu kompensieren, die längere Zeiten erfordern, besteht darin, sie in zwei Teile zu trennen. Der erste Teil einer Animation kann z. B. der leere Inhaltscontainer (bis zu 500 Millisekunden) sein, gefolgt vom Inhalt, der in den Container ausgeblendet wird (bis zu 500 Millisekunden).

- Für Berechnungsgemäße Ladezeiten wird ein determinantes Fortschrittsindikator (Prozent-Fortschrittsindikator) bevorzugt.

- Für Ladezeiten, die nicht berechnet werden können, ist ein ausgelasteten Indikator wie ein Cursor oder eine eingebettete Spinning-Animation (Lade- oder Arbeitsanzeige) geeignet.

### <a name="animation-as-communicator"></a>Animation als Kommunikator
In Visual Studio-Benutzeroberfläche funktioniert Animation nur als Kommunikationstool.  Es wird verwendet, um eine Vielzahl von Informationen zu kommunizieren, wie z. B. strukturelle Änderungen in der Benutzeroberfläche (z. B. wenn ein Menü geöffnet oder geschlossen wird). Animation kann helfen, das zeitabhängige Verhalten komplexer Systeme zu visualisieren, z. B. die Visualisierung des Installationsfortschritts. Animationen können auch verwendet werden, um aufmerksamkeit mit Warnungen und Benachrichtigungen zu erregen.

 UI-Animationen funktionieren in der Regel auf vier Arten: Visualisieren, Aufmerksamkeit erregen, simulieren und Reaktionszeiten/Fortschrittsindikatoren.

#### <a name="visualize"></a>Visualisieren
Animationkannien können die dreidimensionale Natur von Objekten hervorheben und es Benutzern erleichtern, ihre räumliche Struktur zu visualisieren. Um dies zu erreichen, muss die Animation das Objekt möglicherweise in einem vollen Kreis drehen, es langsam hin und her drehen oder das Objekt näher bringen und seine Größe leicht erhöhen, um Rollover oder Fokus hervorzuheben.

Obwohl dreidimensionale Objekte mit Benutzersteuerung verschoben werden können, sollte der Designer im Voraus (programmgesteuert oder manuell) bestimmen, wie eine Bewegung, die ein optimales Verständnis des Objekts bietet, am besten animiert werden kann. Diese programmierte Animation kann dann vom Benutzer aktiviert werden, indem der Cursor über das Objekt platziert wird, während benutzergesteuerte Bewegungen erfordern, dass der Benutzer versteht, wie das Objekt bearbeitet wird. Beschränken Sie die Bewegung auf eine einzelne Achse oder Ausrichtung zu einem Zeitpunkt; entweder skalieren, drehen oder übersetzen, aber nicht mehr als eine gleichzeitig tun.

Die Kategorie Visualisieren umfasst die Aspekte Daten, Beziehungen, Status, Struktur, Reihenfolge und Zeit.

##### <a name="data"></a>Daten
Veranschaulichen Sie komplexe und variable Informationen:

- Wechseln durch Informationsvisualisierungen wie Diagramme und Diagramme

- Schritt durch eine Sequenz, Führung und Paging

- Aufrufen von Details, Zeigen und Hervorheben bestimmter Informationen

- Überlagerung von Details und zusätzlichen Informationen über einem fokussierten Element

- Morphing von einer strukturellen oder organisatorischen Darstellung zu einer anderen

- Darstellung von Änderungen im Laufe der Zeit mithilfe von Zeitschiebereglern, Jog-and-Shuttle-Rädern und Transportsteuerungen (Wiedergabe, Stopp und Pause)

##### <a name="relationships"></a>Beziehungen

- Veranschaulichen, wie Sich Elemente zueinander beziehen oder welche Artikel sich auf einen bestimmten Artikel beziehen

- Anzeigen von Hierarchien und Eltern-Kind- oder Geschwisterbeziehungen

- Ein Element erzeugt ein anderes

- Ein Element wird auf ein anderes Element minimiert

- Ein Element, das an ein anderes gebunden ist

##### <a name="state"></a>State

- Inhaltsaktualisierungen

- Benutzerfokus und Auswahl

- Status

- Errors

##### <a name="structure"></a>Struktur

- Pivotieren der Struktur auf einem Knoten

- Neuausrichtung

- Minimieren und maximieren oder erweitern und reduzieren

##### <a name="sequence"></a>Sequenz

- Diashow-Sequenz

- Blättern durch Bilder

##### <a name="time"></a>Time

- Anzeigen von Änderungen im Zeitverlauf, Zeitraffer und Screencast

- Wechseln zum Papierkorb, Rückgängigmachen und Wiederholen

- Historische Wiederherstellung des historischen Zustands

#### <a name="attract-attention"></a>Aufmerksamkeit
Wenn das Ziel darin besteht, die Aufmerksamkeit des Benutzers auf ein einzelnes Element aus mehreren Elementen zu lenken oder den Benutzer auf aktualisierte Informationen aufmerksam zu machen, kann eine Animation angemessen sein. Beispielsweise kann die Startseite Ihrer Anwendung eine Schaltfläche Erste Schritte verwenden, die nach dem Laden der Seite an Ort und Stelle gleitet.

In der Regel zieht das letzte sich bewegende Element auf dem Bildschirm die Aufmerksamkeit des Benutzers auf sich.  In einer Reihe animierter Elemente folgt die Aufmerksamkeit des Benutzers dem letzten sich bewegenden Objekt.

##### <a name="alert"></a>Warnung

- Alarmieren Sie den Benutzer, erhalten Sie Aufmerksamkeit, zeigen Sie den Fortschritt an

- Zeigen Sie an, dass etwas korrekt oder falsch ausgeführt wird, oder zeigen Sie Fortschritts- oder Fortschrittsänderungen an

- Benutzer während einer Aufgabe auffordern, z. B. weitere Informationen online zu finden oder mehr über die aktuelle Aufgabe zu erfahren

##### <a name="notifications"></a>Benachrichtigungen

- Warnung des Benutzers über eine Fehlerbedingung

- Unterbrechen Sie den Benutzer, um zu sehen, ob er sich um etwas anderes kümmern möchte

- Informieren Sie den Benutzer vorsichtig, dass ein Prozess abgeschlossen oder geändert wurde, z. B. wenn ein Download abgeschlossen ist.

#### <a name="simulate"></a>Simulieren
Diese Kategorie umfasst Körperlichkeit und Dimensionalität.

- Veranschaulichen Sie, woher Objekte kommen oder wohin sie

- Erweitern und reduzieren oder öffnen und schließen

- Schwenken, Scrollen und Seitenumdrehungen

- Stapeln und Z-Ordering

- Karussell und Akkordeon

- Kippen und Drehen der Benutzeroberfläche

#### <a name="response-and-progress-indicators"></a>Reaktions- und Fortschrittsindikatoren
Fortschrittsindikatoren haben einige bemerkenswerte Vorteile:

- Sowohl determinierte als auch unbestimmte Fortschrittsindikatoren versichern dem Benutzer, dass das System nicht abgestürzt ist und an dem Problem arbeitet.

- Determinierte Indikatoren geben dem Benutzer ein Gefühl dafür, wie weit die Aktion voranschreitet, sowie ein Gefühl, dem Ziel näher zu kommen.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Animationsmuster

### <a name="overview"></a>Übersicht
Animationen in Visual Studio dienen einer bestimmten Funktion, ohne die Benutzerproduktivität zu beeinträchtigen. Im Allgemeinen sollten Animationen in Visual Studio wie gesagt sein:

- Klein und unauffällig

- Natürlich und realistisch

- Subtil und gedämpft

- Schnell und effizient

- Entspannt, nicht eilig

Diese Abbildung zeigt die Animationsstile, die wir für Visual Studio empfehlen. Keine Animation oder subtile Animationen wie Ein-/Ausblenden werden am häufigsten verwendet. Es gibt begrenzte Anwendung von Bewegungsanimationen wie Erweitern und Kontraktieren, X- und Y-Positionsänderung und Rotation.

![Empfohlene Animationsstile für Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Empfohlene Animationsstile für Visual Studio

#### <a name="appear-and-disappear"></a>Erscheinen und verschwinden
Bei diesem Muster wechselt ein Element ohne Übergangsanimation von sichtbar zu anicht sichtbar und zurück.

![Animation erscheinen und ausverschwinden](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animation erscheinen und ausverschwinden

##### <a name="correct-usage"></a>Korrekte Verwendung
Frische UI-Elemente, die sofort angezeigt oder verschwinden müssen, damit der Benutzer weder abgelenkt noch behindert wird. Darüber hinaus können langsam eimperliche Animationen als Leistungswiderstand wahrgenommen werden, der mit dem Stil "Erscheinen und Verschwinden" nicht auftritt.

##### <a name="incorrect-usage"></a>Falsche Verwendung
Fälle, in denen die Benutzeroberfläche so abrupt angezeigt wird, dass der Benutzer keine Ahnung hat, was passiert ist, und das Hinzufügen einer Animation würde beim Kontextverständnis helfen.

##### <a name="animation-properties"></a>Animationseigenschaften
Die Zeitverzögerung beträgt in der Regel null Sekunden.

##### <a name="examples"></a>Beispiele
- Automatisches Ausblenden von Toolfenstern

- Tastaturaktivierte Editor-Benutzeroberfläche, wie IntelliSense und Parameter-Hilfe

- Expand-and-Collapse-Codebereiche

#### <a name="fade-in-and-fade-out"></a>Ein- und Ausblenden
Bei diesem Muster wechselt ein UI-Element von nicht sichtbar (0% Deckkraft) zu sichtbar (100% Deckkraft) oder umgekehrt.

![Ein- und Ausblendanimation](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Ein- und Ausblendanimation

##### <a name="correct-usage"></a>Korrekte Verwendung
Dies ist die am häufigsten empfohlene UI-Animation. Es ist ein subtiler Effekt, der Interesse hinzufügt, ohne den Fluss zu unterbrechen. In einigen Fällen erkennt der Benutzer möglicherweise nicht einmal, dass es eine Animation gibt, die ein glattes und fließendes UI-System erkennt.

##### <a name="animation-properties"></a>Animationseigenschaften

- Starten der Deckkraft: 0% für Einbleichen, 100% für Ausblendung

- Endopazität: 100% für Einbleichen, 0% für Ausblendung

- Dauer: 200 Millisekunden im Einzel, 100 Millisekunden bei Verwendung als Teil einer Kombinationsanimationssequenz

- Easing-Stil: Sine InOut

##### <a name="examples"></a>Beispiele

- Automatisches Ausblenden von Toolfenstern

- Menü geöffnet und geschlossen

- Hintergrund- und Vordergrund-Tabübergänge

#### <a name="color-blend-from-a-to-b"></a>Farbmischung von A nach B
Mit diesem Muster ändert sich ein UI-Element von Farbe A in Farbe B.

![Farbverschmelzungsanimation](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Farbverschmelzungsanimation

##### <a name="correct-usage"></a>Korrekte Verwendung
Als animierter Übergang, wenn ein UI-Element die Farbe von einem Kontext oder Zustand in einen anderen ändert.

##### <a name="animation-properties"></a>Animationseigenschaften

- Startfarbe: UI-spezifisch

- Endfarbe: UI-spezifisch

- Dauer: 200 Millisekunden im Einzel, 100 Millisekunden bei Verwendung als Teil einer Kombinationsanimationssequenz

- Easing-Stil: Sine InOut

##### <a name="examples"></a>Beispiele

- Dokumentfensterzustandsübergänge (aktiv, zuletzt aktiv und inaktiv)

- Werkzeugfensterzustandsübergänge (fokussiert und unfokussiert)

#### <a name="expand-and-contract"></a>Erweitern und Vertragen
Bei diesem Muster wird ein UI-Element in X, Y oder in beide Richtungen erweitert.

![Erweiterungs- und Vertragsanimation](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Erweiterungs- und Vertragsanimation

##### <a name="correct-usage"></a>Korrekte Verwendung
Als animierter Übergang, wenn ein UI-Element die Größe von einem Kontext in einen anderen ändert.

##### <a name="animation-properties"></a>Animationseigenschaften

- X-Skala: % oder spezifische Dimension (in Pixel)

- Y-Skala: % oder spezifische Dimension (in Pixel)

- Ankerposition: in der Regel oben links (für Links-nach-rechts-Sprachen) oder von oben rechts (für Rechts-nach-links-Sprachen)

- Dauer: 200 Millisekunden im Einzel, 100 Millisekunden bei Verwendung als Teil einer Kombinationsanimationssequenz

##### <a name="examples"></a>Beispiele

- Architektur-Explorer-Panel erweitern und reduzieren

- Visual Studio 2017 Startseite Element erweitern und reduzieren

#### <a name="x-y-position-change"></a>X-Y Positionsänderung
Bei diesem Muster ändert ein UI-Element seine X- oder Y-Position oder beides.

![X-Y-Positionsänderungsanimation](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X-Y-Positionsänderungsanimation

##### <a name="correct-usage"></a>Korrekte Verwendung
Als animierter Übergang, wenn ein UI-Element die Position von einem Kontext in einen anderen ändert.

##### <a name="animation-properties"></a>Animationseigenschaften

- Start X und Y-Position: UI-spezifisch

- Endung X und Y-Position: UI-spezifisch

- Bewegungspfad: keine

- Dauer: 200 Millisekunden im Einzel, 100 Millisekunden bei Verwendung als Teil einer Kombinationsanimationssequenz

- Easing-Stil: Sine InOut

##### <a name="example"></a>Beispiel
Tab-Neuanordnung

#### <a name="rotate"></a>Drehen
Bei diesem Muster wird das UI-Element gedreht.

![UI-Elementrotationsanimation](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />UI-Elementrotationsanimation

##### <a name="correct-usage"></a>Korrekte Verwendung
Nur für den unbestimmten Spinning Progress Indikator.

##### <a name="animation-properties"></a>Animationseigenschaften

- Drehgrad: 360

- Rotationszentrum: Mitte des Objekts

- Dauer: kontinuierlich

##### <a name="example"></a>Beispiel
Unbestimmte Fortschrittsanzeige (Spinnen)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Häufige Shell-UI-Aktionen und empfohlene Animationen

#### <a name="tab-open"></a>Tab geöffnet
![Tab-Open-Animation](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Tab-Open-Animation

- Stil: erscheinen

- Dauer: null Sekunden

#### <a name="tab-close"></a>Tab-Schließen
![Tab-Close-Animation](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Tab-Close-Animation

- Stil: X Positionsänderung

- Dauer: 200 Millisekunden

#### <a name="tab-reorder"></a>Tab-Neubestellung
![Animation "Neu anordnen" in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Tab-Neuanordnen-Animation

- Stil: X Positionsänderung

- Dauer: 200 Millisekunden

#### <a name="close-floating-document"></a>Schließen eines unverankerten Dokuments
![Schließen der unverankerten Dokumentanimation](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Schließen der unverankerten Dokumentanimation

- Stil: erscheinen

- Dauer: 200 Millisekunden

#### <a name="window-state-transition"></a>Fensterzustandsübergang
![Fensterzustandsübergangsanimation](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Fensterzustandsübergangsanimation

- Stil: Um mit anderen Fenstern konsistent zu sein, lassen Sie das aktuelle Betriebssystem die Dokumentanimation schließen.

- Dauer: 200 Millisekunden

#### <a name="menu-open"></a>Menü geöffnet
![Menü-Offene Animation](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Menü-Offene Animation

- Stil: einblenden

- Dauer: 200 Millisekunden

#### <a name="menu-close"></a>Menü schließen
![Menü-Schließanimation](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Menü-Schließanimation

- Stil: Ausblenden

- Dauer: 200 Millisekunden

#### <a name="auto-hide-tool-window-reveal"></a>Auto-Hide-Tool-Fenster offenbaren
![Auto-Hide-Tool-Fenster zeigen Animation](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Auto-Hide-Tool-Fenster zeigen Animation

- Stil: erscheinen

- Dauer: null Sekunden
