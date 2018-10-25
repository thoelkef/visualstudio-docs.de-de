---
title: Zusammengesetzte Muster für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cece4eb8b2d18f7d3b4297ab06fc01f4e54f8d47
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926643"
---
# <a name="composite-patterns-for-visual-studio"></a>Zusammengesetzte Muster für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zusammengesetzte Muster kombinieren Interaktions- und Elemente in unterschiedlichen Konfigurationen. Einige der wichtigsten zusammengesetzte Muster in Visual Studio im Hinblick auf Konsistenz sind:  

-   [Visualisierung von Daten](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  

-   [Objektgebundenen Benutzeroberfläche und einsehen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  

-   [Auswahlmodelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  

-   [Persistenz und Einstellungen werden gespeichert.](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  

-   [Touch-Punkts](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  

##  <a name="BKMK_DataVisualization"></a> Visualisierung von Daten  

### <a name="overview"></a>Übersicht  
 Diagramme sind eine visuelle Möglichkeit zum Aggregieren und Visualisieren Sie Daten, um Entscheidungen zu verbessern. Sie können die Benutzer, die mit einer Vielzahl von Daten, aber wenig bedeutet finden Sie unter Was Aufmerksamkeit verdient, und was eine Aktion möglicherweise konfrontiert.  

 Der Benutzer wird aus einem Diagramm profitieren, wenn eine der folgenden Bedingungen zutrifft:  

-   Wird das Diagramm den Benutzern, die Aufgaben zu identifizieren, die, denen Sie bearbeiten können, besser?  

-   Wird das Diagramm der Benutzer, die Auswirkungen möglicher Änderungen zu prognostizieren aktiviert?  

-   Wird das Diagramm den Benutzern, die Erkennung von Trends und Muster identifizieren besser?  

-   Lässt das Diagramm Benutzer bessere Entscheidungen zu treffen?  

-   Wird das Diagramm eine bestimmte Frage beantworten, die Benutzer im angegebenen Kontext möglicherweise helfen?  

#### <a name="general-rules-for-charts"></a>Allgemeine Regeln für Diagramme  

-   Klar bezeichnungsdaten. Abbildungen ohne erläuterungen sind nur so ziemlich Bilder.  

-   Starten Sie die Achsen auf 0 (null), um neigen Proportionen zu vermeiden. Länge und Balken Größe sind wichtig visuelle Hinweise für das Verständnis der Beziehungen zwischen Datenpunkten.  

-   Erstellen Sie Diagramme, nicht infografiken. Infografiken stehen künstlerische Darstellungen von Daten, und das primäre Ziel ist das visual Storytelling. Diagramme können (und sollten) visuell ansprechend sein, aber lassen Sie die Daten für sich selbst sprechen.  

-   Vermeiden Sie Skeumorphism, grafische Balkendiagrammen, Kontrast Rautenzeichen und andere Workflows INFOGRAFIK.  

-   Verwenden Sie 3D-Effekte nicht als dekoratives Element aus. Verwenden sie nur, wenn sie die Möglichkeit des Benutzers zu verstehen, die Informationen tatsächlich integraler Bestandteil.  

-   Verwenden Sie mehrere Linien und Füllungen, da mehr als zwei Farben aus, diese Art von Diagramm schwierig dass können zu lesen und richtig interpretieren.  

-   Verwenden Sie ein Diagramm (oder eine beliebige Abbildung) nicht als einziges Mittel der ein Konzept zu verstehen oder interagieren mit Daten. Dies stellt die Probleme für Benutzer mit eingeschränkter sehfähigkeit.  

-   Verwenden Sie die Diagramme nicht als kostenlose oder dekorative Elemente auf einer Seite. Das heißt, wenn ein Diagramm nicht, dass alle Benutzer Wert oder Hilfe beim Lösen eines Problems hinzufügen, verwenden Sie nicht.  

### <a name="chart-types"></a>Diagrammtypen  
 Diagramme, die in Visual Studio verwendet Typen Balkendiagramme, Liniendiagramme, eine geänderte Kreisdiagramm, bekannt als Ringdiagramm oder "Ringdiagramm", Zeitachsen, Punktdiagramm Plots (auch als "cluster-Diagramme" bezeichnet) und Gantt-Diagramme. Jede Art von Diagramm eignet sich für die Kommunikation einer anderen Art von Informationen.  

### <a name="other-charting-considerations"></a>Weitere Überlegungen zum Erstellen von Diagrammen  

#### <a name="color"></a>Farbe  
 Es gibt eine bestimmte Palette der Darstellung von Farben, die für die Verwendung in Visual Studio definiert. Die Palette ist für die wichtigen Arten von Farbenblindheit zugegriffen werden kann, und die Farben unterschieden werden können, auch bei Verwendung als sehr kleine Segmente der Farbe. Sie können diese Farben in beliebiger Kombination in der Benutzeroberfläche für jede Art von Diagramm verwenden. Sie müssen nicht alle sieben Farben zu verwenden, wenn Sie nicht, dass viele unterschiedliche Farben benötigen. Diese Farben wurden nicht mit vordergrundelemente, sodass setzen kein Text oder Symbole, die über diese Farben verwendet werden soll. Diese Farbtöne hartcodiert und benutzeranpassung unter verfügbar gemacht werden **Tools > Optionen** (finden Sie unter [Verfügbarmachen von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  

|Farbmuster|Hex|RGB|  
|------------|---------|---------|  
|![Farbmuster 71 b 252](../../extensibility/ux-guidelines/media/0711-71b252.png "0711_71B252")|# 71 B 252|113,178,82|  
|![Farbmuster BF3F00](../../extensibility/ux-guidelines/media/0711-bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Farbmuster FCB714](../../extensibility/ux-guidelines/media/0711-fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Farbmuster 903F8B](../../extensibility/ux-guidelines/media/0711-903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Farbmuster 117AD1](../../extensibility/ux-guidelines/media/0711-117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Farbmuster 79D7F2](../../extensibility/ux-guidelines/media/0711-79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Farbmuster B5B5B5](../../extensibility/ux-guidelines/media/0711-b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  

##  <a name="BKMK_OnObjectUI"></a> Objektgebundenen Benutzeroberfläche und einsehen  
 Dieser Abschnitt enthält Kontext zum einsehen, auch bekannt als Code Vorschauansicht, eines Typs des objektgebundenen Benutzeroberfläche nur für Visual Studio.  

### <a name="overview"></a>Übersicht  

- Objektgebundenen Benutzeroberfläche sollte dem Benutzer Weitere Informationen oder Interaktivität bieten, ohne Ablenkung von deren Hauptaufgabe sein zu müssen.  

- Das wichtigste Muster für die objektgebundenen-Benutzeroberfläche in Visual Studio wird als "Informationen zum Zeitpunkt der Aufmerksamkeit." bezeichnet.  

- Objektgebundenen-Benutzeroberfläche in Visual Studio ist entweder Inline oder Gleitkommazahl und dauerhafte oder vorübergehende.  

  -   Vorschauansicht "Code", "ein Typ des objektgebundenen UI in Visual Studio ist Inline und dauerhaft.  

  -   Ein Typ des objektgebundenen UI in Visual Studio CodeLens ist Gleitkomma- und vorübergehende  

  Grundlegendes zur Funktionsweise eines Codeabschnitts, oder Suchen von Informationen zu diesen Code, erfordert häufig ein Entwickler den Kontext wechseln, und wechseln zu anderen Inhalten oder einer anderen Fenster. Diese Kontext-Schichten können störend sein, sein, da der Benutzer den Fokus auf ihre ursprünglichen Aufgabe verlieren können, wenn sie ihre Hauptfenster lassen. Darüber hinaus werden abgerufen, dass die ursprünglichen Kontext zurück, insbesondere dann, wenn ihre ursprünglichen Code von der andere Benutzeroberfläche verdeckt werden Wechseln zwischen Fenstern verursacht werden, schwierig sein kann.  

  Objektgebundenen UI folgt einem Muster, die Namen "Informationen zum Zeitpunkt der Aufmerksamkeit." Diese Nachrichten, Popup-Fenster und Dialogfelder bieten den Benutzern zusätzliche, relevanter Informationen, die Informationen zu den oder die Interaktivität hinzufügt, ohne den Fokus auf ihre Hauptaufgabe. Beispiele für objektgebundenen UI sind Popupfenster, die angezeigt werden, wenn ein Benutzer den Zeiger, über ein Symbol im Infobereich angezeigt, die rote Wellenlinie unter ein falsch geschriebenes Wort, und die Vorschauansicht in Visual Studio 2013 eingeführt wurden bewegt.  

### <a name="decision-points"></a>Entscheidungspunkte  
 In Visual Studio gibt es mehrere Möglichkeiten, diese Art von Informationen zum Zeitpunkt der Aufmerksamkeit zu verwenden. Auswählen des richtigen Mechanismus und implementieren es auf eine konsistente, vorhersehbare Weise unbedingt insgesamt die benutzerfreundlichkeit. Andernfalls können Benutzer eine Benutzeroberfläche verwirrend oder inkonsistente angezeigt, das entsteht, den Fokus von der Inhalt selbst beeinträchtigt.  

#### <a name="relationships-between-master-and-detail-content"></a>Beziehungen zwischen Master- und Inhalt  
 Informationen zum Zeitpunkt der Aufmerksamkeit wird verwendet, um die Anzeige einer Beziehung zwischen dem Inhalt, dass der Benutzer konzentriert sich auf (den "master"-Inhalt) und weitere verwandte Inhalte (den Inhalt von "Details"). Bei diesem Muster der Detail-Inhalt klar auf den Inhalt bezieht sich der Benutzer arbeitet mit und in der Nähe der master-Inhalt angezeigt werden kann. Zusätzliche Informationen oder Informationen, die zusammengefasst werden kann, ohne Sie zu einer Überlastung des master-Inhalts sollte, wie z. B. ein Toolfenster, ein weiteres Muster folgen.  

-   **Immer** zeigt den Inhalt der Details in der Nähe der master-Inhalt.  

-   **Immer** stellen Sie sicher, dass der Inhalt der Details weiterhin Benutzer bleiben, konzentriert sich auf den master Inhalt ermöglicht. Häufig besteht die beste Möglichkeit, dies zu erreichen den Detail-Inhalt als in der Nähe der master Inhalt wie möglich zu rendern. Dies kann Rendern des Inhalts Details in einem Popup-Fenster neben dem master Inhalt oder die Details Inhalt Inline unterhalb der master-Inhalt Rendern erfolgen.  

-   **Nie** verwenden Sie die Informationen zum Zeitpunkt der Aufmerksamkeit, die den Benutzer von der master-Inhalt verwendet. Wenn Benutzer den Inhalt Detail separat anzeigen müssen, machen Sie eine explizite Aktion, die dem Benutzer ermöglicht, die dazu.  

#### <a name="design-details"></a>Entwurfsdetails  
 Nachdem Sie ermittelt haben, dass objektgebundenen-Benutzeroberfläche die richtige Wahl ist, gibt es vier wichtige Überlegungen:  

1. **Persistenz:** wird der Inhalt als dauerhafte oder vorübergehende angesehen?   
   Sollten Benutzer sichtbarhalten von Informationen zu verweisen oder damit interagieren? Oder Benutzer sollten Sie einen schnellen Überblick, Informationen und fahren Sie mit der ihre Hauptaufgabe?  

2. **Inhaltstyp:** Inhalt werden nur zu Informationszwecken, Handlungsbedarf sehen bzw. Navigieren?   
   Ist der Benutzer, die zusätzlichen Details über den master Inhalt erforderlich? Muss der Benutzer zum Abschluss einer Aufgabe, die der Hauptschlüssel Inhalt wirkt sich auf? Oder muss der Benutzer auf eine andere Ressource weitergeleitet werden?  

3. **Indikatortyp:** ist ein Indikator ambient sinnvoll?   
   Kann die Informationen in eine nützliche Möglichkeit zusammengefasst und angezeigt, ohne Sie zu einer Überlastung des master-Inhalts?  

4. **Gesten:** was anwendungsstiftbewegungen wird zum Aufrufen und schließen die Benutzeroberfläche verwendet werden?   
   Wie der Benutzer den Inhalt für die Details anzuzeigen und senden Sie sie? Gibt es Wert in eine Geste wie z. B. zum Wechseln zwischen vorübergehenden und dauerhaften Status anheften hinzufügen?  

   Jede dieser vier Entscheidungspunkte werden Auswirkungen auf die Hauptkomponenten des objektgebundenen Benutzeroberfläche haben.  

### <a name="on-object-ui-components"></a>Objektgebundenen UI-Komponenten  

1.  Containertyp (ContentPresenter)  

    -   Gleitkomma  

    -   Inline  

2.  Inhaltstyp  

    -   Information: Daten, die statisch oder dynamisch sein können  

    -   Aktionen erfordernde: Befehle, die den Hauptschlüssel Inhalt ändern  

    -   : Navigationslinks, die der Benutzer in einem anderen Fenster oder einer Anwendung, z. B. MSDN ausführen  

3.  Gesten  

    -   Aufruf  

    -   Kündigung  

    -   Anheften von Zertifikaten  

    -   Weitere Interaktionen  

4.  Persistenz und Commit-Modell  

    -   Transient (vorübergehend)  

    -   Durable  

    -   Automatisch  

    -   Bei Bedarf  

5.  (Optional) der Ambient-Indikatoren  

    -   Wellenlinie unterstrichen  

    -   Smarttag-Symbol  

    -   Andere ambient-Indikatoren  

#### <a name="container-content-presenter-type"></a>Containertyp (ContentPresenter)  
 Es gibt zwei Hauptoptionen zur Verfügung, die zum Zeitpunkt der Aufmerksamkeit zu präsentieren:  

1.  **Inline:** eine Inline-Darstellung, wie z. B. die Peek-Sicht, die in der Visual Studio 2013-Code-Editor, eingeführte macht Platz für neue Inhalte durch die Umstellung der vorhandenen Inhalte.  

    -   **Bevorzugen** Inline-Darstellungen, wenn Sie erwarten, Benutzer möchten verbringen viel Zeit verweisen dass auf oder die Interaktion mit Inhalten, die Sie darstellen.  

    -   **Vermeiden Sie** Inline-Darstellungen, wenn Sie erwarten, Benutzer dass Blick auf die Informationen, die Sie darstellen, und klicken Sie dann ihre Hauptaufgabe mit minimalen Unterbrechungen fortsetzen möchten.  

2.  **Gleitkommawert:** ein unverankerten Presenter so nahe wie möglich dem ausgewählten Inhalt befindet er ändert jedoch nicht das Layout des vorhandenen Inhalts. Verschiedene Strategien verwendet werden, z. B. das Anzeigen eines frei verschiebbaren Panels des Inhalts über die nächstgelegenen verfügbaren Leerraum, um das ausgewählte Symbol.  

    -   **Bevorzugen** floating Presenter, wenn Sie erwarten, Benutzer dass möchten Blick auf die Informationen, die Sie darstellen, und klicken Sie dann ihre Hauptaufgabe mit minimalen Unterbrechungen fortsetzen.  

    -   **Vermeiden Sie** floating Presenter, wenn Sie erwarten, Benutzer dass verbringen viel Zeit verweisen auf oder die Interaktion mit Inhalten sollten Sie vorhanden.  

#### <a name="content-type"></a>Inhaltstyp  
 Es gibt drei Haupttypen von Inhalten, die in jeder objektgebundenen Benutzeroberflächen-Container angezeigt werden können. Eine beliebige Kombination dieser Typen von Informationen kann angezeigt werden. Die drei Typen sind:  

1.  **Information:** die meisten objektgebundenen UI-Containern werden eine Art von Informationelle angezeigt. Der Inhalt kann Informationen zu den aktuellen Zustand der Umgebung darstellen, oder es kann Informationen zu einem potenziellen zukünftigen Zustand der Umgebung dar. Beispielsweise kann verwendet werden, um die Auswirkungen eines bestimmten Befehls ein, z. B. ein refactoring, auf den vorhandenen Code anzuzeigen.  

    -   **Immer** verwenden, die kanonische Darstellung der Informationen, die angezeigt werden. Z. B. Code sollte wie folgt Code, vollständig mit syntaxhervorhebung, Aussehen und sollten berücksichtigt werden, Schriftart und anderen umgebungseinstellungen, die vom Benutzer festgelegt wurde.  

    -   **Immer** erwägen Sie die Unterstützung von Maßnahmen, die über die nur zu Informationszwecken Inhalte, die wäre möglich, wenn die gleiche Informationen als master Inhalt angezeigt wird. Z. B. wenn vorhandener Code innerhalb einer objektgebundenen Benutzeroberflächen-Container zu präsentieren, sollten Sie möglicherweise Unterstützung der Fähigkeit zum Durchsuchen und ändern diesen Code.  

    -   **Immer** sollten Sie eine andere Hintergrundfarbe verwenden, wenn nur zu Informationszwecken Inhalt darstellen, die einen potenziellen zukünftigen Zustand darstellt.  

2.  Umsetzbare: Einige objektgebundenen UI-Container werden die Fähigkeit zum Ausführen einer Aktion über die master-Inhalte, wie z. B. eines Umgestaltungsvorgangs bieten.  

    -   **Immer** umsetzbare Befehle separat von der Informationelle zu positionieren.  

    -   **Immer** aktivieren und Deaktivieren von Aktionen, die bei Bedarf.  

    -   **Immer** finden Sie in der Standardrichtlinien für die Darstellung von Befehlen in Dialogfeldern.  

    -   **Immer** minimale behalten Sie die Anzahl der Aktionen, die in einem Container des objektgebundenen-Benutzeroberfläche auf ein absolutes verfügbar gemacht werden. Interaktion mit objektgebundenen Benutzeroberfläche sollte ein einfaches, schnelles-Erlebnis. Der Benutzer sollte keine Energie zum Verwalten des objektgebundenen-UI-Containers selbst aufwenden.  

    -   **Immer** erwägen Sie, wie und wann ein Benutzeroberflächen-Container mit objektgebundenen geschlossen oder verworfen werden. Als bewährte Methode sollten alle Aktionen, die das Dialogfeld "zwischen der Master- und Inhalt wird abgeschlossen, auch die objektgebundenen Benutzeroberflächen-Container schließen, wenn mit dieser Aktion aufgerufen wird.  

3.  **Navigation:** einige objektgebundenen UI-Container enthalten Links, die der Benutzer in einem anderen Fenster oder einer Anwendung, z. B. öffnen einen MSDN-Artikel im Webbrowser des Benutzers ausführen.  

    -   **Immer** jede Landmarks Verknüpfung mit "Öffnen" voranstellen, damit, dass Benutzer nicht überraschen, werden einige andere Inhalt navigiert wird.  

    -   **Immer** Navigationslinks in umsetzbare Links zu trennen.  

#### <a name="ambient-indicators-optional"></a>(Optional) der Ambient-Indikatoren  
 Ambiente-Indikatoren möglich stimmt, einschließlich Text-, die in einer kontrastreichen Farbe vom Rest des Codes angezeigt oder offensichtlich Tickler-Symbole, z. B. Wellenlinie unterstrichen und Smarttag-Symbole einschließlich. Zusätzliche, relevanter Informationen zu Ambiente-Indikatoren kommunizieren. Im Idealfall bieten sie nützliche Informationen selbst, ohne dass der Benutzer Sie mit ihnen interagieren.  

-   **Immer** positionieren Sie einen ambient-Indikator, sodass abgelenkt werden oder nicht des Benutzers überlasten. Ist dies nicht möglich, einen ambient-Indikator so zu positionieren, sollten Sie eine andere Lösung.  

-   **Immer** positionieren Sie den Ambiente-Indikator so nah wie möglich auf den Inhalt, der es verknüpft ist.  

-   **Immer** versuchen, einen Indikator zu erstellen, die die Informationen zusammengefasst, zur Verfügung stellt. Geben Sie ggf. eine Anzahl die Anzahl der verfügbaren Datenelemente (z. B. "3 Referenzen" anstatt einfach "Referenzen"), oder stellen Sie sich eine andere Möglichkeit zum Zusammenfassen der Daten.  

    -   In Fällen, in denen die Daten für einen Indikator immer berechnet und angezeigt werden können, sofort berücksichtigen von Feedback progressive wie die Werte berechnet werden. Betrachten Sie beispielsweise das Animieren von Änderungen, die Updates für die verfügbaren Daten, die ähnlich wie die widerspiegeln, die die Anzahl der ungelesenen e-Mails erhöht die e-Mail-live-Kachel in Windows Phone aktualisiert wird.  

-   **Nie** hinzufügen Weitere Indikatoren, die als ein Benutzer für einen bestimmten des Inhalts relativ ausführen kann. Ambiente-Indikatoren sollten nützlich sein, ohne Eingreifen des Benutzers. Indikatoren verlieren ihre Umgebung aus, wenn der benötigten Überlauf und andere verwaltungssteuerung für sie sichtbar zu machen.  

#### <a name="gestures"></a>Gesten  
 Ein wichtiger Aspekt der Benutzer auf den master Inhalt konzentrieren kann, ist durch die Unterstützung von rechten Gesten zum Öffnen und schließen den Inhalt zusätzliche Details.  

-   **Immer** muss der Benutzer einige explizite Geste zum Öffnen des weiteren Inhalts führen. Allgemeine open Bewegungen zählen:  

    -   **Wenn darauf gezeigt wird:** QuickInfos oder nicht interaktiven Informationelle  

    -   **Expliziten Befehl:** Inline Presenter  

    -   **Doppelklicken Sie auf der ambient-Indikator:** CodeLens-Popup-Fenster  

-   **Immer** den Detail-Inhalt zu verwerfen, wenn der Benutzer die Esc-Taste drückt.  

-   **Immer** im Rahmen der objektgebundenen-Benutzeroberfläche zu berücksichtigen. Content-Darstellungen, die für die Interaktion in den Container zu ermöglichen, überlegt, ob zusätzliche Informationen zeigen, dies ist wahrscheinlich für den Workflow des Benutzers störend angezeigt.  

-   **Nie** Inhalte anzeigen, wenn darauf gezeigt wird, die angezeigt wird, bearbeitet werden kann, oder lädt der Benutzerinteraktion. Dieses Verhalten kann Benutzer frustrierend sein, wenn sie versuchen, den Cursor über dem Details-Inhalt, bewegen, wie das Standardverhalten für eine QuickInfo wird, um sofort zu schließen, wenn der Cursor nicht mehr über den Master Inhalt ist, die sie erstellt.  

##  <a name="BKMK_SelectionModels"></a> Auswahlmodelle  

### <a name="overview"></a>Übersicht  
 Ein Auswahlmodell ist ein Mechanismus verwendet, um anzugeben, und bestätigen Sie die Vorgänge für eine oder mehrere Objekte von Interesse sind, in der Benutzeroberfläche. In diesem Thema wird erläutert, Auswahl Interaktionsmuster in Editoren von Visual Studio-Dokument: Text-Editoren, Entwurfsoberflächen und Modellierung Flächen.  

 Benutzer benötigen eine Möglichkeit, der angibt, in Visual Studio dort gearbeitet, und Visual Studio muss mit folgendem Antworten vorhersagbares Feedback, die Benutzer über was für den Sie ausgeführt wird. Unterschiede oder einer fehlerhaften für die Kommunikation zwischen dem Benutzer und die Benutzeroberfläche kann zu einem der Benutzer, die nicht an eine Aktion, die haben, kann unerwartete Ergebnisse liefern. Oft unbemerkt der Fehler, bis der Benutzer sieht, dass etwas fehlt oder wurde geändert. Auswahlmodelle sind daher eine der wichtigsten Teile der Entwurf der Benutzeroberfläche. Obwohl Auswahl-Modellen in Visual Studio mit Windows konsistent sind, gibt es leichte abweichungen.  

 Unterscheiden sich in Visual Studio wie Windows Auswahlmodelle je nach Kontext, in dem die Aktivität auftritt. Auswahl können in vier Typen von Objekten auftreten:  

- Text  

- Grafikobjekte  

- Listen und Strukturen  

- Raster  

  Innerhalb dieser Objekte gibt es drei Arten von Optionen:  

- Zusammenhängende  

- Zusammenhanglose  

- Region  

#### <a name="scope"></a>Bereich  
 Die wichtigste Komponente der Auswahl ist das sicherstellen, dass der Benutzer weiß, in welchem Fenster sie (Aktivierung) arbeiten und, in denen der Fokus befindet (Auswahl) befindet. Visual Studio erweitert die Verwaltungsfunktionalität für Fenster in Windows, das Schema für die Aktivierung ist jedoch die gleiche: interagieren mit einem Fenster setzt den Fokus an das Fenster. Visual Studio verfügt über zwei Indikatoren für die Aktivierung: eine für Dokumentfenster und eine für die Toolfenster.  

 Bei Dokumentfenstern wird das aktive Fenster durch ein Tabstoppzeichen der Dokument-Fenster im Vordergrund stammen und die Hintergrundfarbe angezeigt:  

 ![Aktive registerkartenauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-01-activetab.png "0713-01_ActiveTab")  

 **Aktive registerkartenauswahl**  

 Für die Toolfenster wird das aktive Fenster durch eine Änderung in der Farbe der Bereich der Titelleiste des Toolfensters angezeigt:  

 ![Aktive toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-02-activetoolwindow.png "0713-02_ActiveToolWindow")  

 **Zeigt die primäre Auswahl eines Knotens für aktives Toolfenster**  

 ![Inaktive toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-03-inactivetoolwindow.png "0713-03_InactiveToolWindow")  

 **Inaktive Toolfenster latente Auswahl des Knotens anzeigen**  

 Sobald ein Fenster aktiv ist, wird der Schwerpunkt entsprechend der Auswahlmodelle beschrieben, die in diesem Abschnitt der Richtlinien angezeigt.  

#### <a name="context"></a>Kontext  
 Visual Studio wurde entwickelt, eine starke Konzept des Kontexts, beibehalten werden sollen, verfolgen Sie den Fortschritt der, in denen der Benutzer arbeitet. Nur ein Fenster ist aktiv, ob es ein Tool- oder Dokumentfenster-Fenster ist. Das oberste Dokumentfenster behält jedoch immer eine latente Auswahl. Obwohl der Schwerpunkt in einem Toolfenster sein könnte, zeigt das Dokumentfenster, das zuletzt aktiv war eine Auswahl aus und sogar in einen inaktiven Status. Dies erfolgt, wenn Sie den Kontext des Benutzers im Dokument beibehalten möchten, die sie bearbeitet haben, zeigt sie, dass Visual Studio ihren Zustand beibehalten wurde, sodass können nahtlos zwischen Toolfenstern und Dokumentfenstern verschoben und zurückgeben.  

### <a name="text-selection"></a>Textauswahl  
 Visual Studio-Editoren, die ausschließlich Text, z. B. die integrierte Text-Editor verwenden das gleiche Modell des Text-Auswahl und Darstellung beschrieben die [Maus- und Zeiger](https://msdn.microsoft.com/library/dn742466.aspx) auf der Seite das Windows User Experience Interaction Guidelines auf MSDN. Der Eingabefokus im Text-Editor wird durch einen senkrechten Strich wird aufgerufen, die Einfügemarke angezeigt. Die Einfügemarke befindet es sich um ein einzelnes Pixel thick und farbige die Umkehrung des was dahinter angezeigt wird. Es blinkt, entsprechend der Rate, die festlegen, indem die **Cursorblinkrate** festlegen in der **Geschwindigkeit** Registerkarte die **Tastatur** Applet in der Systemsteuerung.  

#### <a name="contiguous-and-disjoint-selection"></a>Aneinandergrenzenden und nicht zusammenhängenden Auswahl  
 Auswahl im Text-Editor ist fortlaufend. Nicht zusammenhängende Auswahl sind nicht zulässig, aber im Objekt-Editor behandelt werden sollte. Wenn der Benutzer den Mauszeiger über einen Textbereich ist, ändert sich der Cursor in eine Maus. Einem einzigen Mausklick platziert die Einfügemarke im Texteditor am Speicherort auf. Die Maustaste gedrückt, eine Markierung für die Auswahl beginnt und die Maustaste loslassen, endet die Markierung der.  

#### <a name="region-selection-box-selection"></a>Die Auswahl der Region (Auswahl)  
 Visual Studio unterstützt die Auswahl der Region in den Text-Editor, und dies wird als bezeichnet, Feldauswahl. Auswahl kann der Benutzer einen Textbereich auswählen, die nicht den regulären Textstream folgt. Wie bei der Auswahl der standard-Text, muss die Auswahl zusammenhängend sein. Auswahl wird initiiert, indem Sie die Alt-Taste gedrückt halten und ziehen mit der Maus. Auswahl kann auch initiiert werden, indem Sie die ALT-Taste und die UMSCHALTTASTE gedrückt halten und mithilfe der Pfeiltasten an, dass die Region der Auswahl. Auswahl verwendet die normale Auswahl Hervorhebung und zeigt den Einfügepunkt blinkt, am Ende den Auswahlbereich.  

 ![Regionale &#40;Feld&#41; Auswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-04-boxselection.png "0713-04_BoxSelection")  

 **Die Auswahl der Region (Feld) in Visual Studio**  

#### <a name="text-selection-appearance"></a>Textdarstellung-Auswahl  
 Die für aktive und inaktive Auswahl im Editor verwendeten Farben können angepasst werden. Um die visuelle Darstellung des Editors anzupassen, man sich ein Benutzer auf **Tools > Optionen**, und suchen Sie unter **Umgebung > Schriftarten und Farben > Text-Editor**.  

### <a name="graphical-selection"></a>Grafische Auswahl  

#### <a name="interaction"></a>Interaktion  
 Auswahl von grafischen Objekten kann komplex sein und hängt von einer Reihe von Faktoren:  

-   **Primäre Auswahl-Modell des Editors.** Editoren, die grafische Objekte enthalten können auch zum Bearbeiten von Text oder Raster verwendet werden. Der Editor kann z. B. einer textbasierten Editor sein, der auch die Platzierung des grafischen Objekte, z. B. den Visual Studio-XAML-Designer unterstützt. Unterstützung mehrerer Objekttypen kann beeinflussen wie der Benutzer Gruppen setzt sich aus verschiedenen Typen von Objekten auswählt.  

-   **Unterstützung für Primär- und sekundärauswahl Zustände.** Ein-Editor kann es sich um Primär- und sekundärauswahl bereitstellen, die Status miteinander, und so weiter, auf die Größe geändert, damit Objekte bearbeitet werden können, gemeinsamen, ausgerichtet.  

-   **Unterstützung für die direkte Bearbeitung.** Editoren können auch den Inhalt ihrer grafische Objekte bearbeitet werden. Beispielsweise könnte eine rechteckige Form auch Text innerhalb enthalten, die vom Benutzer geändert werden können. Darüber hinaus kann Text zentriert oder im Blocksatz ausgerichtet werden. Direkte Bearbeitung eine detailliertere Ebene der Benutzerinteraktion umfasst und erfordert daher einen entsprechenden Satz von optische Hinweise zur Darstellung von Zustandsinformationen für den Benutzer.  

#### <a name="mouse-interaction"></a>Mausinteraktion  

|Eingabe|Ergebnis|  
|-----------|------------|  
|Klicken Sie auf ein nicht ausgewähltes Objekt|Wählt das Objekt, und eine gestrichelte Linie "und" Auswahlpunkte, angezeigt werden, wenn das Objekt geändert werden.|  
|Klicken Sie auf ein ausgewähltes Objekt|Aktiviert die direkte Bearbeitung, wenn das Objekt unterstützt. Klicken außerhalb des Objekts deaktiviert den Bearbeitungsmodus des direktes.|  
|Doppelklicken Sie auf ein Objekt|Den Code hinter dem Objekt zur Bearbeitung geöffnet, und fügen Sie einen Standard-Ereignishandler kann, bei Bedarf.|  
|Zeigen Sie auf ein Objekt|Ändert den Mauszeiger auf den Cursor verschieben. Darstellung des Objekts, z. B. die Brillanz oder die Farbe, kann sich ändern.|  
|Zeigen Sie auf ein Auswahlkästchen|Ändert den Mauszeiger auf den Größenänderungscursor. Für Objekte, die die Rotation zu unterstützen, können einige Auswahlpunkte des Zeigers auf einen Cursor drehen ändern, wenn der Zeiger in Bezug auf das Auswahlkästchen unterschiedlich (z. B. Abstand verschoben) positioniert ist.|  
|Ziehen Sie|Auch wenn das Objekt nicht bereits ausgewählt ist, ändert sich der Zeiger auf den Cursor verschieben, und verschiebt das Objekt.|  
|Editor für den Fokus verliert.|Definieren des direkten Bearbeitungsmodus, zwar das Objekt besetzt, Inhalt und Darstellung, die während der letzten Vorgangsauswahl/Zustand wurde deaktiviert.|  
|Objektauswahl|Durch einen Rahmen, gepunktete Linie oder anderen visuellen unterschiedliche Behandlung, markieren Sie die Begrenzung des Objekts angegeben.|  
|Ändern der Größe eines ausgewählten Objekts|Durch Auswahl von Handles angegeben.<br /><br /> Ein Objekt in der Größe veränderbaren hat acht Handles, die jede Richtung, in dem dann geändert werden kann, die darstellt. Weniger Handles können verwendet werden, wenn das Objekt nur in bestimmten Richtungen angepasst werden kann. Wenn der Benutzer die Größe eines Objekts auf, in denen acht Handles nicht interaktiv sein würde, können vier Handles verwendet werden. Handle Größen sollten gebunden werden, auf die Fenster Rahmen und Edge-Metriken mit der **GetSystemMetrics** Größe proportional die Bildschirmauflösung-API-Funktion.<br /><br /> ![Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-05-resizehandles.png "0713-05_ResizeHandles")|  
|Drehen Sie ein ausgewähltes Objekt|![Handles zum Drehen](../../extensibility/ux-guidelines/media/0713-06-rotate.png "0713-06_Rotate")|  

#### <a name="keyboard-interaction"></a>Tastaturinteraktion  

|Eingabe|Ergebnis|  
|-----------|------------|  
|Registerkarte|Verschiebt den Fokusindikator für die logische Reihenfolge der Objekte im Editor. Dies ist möglicherweise links-nach-rechts oder oben-nach-unten je **TabIndex** (oder Äquivalent)-Eigenschaftswert, Reihenfolge der objekterstellung und den Zweck des Editors. Umschalt + Tab, kehrt die Richtung des Indikators, den Fokus.|  
|LEERTASTE|Schwenkmodus aktiviert, während die Tastatureingabe beibehalten wird. Zusätzliche Mauseingabe ist erforderlich, um die Position der Ansicht zu schwenken.|  
|STRG+LEERTASTE|Zoommodus aktiviert, während die Tastatureingabe beibehalten wird. Zusätzliche Mauseingabe ist erforderlich, um zu erhöhen und verringern den Zoomfaktor.|  
|Strg + Alt + Minuszeichen ()|Wird den Zoomfaktor, um eine Ebene verringert.|  
|Strg + Alt + Pluszeichen|Wird den Zoomfaktor, um eine Ebene erhöht.|  
|UMSCHALT oder STRG|Fügt das Objekt der Auswahlgruppe hinzu. STRG können Sie Objekte einzeln aus der Auswahlgruppe zu entfernen.|  
|EINGABETASTE|Führt den Standardbefehl für das Objekt (in der Regel öffnen oder zu bearbeiten).|  
|F2|Aktiviert die direkte Bearbeitung für das Objekt.|  
|Pfeiltasten|Verschiebt die ausgewählten Objekte in der die Richtung der Pfeiltaste gedrückt ist, in kleinen Schritten (z. B. 1 Pixel zu einem Zeitpunkt)|  
|STRG + Pfeiltasten|Verschiebt die ausgewählten Objekte in der die Richtung der Pfeiltaste gedrückt ist, in größeren Schritten (z. B. 10 Pixel zu einem Zeitpunkt)|  
|UMSCHALT + nach-Schlüssel|Ändert die Größe der ausgewählten Objekte in der jeweiligen Richtung in kleinen Schritten (z. B. 1 Pixel zu einem Zeitpunkt)|  
|STRG + UMSCHALT + Pfeiltasten|Ändert die Größe der ausgewählten Objekte in der jeweiligen Richtung, in größeren Schritten (z. B. 10 Pixel zu einem Zeitpunkt)|  

 Wenn Benutzer über Sicherheitskontrollen, bearbeiten, kann es für Objekte, auf die automatische Größenänderung mit Benutzereingaben sinnvoll. Z. B. wenn der Benutzer ein Label-Steuerelement bearbeitet, soll klicken Sie dann die Bezeichnung vergrößert werden, die den Text anzuzeigen, den der Benutzer gerade eingegeben. Wenn dies nicht erfolgt, muss der Benutzer manuell die Größe des Steuerelements nach dem Bearbeiten von Text. Wenn der Benutzer viele Steuerelemente verfügt, wird dies einen routinemäßigen und Ausfallzeitraum Aufgabe.  

#### <a name="graphical-containers"></a>Grafische Container  
 In einigen Fällen bieten grafische Editoren Container für andere grafische Objekte, z. B. Windows Forms-Bereichssteuerelement oder das Steuerelement Rasterlayout im HTML-Designer. Wenn Ihr Editor Container für andere Grafikobjekte bereitstellt, sollte das folgende Auswahlmodell für den Container nur (Objekte innerhalb der Container gehen Sie folgendermaßen vor, dem Standardmodell wie oben beschrieben) verwendet werden:  

|Eingabe|Ergebnis|  
|-----------|------------|  
|Klicken Sie einfaches für den container|Wählt das Container-Objekt ohne eine Auswahl direkt eines der enthaltenen Objekte. Container kann verschoben und/oder mit standard-Maus und Tastatur (wie oben beschrieben) geändert werden. Enthaltenen Objekte werden in Bezug auf den Container verschoben, aber enthaltenen Objekte werden nicht geändert werden, es sei denn, sie auch direkt ausgewählt werden.|  
|Zeigen Sie auf die Begrenzung der Region des Containers|Aktiviert die Maus in den verschieben-Cursor, der angibt, dass der Container verschoben werden kann.|  
|Ziehen Sie die Grenze Region des Containers|Ändert sich den Mauszeiger auf den Cursor verschieben, und verschiebt den Container (und die enthaltenen Objekte in). Der Container kann nicht verschoben werden, ohne zuerst mit einem einzigen Mausklick ausgewählt werden.|  
|Klicken Sie einfaches auf ein Objekt innerhalb des Containers|Hebt die Auswahl des Containers (sofern aktiviert), und wird nur auf das geklickt wurde Objekt ausgewählt.|  
|UMSCHALT + klicken oder STRG + Klicken Sie auf einen darin enthaltenen Objekte und/oder container|Eine Auswahl oder die Auswahlgruppe hinzugefügt das Objekt auf den geklickt wurde. Wenn das Objekt auf den geklickt wurde bereits ein Mitglied der Auswahlgruppe ist, wird er aus der Auswahlgruppe entfernt.|  

 Die enthaltenen Objekte sollten das grundlegende Auswahlmodell entsprechen, wie im vorherigen Abschnitt beschrieben. Von Nutzbarkeitstests des Windows Forms-Designers, erwartet Benutzer nahtlosen Zugriff auf die enthaltenen Objekte ohne dazwischenliegende Schritte (festgelegt durch die Containment-Objekt).  

#### <a name="disjoint-and-region-selections"></a>Zusammenhanglose und Region  
 Objekt-Editoren sollte nicht zusammenhängende Auswahlbereiche unterstützt. Beachten Sie, dass die folgende Grafik nicht die Darstellung des Steuerelements für Visual Studio angezeigt wird. Finden Sie unter [Darstellung der Grafischen Objekts-Auswahl](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) detaillierte visual Angaben.  

 ![Zusammenhanglose und Region Selektoren](../../extensibility/ux-guidelines/media/0713-07-disjointregionselectors.png "0713-07_DisjointRegionSelectors")  

 **Zusammenhängende Auswahl**  

 Außerdem sollten die grafische Editoren Auswahl der Region mit einem Indikator der Marquee-Type-Auswahl bereitstellen. Wenn der grafische Editor andere Objekttypen (z. B. Text) unterstützt, klicken Sie dann Auswahl der Region möglich, je nach den Einschränkungen dieser anderen Typen von Objekt möglicherweise nicht.  

 ![Laufschriftauswahl](../../extensibility/ux-guidelines/media/0713-08-marqueeselection.png "0713-08_MarqueeSelection")  

 **Laufschriftauswahl**  

#### <a name="primary-and-secondary-selections"></a>Primäre und sekundäre Auswahl  
 Einige Editoren grafischen Objekten erlauben Sie dem Benutzer zu bearbeiten oder Ausrichten von Objekten in Gruppen. In diesem Fall muss das Konzept der primären und sekundären Auswahl eingeführt werden. Die primäre Auswahl handelt es sich um das Objekt, das auf dem aller anderen Objekte für das Gruppieren von Operationen reagieren. Das Objekt, das der Benutzer zunächst auswählt, wird das primäre Steuerelement aus, und nachfolgende Auswahl werden die sekundären Optionen. Die primäre Auswahl hat eine unterschiedliche visual Behandlung von der sekundären Auswahl getroffen haben, um anzugeben, welches Objekt die primäre ist:  

 ![Primär- und sekundärauswahl](../../extensibility/ux-guidelines/media/0713-09-primarysecondary.png "0713-09_PrimarySecondary")  

 **Primäre Auswahl mit zwei sekundäre Auswahl**  

####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Darstellung der grafischen Objekts-Auswahl  
 Ziehpunkte sind Quadrate, die in einem rechteckmuster an, um das umgebende Feld des Objekts gezeichnet wird. Im Diagramm unten sind Beispiele für die verschiedenen Status, die mit Handle größenanpassung und direkte Bearbeitung Darstellung ein grafisches Objekts haben kann. Die Größe des Handles gebunden werden sollte, Fensterrahmen und Edge Metriken verwenden das **GetSystemMetrics** API.  


|          Zustand          |  Darstellung   |                                                                  Visuelle details                                                                  |
|-------------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
|     **Nicht ausgewählt**      |    Standard    |                 ![Schaltfläche Standardstatus](../../extensibility/ux-guidelines/media/0713-10-defaultstate.png "0713-10_DefaultState")                 |
|  **Primäre Auswahl**  |   In der Größe veränderbaren   |       ![Primäre Auswahl mit Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-11-primaryresize.png "0713-11_PrimaryResize")        |
|  **Primäre Auswahl**  | Nicht geändert werden kann |    ![Primäre Auswahl ohne Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-13-primarynoresize.png "0713-13_PrimaryNoResize")    |
|  **Primäre Auswahl**  |    Gesperrt     |              ![Primäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-15-primarylocked.png "0713-15_PrimaryLocked")              |
| **Sekundäre Auswahl** |   In der Größe veränderbaren   |    ![Sekundäre Auswahl mit Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-17-secondaryresize.png "0713-17_SecondaryResize")     |
| **Sekundäre Auswahl** | Nicht geändert werden kann | ![Sekundäre Auswahl ohne Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-19-secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Sekundäre Auswahl** |    Gesperrt     |           ![Sekundäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-21-secondarylocked.png "0713-21_SecondaryLocked")           |
|      **Aktive Benutzeroberfläche**      |    Standard    |                       ![Benutzeroberfläche im aktiven Status](../../extensibility/ux-guidelines/media/0713-23-uiactive.png "0713-23_UIActive")                        |

### <a name="view-selection-models"></a>Die Auswahlmodelle anzeigen  

#### <a name="tree-view"></a>Strukturansicht  
 Mit einer einfachen Hervorhebung wird die Auswahl in einer Strukturansicht angezeigt. Wenn der Benutzer auf einen Knotennamen oder ein Symbol "Knoten" klickt, wird der Knoten ausgewählt. Die dreieckigen Symbole auf der linken Seite des Knotens zu erweitern oder verkleinern Sie die Strukturansicht-Steuerelement, aber wirken sich nicht auf die Auswahl des Benutzers, mit einer Ausnahme: bei einen übergeordneten Knoten reduzieren, wenn die Auswahl auf ein untergeordnetes Element dieses Knotens ist, die Auswahl verschoben wird, das dem übergeordneten.  

 ![Typische Strukturansicht in Visual Studio](../../extensibility/ux-guidelines/media/0713-25-treeview.png "0713-25_TreeView")  

 **Typische Strukturansicht in Visual Studio**  

 Strukturansichten unterstützen aneinandergrenzenden und nicht zusammenhängenden Auswahl, sogar über mehrere Ebenen in der Struktur. Zusammenhängend sein oder zusammenhanglose Mehrfachauswahl sichtbaren Strukturknoten ausgeführt werden müssen. Wenn ein Knoten reduziert ist, die nicht zusammenhängende Auswahl geht verloren, und der Knoten, der reduziert wurde, erhält die Auswahl. Auf diese Weise kann der Benutzer die Knoten anzeigen, die von einem Vorgang betroffen sind. Wenn der Knoten reduziert werden, wird es unklar welche Knoten betroffen sein könnten.  

 Wenn ein übergeordneter Knoten aktiviert ist, sollten der Vorgang auf das übergeordnete Element anwenden, aber es gibt möglicherweise Fälle, wo dies sinnvoll für einen Vorgang aus, um auf das übergeordnete Element und alle seine untergeordneten Elemente anzuwenden ist. Geben Sie in diesem Fall weitere Benutzeroberfläche während des Vorgangs, z. B. ein Kontrollkästchen oder ein Dialogfeld zur Bestätigung, die Option "gelten für alle untergeordneten Elemente" für dem Benutzer explizit zu machen.  

##### <a name="renaming"></a>Umbenennen  
 Wenn der Knoten in der Struktur umbenennen unterstützt, sollte umbenennen direktes erfolgen. Der Vorgang des direktes sollte der Standard für alle Struktursteuerelemente in Visual Studio. Geben Sie einen Befehl Umbenennen, der den Bearbeitungsmodus des direktes, sofort mit die Textauswahl für den gesamten Namen des Knotens, möchten Sie die Benutzereingaben akzeptiert aktiviert. Wenn der Knoten eine Datei darstellt, sollte der Dateinamen die Erweiterung enthalten. Die Markierung der sollte nur den Textteil der Namen der Datei und nicht die Erweiterung enthalten.  

|Eingabe|Ergebnis|  
|-----------|------------|  
|Eingabetaste|Führt einen Commit für die Umbenennung|  
|ESC-Taste|Bricht den Umbenennungsvorgang|  
|Klicken außerhalb des Bearbeitungsbereichs des direktes|Führt einen Commit für die Umbenennung|  
|Rückgängig|Geben Sie einfach rückgängig, um die Umbenennung abzubrechen.|  

#### <a name="selection-within-lists-and-grid-controls"></a>Auswahl in Listen und Rastersteuerelemente  
 Das Hauptkonzept im Listenauswahl ist, dass es basiert auf der Zeile, was bedeutet, dass bei einer die gesamte Zeile Auswahl wird ausgewählt ist, als eine Einheit. Im Gegensatz dazu können Raster bestimmte Zellen ausgewählt werden, ohne Auswirkungen auf andere Aspekte der Zeile. Raster können auch eine Hierarchie von geschachtelten Zeilen (z. B. in einem des Treegrid-Standardsteuerelements) enthalten, mit denen die gesamte Zweige der Hierarchie ausgewählt und durch die Interaktion mit die übergeordneten Zeilen deaktiviert werden. Auswahl in Listen wird durch eine einfache Hervorhebungsfarbe für die gesamte Zeile der Daten angezeigt. Fokus wird angezeigt, von einem gepunkteten einem Pixel-Rahmen um das aktuelle bearbeitbare Zeile oder Zelle (Zeile, wenn alle Zellen schreibgeschützt sind).  

> [!NOTE]
>  **Fokus** und **Auswahl** sind unterschiedliche Konzepte. *Fokus* ist ein Hinweis auf die Benutzeroberfläche Element als Ziel verwendet wird um die Eingaben, die nicht explizit an einem anderen Objekt gerichtet erhalten, während er sich *Auswahl* bezieht sich auf den Status eines Objekts Aufnahme in einen Satz von Objekten auf dem nachfolgenden Vorgänge stattfinden können.  

 Auswahl der in Listen möglicherweise zusammenhängenden, zusammenhanglos, oder die Region. Wenn mehrere Elemente ausgewählt sind, zugelassen, zusammenhängende und nicht zusammenhängenden Auswahl sollte immer unterstützt werden, und bei der Unterstützung für die Auswahl der Region (Feld) ist optional. Auswahl der Region werden durch Ziehen in den Leerraum des Texts Liste initiiert.  


| Object | Auswahl  |
|--------|------------|
|  Liste  | Zusammenhängende |
|  Liste  |  Zusammenhanglose  |
|  Liste  |   Region   |

 Klicken einmal auf eine Liste zur Auswahl der Zeile, an der geklickt wurde. Wenn der Benutzer geschieht in einer Listenzelle klicken, die direkte Bearbeitung unterstützt, wird die Zelle auch sofort für direktes Editieren aktiviert. Andernfalls wird die gesamte Zeile sofort aktiviert ist und eine Hervorhebung zeigt.  

 Ziehen in der Liste Text ist eines von drei Dingen:  

-   Durch die Auswahl einer Region initiiert, wenn die Liste wird unterstützt und die Maus nach unten in Leerzeichen  

-   Initiiert einen Drag & Drop-Vorgang aus, wenn die Listenzelle oder Zeile unterstützt eine Quelle des Ziehvorgangs werden  

-   Markiert die aktuelle Zeile  

##### <a name="in-place-editing"></a>Direktes Bearbeiten  
 Wenn direkte Bearbeitung zulässig ist, es gibt zwei grundlegende Modelle: einfache bearbeiten-Steuerelement und der Eigenschaft Auswahl. Mit einem einfachen Bearbeitungssteuerelement wird der Inhalt, hervorgehoben und bereit für Benutzereingaben als direktes Editieren aktiviert ist. Bei eine Eigenschaftenauswahl implementiert wird, wird die Schaltfläche, die die Eigenschaftenauswahl ruft angezeigt, sobald direkten Bearbeitungsmodus ist aktiviert, und die aktuelle Auswahl nicht hervorgehoben ist. Die Schaltfläche "Auswahl" sollte in der Zelle rechtsbündig ausgerichtet sein. Direkte Bearbeitung Beispiele finden Sie in der **Fenster "Eigenschaften"** und **Aufgabenliste** in Visual Studio.  

##### <a name="keyboard-support"></a>Die Bildschirmtastatur-Unterstützung  
 Die Bildschirmtastatur-Unterstützung für die Auswahl in Listen und Raster folgt die standard-Windows-Konventionen:  

-   Jede Zeile/Zelle auswählen, wie sich der Fokus verschoben wird die Liste navigieren die Pfeiltasten.  

-   UMSCHALT + nach-führt eine zusammenhängende Auswahl in die Richtung der Pfeiltasten an.  

-   STRG + LEERTASTE schaltet gefolgt sind, zwischen hinzufügen und Entfernen von Elementen aus der Auswahl, und erstellen eine nicht zusammenhängende Auswahl-Taste.  

-   Raster, die geschachtelte Hierarchien enthalten, rechts-Taste wird eine übergeordnete Zeile erweitert und links-Taste reduziert einen.  

-   Die Tab-Taste verschiebt den Fokus zwischen den Zellen in der aktuellen Zeile, wenn die Zellen bearbeitet werden.  

-   Die EINGABETASTE führt den Standardbefehl für das Element in der Liste (häufig **öffnen**).  

-   Die F2-Taste wird die direkte Bearbeitung für die derzeit ausgewählte Zelle aktiviert.  

##  <a name="BKMK_PersistenceAndSavingSettings"></a> Persistenz und Einstellungen werden gespeichert.  

### <a name="overview"></a>Übersicht  
 Obwohl jede Softwarekomponente in Visual Studio in der Regel für einen eigenen Status und die Persistenz zuständig ist, speichert Visual Studio-Einstellungen in einigen Fällen wie z. B. mit Fenstergrößen und Positionen. In der folgenden Tabelle ist eine Kombination von Einstellungen, die automatisch gespeichert und Einstellungen, die einen expliziten Benutzer oder programmiert auszuführende Aktion.  

|Object|Was Sie speichern|Beim Speichern|Zum Speichern|  
|------------|------------------|------------------|-------------------|  
|Auswählbare Objekt (z. B. eine Linie von Code)|Einen Haltepunkt in einer Zeile des Codes<br /><br /> Eine Benutzer-Verknüpfung, die die Zeile des Codes zugeordnet|Wenn das Projekt gespeichert wird|Die **Benutzeroptionen (SUO)** Datei für das Projekt|  
|Dialogfeld|Der Speicherort des Dialogfelds, wenn es verschoben wurde, hatte<br /><br /> Die Ansicht, die der Benutzer, die in das Dialogfeld "zuletzt verwendet|Wenn das Dialogfeld wird geschlossen<br /><br /> Wenn die Visual Studio-Sitzung beendet wird|Im Arbeitsspeicher<br /><br /> Registrierung in **HKEY_Current_User**|  
|Fenster|Die Größe und Position des Fensters|Wenn das Fenster wird geschlossen<br /><br /> Wenn der Visual Studio-Modus geändert wurde<br /><br /> Wenn die Visual Studio-Sitzung beendet wird|Die **Benutzeroptionen (SUO)** Datei für das Projekt<br /><br /> Benutzerdefinierte Optionsdatei für Fenster-Einstellungen|  
|Dokument|Die aktuelle Auswahl im Dokument<br /><br /> Die Ansicht des Dokuments<br /><br /> Die letzte mehrfach, die der Benutzer besucht hat|Wenn das Dokument gespeichert wird|Die **Benutzeroptionen (SUO)** Datei für das Projekt|  
|Projekt|Verweise auf Dateien<br /><br /> Verweise auf Verzeichnisse auf dem Datenträger<br /><br /> Verweise auf andere software<br /><br /> Komponenten<br /><br /> Statusinformationen über das Projekt selbst|Wenn das Projekt gespeichert wird|Die Projektdatei|  
|Lösung|Verweise auf Projekte<br /><br /> Verweise auf Dateien|Wenn das Projekt oder Projektmappe gespeichert wird|Die **Projektmappendatei (.sln)** Datei|  
|Einstellungen im **Tools > Optionen**|Tastatur-Anpassungen<br /><br /> Symbolleiste-Anpassungen<br /><br /> Farbschemata|Wenn die **Tools > Optionen** Dialogfeld geschlossen wird.<br /><br /> Wenn die Visual Studio-Sitzung beendet wird|Registrierung in **HKEY_Current_User**|  

 Was der Benutzer Aktionen und, wenn sie ihn ausführen bestimmt, ob eine Einstellung im Arbeitsspeicher (während der Sitzung), auf dem Datenträger gespeichert werden, (sitzungsübergreifend als registrierungseinstellung), gespeichert wird, wird als Teil der Projekt- oder Projektmappendatei selbst als Teil des der **Lösung Optionen (SUO)** aus, oder wie eine benutzerdefinierte, die nur diese Softwarekomponente Einstellungsdatei kennt. Der Tabelle oben werden mehrere Ereignisse, die an denen Einstellungen gespeichert werden können. Es gibt jedoch auch in anderen Fällen, in denen Sie Zustand speichern möchten:  

-   Wenn der Benutzer die Position in einem Dialogfeld oder Fenster ändert  

-   Wenn der Benutzer den Fokus in ein anderes Fenster übertragen  

-   Wenn der Benutzer vom Entwurf bis zur den Debugmodus wechselt.  

-   Wenn Sie ihr Konto meldet den Benutzer  

-   Wenn der Computer in den Ruhezustand wechselt, oder wird heruntergefahren  

-   Wenn die Computer/Festplatte ist, werden erneut formatiert und erneut einrichten  

### <a name="window-configurations"></a>Fensterkonfigurationen  
 Eine Fensterkonfiguration ist die grundlegende Darstellung der Entwicklungsumgebung – es ist ein Schema aus der Liste der Toolfenster vorhanden und die Möglichkeit, die in der sie angeordnet werden. Für Windows, die von der IDE (IDE-Windows) verwaltet wird wird pro Benutzer und Layoutinformationen beibehalten, damit bei einer starten die IDE, das Fensterlayout identisch angezeigt wird, wenn sie zum letzten Visual Studio beendet. Die Status und die Position des IDE-Fenster wird in einer benutzerdefinierten Optionen, die Datei im XML-Format beibehalten. Toolfenster, die von Paketen, die in der IDE geladen erstellt werden behalten ihren Zustand in der Registrierung können und möglicherweise nicht pro Benutzer.  

#### <a name="profile-specific-layouts"></a>Profil-spezifischen layouts  
 Jedes Profil enthält die Tool-Fensterlayouts, auf eine Weise vertraut sind, bestimmte Rollen organisiert (Visual C++-Entwickler erwarten die **Projektmappen-Explorer** auf der linken Seite der IDE, während c#-Entwickler erwarten, dass die findenSieunter **Projektmappen-Explorer** auf der rechten Seite). Profil-spezifische Fensterlayouts werden geladen, nachdem der Benutzer ein Profil auf Start wählt. Autor eines Pakets sollten das Fensterlayout, das am besten zu ihren Kunden zu ermitteln und zu wissen, dass Änderungen, die der Benutzer die angegebene Fensterkonfiguration stellt dann beibehalten werden.  

##  <a name="BKMK_TouchInput"></a> Touch-Punkts  
 Benutzer werden zunehmend Produkte für die Entwicklung von Microsoft für Touch-Geräten verwenden. Es gibt jedoch Hindernissen, die Entwicklungstools für Touch-Geräten verwenden erschweren. Benutzer erwarten, dass unsere Produkte aus, um eine zuverlässige und präzise Touch-Erlebnis zu bieten. Die Absicht dieser Richtlinien besteht darin, Entscheidungen über die Touch-Funktionen zu integrieren und eine konsistente Touch-Funktion in Visual Studio und verwandte Produkte empfehlen.  

### <a name="levels-of-experience"></a>Ebenen der Benutzeroberfläche  
 Die folgenden Ebenen Erfahrung dienen als Anleitung können Teams entscheiden, abhängig von den gewünschten Grad der Investition Interesse an der Touch mit Touch-Funktionen zu bieten.  

-   Die **Grundkenntnisse beim** ist für Teams, die möchten, geben Sie Funktionen touch, daher gibt es keine Warteschlange für unzustellbare Nachrichten enden während ihrer Arbeit.  

-   Die **optimierte Erfahrung** ist für Teams, die die meisten gebräuchlicher-Funktionen (z. B. die in der Regel in der Internet-Browser-Anwendungen verfügbar) bereitstellen möchten.  

-   Die **erhöhte benutzerfreundlichkeit** ist für Teams, die solche Funktionen hinzufügen möchten, die als anwendungsstiftbewegungen oder andere optionale Funktionen, die ihrer Anwendung vornehmen können Touch hat Priorität angezeigter.  

||Grundkenntnisse beim|Optimiert und|Erhöhte benutzerfreundlichkeit|  
|-|----------------------|--------------------------|-------------------------|  
|Ermöglicht es Benutzern...|Korrigieren von Code und die Lösung/Projektebene ohne Ende der Warteschlange für unzustellbare Nachrichten lesen|Aufgaben der Wartung, Überarbeitungen und navigation|Arbeiten Sie in eine konsistente, intuitive und flüssige Erfahrung, mit Zuversicht|  
|Editor|Verschiebung mit den Fingern und Auswahl<br /><br /> Bildlaufleiste Touch zu springen, und drücken + ziehen|Verkleinern Vergrößern<br /><br /> Schnelles Scrollen<br /><br /> Auswahl<br /><br /> Die einfache Verwendung des Kontextmenüs||  
|Top-Toolfenster|Liste Schwenken<br /><br /> Elementauswahl<br /><br /> Bildlaufleiste Touch zu springen, und drücken + ziehen|Einfache Element durchführen eines Bildlaufs und Auswahl||  
|Windowing||Größe der Fenster<br /><br /> Schnellzugriff||  
|Dokumentursprung||Einfache Navigation zwischen geöffneten Dateien||  
|Gesten||Sicherstellen Sie, dass allgemeine Gesten in der IDE zu arbeiten.|Aktion-basierten Aktionen<br /><br /> Unterstützung von Drag & Drop und Designern|  
|Andere Überlegungen|||Benutzerdefinierte Bildschirmtastatur verwenden|  

#### <a name="gestures"></a>Gesten  
 Bewegungen bieten Benutzern eine Verknüpfung mit Befehlen, die andernfalls möglicherweise eine kompliziertere Interaktion erfordern. Finden Sie in der Windows-Richtlinien unter [gebräuchlicher Gesten für Desktop-Anwendungen](http://msdn.microsoft.com/library/windows/desktop/dd940543\(v=vs.85\).aspx), und befolgen Sie diese Anleitung für die meisten Gesten, einschließlich einfache Gesten wie Schwenken und zoomen.

