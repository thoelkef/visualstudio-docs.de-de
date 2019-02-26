---
title: Animationen für Visual Studio | Microsoft-Dokumentation
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d132c9689348fa728fc639d2aa3c8ecd8ba9e25
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796789"
---
# <a name="animations-for-visual-studio"></a>Animationen für Visual Studio
## <a name="animation-fundamentals"></a>Animation-Grundlagen

### <a name="animation-best-practices-in-visual-studio"></a>Animation, bewährte Methoden in Visual Studio
Führen Sie diese Regeln aus, um konsistente und benutzerfreundliche animationsstile für Visual Studio-IDE sicherzustellen.

-   **Werden Sie selektive.** Beschränken Sie Animationen, die bestimmte Zwecke zu erfüllen.

-   **Zeitpunkt und Geschwindigkeit sind wichtig,** um sicherzustellen, dass es sich bei Übergängen können Sie schnelle und natürliche:

    -   Führen Sie animierten Übergänge in eine halbe Sekunde (500 Millisekunden).

    -   Animationen, die häufig auftreten würden müssen schnell genug sein, dass sie den Workflow des Benutzers nicht unterbrechen. Sehen Sie sich die Animation in einer Schleife aus, und passen Sie die zeitliche Steuerung aus, bis die richtige hält.

    -   Animationen darf nicht sein, so schnell oder bedürfen, es ist schwer zu verstehen, aber nicht so langsam ist, dass es eine ungeduldig der Übergang abgeschlossen ist.

    -   Verwenden Sie Variablen zeitliche Steuerung, um die Bedeutung hervorzuheben. Z. B. beim Navigieren durch eine Sequenz von Elementen in einem Diagramm beschleunigt über die Übergänge zwischen den Elementen und dann verlangsamt sich auf wichtige Elemente konzentrieren.

-   **Mithilfe der schrittweisen nicht lineare Beschleunigung** von einem Zustand in einen anderen, bietet einen Überblick über die schwierigen Situationen ruhig und natürliche verschieben.

-   Wenn möglich, **verwenden Sie eine geringfügige Animation, wenn darauf gezeigt wird** interaktive Elemente unter der Maus an.

-   Wenn Sie stark Animationen in Ihrer Funktionen, dann benötigen **bieten eine Möglichkeit zum Abschalten** lokal (für alle Funktionen) als Option in der **Tools > Optionen** Dialogfeld.

-   **Nur eine einzige Animation erfolgen soll, zu einem Zeitpunkt** und nur ein Teil der Informationen zu vermitteln. Mehr als ein Objekt verschieben, oder es wird versucht, mehrere Punkte zu vermitteln kann verwirrend sein.

-   **Besonderheit ist wichtig.** In den meisten Fällen keine Animation, bei Bedarf der Aufmerksamkeit des Benutzers auf die ihr Zweck dienen. Geringfügige Änderungen in der zeitlichen Steuerung, Sequenz und Verhalten können können die Wahrnehmung erheblich beeinträchtigt, und den Unterschied zwischen einer Animation effektiv und ineffizient.

-   Wenn Animationen zu verwenden, um die Aufmerksamkeit auf etwas zu lenken **stellen Sie sicher, dass es lohnt sich den Benutzer unterbrechen**den Gedankengang.

-   **Beim Anzeigen von Fortschritt oder Status** über Animation:

    -   Nicht mehr ausgeführt Bewegung bei der zugrunde liegenden Prozess Vorlauf ist nicht.

    -   Unterscheiden Sie unbestimmt Prozesse von bestimmte Prozesse.

    -   Stellen Sie sicher, dass eine Animation identifizierbaren Abschluss und Fehler Status verfügt.

    -   Minimieren Sie die Verwendung von Auswirkungen Animationen, die der Status, und stellen sicher, dass sie echten Wert aufweisen, durch zusätzliche Informationen von der tatsächlichen Nutzung. Beispiele hierfür sind vorübergehende statusänderungen und Notfälle

#### <a name="animation-donts"></a>Animation-Empfehlungen:

-   Verwenden Sie keine kleine Bewegungen (Verschieben von Daten in einen kleinen Speicherbedarf). Bevorzugt wird ausgeblendet und über das Verschieben von Objekten ändert.

-   Verwenden Sie keine Animationen, die über eine große Fläche Bildschirmplatz ausgeführt werden. Unabhängig von Größe ist diese Art von Animation für den Benutzer verwirrend.

-   Verwenden Sie Animationen, die nicht mit das Objekt, dem der Benutzer auf gerade fokussiert ist oder der Interaktion mit nicht.

-   Verwenden Sie keine Animationen, die eine Benutzerinteraktion, um den Zustand, z. B. zwingen den Benutzer auf eine blinkende Benachrichtigung damit darauf blinken beenden reagieren zurücksetzen erfordern. In keiner Weise mit ihnen interagieren sollte ausreichen, um sie zu schließen.

Weitere Informationen zu Anwendungen, die für diese bewährten Methoden finden Sie unter [Animation Muster](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Animation-Metriken

-   Das System sollte sichtbar auf Benutzergesten in weniger als 10 Millisekunden zu reagieren.

-   Animierten Übergänge darf nicht länger als 500 Millisekunden abgeschlossen werden.

-   Eine Möglichkeit um Übergänge zu kompensieren, die längere Zeiträume zu erfordern, ist für die Trennung in zwei Teile. Der erste Teil einer Animation kann z. B. die leere Inhaltscontainer (bis zu 500 Millisekunden), gefolgt von der Inhalte ausblenden von Fenstern in den Container (bis zu 500 Millisekunden) sein.

-   Für die Ladezeiten, die berechnet werden können, wird eine Determinante Statusanzeige (Prozent-fertig Statusanzeige) bevorzugt.

-   Für die Ladezeiten, die nicht berechnet werden können, ist ein auslastungsindikator angezeigt, wie ein Cursor oder eine eingebettete rotierende Animation (geladen oder Verwendung Indikators) geeignet.

### <a name="animation-as-communicator"></a>Animation als communicator
-Funktionen in Visual Studio-Benutzeroberfläche Animation nur als ein Tool für die Kommunikation.  Es wird verwendet, um eine Vielzahl von Informationen, wie etwa die strukturellen Änderungen in der Benutzeroberfläche (z. B., wenn ein Menü öffnet oder schließt) zu kommunizieren. Animation kann helfen, das zeitabhängige Verhalten komplexer Systeme, wie die Installation Fortschritt Visualisierung visualisieren. Animationen können auch verwendet werden, um die Aufmerksamkeit mit Warnungen und Benachrichtigungen zu gewinnen.

 UI-Animationen in der Regel funktionieren, es gibt vier Möglichkeiten: visualisieren, wecken, zu simulieren, und die Antwort Zeiten/Bearbeitung Indikatoren.

#### <a name="visualize"></a>Visualisieren
Animation kann hervorheben die dreidimensionale Art von Objekten und für Benutzer zum Visualisieren der Struktur ihrer räumlichen erleichtern. Um dies zu erreichen, kann die Animation müssen, starten das Objekt in einen vollständigen Kreis zu langsam hin und her aktivieren oder verschieben Sie das Objekt näher und leicht erhöhen die Größe um Rollover oder den Fokus zu verdeutlichen.

Obwohl bei dreidimensionale Objekten mit-Steuerelement verschoben werden können, der Designer sollte (programmgesteuert oder manuell) im Voraus bestimmen animieren wie zur optimalen eine Verschiebung, die optimalen Überblick über das Objekt bereitstellt. Diese Animation kann programmiert und dann vom Benutzer durch Platzieren den Cursor auf das Objekt, aktiviert werden, während Benutzer gesteuerte Bewegungen der Benutzer zu verstehen, wie das Objekt ändern müssen. Beschränken Sie die Bewegung auf eine einzelne Achse oder Ausrichtung zu einem Zeitpunkt. entweder skalieren, drehen, oder übersetzt werden, jedoch nicht mehrere gleichzeitig tun.

Die Kategorie "visualisieren" enthält die Aspekte der Daten, Beziehungen, State, Struktur, Sequenz und Zeit.

##### <a name="data"></a>Daten
Informationen zu komplexen und Variablen zu veranschaulichen:

-   Durchsuchen von Informationen Visualisierungen wie Diagramme und Grafiken

-   Eine Sequenz durchlaufen, Führung und paging

-   Details aufrufen, verweisen und markieren spezifische Informationen

-   Überlagern Details und zusätzliche Informationen über ein Fokuselement

-   Verwandeln in eine andere aus einer strukturellen oder die Organisationseinheit Darstellung

-   Die Änderungen im Zeitverlauf mit der Zeit-Schieberegler, dauerlauf-Shuttle Wheels und Transport-Steuerelemente (Wiedergabe-, Stopp- und anhalten) darstellen.

##### <a name="relationships"></a>Beziehungen

-   Veranschaulicht, wie Elemente miteinander in Beziehung stehen, oder welche Elemente mit einem bestimmten Element beziehen.

-   Hierarchien und über-und untergeordneten oder nebengeordneten Beziehungen anzeigen

-   Ein Element erzeugt eine andere

-   Ein Element wird auf ein anderes Element minimiert.

-   Ein Element in eine andere verbundene

##### <a name="state"></a>Zustand

-   Die Inhaltsupdates

-   Den Benutzerfokus und Auswahl

-   Status

-   Fehler

##### <a name="structure"></a>Struktur

-   Pivotieren die Struktur auf einem Knoten

-   Neuorientieren

-   Zu minimieren Sie und Maximieren Sie, oder Erweitern Sie sowie reduzieren

##### <a name="sequence"></a>Sequenz

-   Diaschau Sequenz

-   Länger Papierseiten durch Bilder

##### <a name="time"></a>zeit

-   Anzeigen von Änderungen im Laufe der Zeit, Zeitsprung-screencast

-   Verschieben Sie in den Papierkorb, Rückgängig / Wiederholen

-   Wiederherstellen des historischen Zustands

#### <a name="attract-attention"></a>Wecken Sie
Wenn das Ziel zum Zeichnen der Aufmerksamkeit des Benutzers auf ein einzelnes Element aus mehreren oder Benachrichtigung des Benutzers auf aktualisierte Informationen ist, kann eine Animation geeignet. Startseite für Ihre Anwendung kann z. B. eine Schaltfläche "Erste Schritte" können das an Stelle verschoben werden soll, nachdem die Seite geladen.

Als Faustregel gilt anzieht das letzte verschieben Element auf dem Bildschirm die Aufmerksamkeit des Benutzers.  In einer Reihe von animierten Elemente wird die Aufmerksamkeit des Benutzers das letzte Bewegungsobjekt folgen.

##### <a name="alert"></a>Warnung

-   Warnen Sie die Benutzer, erhalten Sie Ihre Aufmerksamkeit zu, die den zeigen Fortschritt an

-   Zeigen Sie an, dass etwas richtig oder falsch ausgeführt wird oder zeigen Fortschritt oder Status Änderungen an

-   Auffordern Sie Benutzer, während eine Aufgabe, wie z. B. Suchen nach weiteren Informationen online oder Informationen zu den aktuellen task

##### <a name="notifications"></a>Benachrichtigungen

-   Warnen Sie die Benutzer zu einer fehlerbedingung

-   Unterbrechen Sie den Benutzer aus, um festzustellen, ob sie etwas anderem Aufmerksamkeit schenken müssen möchten

-   Vorsichtig informieren Sie den Benutzer, den ein Prozess abgeschlossen ist oder geändert haben, z. B. wenn ein Download abgeschlossen ist.

#### <a name="simulate"></a>Simulieren
Diese Kategorie behandelt Physicality und Dimensionalität.

-   Veranschaulicht, in denen Objekte aus stammen oder wo auf

-   Erweitern und reduzieren oder zu öffnen und schließen

-   Schwenken, Durchführen eines Bildlaufs und Seite aktiviert.

-   Stapeln und Z-Anordnung

-   Karussellsicht und ' Accordion '

-   Kippen und Drehen von der Benutzeroberfläche

#### <a name="response-and-progress-indicators"></a>Antwort der Status-und Status
Statusanzeigen haben einige wichtige Vorteile:

-   Beide bestimmte und unbestimmt Statusanzeigen versichern den Benutzer, den das System nicht abgestürzt ist, und arbeitet an der das Problem.

-   Bestimmte Indikatoren können Benutzer, die, den ein Eindruck davon, wie weit die Aktion fortgesetzt wird, den sowie einen Eindruck, näher to the Fertig stellen.

##  <a name="BKMK_AnimationPatterns"></a> Animation-Muster

### <a name="overview"></a>Übersicht
Animationen in Visual Studio sind für eine bestimmte Funktion zu erhalten, ohne dass behindert die Produktivität der Benutzer vorgesehen. Animationen in Visual Studio sollte in der Regel wie folgt aussehen:

-   Klein und unauffällig

-   Natürliche und realistische

-   Geringfügige und sind daher bei gedämpften

-   Schnelle und effiziente

-   Gelockerte, nicht Eile

Diese Abbildung zeigt die animationsstile, es wird empfohlen für Visual Studio. Keine Animationen oder geringfügige Animationen wie ein- / ausblenden, werden die am häufigsten verwendet. Eingeschränkte Anwendung von Animationen verschieben, wie die Erweiterung und Verkleinerung vorhanden ist, die X- und Y-position ändern und Drehung.

![Empfohlene animationsstile für Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-A_VSAnimStyles")<br />Empfohlene Animationsstile für Visual Studio

#### <a name="appear-and-disappear"></a>Angezeigt und ausgeblendet werden
Bei diesem Muster wechselt ein Element aus sichtbar, außerhalb-des-Ansicht und ohne eine übergangsanimation zurück.

![Angezeigt und ausgeblendet werden Animation](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-B_AppearAndDisappear")<br />Angezeigt und ausgeblendet werden animation

##### <a name="correct-usage"></a>Richtige Verwendung
Neue UI-Elemente müssen sofort erscheinen oder verschwinden, sodass der Benutzer weder abgelenkt noch verdeckt wird. Darüber hinaus möglicherweise langsam zu verschiebende Animationen als ein Ziehvorgang Leistung angesehen werden die nicht mit dem Format angezeigt und ausgeblendet auftritt.

##### <a name="incorrect-usage"></a>Falsche Verwendung
Fälle, in der Benutzeroberfläche wird plötzlich die Benutzer keine Ahnung hat, was passiert ist, und eine Animation hinzufügen würde mit kontextverständnis zu helfen.

##### <a name="animation-properties"></a>Animationseigenschaften
Die zeitliche Verzögerung beträgt in der Regel 0 (null) Sekunden.

##### <a name="examples"></a>Beispiele
-   Automatisches Ausblenden von Toolfenstern

-   Tastatur aktivierten Editor wie IntelliSense und die Parameterhilfe-Benutzeroberfläche

-   Erweitern und reduzieren Codebereiche

#### <a name="fade-in-and-fade-out"></a>Dem Einblenden und Ausblenden der videoüberlagerung benötigt
Mit diesem Muster ist ein Element der Benutzeroberfläche, die aus nicht sichtbar (0 % Deckkraft) geht in sichtbar (100 % Deckkraft) oder umgekehrt.

![Dem Einblenden und Ausblenden der videoüberlagerung benötigt Animation](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-C_FadeInFadeOut")<br />Dem Einblenden und Ausblenden der videoüberlagerung benötigt animation

##### <a name="correct-usage"></a>Richtige Verwendung
Dies wird am häufigsten animierte Benutzeroberfläche empfohlen. Es ist eine geringfügige Auswirkungen, die relevanten hinzufügt, ohne Unterbrechung von Flow. In einigen Fällen kann der Benutzer nicht einmal bewusst ist, dass es ist eine Animation, empfindungsfähiges ein Smooth Streaming und UI-System übertragen.

##### <a name="animation-properties"></a>Animationseigenschaften

-   Starten Sie die Deckkraft: 0 % für das Einblenden der videoüberlagerung, 100 % für das Ausblenden der videoüberlagerung benötigt

-   Beenden die Deckkraft: 100 % für dem einblenden, Ausblenden der videoüberlagerung benötigt % 0

-   Dauer: 200 Millisekunden eigenständige, 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination

-   Einfachere Format an: Sinus InOut

##### <a name="examples"></a>Beispiele

-   Automatisches Ausblenden von Toolfenstern

-   Menü öffnen und schließen

-   Hintergrund- und Vordergrundfarben Registerkarte Übergänge

#### <a name="color-blend-from-a-to-b"></a>Farbe von Blend von A nach B
Bei diesem Muster wird nun ein Element der Benutzeroberfläche von Farbe ein Farbe b

![Farbüberblendung](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-D_ColorBlend")<br />Blend-Farbanimation

##### <a name="correct-usage"></a>Richtige Verwendung
Als einen animierten Übergang, wenn ein Element der Benutzeroberfläche aus einem Kontext- oder Statusinformationen in eine andere Farbe ändert.

##### <a name="animation-properties"></a>Animationseigenschaften

-   Startfarbe: UI-spezifischen

-   Endfarbe: UI-spezifischen

-   Dauer: 200 Millisekunden eigenständige, 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination

-   Einfachere Format an: Sinus InOut

##### <a name="examples"></a>Beispiele

-   Dokumentieren Sie Fenster Statusübergänge (aktiv, letzte aktive und inaktive)

-   Statusübergänge für Fenster-Tool (mit Fokus und ohne Fokus)

#### <a name="expand-and-contract"></a>Erweiterung und Verkleinerung
Bei diesem Muster wird ein Element der Benutzeroberfläche erweitert, in der X-, Y- oder beide Richtungen.

![Erweiterung und Verkleinerung Animation](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-E_ExpandContract")<br />Erweiterung und Verkleinerung der animation

##### <a name="correct-usage"></a>Richtige Verwendung
Als einen animierten Übergang, wenn ein Element der Benutzeroberfläche aus einem Kontext in eine andere Größe ändert.

##### <a name="animation-properties"></a>Animationseigenschaften

-   X-Skalierung: % oder einer bestimmten Dimension (in Pixel)

-   Y skalieren: % oder einer bestimmten Dimension (in Pixel)

-   Verankern Sie die Position: im Allgemeinen die obere linke (für Links-nach-rechts-Sprachen) oder rechts (für rechts-nach-links-Sprachen)

-   Dauer: 200 Millisekunden eigenständige, 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination

##### <a name="examples"></a>Beispiele

-   Architektur-Explorer-Bereich erweitern und reduzieren

-   Visual Studio 2017-Startseite-Element erweitern und reduzieren

#### <a name="x-y-position-change"></a>X-Y-position ändern
Bei diesem Muster ändert ein Element der Benutzeroberfläche an seine X- oder Y-Position oder beides.

![X-Y-Position ändern Animation](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-F_XYPositionChange")<br />X-und Y-Position ändern animation

##### <a name="correct-usage"></a>Richtige Verwendung
Als einen animierten Übergang, wenn ein Element der Benutzeroberfläche in eine andere Position aus einem Kontext ändert.

##### <a name="animation-properties"></a>Animationseigenschaften

-   Starten von X- und Y-Position: UI-spezifischen

-   Am Ende X und Y-Position: UI-spezifischen

-   Animationspfad: keine

-   Dauer: 200 Millisekunden eigenständige, 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination

-   Einfachere Format an: Sinus InOut

##### <a name="example"></a>Beispiel
Registerkarte neuanordnung

#### <a name="rotate"></a>Drehen
Mit diesem Muster ist die dreht des Elements der Benutzeroberfläche aus.

![UI-Element Drehungsanimation](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-G_Rotate")<br />UI-Element Drehungsanimation

##### <a name="correct-usage"></a>Richtige Verwendung
Nur für die unbestimmten sich drehende Statusanzeige.

##### <a name="animation-properties"></a>Animationseigenschaften

-   Der Grad der Drehung: 360

-   Drehmittelpunkt: Mitte des Objekts

-   Dauer: kontinuierliche

##### <a name="example"></a>Beispiel
Unbestimmte Statusanzeige (rotierende)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Häufig verwendete Shell-UI-Aktionen und empfohlene Animationen

#### <a name="tab-open"></a>Registerkarte öffnen
![Registerkarte öffnen Animation](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-H_TabOpen")<br />Animation der Registerkarte öffnen

-   Style: angezeigt werden

-   Dauer: 0 (null) Sekunden

#### <a name="tab-close"></a>Registerkarte schließen
![Registerkarte schließen Animation](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-I_TabClose")<br />Animation der Registerkarte schließen

-   Style: Ändern Sie die X-position

-   Dauer: 200 Millisekunden

#### <a name="tab-reorder"></a>Registerkarte "neu anordnen
![Animation "neu anordnen" in Visual Studio Registerkarte](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-J_TabReorder")<br />Registerkarte "Reorder animation

-   Style: Ändern Sie die X-position

-   Dauer: 200 Millisekunden

#### <a name="close-floating-document"></a>Unverankertes Dokument schließen
![Unverankerte Dokument Animation schließen](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-K_CloseFloatingDocument")<br />Animation für unverankertes Dokument schließen

-   Style: angezeigt werden

-   Dauer: 200 Millisekunden

#### <a name="window-state-transition"></a>Statusübergang für Fenster
![Animation "fensterstatusübergang"](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-L_WindowStateTransition")<br />Animation "fensterstatusübergang"

-   Style: um mit anderen Fenstern konsistent zu sein, können Sie das aktuelle Betriebssystem, das die Dokument schließen Animation definieren.

-   Dauer: 200 Millisekunden

#### <a name="menu-open"></a>Menü öffnen
![Open Menüanimation](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-M_MenuOpen")<br />Animation der Menü öffnen

-   Style: dem einblenden

-   Dauer: 200 Millisekunden

#### <a name="menu-close"></a>Menü "Schließen"
![Schließen Menüanimation](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-N_MenuClose")<br />Menü schließen-animation

-   Style: Ausblenden der videoüberlagerung benötigt

-   Dauer: 200 Millisekunden

#### <a name="auto-hide-tool-window-reveal"></a>Automatisches Ausblenden Tool-Fenster anzeigen
![Automatisch ausblendbare Tool Enthüllen Fensteranimation](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-O_AutoHideToolWindowReveal")<br />Automatisch ausblendbare Tool Enthüllen Fensteranimation

-   Style: angezeigt werden

-   Dauer: 0 (null) Sekunden