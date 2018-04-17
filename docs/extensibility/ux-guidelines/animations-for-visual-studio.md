---
title: Animationen für Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f28e4d6f9ae1a0af060723047621b3e205d012c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="animations-for-visual-studio"></a>Animationen für Visual Studio
## <a name="animation-fundamentals"></a>Animation-Grundlagen  
  
### <a name="animation-best-practices-in-visual-studio"></a>Animation bewährten Methoden in Visual Studio  
Regeln Sie diese, um sicherzustellen, einheitliche und benutzerfreundliche animationsstile für Visual Studio-IDE.  
  
-   **Werden Sie selektive.** Beschränken Sie Animationen auf solche, die bestimmte Zwecken dienen.  
  
-   **Zeitliche Steuerung und Geschwindigkeit sind wichtig** um sicherzustellen, dass die Übergänge schnelle und natürliche können:  
  
    -   Führen Sie die animierte Übergänge innerhalb einer halben Sekunde (500 Millisekunden).  
  
    -   Animationen, die häufig auftreten würde müssen schnell genug sein, dass sie den Workflow des Benutzers nicht unterbrechen. Überwachen Sie die Animation in einer Schleife, und passen Sie die zeitliche Steuerung, bis es rechts idealer. 
  
    -   Animationen darf nicht sein, so schnell oder berücksichtigen, dass es ist schwierig zu verstehen sein, aber nicht so langsam ist, dass eine für die Umstellung auf Fertig stellen ungeduldig vereinfacht.  
  
    -   Verwenden Sie Variablen zeitlichen Steuerung, um die Wichtigkeit zu betonen. Z. B. beim Navigieren durch eine Sequenz von Elementen in einem Klassendiagramm über Übergänge zwischen Elementen zu beschleunigen Sie, und verlangsamen Sie wichtige Elemente konzentrieren.  
  
-   **Verwenden Sie die schrittweisen nichtlineare Beschleunigungsfunktionen** von einem Zustand in einen anderen ermöglicht einen Eindruck von ruhig und natürliche Bewegung.  
  
-   Wenn möglich, **eine geringfügige Animation verwenden, wenn darauf gezeigt wird** um interaktive Elemente unter der Maus anzugeben.  
  
-   Wenn Sie stark Animationen in Ihrer Funktionen, dann benötigen **bieten eine Möglichkeit zum Abschalten** lokal (für alle Features) als Option in der **Tools > Optionen** Dialogfeld.  
  
-   **Nur eine einzige Animation sollte zu einem Zeitpunkt auftreten** und nur ein Teil der Informationen zu vermitteln. Mehr als ein Objekt verschieben oder um mehrere Dinge zu übermitteln versucht kann verwirrend sein. 
  
-   **Besonderheit ist wichtig.** In den meisten Fällen keine Animation, bei Bedarf Benutzereingriff auf ihren Zweck dienen. Geringfügige Änderungen in der zeitlichen Steuerung, Sequenzierung und Verhalten können Gefühl können erheblich beeinträchtigt werden, und den Unterschied zwischen einer Animation effizient und effektiv wirkungslos.  
  
-   Wenn hervorzuheben, die eine Animation mithilfe **stellen Sie sicher, dass es lohnt sich den Benutzer unterbrechen**des Gedankengang.  
  
-   **Beim Anzeigen von Fortschritt oder Status** über Animation:  
  
    -   Fortschritt Bewegung angezeigt, wenn des zugrunde liegenden Prozesses Vorlauf ist nicht zu beenden. 
  
    -   Unterscheiden Sie unbestimmt Prozesse von bestimmte Prozesse.  
  
    -   Stellen Sie sicher, dass eine Animation identifizierbaren Abschluss und Fehler Status hat.  
  
    -   Minimieren Sie die Verwendung des Effekt-Animationen, die Status anzeigen und stellen Sie sicher, dass zusätzliche Informationen von der tatsächlichen Verwendung Reeller Wert ist. Beispiele für vorübergehende statusänderungen und Notfällen  
  
#### <a name="animation-donts"></a>Animation für die Navigation:
  
-   Verwenden Sie keine kleine Bewegungen (Bewegung in einen geringen Ressourcenbedarf). Bevorzugen Sie ausgeblendet und über das Verschieben von Objekten ändert.  
  
-   Verwenden Sie keine Animationen, die über einen großen Bereich von Bildschirmfläche stattfinden. Diese Art der Animation lenkt unabhängig von der Größe für den Benutzer ist.  
  
-   Verwenden Sie keine Animationen, die das Objekt, dem der Benutzer gerade auf fokussiert ist unabhängig vom stagingstatus oder interagieren.  
  
-   Verwenden Sie keine Animationen, die um den Status, wie die Benutzer so reagieren Sie auf eine blinkende Benachrichtigung damit diese blinken beenden auch zwingen Benutzerinteraktion erforderlich ist. Interaktion mit ihnen in keiner Weise sollte ausreichen, um sie zu schließen.  
  
Weitere Informationen zu Anwendungen für diese best Practices, finden Sie unter [Animation Muster](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Animation-Metriken  
  
-   Das System sollte sichtbar auf Benutzergesten in weniger als 10 Millisekunden, reagieren.  
  
-   Animierte Übergänge darf nicht mehr als 500 Millisekunden abgeschlossen werden.  
  
-   Eine Möglichkeit, für die Übergänge zu kompensieren, die erfordern längere Zeiträume ist in zwei Bereiche abzugrenzen. Der erste Teil einer Animation kann z. B. die leeren Inhalt Container (bis zu 500 Millisekunden), gefolgt von den Inhalt ein-oder Ausblenden in den Container (bis zu 500 Millisekunden) sein.  
  
-   Für die Ladezeiten, die berechnet werden können, wird eine Determinante Statusanzeige (Prozent abgeschlossen Statusanzeige) bevorzugt.  
  
-   Für Ladezeiten, die nicht berechnet werden können, ist ein Indikator ausgelastet, wie ein Cursor oder eine eingebettete Spinvorgänge Animation (Laden von oder arbeiten Indikator) geeignet.  
  
### <a name="animation-as-communicator"></a>Animation als communicator  
In Visual Studio-Benutzeroberfläche funktioniert Animation nur als ein Kommunikationstool ein.  Es wird verwendet, um eine Vielzahl von Informationen, z. B. strukturelle Änderungen in der Benutzeroberfläche (z. B., wenn ein Menü öffnet oder schließt) zu kommunizieren. Animation können Sie das Verhalten der zeitabhängige komplexer Systeme, z. B. Installation Fortschritt Visualisierung visualisieren. Animationen können auch verwendet werden, um Aufmerksamkeit mit Warnungen und Benachrichtigungen zu gewinnen.  
  
 UI-Animationen funktionieren in der Regel gibt es vier Möglichkeiten: visualisieren, gewinnen Aufmerksamkeit, zu simulieren, und Antwort Zeiten/Fortschritt Indikatoren.  
  
#### <a name="visualize"></a>Visuell darstellen  
Animation kann hervorheben die dreidimensionale Art von Objekten und für Benutzer zum Anzeigen von deren räumliche Struktur vereinfachen. Um dies zu erreichen, die Animation möglicherweise drehen Sie das Objekt in einen vollständigen Kreis langsam hin und her aktivieren oder verschieben Sie das Objekt näher und leicht erhöhen die Größe um Rollover oder den Fokus zu verdeutlichen.  
  
Obwohl dreidimensionale Objekte mit Benutzersteuerelement, verschoben werden können, der Designer sollten im voraus (programmgesteuert oder manuell) bestimmen animieren wie am besten eine Verschiebung, die optimale Verständnis des Objekts bereitstellt. Diese Animation kann programmiert und vom Benutzer durch den Cursor über dem Objekt platzieren aktiviert werden, während benutzergesteuerte Bewegungen den Benutzer erfahren, wie das Objekt bearbeiten erfordern. Beschränken Sie die datenverschiebung zu einer einzelnen Achse oder die Ausrichtung zu einem Zeitpunkt. entweder zu skalieren, zu drehen oder übersetzt werden, jedoch nicht mehr als eine gleichzeitig ausführen.  
  
Die Kategorie "visualisieren" enthält die Aspekte der Daten, Beziehungen, State, Struktur-, Sequenz und Zeit.  
  
##### <a name="data"></a>Daten  
Veranschaulichen Sie komplexe und Variable Informationen an:  
  
-   Durchsuchen von Informationen Visualisierungen wie Diagramme und Grafiken  
  
-   Schrittweises Durchlaufen von einer Sequenz, Einführung und paging  
  
-   Hervorhebung spezifische Informationen zeigen und Kennzeichnung von details  
  
-   Überlagern Details und Weitere Informationen über ein Fokuselement
  
-   Von einer strukturellen oder die Organisationseinheit Darstellung Morphing in eine andere  
  
-   Die Änderungen im Zeitverlauf mit Schieberegler Knick Bereichssymbol Räder und Steuerelemente (wiedergeben, beenden und anhalten) darstellt. 
  
##### <a name="relationships"></a>Beziehungen  
  
-   Veranschaulicht, wie Elemente miteinander in Beziehung stehen, oder welche Elemente auf ein bestimmtes Element beziehen
  
-   Hierarchien und über-und untergeordneten oder nebengeordneten Beziehungen anzeigen
  
-   Ein Element erzeugt eine andere
  
-   Ein Element wird auf ein anderes Element minimiert.
  
-   Ein Element in eine andere Anbindung
  
##### <a name="state"></a>Zustand  
  
-   Inhaltsupdates
  
-   Den Benutzerfokus und Auswahl  
  
-   Status  
  
-   Fehler  
  
##### <a name="structure"></a>Struktur  
  
-   Pivotieren die Struktur auf einem Knoten  
  
-   Neuorientieren  
  
-   Minimieren Sie und Maximieren Sie, oder Erweitern Sie und reduzieren  
  
##### <a name="sequence"></a>Sequenz  
  
-   Diaschau-Sequenz  
  
-   Kippen über Bilder  
  
##### <a name="time"></a>zeit  
  
-   Änderung im Verlauf der Zeit, Zeitsprung und Screencast anzeigen  
  
-   Verschieben Sie in den Papierkorb, rückgängig machen und wiederholen  
  
-   Stellen Sie die Verlaufsstatus wieder her.  
  
#### <a name="attract-attention"></a>Gewinnen Sie Aufmerksamkeit  
Wenn das Ziel mit der Benutzer auf ein einzelnes Element aus mehreren gekennzeichnet oder Benachrichtigung des Benutzers auf aktualisierte Informationen ist, kann eine Animation geeignet sein. Ihre Startseite der Anwendung könnte z. B. eine Schaltfläche "Erste Schritte" nutzen, über die einrastet Folien, nachdem die Seite geladen.  
  
In der Regel desto das letzte verschieben Element auf dem Bildschirm des Benutzers Aufmerksamkeit zielgerichteter.  In einer Reihe von animierten Elementen wird die Aufmerksamkeit des Benutzers das letzte verschieben Objekt folgen.  
  
##### <a name="alert"></a>Warnung  
  
-   Der Benutzer gewarnt werden, erhalten Sie Aufmerksamkeit, Status anzeigen  
  
-   Zeigen Sie, dass etwas ordnungsgemäß oder nicht ordnungsgemäß ausgeführt wird oder zeigen ausgeführt werden oder auf Änderungen des Status an  
  
-   Eine Aufgabe, wie z. B. Suchen nach weiteren Informationen online oder über die aktuelle Aufgabe erfahren auffordern Sie Benutzer  
  
##### <a name="notifications"></a>Benachrichtigungen  
  
-   Benachrichtigt den Benutzer zu einer fehlerbedingung  
  
-   Unterbrechen Sie den Benutzer aus, um festzustellen, ob sie etwas anderes teilnehmen möchten.  
  
-   Vorsichtig informieren Sie den Benutzer, den ein Prozess abgeschlossen ist oder geändert wird, wie z. B. wenn ein Download abgeschlossen ist.  
  
#### <a name="simulate"></a>Simulieren  
Diese Kategorie behandelt Physicality und Dimensionalität.  
  
-   Veranschaulichen Sie, woher Objekte stammen oder wo an  
  
-   Erweitern und reduzieren oder zu öffnen und schließen  
  
-   Schwenken, Durchführen eines Bildlaufs und Seite aktiviert  
  
-   Stapeln und Z-Reihenfolge  
  
-   Karussellsicht und ' Accordion '  
  
-   Kippen und Drehen von Benutzeroberflächen  
  
#### <a name="response-and-progress-indicators"></a>Antwort und den Status von Indikatoren  
Statusanzeigen haben einige wichtige Vorteile:  
  
-   Beide Statusanzeigen bestimmte und unbestimmt versichern den Benutzer, den das System nicht abgestürzt und funktioniert über das Problem.  
  
-   Bestimmte Indikatoren weisen Sie dem Benutzer, den eine Vorstellung davon, wie weit die Aktion, den sowie ein Gefühl der erste to the Fertig stellen näher voranschreitet.  
  
##  <a name="BKMK_AnimationPatterns"></a> Animation-Muster  
  
### <a name="overview"></a>Übersicht  
Animationen in Visual Studio eine bestimmte Funktion nicht Benutzerproduktivität beeinträchtigt dienen soll. Im Allgemeinen sollte die Animationen in Visual Studio:  
  
-   Kleine und unaufdringliche  
  
-   Natürliche und realistische  
  
-   Feine und Analysenschritte  
  
-   Schnelle und effiziente  
  
-   Gelockerte, nicht Eile  
  
Diese Abbildung zeigt die animationsstile empfohlen für Visual Studio. Keine Animation oder geringfügige Animationen wie ein- / ausblenden, werden die am häufigsten verwendet. Begrenzten Anwendung der Bewegungsanimationen wie Erweiterung und Verkleinerung vorhanden ist, ändern und Drehung X- und Y zu positionieren. 
  
![Empfohlene animationsstile für Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 A_VSAnimStyles")<br />Empfohlene Animationsstile für Visual Studio
  
#### <a name="appear-and-disappear"></a>Angezeigt werden und nicht mehr vorhanden  
Mit diesem Muster wechselt ein Element aus sichtbar außerhalb-des-Ansicht und ohne eine Animation Übergang zurück.  
  
![Angezeigt und ausgeblendet Animation](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 B_AppearAndDisappear")<br />Angezeigt werden und nicht mehr Animation angezeigt.  
  
##### <a name="correct-usage"></a>Richtige Verwendung  
Neue UI-Elemente müssen, die sofort werden ein- bzw. ausgeblendet, damit der Benutzer weder abgelenkt noch verdeckt wird. Darüber hinaus möglicherweise langsam verschieben Animationen als Leistung ziehen, die auftreten, in dem Format angezeigt und ausgeblendet wird nicht wahrgenommen werden.  
  
##### <a name="incorrect-usage"></a>Falsche Verwendung  
Fälle, in der Benutzeroberfläche wird Was ist geschehen abrupt der Benutzer ohne Idee hat angezeigt, und Hinzufügen einer Animation würden mit kontextverständnis zu helfen.  
  
##### <a name="animation-properties"></a>Animationseigenschaften  
Die Wartezeit ist in der Regel 0 (null) Sekunden.  
  
##### <a name="examples"></a>Beispiele    
-   Automatisches Ausblenden von Toolfenstern  
  
-   Tastatur aktivierten Editor Benutzeroberfläche, z. B. IntelliSense und Parameter-Hilfe  
  
-   Erweitern und reduzieren Codebereiche  
  
#### <a name="fade-in-and-fade-out"></a>Auf- und Ausblenden der videoüberlagerung benötigt  
Mit diesem Muster wird ein Element der Benutzeroberfläche aus nicht sichtbar (0 % Deckkraft) geht sichtbar (100 % Deckkraft) oder umgekehrt.  
  
![Auf- und Ausblenden der videoüberlagerung benötigt Animation](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 C_FadeInFadeOut")<br />Auf- und Ausblenden der videoüberlagerung benötigt animation  
  
##### <a name="correct-usage"></a>Richtige Verwendung  
Dies ist die am häufigsten UI Animation empfohlen. Es ist eine geringfügige Auswirkung, die zu überwachende ohne Unterbrechung Datenfluss hinzufügt. In einigen Fällen kann der Benutzer nicht einmal bewusst ergibt sich eine Animation eine problemlose Wesen und Benutzeroberflächen-System fließen.  
  
##### <a name="animation-properties"></a>Animationseigenschaften  
  
-   Starten die Deckkraft: 0 "für Hereingleiten", "100 % für das Ausblenden der videoüberlagerung benötigt  
  
-   Beenden die Deckkraft: 100 % "für" Hereingleiten "," 0 "% für das Ausblenden der videoüberlagerung benötigt  
  
-   Dauer: 200 Millisekunden eigenständigem 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination  
  
-   Einfachere Stil: Sinus InOut  
  
##### <a name="examples"></a>Beispiele  
  
-   Automatisches Ausblenden von Toolfenstern  
  
-   Menü öffnen und schließen  
  
-   Hintergrund- und Vordergrundfarben Registerkarte Übergänge  
  
#### <a name="color-blend-from-a-to-b"></a>Farbe Blend von A zu B  
Mit diesem Muster ändert ein Element der Benutzeroberfläche von Farbe ein Farbe B.  
  
![Farbüberblendung](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 D_ColorBlend")<br />Blend-Animation Farbe  
  
##### <a name="correct-usage"></a>Richtige Verwendung  
Wie eine animierte Übergang, wenn ein Element der Benutzeroberfläche in eine andere Farbe aus einem Kontext oder der Status ändert.  
  
##### <a name="animation-properties"></a>Animationseigenschaften  
  
-   Anfangsfarbe: UI-spezifisch  
  
-   Endfarbe: UI-spezifisch  
  
-   Dauer: 200 Millisekunden eigenständigem 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination  
  
-   Einfachere Stil: Sinus InOut  
  
##### <a name="examples"></a>Beispiele  
  
-   Dokumentieren Sie Fenster Statusübergänge (aktiv, letzte aktive und inaktive)  
  
-   Fenster Statusübergänge-Tool (fokussierte und ohne Fokus)  
  
#### <a name="expand-and-contract"></a>Erweiterung und Verkleinerung  
Mit diesem Muster wird ein Benutzeroberflächenelement erweitert, X, Y oder beide Richtungen.  
  
![Erweiterung und Verkleinerung Animation](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 E_ExpandContract")<br />Erweiterung und Verkleinerung animation  
  
##### <a name="correct-usage"></a>Richtige Verwendung  
Wie eine animierte Übergang, wenn ein Element der Benutzeroberfläche aus einem Kontext in eine andere Größe ändert.  
  
##### <a name="animation-properties"></a>Animationseigenschaften  
  
-   X-Skalierung: % oder einer bestimmten Dimension (in Pixel)  
  
-   Y-Skalierung: % oder einer bestimmten Dimension (in Pixel)  
  
-   Position verankert: im Allgemeinen die obere linke (für Links-nach-rechts-Sprachen) oder rechts (für rechts-nach-links-Sprachen)  
  
-   Dauer: 200 Millisekunden eigenständigem 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination  
  
##### <a name="examples"></a>Beispiele  
  
-   Architektur-Explorer-Bereich erweitert und reduziert  
  
-   Startseite Element erweitern und reduzieren  
  
#### <a name="x-y-position-change"></a>X-Y-position ändern  
Mit diesem Muster ändert ein Benutzeroberflächenelement seine X- oder Y-Position oder beides.  
  
![X-Y-Position ändern Animation](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 F_XYPositionChange")<br />X-Y-Position ändern animation  
  
##### <a name="correct-usage"></a>Richtige Verwendung  
Wie eine animierte Übergang, wenn ein Element der Benutzeroberfläche in eine andere Position aus einem Kontext ändert.  
  
##### <a name="animation-properties"></a>Animationseigenschaften  
  
-   Starten von X- und Y-Position: UI-spezifisch  
  
-   Beenden von X- und Y-Position: UI-spezifisch  
  
-   Pfad: keine  
  
-   Dauer: 200 Millisekunden eigenständigem 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination  
  
-   Einfachere Stil: Sinus InOut  
  
##### <a name="example"></a>Beispiel  
Registerkarte neu anordnen  
  
#### <a name="rotate"></a>Drehen  
Mit diesem Muster die dreht des Benutzeroberflächenelements aus.  
  
![Benutzeroberflächenautomatisierungs-Element Drehungsanimation](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 G_Rotate")<br />Benutzeroberflächenautomatisierungs-Element Drehungsanimation  
  
##### <a name="correct-usage"></a>Richtige Verwendung  
Nur für die Statusanzeige unbestimmt Spinvorgänge.  
  
##### <a name="animation-properties"></a>Animationseigenschaften  
  
-   Grad der Drehung: 360  
  
-   Drehung Center: Mitte des Objekts  
  
-   Dauer: fortlaufende  
  
##### <a name="example"></a>Beispiel  
Unbestimmt Statusanzeige (Spinvorgänge)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Allgemeine Shell-UI-Aktionen und empfohlene Animationen  
  
#### <a name="tab-open"></a>Registerkarte öffnen  
![Registerkarte öffnen Animation](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 H_TabOpen")<br />Animation "Registerkarte öffnen"  
    
-   Art: angezeigt werden  
  
-   Dauer: 0 (null) Sekunden  

#### <a name="tab-close"></a>Schließen Sie die Registerkarte "  
![Registerkarte schließen Animation](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 I_TabClose")<br />Animation "Registerkarte schließen"  
  
-   Format: X-Position ändern  
  
-   Dauer: 200 Millisekunden  
  
#### <a name="tab-reorder"></a>Registerkarte neu anordnen  
![Registerkarte neu anordnen Animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 J_TabReorder")<br />Animation "Registerkarte-neu anordnen"

-   Format: X-Position ändern  
  
-   Dauer: 200 Millisekunden  
    
#### <a name="close-floating-document"></a>Schließen unverankertes Dokument  
![Gleitkommawert Dokument Animation schließen](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 K_CloseFloatingDocument")<br />Schließen unverankertes Dokument animation  
   
-   Art: angezeigt werden  
  
-   Dauer: 200 Millisekunden   
 
#### <a name="window-state-transition"></a>Fenster Zustandsübergang  
![Fenster Status Übergangsanimationen](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 L_WindowStateTransition")<br />Übergang von Fensteranimation-Status  
    
-   Format: zur Wahrung der Konsistenz mit anderen Windows können Sie das aktuelle Betriebssystem das Dokument schließen Animation definieren.  
  
-   Dauer: 200 Millisekunden  
  
#### <a name="menu-open"></a>Menü öffnen  
![Animation "Menü öffnen"](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 M_MenuOpen")<br />Animation "Menü öffnen"  
    
-   Art: Hereingleiten  
  
-   Dauer: 200 Millisekunden  
  
#### <a name="menu-close"></a>Menü schließen  
![Schließen Menüanimation](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 N_MenuClose")<br />Animation "Menü schließen"  
    
-   Art: Ausblenden der videoüberlagerung benötigt  
  
-   Dauer: 200 Millisekunden  
  
#### <a name="auto-hide-tool-window-reveal"></a>Automatisch im Hintergrund Tool Fenster anzeigen  
![Automatisch im Hintergrund Tool anzeigen Fensteranimation](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 O_AutoHideToolWindowReveal")<br />Automatisch im Hintergrund Tool anzeigen Fensteranimation  

-   Art: angezeigt werden  
  
-   Dauer: 0 (null) Sekunden