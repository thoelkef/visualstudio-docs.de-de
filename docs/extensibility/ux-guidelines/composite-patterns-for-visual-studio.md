---
title: "Zusammengesetzte Muster f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Zusammengesetzte Muster f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zusammengesetzte Muster kombinieren Interaktion und Design-Elemente in unterschiedlichen Konfigurationen. Einige der wichtigsten zusammengesetzte Muster in Visual Studio im Hinblick auf Konsistenz gehören:  
  
-   [Visualisierung von Daten](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Auf Benutzeroberfläche und einsehen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Auswahlmodelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistenz und Speichern von Einstellungen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Fingereingabe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="a-namebkmkdatavisualizationa-data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualisierung von Daten  
  
### <a name="overview"></a>Übersicht  
 Diagramme sind eine visuelle Möglichkeit zum Aggregieren und Visualisieren von Daten um Entscheidungsprozess zu verbessern. Sie können Benutzer mit vielen Daten jedoch wenig bedeutet finden Sie unter Was Aufmerksamkeit verdient und eine Aktion, benötigen möglicherweise konfrontiert.  
  
 Der Benutzer profitieren von einem Diagramm, wenn Folgendes zutrifft:  
  
-   Hilft das Diagramm Benutzer Aufgaben zu identifizieren, denen sie nutzen können?  
  
-   Wird das Diagramm Benutzer folgen möglicher Änderungen zu prognostizieren aktivieren?  
  
-   Hilft das Diagramm Benutzer Ermittlung von Trends und Muster identifizieren?  
  
-   Ermöglicht das Diagramm Benutzer bessere Entscheidungen treffen?  
  
-   Wird das Diagramm Hilfe eine bestimmte Frage beantworten, die Benutzer im angegebenen Kontext möglicherweise?  
  
#### <a name="general-rules-for-charts"></a>Allgemeine Regeln für Diagramme  
  
-   Daten deutlich beschriften. Abbildungen ohne Erklärung sind nur hübsche Bilder.  
  
-   Starten Sie die Achsen auf 0 (null), neigen Proportionen zu vermeiden. Länge und Balken Größe sind wichtige visuelle Hinweise für das Verständnis der Beziehungen zwischen Datenpunkten.  
  
-   Erstellen Sie Diagramme, nicht infografiken. Infografiken sind künstlerische Darstellung von Daten und deren Hauptaufgabe besteht visual Storytelling. Diagramme können (und sollten) werden Sie visuell ansprechend, aber lassen Sie die Daten für sich selbst sprechen.  
  
-   Vermeiden Sie Skeumorphism, bildliche Balkendiagramme, Kontrast Hashmarks und andere INFOGRAFIK berührt.  
  
-   Verwenden Sie 3D-Effekte nicht als dekorativen Element aus. Verwenden sie nur, wenn sie wirklich integraler Bestandteil der Benutzer die Informationen zu verstehen.  
  
-   Verwenden Sie mehrere Linien und Füllungen, wie mehr als zwei Farben können diese Art von Diagramm schwer zu lesen und korrekt interpretieren.  
  
-   Verwenden Sie ein Diagramm (oder eine Illustration) nicht als einziges Mittel der Verständnis eines Konzepts oder der Interaktion mit Daten. Dies stellt die Probleme für Benutzer mit eingeschränkter sehfähigkeit.  
  
-   Verwenden Sie Diagramme nicht als überflüssiger oder dekorativen Elementen auf einer Seite. Das heißt, wenn ein Diagramm nicht, dass jeder Wert oder Hilfe Benutzer ein Problem lösen hinzufügen, verwenden Sie nicht es.  
  
### <a name="chart-types"></a>Diagrammtypen  
 Diagramme, die in Visual Studio verwendet Balkendiagramme, Linien-, eine geänderte Kreisdiagramm bekannt als Ring Diagramm oder "Ringdiagramm", Zeitpläne, Typen scatter Plots (auch als "cluster Diagramme" bezeichnet) und Balkendiagramme. Jede Art von Diagramm eignet sich für eine andere Art von Informationen zu kommunizieren.  
  
### <a name="other-charting-considerations"></a>Überlegungen zum Erstellen von Diagrammen  
  
#### <a name="color"></a>Farbe  
 Es ist eine bestimmte Palette zum Erstellen von Diagrammen von Farben, die für die Verwendung in Visual Studio definiert. Die Palette ist für die wichtigsten Arten von Farbenblindheit zugänglich, und die Farben unterschieden werden können, selbst bei Verwendung als sehr kurze Segmente der Farbe. Sie können diese Farben in beliebiger Kombination in Ihrer Benutzeroberfläche für jede Art von Diagramm verwenden. Sie müssen nicht alle sieben Farben zu verwenden, wenn Sie nicht, dass viele verschiedene Farben benötigen. Diese Farben wurden nicht entwickelt, mit allen Elementen Vordergrund, damit kein Text oder Symbole auf diese Farben setzen verwendet werden. Diese Farbtöne hartcodiert und Anpassungsfunktionen unter ausgesetzt werden **Tools > Optionen** (finden Sie unter [Verfügbarmachen von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Farbmuster|Hex|RGB|  
|------------|---------|---------|  
|![Farbmuster 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71 B 252|113,178,82|  
|![Farbmuster BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Farbmuster FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Farbmuster 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Farbmuster 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Farbmuster 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Farbmuster B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="a-namebkmkonobjectuia-on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Auf Benutzeroberfläche und einsehen  
 Dieser Abschnitt enthält Kontext zum einsehen, auch bekannt als Peek Codeansicht ein objektgebundenen UI nur in Visual Studio.  
  
### <a name="overview"></a>Übersicht  
  
-   Auf Benutzeroberfläche sollte der Benutzer Weitere Informationen oder Interaktivität erteilen, ohne ihre Hauptaufgabe sein zu müssen.  
  
-   Die wichtigste Muster für auf Objekt-Benutzeroberfläche in Visual Studio wird als "Informationen zum Zeitpunkt der Aufmerksamkeit." bezeichnet.  
  
-   Auf Objekt-Benutzeroberfläche in Visual Studio sind entweder Inline oder Gleitkomma- und dauerhaft oder vorübergehend.  
  
    -   Peek Codeansicht, ein Typ, der auf der Benutzeroberfläche in Visual Studio ist Inline und dauerhaft.  
  
    -   CodeLens, ein Typ, der auf der Benutzeroberfläche in Visual Studio ist Gleitkomma- und vorübergehende  
  
 Grundlegendes zur Funktionsweise eines Codeabschnitts oder die Suche nach Informationen zu diesem Code erfordert häufig ein Entwickler den Kontext wechseln, und wechseln zu anderen Inhalten oder einem anderen Fenster. Dieser Kontext Schichten können störend, sein, weil Benutzer den Fokus auf ihre ursprünglichen Aufgabe verlieren, wenn sie ihre Hauptfenster lassen. Abrufen von darüber hinaus, dass die ursprünglichen Kontext zurück kann schwierig sein, insbesondere, wenn ihre ursprünglichen Code von anderen Benutzeroberfläche verdeckt werden Wechseln zwischen Fenstern verursacht werden.  
  
 Auf Benutzeroberfläche folgt einem Muster, die Bezeichnung "Informationen zum Zeitpunkt der Aufmerksamkeit". Diese Nachrichten, Popup-Fenster und Dialogfelder gewähren Sie Benutzern zusätzliche Informationen, die Klärung oder Interaktivität ohne Fokus auf ihre Hauptaufgabe hinzufügt. Auf Benutzeroberfläche gehören Popup-Fenster angezeigt werden, wenn ein Benutzer den Mauszeiger über ein Symbol im Infobereich angezeigt, die rote Wellenlinie unter ein falsch geschriebenes Wort und der Peek-Ansicht in Visual Studio 2013 eingeführt bewegt.  
  
### <a name="decision-points"></a>Entscheidungspunkte  
 Es gibt einige Verwendungsmöglichkeiten für diese Art von Informationen zum Zeitpunkt der Aufmerksamkeit, in Visual Studio. Auswählen des richtigen Mechanismus und implementieren sie eine konsistente, vorhersehbare Weise unbedingt insgesamt. Andernfalls möglicherweise Benutzer verwirrend oder inkonsistente nutzen, die optimal für den Fokus aus dem Content selbst angezeigt werden.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Beziehung zwischen Master- und Inhalt  
 Informationen zum Zeitpunkt der Aufmerksamkeit wird verwendet, um eine Beziehung anzeigen im Zusammenhang zwischen dem Inhalt, dass der Benutzer auf (Inhalt der "master") und zusätzliche Inhalte (der Inhalt der "Details"). Bei diesem Muster der Detail-Inhalt klar auf den Inhalt bezieht sich der Benutzer arbeitet mit und nahe am master Content angezeigt werden kann. Zusätzliche Informationen oder Informationen, die zusammengefasst werden kann, ohne zu einer Überlastung des master-Inhalts muss ein weiteres Muster, wie z. B. ein Toolfenster.  
  
-   **Immer** zeigt den Inhalt der Details in der Nähe der master-Inhalt.  
  
-   **Immer** sicherzustellen, dass der Detail-Inhalt immer noch ein Benutzer konzentrieren sich auf die master-Inhalte bleiben kann. Häufig besteht die beste Möglichkeit, dies zu erreichen den Detail-Inhalt als nahe am master Content wie möglich zu rendern. Das Rendern des Detail-Inhalts in einem Popupfenster neben den Inhalten, master oder Rendern der Detail-Inhalt Inline unterhalb der master-Inhalt möglich.  
  
-   **Nie** Informationen zum Zeitpunkt der Aufmerksamkeit, die der Benutzer von der master-Inhalt verwenden. Wenn Benutzer den Inhalt Detail separat anzeigen müssen, machen Sie eine explizite Aktion, die dem Benutzer ermöglicht, die dazu verfügbar.  
  
#### <a name="design-details"></a>Details zum Design  
 Nachdem Sie festgestellt haben, dass die Benutzeroberfläche auf die richtige Wahl ist, gibt es vier wichtige Aspekte:  
  
1.  **Persistenz:** muss der Inhalt permanent oder vorübergehend sein?   
    Möchten Benutzer behalten Sie die Informationen finden Sie unter oder damit interagieren? Oder möchten Benutzer schnell einen Blick auf die Informationen, und fahren mit ihrer Hauptaufgabe?  
  
2.  **Inhaltstyp:** Inhalt werden nur zu Informationszwecken, verwertbare oder Navigation?   
    Ist der Benutzer, die zusätzlichen Details über den Inhalt des master erforderlich? Muss der Benutzer zum Abschluss einer Aufgabe, die am master Content betroffen sind? Oder muss der Benutzer zu einer anderen Ressource weitergeleitet werden?  
  
3.  **Indikator:** ist der Indikator sinnvoll?   
    Die Informationen auf sinnvolle Weise zusammengefasst und angezeigt werden kann ohne überwältigend am master Content?  
  
4.  **Gesten:** Was Gesten aufrufen und Schließen der Benutzeroberfläche verwendet?   
    Wie die Benutzer schalten den Detail-Inhalt und senden Sie sie? Gibt es Wert in eine Geste, z. B. zum Wechseln zwischen vorübergehenden und dauerhaften Status festhalten hinzufügen?  
  
 Jede dieser vier Entscheidungspunkte wird auf die wichtigsten Komponenten der Benutzeroberfläche auf Objekt auswirken.  
  
### <a name="on-object-ui-components"></a>Auf UI-Komponenten  
  
1.  Container (ContentPresenter)-Typ  
  
    -   Gleitkomma  
  
    -   Inline  
  
2.  Inhaltstyp  
  
    -   Information: Daten, die statisch oder dynamisch sein können  
  
    -   Aussagefähige: Befehle, die am master Content ändern  
  
    -   : Navigationslinks, der den Benutzer auf ein anderes Fenster oder Anwendung, z. B. MSDN  
  
3.  Gesten  
  
    -   Aufruf  
  
    -   Kündigung  
  
    -   Anheften  
  
    -   Andere Interaktionen  
  
4.  Persistenz und Commit-Modell  
  
    -   Vorübergehender  
  
    -   Durable  
  
    -   Automatisch  
  
    -   Bei Bedarf  
  
5.  Ambient-Indikatoren (optional)  
  
    -   Wellenlinie unterstrichen  
  
    -   Smarttag-Symbol  
  
    -   Andere ambient-Indikatoren  
  
#### <a name="container-content-presenter-type"></a>Container (ContentPresenter)-Typ  
 Es gibt zwei wichtige Inhalte zum Zeitpunkt der Aufmerksamkeit verfügbaren Optionen:  
  
1.  **Inline:** eine Inline-Darstellung, wie z. B. die Peek-Ansicht, die in Visual Studio 2013 Code-Editor, eingeführt wurde schafft Speicherplatz für neue Inhalte durch die Umstellung von vorhandenem Inhalt.  
  
    -   **Lieber** Vortragende Inline, wenn Sie erwarten, Benutzer eine längere Zeitspanne verweisen dass auf oder der Interaktion mit dem Inhalt ausgeben möchten, die Sie darstellen.  
  
    -   **Vermeiden Sie** Moderatoren Inline, wenn Sie erwarten, Benutzer dass Blick auf die Informationen präsentieren Sie ihre Hauptaufgabe mit minimaler Unterbrechung fortsetzen möchten.  
  
2.  **Gleitkommawert:** schwebenden Vortragenden befindet sich der ausgewählte Inhalt möglichst nahe, aber verändert sich nicht auf das Layout des vorhandenen Inhalts. Verschiedene Strategien Standardoption, z. B. das Anzeigen einer frei verschiebbaren Panels Inhalt über die nächste verfügbare Leerraum um das ausgewählte Symbol.  
  
    -   **Lieber** Vortragende Gleitkommawert, wenn Sie erwarten, Benutzer dass möchten Blick auf die Informationen präsentieren Sie ihre Hauptaufgabe mit minimaler Unterbrechung fortsetzen.  
  
    -   **Vermeiden Sie** Moderatoren Gleitkommawert, wenn Sie erwarten, Benutzer dass möchten verbringen viel Zeit verweisen auf oder der Interaktion mit dem Inhalt Sie vorhanden.  
  
#### <a name="content-type"></a>Inhaltstyp  
 Es gibt drei Haupttypen von Inhalten, die alle auf Benutzeroberflächen-Container angezeigt werden können. Eine beliebige Kombination dieser Arten von Informationen kann angezeigt werden. Die drei Typen sind:  
  
1.  **Information:** die meisten UI-Containern werden eine Art von Information angezeigt bei Objekt. Der Inhalt kann Informationen zu den aktuellen Zustand der Umgebung darstellen, oder es kann Informationen zu einem potenziellen zukünftigen Zustand der Umgebung dar. Beispielsweise kann verwendet werden, um den Effekt eines bestimmten Befehls, z. B. eine Umgestaltung auf den vorhandenen Code darzustellen.  
  
    -   **Immer** verwenden kanonische Darstellung der Informationen, die angezeigt werden. Z. B. Code sollte der Code kann mit syntaxhervorhebung, Darstellung und sollten Sie berücksichtigen, Schriftart und anderen umgebungseinstellungen, die der Benutzer gesetzt hat.  
  
    -   **Immer** erwägen Sie eine Unterstützung von Maßnahmen, die über die Information Inhalte, die wäre möglich, wenn die gleiche Informationen als master Inhalt angezeigt wird. Wenn Sie vorhandenen Code in eine auf Benutzeroberflächen-Container zu präsentieren, Angenommen Sie stark, unterstützen die Möglichkeit, Code zu suchen.  
  
    -   **Immer** eine andere Hintergrundfarbe erwägen, wenn die Präsentation von Informationen, die einen potenziellen zukünftigen Status darstellt.  
  
2.  Aussagefähige: einige auf UI-Container stellt die Möglichkeit, eine Aktion ausführt, über den Hauptschlüssel Inhalt, z. B. eine Umgestaltung Operation bereit.  
  
    -   **Immer** umsetzbare Befehle separat aus dem Inhalt der Information zu positionieren.  
  
    -   **Immer** Aktivieren und Deaktivieren von Aktionen, die bei Bedarf.  
  
    -   **Immer** finden Sie in der standardmäßigen Richtlinien für die Befehle in den Dialogfeldern darstellt.  
  
    -   **Immer** Anzahl von Aktionen, die in einem auf UI-Container auf ein absolutes verfügbar gemacht werden minimale beibehalten. Interaktion mit objektgebundenen Benutzeroberfläche sollte ein einfaches, schnelles-Erlebnis. Der Benutzer sollte keine Energie zum Verwalten des objektgebundenen UI Containers selbst zu erweitern.  
  
    -   **Immer** berücksichtigen, wie und wann ein Benutzeroberflächen-Container auf Objekt geschlossen oder verworfen werden. Als bewährte Methode sollten alle Aktionen, die das Dialogfeld zwischen der Master- und Inhalt wird abgeschlossen auf Benutzeroberflächen-Container auch schließen, wenn diese Aktion aufgerufen wird.  
  
3.  **Navigation:** einige objektgebundenen UI-Containern enthalten Links, der den Benutzer auf ein anderes Fenster oder Anwendung, z. B. einen MSDN-Artikel im Webbrowser des Benutzers zu öffnen.  
  
    -   **Immer** voranstellen jede Navigation Verknüpfung mit "Öffnen", damit Benutzer nicht überraschen, werden einige andere Inhalte navigiert wird.  
  
    -   **Immer** Navigationslinks umsetzbare Links getrennt.  
  
#### <a name="ambient-indicators-optional"></a>Ambient-Indikatoren (optional)  
 Ambiente-Indikatoren kann feine, einschließlich Text in einer gegensätzlichen Farbe vom Rest des Codes angezeigt oder offensichtlich, einschließlich Tickler-Symbole, z. B. Wellenlinie unterstrichen und Smarttag-Symbole. Ambiente-Indikatoren kommunizieren die Verfügbarkeit von zusätzlichen Informationen. Im Idealfall bieten sie nützliche Informationen, auch ohne dass der Benutzer mit ihnen interagieren.  
  
-   **Immer** ambient Indikator positionieren, sodass keine ablenken oder den Benutzer überlasten. Ist es unmöglich, einen ambient Indikator so positionieren, sollten Sie eine andere Lösung.  
  
-   **Immer** so nah wie möglich auf die Inhalte, die mit verknüpft ist, die ambient-Indikator zu positionieren.  
  
-   **Immer** versuchen, einen Indikator zu erstellen, die die Informationen zusammengefasst, zur Verfügung stellt. Erwägen Sie eine Anzahl von Datenelementen, die verfügbar sind (z. B. "3 Verweise" anstatt einfach "Verweise") oder eine andere Möglichkeit zum Zusammenfassen der Daten vorstellen.  
  
    -   In Fällen, in denen die Daten für einen Indikator immer berechnet und angezeigt werden können, sofort erwägen Sie progressive Feedback wie die Werte berechnet werden. Betrachten Sie z. B. Animieren von Änderungen, die Updates für die verfügbaren Daten, die ähnlich wie widerspiegeln, die die e-Mail-live-Kachel auf Windows Phone ungelesene e-Mails mit steigender Zahl der aktualisiert wird.  
  
-   **Nie** Hinzufügen von mehr als ein Benutzer für einen bestimmten Inhalt angemessen durchführen kann. Ambiente-Indikatoren sollten nützlich sein, ohne ein Eingreifen des Benutzers. Indikatoren verlieren ihre Umgebung aus, wenn sie Überlauf und andere Management-Steuerelemente, die sie in der Ansicht erscheinen erfordern.  
  
#### <a name="gestures"></a>Gesten  
 Ein wichtiger Aspekt von dem der Benutzer den Fokus auf dem master Inhalt zu verwalten, ist durch die Unterstützung der richtigen Gesten zum Öffnen und schließen den Inhalt der zusätzliche Details.  
  
-   **Immer** muss der Benutzer einige explizite Aktion zum Öffnen von des zusätzlichen Inhalts ausführen. Allgemeine öffnende Gesten gehören:  
  
    -   **Hover:** QuickInfos oder nicht interaktiven Information  
  
    -   **Expliziten Befehl:** Inline Presenter  
  
    -   **Doppelklicken Sie auf die ambient-Anzeige:** CodeLens-Popup-Fenster  
  
-   **Immer** den Detail-Inhalt zu schließen, wenn der Benutzer die Esc-Taste drückt.  
  
-   **Immer** beachten den Kontext der Benutzeroberfläche auf. Inhalt Referenten, die Aktivität innerhalb des Containers ermöglichen, überlegt, ob zusätzliche Informationen beim Daraufzeigen anzeigen, die an den Workflow des Benutzers störend sein dürfte.  
  
-   **Nie** Inhalte anzeigen, wenn darauf gezeigt wird, die bearbeitet werden angezeigt, oder lädt ein Eingreifen des Benutzers. Dieses Verhalten kann Benutzer frustriert, versuchen, den Cursor über dem Detail-Inhalt verschieben wie das Standardverhalten für die QuickInfo wird sofort zu schließen, wenn der Cursor nicht mehr über den Master Inhalt, der es erstellt wurde.  
  
##  <a name="a-namebkmkselectionmodelsa-selection-models"></a><a name="BKMK_SelectionModels"></a> Auswahlmodelle  
  
### <a name="overview"></a>Übersicht  
 Ein Auswahlmodell ist der Mechanismus verwendet, um anzugeben, und bestätigen die Vorgänge für ein oder mehrere Objekte von Interesse sind, in der Benutzeroberfläche. In diesem Thema wird erläutert, Interaktion Auswahlmuster innerhalb von Visual Studio-Dokument-Editoren: Text-Editoren, Entwurfsoberflächen und Modellierung Flächen.  
  
 Benutzer benötigen eine Möglichkeit, Visual Studio zu signalisieren, was sie gerade arbeiten, und Visual Studio muss Feedback vorhersagbares Antworten, Benutzern zu, was für den Sie ausgeführt wird. Unterschiede oder einer fehlerhaften Kommunikation zwischen dem Benutzer und die Benutzeroberfläche kann der Benutzer nicht unbemerkt eine Aktion, die verfügen kann, führen unbeabsichtigten Konsequenzen. Oft unbemerkt Fehler, bis der Benutzer sieht, dass etwas fehlt oder wurde geändert. Auswahlmodelle sind daher eine der wichtigsten Bestandteile der Entwurf der Benutzeroberfläche. Zwar Auswahl von Modellen in Visual Studio mit Windows konsistent sind, sind leichte Unterschiede.  
  
 Unterscheiden sich in Visual Studio, wie in Windows Auswahlmodelle je nach Kontext, in dem die Aktivität auftritt. Auswahl können in vier Typen von Objekten auftreten:  
  
-   Text  
  
-   Grafikobjekte  
  
-   Listen und Strukturen  
  
-   Raster  
  
 Innerhalb dieser Objekte gibt es drei Arten von Optionen:  
  
-   Zusammenhängenden  
  
-   Unabhängige  
  
-   Region  
  
#### <a name="scope"></a>Bereich  
 Die wichtigste Komponente der Auswahl müssen Sie sicherstellen, dass der Benutzer weiß, in welchem Fenster (Aktivierung) funktionieren und, in denen der Fokus befindet (Auswahl) ist. Visual Studio erweitert die Fenster Management-Funktionen in Windows, das Schema für die Aktivierung ist jedoch identisch: Interaktion mit einem Fenster setzt den Fokus auf das Fenster. Visual Studio verfügt über zwei Indikatoren für die Aktivierung: eine für Dokumentfenster und eine für die Toolfenster.  
  
 Für Dokumentfenster wird das aktive Fenster durch eine Dokumentregisterkarte Fenster im Vordergrund stammt und die Hintergrundfarbe angezeigt:  
  
 ![Aktive Registerkartenauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")  
  
 **Aktive registerkartenauswahl**  
  
 Für die Toolfenster wird das aktive Fenster durch eine Änderung in der Farbe der Bereich der Titelleiste des Toolfensters angezeigt:  
  
 ![Aktive Toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")  
  
 **Aktives Toolfenster, die primäre Auswahl eines Knotens anzeigen**  
  
 ![Inaktive Toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")  
  
 **Inaktive Toolfenster, latente Auswahl des Knotens anzeigen**  
  
 Sobald ein Fenster aktiv ist, wird der Schwerpunkt gemäß der Auswahlmodelle, die in diesem Abschnitt der Richtlinien beschriebenen angegeben.  
  
#### <a name="context"></a>Kontext  
 Visual Studio wurde entwickelt, ein sicheres Konzept des Kontexts beibehalten, verfolgt, in dem der Benutzer arbeitet. Nur ein Fenster ist aktiv, ob dieses Tool oder Dokumentfenster angezeigt wird. Das oberste Dokumentfenster behält jedoch immer eine latente Auswahl. Zwar der Fokus in einem Toolfenster zeigt das Dokumentfenster, das zuletzt aktiv war eine Auswahl auch in einem inaktiven Zustand. Dies geschieht, um den Kontext des Benutzers im Dokument beibehalten, die sie bearbeitet haben, zeigt, dass Visual Studio ihren Status beibehalten wurde, sodass sie zurückkehren und nahtlos zwischen Toolfenstern und Dokumentfenstern verschieben können.  
  
### <a name="text-selection"></a>Textauswahl  
 Visual Studio-Editoren, die ausschließlich Text, wie z. B. die integrierte Text-Editor, verwenden Sie das gleiche Modell des Text-Auswahl und Darstellung beschrieben, der [Maus- und Zeiger](https://msdn.microsoft.com/en-us/library/dn742466.aspx) auf der Seite Windows User Experience Interaction Guidelines auf MSDN. Der Eingabefokus im Text-Editor wird durch einen senkrechten Strich aufgerufen, die Einfügemarke angegeben. Die Einfügemarke wird ein einzelnes Pixel breit und farbige als Quantile was dahinter angezeigt wird. Es blinkt Satz festlegen, indem Sie die **Cursorblinkrate** festlegen in der **Geschwindigkeit** Registerkarte der **Tastatur** Applet in der Systemsteuerung.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Auswahl von zusammenhängenden und getrennten  
 Auswahl in den Text-Editor ist fortlaufend. Nicht zusammenhängende Auswahl sind nicht zulässig, jedoch sollten im Objekt-Editor behandelt werden. Wenn der Benutzer den Mauszeiger über einen Textbereich befindet, ändert sich der Cursor in eine Maus. Einem einzigen Klick positioniert die Einfügemarke im Text-Editor an der Position auf. Halten die Maustaste gedrückt startet eine Markierung und Loslassen der Maustaste die Markierung endet.  
  
#### <a name="region-selection-box-selection"></a>Bereichsauswahl (Auswahl)  
 Visual Studio unterstützt die Auswahl der Region im Text-Editor, und diese Auswahl aufgerufen. Auswahl kann der Benutzer einen Textbereich auswählen, die den reguläre Stream nicht folgt. Wie bei standard-Text auswählen, muss die Auswahl zusammenhängend sein. Auswahl wird initiiert, indem Sie die Alt-Taste gedrückt halten und ziehen mit der Maus. Auswahl kann auch initiiert werden, indem Sie die ALT-Taste oder der UMSCHALTTASTE gedrückt halten und mit den Pfeiltasten, um den Bereich der Auswahl anzuzeigen. Auswahl verwendet die Markierung der normalen und zeigt den Einfügepunkt blinkt, am Ende des Auswahlbereichs.  
  
 ![Regionale &#40; Feld &#41; Auswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")  
  
 **Regionauswahl (Feld) in Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Auswahl Erscheinungsbild  
 Die Farben für aktive und inaktive Auswahl im Editor können angepasst werden. Um die visuelle Darstellung des Editors anzupassen, kann zu ein Benutzer wechseln **Tools > Optionen**, und suchen Sie unter **Umgebung > Schriftarten und Farben > Text-Editor**.  
  
### <a name="graphical-selection"></a>Grafische Auswahl  
  
#### <a name="interaction"></a>Interaktion  
 Grafikobjekt Auswahl kann komplex sein und hängt von einer Reihe von Faktoren ab:  
  
-   **Primäre Auswahl-Modell des Editors.** Editoren, die grafisch Objekte enthalten können auch zum Bearbeiten von Text oder Rastern verwendet werden. Zum Beispiel möglicherweise Editor einem textbasierten Editor, der auch die Platzierung der Grafikobjekte, z. B. den Visual Studio-XAML-Designer unterstützt. Unterstützung mehrerer Objekttypen beeinträchtigt wie der Benutzer Gruppen bestehen aus verschiedenen Typen von Objekten auswählt.  
  
-   **Unterstützung für die primären und sekundären Auswahlzustand.** Ein Editor bieten primäre und sekundäre Auswahl Zustände miteinander zusammen, und so weiter angepasst, damit Objekte bearbeitet werden können, bietet, ausgerichtet.  
  
-   **Unterstützung für die direkte Bearbeitung.** Editoren können auch den Inhalt ihrer grafisch Objekte bearbeitet werden. Beispielsweise kann eine rechteckige Form auch Text innerhalb enthalten, die vom Benutzer geändert werden können. Darüber hinaus kann Text zentriert oder ausgerichtet werden. Direkte Bearbeitung umfasst mehr Detailebene der Benutzerinteraktion und erfordert daher einen entsprechenden Satz von visuellen Hinweise für die Präsentation von Informationen für den Benutzer.  
  
#### <a name="mouse-interaction"></a>Mausinteraktion  
  
|Eingabe|Ergebnis|  
|-----------|------------|  
|Klicken Sie auf ein nicht ausgewähltes Objekt|Wählt das Objekt, und eine gestrichelte Linie und Ziehpunkte, angezeigt, wenn das Objekt geändert werden kann.|  
|Klicken Sie auf ein ausgewähltes Objekt|Aktiviert die direkte Bearbeitung, wenn das Objekt unterstützt. Klicken außerhalb des Objekts deaktiviert direkten Bearbeitungsmodus.|  
|Doppelklicken Sie auf ein Objekt|Den Code hinter dem Objekt zur Bearbeitung geöffnet und kann einen Standardereignishandler einzufügen, falls zutreffend.|  
|Zeigen Sie auf ein Objekt|Der Mauszeiger in den Cursor verschieben. Darstellung des Objekts, z. B. die Helligkeit oder Farbe möglicherweise ändern.|  
|Zeigen Sie auf ein Auswahlkästchen|Der Mauszeiger in den Größenänderungscursor zum Ändern der. Für Objekte, die Drehung zu unterstützen, können einige Ziehpunkte den Zeiger auf einen Cursor drehen ändern, wenn der Zeiger in Bezug auf das Auswahlkästchen anders (z. B. Abstand verschoben) befindet.|  
|Ziehen|Selbst wenn das Objekt nicht bereits ausgewählt ist, ändert sich der Zeiger auf den Cursor verschieben, und verschiebt das Objekt.|  
|Editor den Fokus verliert.|Direktes Bearbeitungsmodus deaktiviert, obwohl das Objekt behält den Inhalt und die Darstellung, die während der letzten Vorgang/Auswahlzustand verwendet wurde.|  
|Objektauswahl|Durch einen Rahmen, gepunktete Linie oder anderen visuell Behandlung, markieren Sie die Grenze des Objekts angegeben.|  
|Ändern der Größe eines ausgewählten Objekts|Durch Auswahlpunkte gekennzeichnet.<br /><br /> Ein Objekt in der Größe veränderbaren hat acht Handles darstellt jeder Richtung, in dem dann geändert werden kann. Weniger Handles können verwendet werden, wenn das Objekt nur in bestimmten Richtungen angepasst werden kann. Wenn der Benutzer die Größe eines Objekts auf, in denen acht Ziehpunkte nicht interaktive wären, möglicherweise vier Handles verwendet werden. Handle Größen sollten gebunden werden, die Fenster Rahmen und Rand Metriken mit der **GetSystemMetrics** -API-Funktion Größe proportional zur Auflösung.<br /><br /> ![Vergrößern](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|  
|Drehen eines ausgewählten Objekts|![Handles zum Drehen](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Tastaturinteraktion  
  
|Eingabe|Ergebnis|  
|-----------|------------|  
|Registerkarte|Verschiebt den Fokusindikator für die logische Reihenfolge der Objekte im Editor. Möglicherweise links-nach-rechts oder oben-nach-unten abhängig **TabIndex** (oder Äquivalent) Eigenschaftswert Reihenfolge der Erstellung des Objekts und den Zweck des Editors. Umschalt + Tab, kehrt die Richtung des Indikators für den Fokus.|  
|LEERTASTE|Schwenkmodus aktiviert, während Tastatureingabe verwaltet wird. Zusätzliche Mauseingabe ist erforderlich, um die Position der Ansicht schwenken.|  
|STRG+LEERTASTE|Zoommodus aktiviert, während Tastatureingabe verwaltet wird. Zusätzliche Mauseingabe ist erforderlich, um erhöhen und verringern den Zoomfaktor.|  
|Strg + Alt + Minuszeichen|Wird den Zoomfaktor, um eine Ebene verringert.|  
|Strg + Alt + Pluszeichen|Wird den Zoomfaktor, um eine Ebene erhöht.|  
|UMSCHALT oder STRG|Fügt das Objekt der Auswahlgruppe hinzu. STRG können Sie Objekte einzeln aus der Auswahlgruppe entfernen.|  
|Eingabe|Führt den Standardbefehl für das Objekt (in der Regel öffnen oder bearbeiten).|  
|F2|Aktiviert die direkte Bearbeitung des Objekts.|  
|Pfeiltasten|Verschiebt die ausgewählten Objekte in die Richtung der Pfeiltaste gedrückt, in kleinen Schritten (z. B. 1 Pixel zu einem Zeitpunkt)|  
|STRG + Pfeiltasten|Verschiebt die ausgewählten Objekte in die Richtung der Pfeiltaste gedrückt, in größeren Schritten (z. B. 10 Pixel auf einmal)|  
|UMSCHALT + nach-Schlüssel|Ändert die Größe der ausgewählten Objekte in der entsprechenden Richtung in kleinen Schritten (z. B. 1 Pixel zu einem Zeitpunkt)|  
|STRG + UMSCHALT + Pfeiltasten|Ändert die Größe der ausgewählten Objekte in der entsprechenden Richtung in größeren Schritten (z. B. 10 Pixel auf einmal)|  
  
 Wenn Benutzer Platzieren der Steuerelemente bearbeiten, kann es für Objekte mit Benutzereingaben, seine Größe automatisch sinnvoll. Z. B. wenn der Benutzer ein Label-Steuerelement bearbeitet, soll dann die Bezeichnung vergrößert werden den Text angezeigt, den der Benutzer gerade eingegeben haben. Wenn dies nicht erfolgt, muss der Benutzer Größe des Steuerelements manuell nach den Text bearbeiten. Verfügt der Benutzer viele Steuerelemente, wird diese an einen routinemäßigen und Ausfallzeitraum Aufgabe.  
  
#### <a name="graphical-containers"></a>Grafik-Container  
 In einigen Fällen stellen grafische Editoren Container für andere grafische Objekte, z. B. das Windows Forms-Steuerelement oder das Steuerelement Rasterlayout im HTML-Designer. Wenn der Editor Container für andere Grafikobjekte bereitstellt, sollte die folgende Auswahlmodell für den Container nur (Objekte innerhalb der Container gehen Sie folgendermaßen vor, das Standardmodell wie oben beschrieben) verwendet werden:  
  
|Eingabe|Ergebnis|  
|-----------|------------|  
|Klicken Sie einfaches für den container|Wählt das Container-Objekt ohne die darin enthaltenen Objekte direkt auswählen. Der Container kann verschoben oder mit standard-Maus und Tastatur (wie oben beschrieben) geändert werden. Enthaltene Objekte werden in Bezug auf den Container verschoben, aber enthaltenen Objekte werden nicht geändert, es sei denn, sie auch direkt aktiviert sind.|  
|Zeigen Sie auf den Container Grenze region|Aktiviert die Maus in den verschieben-Cursor, die angibt, dass der Container verschoben werden kann.|  
|Ziehen Sie den Container Grenze region|Ändert den Mauszeiger auf den Cursor verschieben, und verschiebt den Container (und die enthaltenen Objekte in). Der Container kann nicht verschoben werden, ohne zuerst mit einem Mausklick ausgewählt werden.|  
|Klicken Sie einfaches auf ein Objekt im container|Hebt die Auswahl des Containers (falls aktiviert), und wählt nur das Objekt, auf den geklickt wurde.|  
|UMSCHALT + klicken oder STRG + Klicken Sie auf ein enthaltenes Objekt und/oder container|Eine Auswahl oder Auswahlgruppe hinzugefügt ausgewählten Objekts. Wenn das Objekt geklickt wurde bereits ein Mitglied der Auswahlgruppe ist, wird es aus der Auswahlgruppe entfernt.|  
  
 Die enthaltenen Objekte müssen das grundlegende Auswahlmodell entsprechen, wie im vorherigen Abschnitt beschrieben. Von Nutzbarkeitstests von Windows Forms-Designer, erwartet Benutzer nahtlosen Zugriff auf die enthaltenen Objekte ohne dazwischenliegende Schritte (die Containment-Objekt).  
  
#### <a name="disjoint-and-region-selections"></a>Unabhängige und Region  
 Objekt-Editoren sollten nicht zusammenhängende Auswahlbereiche unterstützt. Beachten Sie, dass diese Grafik nicht die Darstellung des Steuerelements für Visual Studio angezeigt wird. Finden Sie unter [Objekt Auswahl Darstellung](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) ausführliche visual-Spezifikationen.  
  
 ![Auswahl nicht zusammenhängender Bereiche und Regionen](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")  
  
 **Nicht zusammenhängende Auswahl**  
  
 Außerdem sollten grafische Editoren Region Auswahl mit einer Auswahl Marquee-Typindikator bereitstellen. Wenn der grafische-Editor andere Objekttypen (z. B. Text) unterstützt, dann Region Auswahl kann je nach den Einschränkungen dieser anderen Typen von Objekt möglicherweise nicht.  
  
 ![Laufschriftauswahl](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")  
  
 **Auswahlrahmen**  
  
#### <a name="primary-and-secondary-selections"></a>Primäre und sekundäre Auswahl  
 Grafikobjekt Editoren können Benutzer bearbeiten oder Ausrichten von Objekten in Gruppen. In diesem Fall muss das Konzept von primären und sekundären Auswahl eingefügt werden soll. Die primäre Auswahl ist das Objekt, auf dem alle anderen Objekte für das Gruppieren von Operationen zu reagieren. Das Objekt, das der Benutzer zuerst wählt wird das primäre Steuerelement, und nachfolgende Auswahl werden die sekundären Auswahl. Die primäre Auswahl ist eine unterschiedliche visual Behandlung von der sekundären eine Wahl, um anzugeben, welches Objekt ein Primärschlüssel ist:  
  
 ![Primär- und Sekundärauswahl](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")  
  
 **Primäre Auswahl mit zwei sekundäre Auswahl**  
  
####  <a name="a-namebkmkgraphicalobjectselectionappearancea-graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Darstellung der Objekt-Auswahl  
 Ziehpunkte sind Quadrate, die in einem rechteckmuster, um das umgebende Feld des Objekts gezeichnet. In der folgenden Tabelle werden Beispiele für die verschiedenen Zustände, die ein Objekt mit Handle, Größe und direkte Bearbeitung Darstellung aufweisen können. Die Größe der Ziehpunkte sollten scheinbar Fensterrahmen und Edge Metriken mit der **GetSystemMetrics** API.  
  
|Zustand|Darstellung|Visuelle details|  
|-----------|----------------|--------------------|  
|**Diese Option nicht ausgewählt**|Default|![Status der Standardschaltfläche](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState")||  
|**Primäre Auswahl**|Größe änderbar|![Primäre Auswahl mit Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize")|![Primäre Auswahl mit Handles & #40 Größe; vergrößert &#41;](../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713-12_PrimaryResizeZoom")|  
|**Primäre Auswahl**|Nicht geändert werden kann|![Primäre Auswahl ohne Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize")|![Primäre Auswahl ohne Handles & #40 Größe; vergrößert &#41;](../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713-14_PrimaryNoResizeZoom")|  
|**Primäre Auswahl**|Gesperrt|![Primäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked")|![Primäre Auswahl gesperrt &#40; vergrößert &#41;](../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713-16_PrimaryLockedZoom")|  
|**Sekundäre Auswahl**|Größe änderbar|![Sekundäre Auswahl mit Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize")|![Sekundäre Auswahl mit Handles & #40 Größe; vergrößert &#41;](../../extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713-18_SecondaryResizeZoom")|  
|**Sekundäre Auswahl**|Nicht geändert werden kann|![Sekundäre Auswahl ohne Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize")|![Sekundäre Auswahl ohne die Größe des &#40; vergrößert &#41;](../../extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713-20_SecondaryNoResizeZoom")|  
|**Sekundäre Auswahl**|Gesperrt|![Sekundäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked")|![Sekundäre Auswahl gesperrt &#40; vergrößert &#41;](../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713-22_SecondaryLockedZoom")|  
|**UI aktiv**|Default|![Benutzeroberfläche im aktiven Status](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive")|![Benutzeroberfläche im aktiven Status &#40; vergrößert &#41;](../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713-24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Die Auswahlmodelle anzeigen  
  
#### <a name="tree-view"></a>Strukturansicht  
 Mit einer einfachen Hervorhebung wird Auswahl in einer Strukturansicht angezeigt. Wenn der Benutzer auf einen Knotennamen oder ein Knoten Symbol klickt, wird der Knoten ausgewählt. Die dreieckigen Symbole auf der linken Seite des Knotens erweitern oder Verkleinern des Strukturansicht-Steuerelements aber wirken sich nicht auf die Auswahl des Benutzers, mit einer Ausnahme: beim Reduzieren von einem übergeordneten Knoten wird die Auswahl auf ein untergeordnetes Element dieses Knotens verschiebt die Auswahl zum übergeordneten Element.  
  
 ![Typische Strukturansicht in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")  
  
 **Typische Strukturansicht in Visual Studio**  
  
 Strukturansichten können sogar über mehrere Ebenen in der Struktur zusammenhängenden und nicht zusammenhängenden Auswahl unterstützen. Zusammenhängenden oder nicht zusammenhängenden Mehrfachauswahl auf sichtbaren Strukturknoten vorgenommen werden müssen. Wenn ein Knoten reduziert wird, die nicht zusammenhängende Auswahl geht verloren, und der Knoten, der reduziert wurde, erhält die Auswahl. Auf diese Weise können die Knoten anzeigen, die von einem Vorgang betroffen sind. Wenn der Knoten reduziert werden, wird es unklar welche Knoten betroffen sein könnten.  
  
 Bei ein übergeordneten Knoten ausgewählt ist, sollten der Vorgang des übergeordneten anwenden, obwohl es gibt möglicherweise Fälle, in denen es für einen Vorgang für das übergeordnete Element und alle untergeordneten sinnvoll. In diesem Fall geben Sie zusätzliche Benutzeroberfläche während des Vorgangs, z. B. ein Kontrollkästchen oder ein Dialogfeld zur Bestätigung, die Option "gelten für alle untergeordneten Elemente" für dem Benutzer explizit zu machen.  
  
##### <a name="renaming"></a>Umbenennen  
 Wenn Knoten in der Struktur nicht umbenennen, sollten umbenennen an Stelle vorgenommen werden. Der in-Place-Vorgang sollte der Standard für alle Struktursteuerelemente in Visual Studio. Geben Sie einen Befehl Umbenennen, der sofort, den in-Place-Bearbeitungsmodus mit der Textauswahl, die für den gesamten Namen des Knotens bereit aktiviert, das Benutzereingaben akzeptiert. Wenn der Knoten eine Datei darstellt, sollte der Dateinamen die Erweiterung enthalten. Die Markierung sollte nur den Text der Dateiname und nicht die Erweiterung enthalten.  
  
|Eingabe|Ergebnis|  
|-----------|------------|  
|Eingabetaste|Führt einen Commit für die Umbenennung|  
|ESC-Taste|Bricht die Umbenennung|  
|Klicken außerhalb des Bearbeitungsbereichs direktes|Führt einen Commit für die Umbenennung|  
|Rückgängig|Geben Sie einfach rückgängig, um die Umbenennung abzubrechen.|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Auswahl in Listen und DataGrid-Steuerelementen  
 Das Schlüsselkonzept in Listenauswahl ist, dass die Zeile-basiert ist, was bedeutet, dass bei eine Auswahl wird die gesamte Zeile als eine Einheit ausgewählt ist. Im Gegensatz dazu können Raster bestimmte Zellen ausgewählt werden, ohne alle anderen Aspekte der Zeile. Raster können auch eine Hierarchie von geschachtelten Zeilen (z. B. in einem TreeGrid) enthalten, mit denen die gesamte Zweige der Hierarchie ausgewählt und durch die Interaktion mit der übergeordneten Zeilen deaktiviert werden. Auswahl in Listen wird durch eine einfache Markierungsfarbe für die gesamte Zeile der Daten angezeigt. Fokus wird durch einen einzelnen Pixel gepunkteten Rahmen der aktuellen bearbeitbaren Zeile oder der Zelle (Zeile, wenn Sie alle Zellen schreibgeschützt sind) angezeigt.  
  
> [!NOTE]
>  **Fokus** und **Auswahl** sind unterschiedliche Konzepte. *Fokus* ist ein Hinweis darauf, welche Benutzeroberfläche Element zielt, um Eingaben nicht explizit auf ein anderes Objekt zu erhalten, während er sich *Auswahl* bezieht sich auf den Status eines Objekts Aufnahme in einen Satz von Objekten, die auf die nachfolgenden Vorgänge stattfinden können.  
  
 Auswahl in den Listen unter Umständen zusammenhängenden disjunkt, oder die Region. Wenn Mehrfachauswahl zulässig, zusammenhängenden und nicht zusammenhängenden Auswahl sollte immer unterstützt werden, und zwar für die Auswahl der Region (Feld) ist optional. Auswahl der Region werden durch Ziehen in den Leerraum des Textkörpers Liste initiiert.  
  
|Objekt|Auswahl|  
|------------|---------------|  
|Liste|Zusammenhängenden|(Wenn es sich um eine Mehrfachauswahl zulässig sind) wird immer unterstützt.|  
|Liste|Unabhängige|(Wenn es sich um eine Mehrfachauswahl zulässig sind) wird immer unterstützt.|  
|Liste|Region|Die Unterstützung ist optional. Durch Ziehen der Maus in den Leerraum des Textkörpers Liste initiiert.|  
  
 Klicken einmal auf eine Liste zur Auswahl der Zeile, in dem der Klick aufgetreten ist. Wenn der Benutzer auf eine Zelle klicken, die in-Place-Bearbeitung unterstützt, wird die Zelle auch sofort für die direkte Bearbeitung aktiviert. Andernfalls wird die gesamte Zeile sofort aktiviert ist und eine Hervorhebung zeigt.  
  
 Ziehen in der Liste Text ist eine der drei Dinge:  
  
-   Eine Bereichsauswahl initiiert, wenn die Liste unterstützt und die Maus-nach-unten in Leerzeichen  
  
-   Initiiert einen Drag & Drop-Vorgang, wenn die Zelle oder Zeile unterstützt wird als Quelle des Ziehvorgangs  
  
-   Markiert die aktuelle Zeile  
  
##### <a name="in-place-editing"></a>Direktes Bearbeiten  
 Wenn direkte Bearbeitung zulässig ist, es gibt zwei grundlegende Modelle: Steuerelement und der Eigenschaft Auswahl einer einfachen bearbeiten. Mit einem einfachen Bearbeitungssteuerelement ist der Inhalt markiert und kann für Benutzereingaben als in-Place-Bearbeitung aktiviert ist. Bei eine Auswahl einer Eigenschaft implementiert wird, wird die Schaltfläche, die die Auswahl einer Eigenschaft aufruft angezeigt, sobald direkten Bearbeitungsmodus aktiviert wird, und die aktuelle Auswahl nicht hervorgehoben ist. Die Auswahl einer Schaltfläche sollte in der Zelle rechtsbündig ausgerichtet sein. Direkte Bearbeitung Beispiele finden Sie in der **im Eigenschaftenfenster** und **Aufgabenliste** in Visual Studio.  
  
##### <a name="keyboard-support"></a>Tastaturfunktionen  
 Tastaturunterstützung für die Auswahl in Listen und Raster folgt den standard-Windows-Konventionen:  
  
-   Pfeiltasten wechseln Sie die Liste, die jede Zeile/Zelle auswählen, wie der Fokus verschoben wird.  
  
-   UMSCHALT + nach-führt eine zusammenhängende Auswahl in die Richtung der Pfeiltasten.  
  
-   STRG + nach-gefolgt vom LEERTASTE Schaltet zwischen hinzufügen und Entfernen von Elementen aus der Auswahl eine separaten Auswahl erstellen.  
  
-   Rastern, die geschachtelte Hierarchien enthalten, die nach-rechts-Taste erweitert eine übergeordnete Zeile und die nach-links-Taste Blendet eine.  
  
-   Die Tab-Taste verschiebt den Fokus zwischen den Zellen in der aktuellen Zeile, wenn die Zellen bearbeitet werden.  
  
-   Die EINGABETASTE führt den Standardbefehl für das Element in der Liste (häufig **Öffnen**).  
  
-   Die F2-Taste wird die direkte Bearbeitung für die derzeit ausgewählte Zelle aktiviert.  
  
##  <a name="a-namebkmkpersistenceandsavingsettingsa-persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistenz und Speichern von Einstellungen  
  
### <a name="overview"></a>Übersicht  
 Obwohl jede Softwarekomponente in Visual Studio in der Regel für einen eigenen Status und die Persistenz zuständig ist, speichert Visual Studio Einstellungen in einigen Fällen, z. B. mit Fenstergrößen und Positionen. In der folgenden Tabelle ist eine Kombination der Einstellungen automatisch gespeichert und Einstellungen, die einen expliziten Benutzer erfordern oder programmiert auszuführende Aktion.  
  
|Objekt|Sichern|Beim Speichern|Speicherort|  
|------------|------------------|------------------|-------------------|  
|Auswählbare Objekt (z. B. eine Zeile Code)|Einen Haltepunkt in einer Codezeile<br /><br /> Eine Benutzer-Verknüpfung, die die Zeile des Codes zugeordnet|Wenn das Projekt gespeichert wird|Die **Benutzeroptionen (.suo)** -Datei für das Projekt|  
|Dialogfeld|Der Speicherort des Dialogfelds, wenn es verschoben wurde, hatte<br /><br /> Die Ansicht, die der Benutzer im Dialogfeld zuletzt verwendet|Wenn das Dialogfeld wird geschlossen<br /><br /> Wenn die Visual Studio-Sitzung beendet|Im Arbeitsspeicher<br /><br /> Registrierung **HKEY_Current_User**|  
|Fenster|Die Größe und Position des Fensters|Wenn das Fenster wird geschlossen<br /><br /> Wenn der Visual Studio-Modus geändert wird<br /><br /> Wenn die Visual Studio-Sitzung beendet|Die **Benutzeroptionen (.suo)** -Datei für das Projekt<br /><br /> Benutzerdefinierte Datei für Fenster-Einstellungen|  
|Dokument|Die aktuelle Auswahl im Dokument<br /><br /> Die Ansicht des Dokuments<br /><br /> Die letzte verschiedenen Orten, die der Benutzer bereits besucht|Wenn das Dokument gespeichert wird|Die **Benutzeroptionen (.suo)** -Datei für das Projekt|  
|Projekt|Verweise auf Dateien<br /><br /> Verweise auf Verzeichnisse auf dem Datenträger<br /><br /> Verweise auf andere software<br /><br /> Komponenten<br /><br /> Statusinformationen über das Projekt selbst|Wenn das Projekt gespeichert wird|Die Projektdatei|  
|Lösung|Verweise auf Projekte<br /><br /> Verweise auf Dateien|Wenn das Projekt oder die Projektmappe gespeichert wird|Die **Projektmappendatei (.sln)** Datei|  
|Einstellungen in **Tools > Optionen**|Tastatur anpassen<br /><br /> Benutzerdefinierten Symbolleisten<br /><br /> Farbschemata|Wenn die **Tools > Optionen** Dialogfeld geschlossen wird.<br /><br /> Wenn die Visual Studio-Sitzung beendet|Registrierung **HKEY_Current_User**|  
  
 Was der Benutzer tut, und beim durchführen will, bestimmt, ob eine Einstellung im Arbeitsspeicher (in der Sitzung), (sitzungsübergreifend als eine Einstellung in der Registrierung), auf dem Datenträger gespeichert gespeichert wird als Teil der Projekt- oder Projektmappendatei selbst als Teil von der **Lösungsoptionen (.suo)** Datei oder als eine benutzerdefinierte, die nur diesem Softwarekomponente Einstellungsdatei kennt. Die Tabelle enthält mehrere Ereignisse, die in denen Einstellungen gespeichert werden können. Es gibt jedoch manchmal in denen Zustand speichern möchten:  
  
-   Wenn der Benutzer die Position in einem Dialogfeld oder Fenster ändert  
  
-   Wenn der Benutzer den Fokus auf ein anderes Fenster übertragen  
  
-   Wenn der Benutzer vom Entwurf in den Debugmodus wechselt.  
  
-   Wenn Sie ihr Konto meldet den Benutzer  
  
-   Wenn der Computer in den Ruhezustand wechselt oder heruntergefahren  
  
-   Wenn der Computer/Festplatte handelt, werden erneut formatiert und erneut einrichten  
  
### <a name="window-configurations"></a>Fensterkonfigurationen  
 Eine Fensterkonfiguration ist die grundlegende Darstellung von der Development Environment – es wird ein Schema aus der Liste der Toolfenster vorhanden und die Möglichkeit, in der sie angeordnet sind. Für Windows von der IDE (IDE-Fenster) verwaltet wird Layoutinformationen pro Benutzer und beibehalten, wenn ein Benutzer startet die IDE das Layout des Eigenschaftenfensters angezeigt wird, identisch, wenn sie zum letzten Visual Studio beendet. Den Status und die Position des IDE-Fenster wird in einer benutzerdefinierten Datei im XML-Format beibehalten. Toolfenster, die von Paketen, die in der IDE geladen wurden behalten ihren Status in der Registrierung und können möglicherweise nicht pro Benutzer.  
  
#### <a name="profile-specific-layouts"></a>Spezifische layouts  
 Jedes Profil enthält Tool-Fensterlayouts, organisiert in einer Weise, die bestimmte Rollen vertraut (Visual C++-Entwickler erwarten die **Projektmappen-Explorer** auf der linken Seite der IDE, während die C#-Entwickler erwarten die **Projektmappen-Explorer** auf der rechten Seite). Spezifische Fensterlayouts werden geladen, nachdem der Benutzer ein Profil auf Start wählt. Der Paketautor eines sollten das Fensterlayout für ihre Kundenzufriedenheit am besten geeigneten bestimmen, zu wissen, dass Änderungen, die vom Benutzer an der Fensterkonfiguration im dann beibehalten werden.  
  
##  <a name="a-namebkmktouchinputa-touch-input"></a><a name="BKMK_TouchInput"></a> Fingereingabe  
 Benutzer verwenden immer Microsoft Development-Produkte auf Touch-Geräte. Es gibt jedoch Barrieren, die mit Entwicklungstools für Touch-Geräte erschweren. Benutzer erwarten, dass unsere Produkte, um eine zuverlässige und präzise Touch-Erfahrung bereitzustellen. Der Zweck dieser Richtlinien ist Entscheidungen mit Touch-Funktionen integrieren und eine konsistente Touch-Erfahrung über Visual Studio und verwandte Produkte zu informieren.  
  
### <a name="levels-of-experience"></a>Ebenen Erfahrung  
 Die folgenden Ebenen Erfahrung dienen als Anleitung können Teams entscheiden, abhängig von gewünschten Maß Zinsen in Kontakt mit Touch-Funktionen zu bieten.  
  
-   Die **Grundkenntnisse** ist für Teams, die bereitstellen möchten Funktionen touch, damit es keine Sackgassen ihren arbeiten gibt.  
  
-   Die **optimierte Erfahrung** ist für Teams, die die meisten allgemeinen Touch-Funktionen (z. B. die in der Regel im Internetbrowser verfügbar) bereitstellen möchten.  
  
-   Die **Erfahrung erhöhten** ist für Teams, die solche Funktionen hinzufügen möchten, die als Gesten oder andere optionale Funktionen, die ihrer Anwendung vornehmen können Fingereingabe angezeigter.  
  
||Grundkenntnisse|Optimierte Erfahrung|Erfahrung mit erhöhten rechten|  
|-|----------------------|--------------------------|-------------------------|  
|Ermöglicht es Benutzern...|Beheben von Code und Projektmappe/Projekt-Ebene ohne Sackgassen lesen|Aufgaben der Wartung, umgestaltungen angezeigt und navigation|Arbeiten Sie in eine konsistente, intuitive und flüssige Erfahrung mit Zuversicht|  
|Editor|Tippen Sie schwenken und Auswahl<br /><br /> Bildlaufleiste berühren, wechseln, und drücken + ziehen|Verkleinern Vergrößern<br /><br /> Schnelle Scrollen<br /><br /> Auswahl<br /><br /> Einfache Verwendung von Kontextmenüs||  
|Top-Toolfenster|Liste Schwenken<br /><br /> Elementauswahl<br /><br /> Bildlaufleiste berühren, wechseln, und drücken + ziehen|Einfache Element Bildlauf und Auswahl||  
|Windowing||Die Größe öffnen<br /><br /> Schnellzugriff||  
|Dokumentieren Sie gut||Einfache Navigation zwischen geöffneten Dateien||  
|Gesten||Sicherstellen Sie, dass allgemeine Gesten in der IDE funktionieren|Bewegungsgesteuerte Aktionen<br /><br /> Unterstützung von Drag-and-Drop und Designer|  
|Andere Überlegungen|||Benutzerdefinierte Bildschirmtastatur|  
  
#### <a name="gestures"></a>Gesten  
 Gesten bieten Benutzern eine Verknüpfung mit Befehlen, die andernfalls möglicherweise eine kompliziertere Interaktion erfordern. Anhand der Windows-Richtlinien auf [gemeinsamen Touchgesten für Desktopanwendungen](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx), und befolgen Sie diese Anleitung für die meisten Gesten, einschließlich der einfachen Gesten wie Schwenken und zoomen.