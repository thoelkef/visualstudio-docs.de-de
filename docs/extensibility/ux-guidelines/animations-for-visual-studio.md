---
title: "Animationen f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Animationen f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Animation\-Grundlagen  
  
### Animation bewährten Methoden in Visual Studio  
 Führen Sie diese Regeln, um konsistente und benutzerfreundliche animationsstile für Visual Studio\-IDE sicherzustellen.  
  
-   **Werden Sie selektive.** Beschränken Sie Animationen auf die speziellen Zwecken dienen.  
  
-   **Timing und Geschwindigkeit sind wichtige** um sicherzustellen, dass die Übergänge schnelle und natürliche können:  
  
    -   Führen Sie die animierte Übergänge in eine halbe Sekunde \(500 Millisekunden\).  
  
    -   Animationen, die häufig vorkommen, müssen schnell genug, dass sie den Workflow des Benutzers nicht unterbrechen.  
  
    -   Animationen sollte nicht so schnell oder bedürfen, es ist schwer zu verstehen, aber nicht so langsam, dass es eine ungeduldig der Übergang abgeschlossen ist.  
  
    -   Verwenden Sie Variablen Timing, um Bedeutung hervorzuheben. Angenommen, bei der Navigation durch eine Sequenz von Elementen in einem Klassendiagramm beschleunigen über Übergänge zwischen Elementen und dann verlangsamt sich auf wichtige Elemente konzentrieren.  
  
-   **Mithilfe der schrittweisen nicht lineare Beschleunigung** von einem Zustand in einen anderen, damit Sie ein Eindruck der ruhige und natürliche Bewegung  
  
-   Wenn möglich, **verwenden eine feine Animation Daraufzeigen** interaktive Elemente unter der Maus an.  
  
-   Stark auf Animationen in Ihrer Funktionen dann stützen **bieten eine Möglichkeit zum Abschalten** lokal \(für alle Funktionen\) als Option für die **Tools \> Optionen** Dialogfeld.  
  
-   **Nur eine einzige Animation zu einem Zeitpunkt erfolgen sollte** und nur ein Teil der Informationen vermitteln.  
  
-   **Besonderheit ist wichtig.** In den meisten Fällen keine Animation, bei Bedarf der Aufmerksamkeit des Benutzers auf den Zweck dienen. Geringfügige Änderungen in der zeitlichen Steuerung, Sequenzierung und Verhalten können Wahrnehmung erheblich beeinträchtigen können, und den Unterschied zwischen einer Animation wirksam und ineffizient.  
  
-   Verwendung von Animationen auf etwas, hervorzuheben **Stellen Sie sicher, dass es lohnt sich den Benutzer zu unterbrechen**der Gedankengang.  
  
-   **Bei der Arbeit mit** über Animation:  
  
    -   Beenden Sie die Bewegung Fortschritt anzeigen, wenn Sie der zugrunde liegenden Prozess nicht Vorlauf ist.  
  
    -   Unterscheiden zwischen Sie unbestimmt Prozesse bestimmte Prozesse.  
  
    -   Sicherstellen Sie, dass eine Animation identifizierbaren Abschluss oder Abbruch Status hat.  
  
    -   Minimieren Sie die Verwendung von Effekt\-Animationen, bei denen Status, und stellen Sie sicher, dass sie wahre Wert haben, indem Sie zusätzliche Informationen der tatsächlichen Verwendung. Beispiele hierfür sind vorübergehende ändert und Notfällen  
  
#### Beachten Sie:  
  
-   Verwenden kleine Bewegung \(Bewegung in einen geringen Speicherbedarf\), Bevorzugung ausgeblendet, und über das Verschieben von Objekten geändert wird.  
  
-   Verwenden Sie Animationen, die über einen großen Bereich von Platz auf dem Bildschirm stattfinden. Unabhängig von der Größe wird diese Art von Animation für den Benutzer stören.  
  
-   Verwenden Sie Animationen, die nicht auf das Objekt, dem der Benutzer gerade auf fokussiert ist oder der Interaktion mit beziehen.  
  
-   Verwenden Sie Animationen, die Benutzer eingreifen, um den Status, z. B. den Benutzer so reagieren Sie auf eine blinkende Benachrichtigung damit darauf blinken beenden zwingen zurückzusetzen. In keiner Weise mit ihnen interagieren sollte ausreichen, um diese zu schließen.  
  
 Weitere Informationen zu Programmen, wurden diese bewährten Methoden finden Sie unter [Animation-Muster](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### Animation\-Metriken  
  
-   Das System sollte deutlich auf Benutzeraktionen in weniger als 10 Millisekunden reagieren.  
  
-   Animierte Übergänge dauert nicht länger als 500 Millisekunden abgeschlossen.  
  
-   Übergänge zu kompensieren, die längere Zeiträume benötigen werden, es in zwei Teile aufzuteilen. der erste Teil einer Animation könnte z. B. die leeren Inhalt Container \(bis zu 500 Millisekunden\) gefolgt von dem Inhalt ein\-oder Ausblenden in den Container \(bis zu 500 Millisekunden\) sein.  
  
-   Für Ladezeiten, die berechnet werden können, wird eine Determinante Statusanzeige \(Prozent\-fertig Statusanzeige\) bevorzugt.  
  
-   Für Ladezeiten, die berechnet werden können, ist ein auslastungsindikator wie z. B. ein Cursor oder eine eingebettete rotierende Animation \(laden oder arbeiten Indikator\) geeignet.  
  
### Animation als communicator  
 \-Funktionen in Visual Studio\-Benutzeroberfläche Animation nur als Kommunikationstool für die.  Es wird eine Vielzahl von Informationen, z. B. strukturelle Änderungen in der Benutzeroberfläche zu kommunizieren. z. B. wenn ein Menü öffnet oder schließt. Animationen kann Visualisieren der zeitabhängige Verhalten komplexer Systeme, wie z. B. Installation Fortschritt Visualisierung oder verwendet werden, um die Aufmerksamkeit mit Warnungen und Benachrichtigungen zu gewinnen.  
  
 UI\-Animationen funktionieren in der Regel vier Methoden: visualisieren, wecken, simulieren und Antwort angeben Zeiten\/Status.  
  
#### Visuell darstellen  
 Animation kann hervorheben die dreidimensionale Art von Objekten und erleichtern Benutzern, deren räumliche Struktur visualisieren. Um dies zu erreichen, kann die Animation das Objekt in einen vollständigen Kreis, dreht langsam hin und her aktivieren oder das Objekt näher zu bringen und etwas vergrößern um Rollover oder den Fokus zu verdeutlichen.  
  
 Obwohl dreidimensionale Objekte mit Benutzersteuerelements verschoben werden können, der Designer sollten im voraus \(programmgesteuert oder manuell\) bestimmen animieren wie am besten eine Bewegung, die optimale Verständnis des Objekts bereitstellt. Diese Animation kann programmiert und vom Benutzer durch Platzieren den Cursor über dem Objekt aktiviert werden, während benutzergesteuerten Bewegung den Benutzer zu verstehen, wie das Objekt bearbeitet, erfordern. Beschränken Sie die Bewegung auf eine einzelne Achse oder Ausrichtung zu einem Zeitpunkt. entweder skalieren, drehen oder übersetzen, jedoch nicht mehrere gleichzeitig.  
  
 Die Visualisierung Kategorie umfasst die Aspekte der Daten, Beziehungen, State, Struktur, Sequenz und Zeit.  
  
##### Daten  
 Veranschaulichen Sie komplexe und Variable\-Informationen:  
  
-   Navigieren durch Informationen Visualisierungen wie Diagramme und Grafiken  
  
-   Eine Sequenz durchlaufen, Führung und paging  
  
-   Details aufrufen, zeigen und Hervorhebung spezifische Informationen  
  
-   Details und zusätzliche Informationen über eine fokussierte Element überlagern  
  
-   Von einer strukturellen oder die Organisationseinheit Darstellung Morphing zu einer anderen  
  
-   Die Änderungen im Zeitverlauf mit Schieberegler Knick Bereichssymbol Räder und Steuerelemente \(Wiedergabe, Stopp\- und Pauseschaltflächen\) darstellt.  
  
##### Beziehungen  
  
-   Veranschaulicht, wie Elemente zueinander in Beziehung stehen oder welche Elemente auf ein bestimmtes Element beziehen.  
  
-   Hierarchien und übergeordnete, untergeordnete oder gleichgeordnete Beziehungen anzeigen  
  
-   Ein Element erzeugt eine andere  
  
-   Ein Element wird auf ein anderes Element minimiert.  
  
-   Ein Element in einen anderen Anbindung  
  
##### Zustand  
  
-   Aktualisierungen des Inhalts.  
  
-   Benutzerfokus und Auswahl  
  
-   Status  
  
-   Fehler  
  
##### Struktur  
  
-   Pivotieren die Struktur auf einem Knoten  
  
-   Neuorientieren  
  
-   Minimieren Sie und Maximieren Sie, oder Erweitern Sie und reduzieren  
  
##### Sequenz  
  
-   Bildschirmpräsentation Sequenz  
  
-   Beim Durchsuchen der Bilder  
  
##### zeit  
  
-   Ändern sich mit der Zeit, Zeit und Screencast anzeigen  
  
-   Verschieben Sie Abfall, rückgängig machen und wiederholen  
  
-   Wiederherstellen von Fenstern  
  
#### Wecken  
 Wenn das Ziel die Aufmerksamkeit des Benutzers auf ein einzelnes Element aus mehreren zeichnen oder Benachrichtigung des Benutzers auf aktualisierte Informationen ist, möglicherweise eine Animation geeignet. Startseite für die Anwendung kann z. B. eine Schaltfläche "Erste Schritte" verwenden, die Folien stattfindet, nachdem die Seite geladen.  
  
 In der Regel anzieht das letzte verschieben Element auf dem Bildschirm die Aufmerksamkeit des Benutzers.  In eine Reihe von animierten Elemente führen die Aufmerksamkeit des Benutzers der letzten Bewegungsobjekt.  
  
##### Warnung  
  
-   Der Benutzer gewarnt, Aufmerksamkeit erhalten, Fortschritt anzeigen  
  
-   Zeigen Sie an, dass etwas richtig oder falsch ausgeführt wird oder zeigen Fortschritt oder Status Änderungen an  
  
-   Auffordern Sie Benutzer, während einer Aufgabe, z. B. Suchen nach weiteren Informationen online oder Informationen über die aktuelle Aufgabe  
  
##### Benachrichtigungen  
  
-   Warnen Sie die Benutzer über einen Fehlerzustand  
  
-   Unterbrechen Sie den Benutzer aus, um festzustellen, ob sie etwas anderes besuchen möchten  
  
-   Vorsichtig informieren des Benutzers, den ein Prozess beendet oder geändert werden, z. B. wenn der Download abgeschlossen ist.  
  
#### Simulieren  
 Diese Kategorie umfasst Physicality und Dimensionalität.  
  
-   Herkunft der Objekte oder wo zu veranschaulichen  
  
-   Erweitern und reduzieren oder zu öffnen und schließen  
  
-   Schwenken, Bildlauf und Seite aktiviert  
  
-   Stapeln und Z\-Reihenfolge  
  
-   Karussell und Akkordeon  
  
-   Kippen und Drehen von Benutzeroberfläche  
  
#### Antwort und Fortschritt anzeigen  
 Statusanzeigen haben einige wichtige Vorteile:  
  
-   Beide bestimmte und unbestimmt Statusanzeigen versichern den Benutzer, den das System nicht abgestürzt ist und das Problem.  
  
-   Bestimmte Indikatoren weisen Sie dem Benutzer, den eine Vorstellung davon, wie weit die Aktion, den sowie einen Eindruck bekommen näher an das Ende voranschreitet.  
  
##  <a name="BKMK_AnimationPatterns"></a> Animation\-Muster  
  
### Übersicht  
 Animationen in Visual Studio soll eine bestimmte Funktion dienen und Produktivität der Benutzer nicht behindern. Allgemeine Animation Merkmale zu befolgen sind:  
  
-   Klein und unauffällig und  
  
-   Natürlich und realistisch  
  
-   Feine und Analysenschritte  
  
-   Schnelle und effiziente  
  
-   Gelockerte, nicht Eile  
  
 Die folgende Abbildung zeigt die animationsstile für die Verwendung in Visual Studio empfohlen. Keine Animation und raffinierten Animationen wie einblenden \/ ausblenden, werden die am häufigsten verwendet. Begrenzte Anwendung Bewegung Animationen wie vergrößern oder verkleinern, X\- und Y\-position ändern und Drehung.  
  
 ![Recommended animation styles for Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202\-a\_VSAnimStyles")  
  
 **Empfohlene Animationsstile für Visual Studio**  
  
#### Angezeigt und ausgeblendet werden  
 Mit diesem Muster wechselt ein Element aus sichtbar Out\-des\-Ansicht und ohne eine Übergangsanimationen zurück:  
  
 ![Appear&#47;Disappear animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202\-b\_AppearAndDisappear")  
  
##### Richtige Verwendung  
 Neue Elemente der Benutzeroberfläche müssen sofort angezeigt oder ausgeblendet, damit der Benutzer weder abgelenkt noch verdeckt wird. Darüber hinaus möglicherweise langsame bewegliche Animationen als Leistung ziehen, die auftreten, in dem Format angezeigt und ausgeblendet wird nicht wahrgenommen werden.  
  
##### Falsche Verwendung  
 Fälle, in der UI angezeigt plötzlich die Benutzer keine Ahnung hat, was passiert ist, und Hinzufügen einer Animation würde kontextbezogene Kenntnisse zu helfen.  
  
##### Animationseigenschaften  
 Die Verzögerung ist im allgemeinen 0 \(null\) Sekunden.  
  
##### Beispiele  
  
-   Toolfenster automatisch ausblenden  
  
-   Tastatur aktivierten\-Editor\-Benutzeroberfläche, z. B. IntelliSense und Parameter\-Hilfe  
  
-   Erweitern und reduzieren Codebereiche  
  
#### Auf\- und Abblendzeit  
 Mit diesem Muster geht ein Element der Benutzeroberfläche aus nicht sichtbar ist \(0 % Deckkraft\) sichtbar \(100 % Deckkraft\) oder umgekehrt:  
  
 ![Fade&#45;in&#47;Fade&#45;out animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202\-c\_FadeInFadeOut")  
  
##### Richtige Verwendung  
 Dies ist die am häufigsten UI Animation empfohlen. Effekte, die Zinsen hinzufügt, ohne Unterbrechung der Datenfluss sehr ist. In einigen Fällen kann der Benutzer nicht einmal bewusst ist, dass es eine Animation und einfach eine glatte, fließende Benutzeroberflächensystem arbeitet.  
  
##### Animationseigenschaften  
  
-   Starten die Deckkraft: Fade\-in 0 %, 100 % Ausblenden der videoüberlagerung benötigt  
  
-   Beenden die Deckkraft: 100 % Fade\-in, Ausblenden der videoüberlagerung benötigt % 0  
  
-   Dauer: 200 Millisekunden eigenständige, 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination  
  
-   Beschleunigung von Style: Sinus InOut  
  
##### Beispiele  
  
-   Toolfenster automatisch ausblenden  
  
-   Menü öffnen und schließen  
  
-   Hintergrund\- und Vordergrundfarben Registerkarte Übergänge  
  
#### Farbe Blend von A zu B  
 Mit diesem Muster ersetzt ein Element der Benutzeroberfläche von Farbe eine Farbe B:  
  
 ![Color blend animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202\-d\_ColorBlend")  
  
##### Richtige Verwendung  
 Als einen animierten Übergang, wenn ein Element der Benutzeroberfläche in eine andere Farbe aus einem Kontext oder Zustand ändert.  
  
##### Animationseigenschaften  
  
-   Anfangsfarbe: UI\-spezifischen  
  
-   Endfarbe: UI\-spezifischen  
  
-   Dauer: 200 Millisekunden eigenständige, 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination  
  
-   Beschleunigung von Style: Sinus InOut  
  
##### Beispiele  
  
-   Dokumentieren von Zustandsübergängen Fenster \(aktiv, letzte aktive und inaktive\)  
  
-   Fenster Statusübergänge\-Tool \(fokussierte und ohne Fokus\)  
  
#### Vergrößern oder verkleinern  
 Mit diesem Muster erweitert ein Benutzeroberflächenelement X, Y oder beide Richtungen:  
  
 ![Expand&#47;Contract animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202\-e\_ExpandContract")  
  
##### Richtige Verwendung  
 Als einen animierten Übergang, wenn ein Element der Benutzeroberfläche aus einem Kontext zu einer anderen Größe ändert.  
  
##### Animationseigenschaften  
  
-   X\-Skalierung: % oder eine bestimmte Dimension \(in Pixel\)  
  
-   Y\-Skalierung: % oder eine bestimmte Dimension \(in Pixel\)  
  
-   Verankern Sie Position: in der Regel die linke obere \(für Links\-nach\-rechts\-Sprachen\) oder rechts \(für rechts\-nach\-links\-Sprachen\)  
  
-   Dauer: 200 Millisekunden eigenständige, 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination  
  
##### Beispiele  
  
-   Architektur\-Explorer\-Bereich erweitern und reduzieren  
  
-   Starten Sie die Seite Element erweitern und reduzieren  
  
#### X\-Y\-position ändern  
 Mit diesem Muster ändert ein Benutzeroberflächenelement und\/oder die X\- oder Y\-Position:  
  
 ![X&#47;Y position change animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202\-f\_XYPositionChange")  
  
##### Richtige Verwendung  
 Als einen animierten Übergang, wenn ein Element der Benutzeroberfläche in eine andere Position aus einem Kontext ändert.  
  
##### Animationseigenschaften  
  
-   Starten von X und Y\-Position: UI\-spezifischen  
  
-   Beenden von X und Y\-Position: UI\-spezifischen  
  
-   Pfad: keine  
  
-   Dauer: 200 Millisekunden eigenständige, 100 Millisekunden bei Verwendung als Teil einer Animationssequenz Kombination  
  
-   Beschleunigung von Style: Sinus InOut  
  
##### Beispiel  
 Registerkarte neu anordnen  
  
#### Drehen  
 Mit diesem Muster dreht ein UI\-Element:  
  
 ![Rotate animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202\-g\_Rotate")  
  
##### Richtige Verwendung  
 Nur für die Statusanzeige unbestimmt drehen.  
  
##### Animationseigenschaften  
  
-   Grad der Drehung: 360  
  
-   Drehmittelpunkt: Mitte des Objekts  
  
-   Dauer: kontinuierliche  
  
##### Beispiel  
 Unbestimmt Statusanzeige \(Drehen\)  
  
### Allgemeine Shell UI\-Aktionen und empfohlene Animationen  
  
#### Registerkarte öffnen  
  
-   Format: angezeigt werden  
  
-   Dauer: 0 \(null\) Sekunden  
  
 ![Tab open animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202\-h\_TabOpen")  
  
#### Registerkarte schließen  
  
-   Format: X\-Position ändern  
  
-   Dauer: 200 Millisekunden  
  
 ![Tab close animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202\-i\_TabClose")  
  
#### Registerkarte neu anordnen  
  
-   Format: X\-Position ändern  
  
-   Dauer: 200 Millisekunden  
  
 ![Tab reorder animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202\-j\_TabReorder")  
  
#### Unverankertes Dokument schließen  
  
-   Format: angezeigt werden  
  
-   Dauer: 200 Millisekunden  
  
 ![Close floating document animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202\-k\_CloseFloatingDocument")  
  
#### Fenster Zustandsübergang  
  
-   Format: Mit anderen Fenstern konsistent sind, können Sie das aktuelle Betriebssystem die Dokument schließen Animation definieren.  
  
-   Dauer: 200 Millisekunden  
  
 ![Window state transition animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202\-l\_WindowStateTransition")  
  
#### Menü öffnen  
  
-   Format: Fade\-in  
  
-   Dauer: 200 Millisekunden  
  
 ![Menu open animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202\-m\_MenuOpen")  
  
#### Menü schließen  
  
-   Format: Ausblenden der videoüberlagerung benötigt  
  
-   Dauer: 200 Millisekunden  
  
 ![Menu close animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202\-n\_MenuClose")  
  
#### Automatisch im Hintergrund Tool Fenster anzeigen  
  
-   Format: angezeigt werden  
  
-   Dauer: 0 \(null\) Sekunden  
  
 ![Auto&#45;hide tool window animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202\-o\_AutoHideToolWindowReveal")