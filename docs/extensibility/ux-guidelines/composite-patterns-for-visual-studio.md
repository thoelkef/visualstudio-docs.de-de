---
title: "Zusammengesetzte Muster für Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6ce0fccf3a957edfdf732ce3ea462bef26c5a0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="composite-patterns-for-visual-studio"></a>Zusammengesetzte Muster für Visual Studio
Zusammengesetzte Muster kombinieren Interaktion und Entwurf Elemente in unterschiedlichen Konfigurationen. Die wichtigsten zusammengesetzte Muster in Visual Studio im Hinblick auf Konsistenz gehören:  
  
-   [Datenvisualisierung](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Auf Objekt Benutzeroberfläche und einsehen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Auswahlmodelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistenz und Speichern der Einstellungen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Fingereingabe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="BKMK_DataVisualization"></a>Datenvisualisierung  
  
### <a name="overview"></a>Übersicht  
 Diagramme sind eine visuelle Darstellung zum Aggregieren und Daten anzeigen, um die entscheidungsfindung zu verbessern. Sie können Benutzer mit einer Vielzahl von Daten, sondern nur wenig bedeutet finden Sie in was Aufmerksamkeit erhalten soll und was eine Aktion möglicherweise konfrontiert.  
  
 Der Benutzer wird aus einem Diagramm profitieren, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Hilft das Diagramm Benutzer Aufgaben zu identifizieren, denen sie nutzen können?  
  
-   Wird das Diagramm der Benutzer, der potenziellen Änderungen des Konsequenzen zu prognostizieren aktiviert?  
  
-   Hilft das Diagramm Benutzer Erkennung von Trends und Muster identifizieren?  
  
-   Wird das Diagramm Benutzern bessere Entscheidungen treffen erlauben?  
  
-   Wird das Diagramm nützlich, die Benutzer im angegebenen Kontext haben möglicherweise eine bestimmte Frage zu beantworten?  
  
#### <a name="general-rules-for-charts"></a>Allgemeine Regeln für Diagramme  
  
-   Deutlich bezeichnungsdaten. Abbildungen ohne Erläuterung sind nur Bilder ziemlich.  
  
-   Starten Sie die Achsen auf 0 (null), um neigen Proportionen zu vermeiden. Größe für Länge und Leiste sind wichtige visuelle Hinweise für das Verständnis der Beziehungen zwischen Datenpunkten an.  
  
-   Erstellen Sie Diagramme, die nicht infografiken. Infografiken stehen künstlerische Darstellung der Daten und deren Hauptziel ist visual Storytelling. Diagramme können (und sollten) werden Sie visuell ansprechend, aber lassen Sie die Daten für sich selbst sprechen.  
  
-   Vermeiden Sie Skeumorphism, bildliche Balkendiagramme Kontrast Hashmarks und andere INFOGRAFIK berührt.  
  
-   Verwenden Sie 3D-Effekte nicht als dekorativen Element aus. Verwenden sie nur, wenn sie tatsächlich integraler Bestandteil des Benutzers formationen Lage.  
  
-   Verwenden Sie mehrere Linien und Füllungen, wenn mehr als zwei Farben diese Art von Diagramm schwierig vornehmen können zu lesen und richtig interpretieren.  
  
-   Verwenden Sie ein Diagramm (oder eine beliebige Abbildung) nicht als einziges Mittel der Verständnis ein Konzept oder mit Daten interagieren. Dies stellt Probleme für Benutzer mit eingeschränkter sehfähigkeit.  
  
-   Verwenden Sie Diagramme nicht als gratis oder dekorativen Elemente auf einer Seite. Das heißt, wenn ein Diagramm nicht, dass alle Benutzer Wert oder Hilfe ein Problem lösen hinzufügen, verwenden Sie nicht.  
  
### <a name="chart-types"></a>Diagrammtypen  
 Von Diagrammen in Visual Studio verwendet die folgenden Anweisungstypen Balkendiagramme, Liniendiagramme, eine geänderte Kreisdiagramm als Ring Diagramm oder "Ringdiagramm", Zeitplänen, Punktdiagramm Darstellungen (auch als "cluster Diagramme" bezeichnet) und Balkendiagramme. Jede Art von Diagramm eignet sich für die Kommunikation von eines anderen Typs von Informationen.  
  
### <a name="other-charting-considerations"></a>Weitere Überlegungen zum Erstellen von Diagrammen  
  
#### <a name="color"></a>Farbe  
 Es ist eine bestimmte Palette von Diagrammen Farben für die Verwendung in Visual Studio definiert. Die Palette ist für die wichtigsten Typen von farbenblind zugegriffen werden kann, und die Farben können unterschieden werden, auch bei Verwendung als sehr kurze Segmente der Farbe. Sie können diese Farben in beliebiger Kombination für jede Art von Diagramm in die Benutzeroberfläche verwenden. Sie müssen nicht alle sieben Farben zu verwenden, wenn Sie viele unterschiedliche Farben nicht benötigen. Diese Farben wurden nicht darauf ausgelegt, mit der alle vordergrundelemente, damit kein Text oder Symbolen zusätzlich zu diesen Farben setzen verwendet werden soll. Diese Farbtöne hartcodiert und für die Anpassung unter verfügbar gemacht werden soll **Tools > Optionen** (siehe [Verfügbarmachen von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Farbfeld|Hex|RGB|  
|------------|---------|---------|  
|![Farbfeld 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Farbfeld BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Farbfeld FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Farbfeld 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Farbfeld 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Farbfeld 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Farbfeld B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="BKMK_OnObjectUI"></a>Auf Objekt Benutzeroberfläche und einsehen  
 Dieser Abschnitt enthält Kontext zum einsehen, auch bekannt als Peek Codeansicht, eines Typs auf Objekt Benutzeroberflächen für Visual Studio eindeutig.  
  
### <a name="overview"></a>Übersicht  
  
-   Auf Objekt UI sollte dem Benutzer mehr Informationen oder Interaktivität bieten, ohne ihre Hauptaufgabe sein zu müssen.  
  
-   Das Haupt-Muster für auf Objekt-Benutzeroberfläche in Visual Studio wird als "Informationen zum Zeitpunkt der Aufmerksamkeit." bezeichnet.  
  
-   Im Objekt-Benutzeroberfläche in Visual Studio ist entweder Inline oder Gleitkommatyp und dauerhaft oder flüchtig.  
  
    -   Peek Codeansicht, einen Typ von auf der Benutzeroberfläche in Visual Studio wird Inline und dauerhaft sein.  
  
    -   Codelens, IntelliTrace, einen Typ von auf der Benutzeroberfläche in Visual Studio ist Gleitkomma- und vorübergehende  
  
 Grundlegendes zur Funktionsweise eines Codeabschnitts, oder Suchen von Informationen zu diesen Code erfordert häufig ein Entwickler den Kontext wechseln, und wechseln zu anderen Inhalten oder einer anderen Fenster. Diese Kontext-Schichten können störend, sein, weil Benutzer den Fokus auf ihre ursprünglichen Aufgabe verloren gehen können, wenn sie ihre im Hauptfenster lassen. Darüber hinaus erhalten, dass die ursprünglichen Kontext wieder kann schwierig sein, insbesondere dann, wenn ihre ursprünglichen Code auf eine andere Benutzeroberfläche verdeckt werden Wechsel von Windows verursacht werden.  
  
 Benutzeroberfläche für Objekt folgt einem Muster, die Bezeichnung "Informationen zum Zeitpunkt der Aufmerksamkeit." Diese Nachrichten, Popup-Fenstern und Dialogfeldern ermöglichen Benutzern zusätzliche, relevante Informationen, die Klärung oder Interaktivität hinzufügt, ohne Fokus auf ihre Hauptaufgabe an. Beispiele für auf Objekt Benutzeroberfläche sind Popupfenster, die angezeigt werden, wenn ein Benutzer den Mauszeiger bewegt, über ein Symbol im Infobereich angezeigt, die rote Wellenlinie unter ein falsch geschriebenes Wort und der Peek-Ansicht, die in Visual Studio 2013 eingeführt wurden wird.  
  
### <a name="decision-points"></a>Entscheidungspunkte  
 Es gibt mehrere Möglichkeiten, verwenden diese Art von Informationen zum Zeitpunkt der Aufmerksamkeit, innerhalb von Visual Studio. Auswählen des richtigen Mechanismus und auf eine konsistente, vorhersehbare Weise implementieren, ist entscheidend dafür, dass die durchgängig. Andernfalls möglicherweise Benutzern eine Erfahrung verwirrend oder inkonsistente vorgeschlagen, die optimal für den Fokus aus dem Inhalt selbst.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Beziehungen zwischen Master- und Detailtabelle Inhalt  
 Informationen zum Zeitpunkt der Aufmerksamkeit wird verwendet, um eine Beziehung anzeigen im Zusammenhang zwischen dem Inhalt der Benutzer ist, konzentriert sich auf die (der "master"-Inhalt) sowie zusätzliche Inhalte (dem Inhalt "Detail"). Bei diesem Muster der Detail-Inhalt deutlich auf den Inhalt bezieht sich der Benutzer arbeitet mit und in der Nähe der master-Inhalt angezeigt werden kann. Zusätzliche Informationen oder Informationen, die zusammengefasst werden kann, ohne Sie zu einer Überlastung des master-Inhalts sollte eine andere Muster, z. B. ein Toolfenster folgen.  
  
-   **Immer** zeigt den Inhalt der Details in der Nähe der master-Inhalt.  
  
-   **Immer** stellen Sie sicher, dass der Detail-Inhalt immer noch ein Benutzer konzentriert sich auf den master Inhalt bleiben kann. Häufig besteht die beste Möglichkeit, dies zu erreichen, beim Rendern des Inhalts "Detail" als in der Nähe der master Inhalt wie möglich. Dies kann durch der Detail-Inhalt in einem Popupfenster neben den Hauptschlüssel Inhalt rendern oder durch das Detail Inhalt Inline unterhalb der master-Inhalt Rendern erfolgen.  
  
-   **Nie** Informationen zum Zeitpunkt der Aufmerksamkeit, die der Benutzer von der master-Inhalt verwenden. Wenn Benutzer den Inhalt Detail separat anzeigen müssen, machen Sie eine explizite Aktion, die dem Benutzer ermöglicht, die dazu verfügbar.  
  
#### <a name="design-details"></a>Details zum Design  
 Nachdem Sie festgestellt haben, dass auf dem Objekt-Benutzeroberfläche die richtige Wahl ist, gibt es vier wichtigsten Entwurfsaspekte:  
  
1.  **Persistenz:** muss der Inhalt dauerhaft oder vorübergehend sein?   
    Sollten Benutzer die Informationen sichtbarhalten finden Sie unter oder damit interagieren? Oder sollten Benutzer schnellen Blick auf die Informationen, und fahren Sie mit ihren Hauptaufgabe um?  
  
2.  **Inhaltstyp:** Inhalt werden nur zu Informationszwecken, aussagefähige oder Navigation?   
    Ist der Benutzer zusätzlichen Details über den Hauptschlüssel Inhalt erforderlich? Muss der Benutzer zum Abschluss einer Aufgabe, die der Hauptschlüssel Inhalt wirkt sich auf? Oder muss der Benutzer zu einer anderen Ressource weitergeleitet werden?  
  
3.  **Indikatortyp:** ist ein ambient-Indikator sinnvoll?   
    Die Informationen auf sinnvolle Weise zusammengefasst und angezeigt werden kann ohne Sie zu einer Überlastung des master-Inhalts?  
  
4.  **Gesten:** Aktionen von Was wird aufgerufen, und schließen die Benutzeroberfläche verwendet werden?   
    Wie wird der Benutzer den Inhalt Details aufzurufen und senden Sie sie? Ist es Wert in eine Geste, z. B. zum Wechseln zwischen transiente und permanente Status anheften hinzufügen?  
  
 Jedes dieser vier Entscheidungspunkte weist wirkt sich auf die wichtigsten Komponenten der Benutzeroberfläche auf Objekt.  
  
### <a name="on-object-ui-components"></a>Im Objekt-UI-Komponenten  
  
1.  Containertyp (Content Referenten.)  
  
    -   Gleitkomma  
  
    -   Inline  
  
2.  Inhaltstyp  
  
    -   Information: Daten, die statisch oder dynamisch sein könnte  
  
    -   Handlungsbedarf: Befehle, die den Hauptschlüssel Inhalt ändern  
  
    -   : Navigationslinks, der den Benutzer auf ein anderes Fenster oder Anwendung, z. B. MSDN  
  
3.  Gesten  
  
    -   Aufruf  
  
    -   Kündigung  
  
    -   Anheften  
  
    -   Andere Aktivitäten  
  
4.  Persistenz und Commit-Modell  
  
    -   Vorübergehend  
  
    -   Durable  
  
    -   Automatisch  
  
    -   Bei Bedarf  
  
5.  Ambient-Indikatoren (optional)  
  
    -   Wellenlinie "Unterstreichen"  
  
    -   Smarttag-Symbol  
  
    -   Andere ambient-Indikatoren  
  
#### <a name="container-content-presenter-type"></a>Containertyp (Content Referenten.)  
 Es gibt zwei Hauptoptionen zur Verfügung, um Inhalt zum Zeitpunkt der Aufmerksamkeit:  
  
1.  **Inline:** eine Inline-Darstellung, wie z. B. die Peek-Sicht, die in Visual Studio 2013 Code-Editor, eingeführt wurde Speicherplatz für neue Inhalte verfügbar macht, durch die Umstellung der vorhandenen Inhalte.  
  
    -   **Bevorzugen** Vortragende Inline, wenn Sie davon ausgehen, Benutzer sollten eine längere Zeitspanne verweisen dass auf oder die Interaktion mit dem Inhalt verbringen Sie darstellen.  
  
    -   **Vermeiden Sie** Vortragende Inline, wenn Sie davon ausgehen, Benutzer dass Blick auf die Informationen, die Sie darstellen, und klicken Sie dann ihre Hauptaufgabe mit minimaler Unterbrechung fortsetzen möchten.  
  
2.  **Gleitkommawert:** unverankerte Referent nahe bei den ausgewählten Inhalt möglichst positioniert ist, aber das Layout des vorhandenen Inhalts wird nicht verändert. Verschiedene Strategien können verwendet werden, z. B. das Anzeigen einer frei verschiebbaren Panels Inhalt über den nächsten verfügbaren Leerraum, um das ausgewählte Symbol.  
  
    -   **Bevorzugen** Vortragende Gleitkommawert, wenn Sie davon ausgehen, Benutzer dass sollten Blick auf die Informationen, die Sie darstellen, und klicken Sie dann ihre Hauptaufgabe mit minimaler Unterbrechung fortsetzen.  
  
    -   **Vermeiden Sie** Vortragende Gleitkommawert, wenn Sie davon ausgehen, Benutzer dass wird eine längere Zeitspanne verweisen auf oder die Interaktion mit dem Inhalt ausgeben möchten Sie vorhanden.  
  
#### <a name="content-type"></a>Inhaltstyp  
 Es gibt drei Haupttypen von Inhalten, die in alle Benutzeroberflächen-Container auf Objekt angezeigt werden können. Eine beliebige Kombination dieser Typen von Informationen kann angezeigt werden. Die drei Typen sind:  
  
1.  **Information:** die meisten UI Container zeigt eine Art von Information bei Objekt. Der Inhalt kann Informationen zu den aktuellen Zustand der Umgebung darstellen, oder es kann Informationen zu einem potenziellen zukünftigen Zustand der Umgebung dar. Beispielsweise kann verwendet werden, um die Auswirkung eines bestimmten Befehls, z. B. ein refactoring auf den vorhandenen Code angezeigt.  
  
    -   **Immer** verwenden die kanonische Darstellung der Informationen, die Sie anzeigen. Z. B. Code sollte wie im Code kann mit syntaxhervorhebung, Aussehen und berücksichtigen sollten, Schriftart und anderen umgebungseinstellungen, die der Benutzer gesetzt hat.  
  
    -   **Immer** sollten Sie die Unterstützung von Maßnahmen, die über die Information Inhalte, die wäre möglich, wenn die gleiche Informationen als master Inhalt angezeigt wird. Wenn Sie vorhandenen Code in einem in Objekt-Benutzeroberflächen-Container zu präsentieren, Angenommen Sie stark, unterstützen die Möglichkeit, Code zu suchen.  
  
    -   **Immer** sollten Sie eine andere Hintergrundfarbe verwenden, wenn nur zu Informationszwecken Inhalt darstellen, die einen potenziellen zukünftigen Status darstellt.  
  
2.  Handlungsbedarf: einige auf Objekt UI-Container die Fähigkeit zum Ausführen einer Aktion über die master-Inhalte, z. B. ein refactoring Vorgang bieten.  
  
    -   **Immer** aussagefähige Befehle separat aus dem nur zu Informationszwecken Inhalt zu positionieren.  
  
    -   **Immer** aktivieren und Deaktivieren von Aktionen, wenn dies angebracht.  
  
    -   **Immer** finden Sie in der Standardrichtlinien für die Befehle in Dialogfeldern darstellt.  
  
    -   **Immer** minimale behalten Sie die Anzahl der Aktionen, die in einem in Objekt-UI-Container auf ein absolutes verfügbar gemacht werden. Interaktion mit der Benutzeroberfläche auf Objekt muss ein einfaches, schnelles Erfahrung. Der Benutzer sollte keine Energie zum Verwalten der im Objekt-Benutzeroberflächen-Container selbst zu erweitern.  
  
    -   **Immer** berücksichtigen, wie und wann ein Benutzeroberflächen-Container auf Objekt geschlossen oder verworfen werden. Als bewährte Methode sollten alle Aktionen, die das Dialogfeld "zwischen der Master- und Detailtabelle, die Inhalt wird abgeschlossen auf Objekt Benutzeroberflächen-Container auch schließen, wenn mit dieser Aktion aufgerufen wird.  
  
3.  **Navigation:** einige auf-Objekt UI Container enthalten Links, die der Benutzer auf ein anderes Fenster oder Anwendung, z. B. öffnen einen MSDN-Artikel im Webbrowser des Benutzers ausführen.  
  
    -   **Immer** voranstellen jede Navigation Verknüpfung mit "Öffnen", damit Benutzer nicht überrascht werden einige andere Inhalte navigiert wird.  
  
    -   **Immer** Navigationslinks aus aussagefähige Links zu trennen.  
  
#### <a name="ambient-indicators-optional"></a>Ambient-Indikatoren (optional)  
 Ambiente Indikatoren möglich feine, einschließlich Text in einer kontrastreiche Farbe vom Rest des Codes, dargestellt oder offensichtlich, einschließlich Tickler-Symbolen, z. B. Wellenlinie unterstrichen und Smarttag Symbole. Ambiente Indikatoren kommunizieren die Verfügbarkeit von weitere relevante Informationen an. Im Idealfall bieten sie nützliche Informationen selbst, ohne dass der Benutzer mit ihnen interagieren.  
  
-   **Immer** positionieren Sie einen Ambiente-Indikator aus, sodass abgelenkt oder nicht überlastet den Benutzer bleibt. Ist es nicht möglich, einen Indikator ambient so zu positionieren, sollten Sie eine andere Lösung.  
  
-   **Immer** positionieren Sie den Ambiente-Indikator so nah wie möglich auf den Inhalt, die mit der Sie verknüpft ist.  
  
-   **Immer** versuchen, einen Indikator zu erstellen, die die Informationen zusammengefasst sind, zur Verfügung stellt. Erwägen Sie einen Zähler für die Anzahl von Datenelementen verfügbar (beispielsweise "3 Referenzen" statt einfach "Verweise") oder betrachten Sie eine andere Möglichkeit zum Zusammenfassen von Daten.  
  
    -   In Fällen, in denen die Daten für einen Indikator immer berechnet und angezeigt werden können nicht, sofort berücksichtigen Sie progressiven Feedback bereitstellen, wie die Werte berechnet werden. Betrachten Sie z. B. Animieren von Änderungen, die Updates für die verfügbaren Daten, die ähnlich wie bei widerspiegeln, die ungelesene e-Mails mit steigender Anzahl an die e-Mail-live-Kachel auf Windows Phone aktualisiert wird.  
  
-   **Nie** hinzufügen Weitere Indikatoren, die als ein Benutzer für einen bestimmten Inhalt angemessen ergreifen kann. Ambiente-Indikatoren sollte nützlich sein, ohne dass ein Eingreifen des Benutzers. Indikatoren verlieren ihre Umgebung erforderlich sind Überlauf und andere Management-Steuerelemente, die sie sichtbar zu machen.  
  
#### <a name="gestures"></a>Gesten  
 Ein wichtiger Aspekt der Benutzer Schwerpunkt auf den master Inhalt wird durch die Unterstützung der richtigen Gesten zum Öffnen und schließen den Inhalt für die zusätzliche Details.  
  
-   **Immer** muss der Benutzer zum Ausführen von einige explizite Geste, um die zusätzlichen Inhalte zu öffnen. Allgemeine open Gesten gehören:  
  
    -   **Wenn darauf gezeigt wird:** QuickInfos oder nicht interaktiv informative Inhalt  
  
    -   **Expliziten Befehl:** Inline Referenten.  
  
    -   **Doppelklicken Sie auf die ambient-Indikators:** CodeLens-Popup-Fenster  
  
-   **Immer** den Detail-Inhalt zu schließen, wenn der Benutzer die Esc-Taste drückt.  
  
-   **Immer** sollten Sie den Kontext der Benutzeroberfläche auf Objekt. Für Inhalt Vortragende, die für die Interaktion innerhalb des Containers zu ermöglichen, sorgfältig prüfen, ob zusätzliche Informationen darauf gezeigt wird, ist wahrscheinlich störend auf den Workflow des Benutzers werden angezeigt.  
  
-   **Nie** Inhalt anzeigen, wenn darauf gezeigt wird, die scheinbar bearbeitet werden, oder lädt Eingreifen des Benutzers. Dieses Verhalten kann Benutzer stören, versuchen die Benutzer so verschieben Sie den Cursor über die Inhalte Details wie das Standardverhalten für eine QuickInfo sofort zu schließen, wenn der Cursor nicht mehr über den Master Inhalt handelt, den sie generiert wird.  
  
##  <a name="BKMK_SelectionModels"></a>Auswahlmodelle  
  
### <a name="overview"></a>Übersicht  
 Ein Auswahlmodell ist der Mechanismus verwendet, um anzugeben, und bestätigen Vorgänge für eine oder mehrere Objekte von Interesse sind, in der Benutzeroberfläche. In diesem Thema wird erläutert, Auswahl interaktionsmustern in Visual Studio-Dokument-Editoren: Text-Editoren, Entwurfsoberflächen und Modellierung Flächen.  
  
 Benutzer benötigen eine Möglichkeit, der angibt, zu Visual Studio sie gearbeitet, und Visual Studio muss mit folgendem Antworten erwartungsgemäß Feedback an Benutzer zum was es in Betrieb ist. Unterschiede oder eine Fehlkommunikation zwischen dem Benutzer und die Benutzeroberfläche kann dazu führen, der Benutzer eine Aktion, die haben, kann nicht zu bemerken unerwartete Ergebnisse liefern. Der Fehler geht häufig nicht einmal bemerkt, bis der Benutzer sieht, dass ein Element nicht vorhanden ist oder wurde geändert. Auswahlmodelle sind daher eines der wichtigsten Teile der Entwurf der Benutzeroberfläche. Obwohl Auswahl-Modellen in Visual Studio mit Windows konsistent sind, sind leicht abgewandelten Form.  
  
 Unterscheiden sich in Visual Studio, wie unter Windows werden Auswahlmodelle je nach Zusammenhang, in dem die Aktivität auftritt. Auswahl können in vier Typen von Objekten auftreten:  
  
-   Text  
  
-   Grafikobjekte  
  
-   Listen und Strukturen  
  
-   Raster  
  
 Innerhalb dieser Objekte gibt es drei Arten von Optionen:  
  
-   zusammenhängenden  
  
-   Zusammenhanglose  
  
-   Region  
  
#### <a name="scope"></a>Bereich  
 Die wichtigste Komponente der Auswahl ist das sicherstellen, dass dem Benutzer bekannt ist, in welchem Fenster (Aktivierung) funktionieren und, in dem der Fokus befindet (Auswahl) befindet. Visual Studio erweitert die Fenster-Management-Funktion in Windows, das Schema für die Aktivierung ist jedoch identisch: Interaktion mit einem Fenster setzt den Fokus auf das Fenster. Visual Studio verfügt über zwei Indikatoren für die Aktivierung: eine für Dokumentfenster, und eine für Toolfenster.  
  
 Für Dokumentfenster wird ein Fenster Dokumentregisterkarte am Dateianfang stammen, und ändern die Hintergrundfarbe des aktiven Fensters ersichtlich:  
  
 ![Aktive registerkartenauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713 01_ActiveTab")  
  
 **Aktive registerkartenauswahl**  
  
 Für Toolfenster wird das aktive Fenster durch eine Änderung in der Farbe der Bereich der Titelleiste des Toolfensters angezeigt:  
  
 ![Aktive toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713 02_ActiveToolWindow")  
  
 **Primäre Auswahl eines Knotens mit aktives Toolfenster**  
  
 ![Inaktive toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713 03_InactiveToolWindow")  
  
 **Inaktive Toolfenster mit potenzieller Wartezeit Auswahl des Knotens**  
  
 Sobald ein Fenster aktiv ist, wird der Schwerpunkt entsprechend der Auswahlmodelle beschrieben, die in diesem Abschnitt der Richtlinien angegeben.  
  
#### <a name="context"></a>Kontext  
 Visual Studio wurde entwickelt, ein sicheres Konzept des Kontexts, beibehalten werden sollen, verfolgt, in dem der Benutzer arbeitet. Nur ein Fenster ist aktiv, ob es sich um ein Fenster Tool- oder Dokumentfenster handelt. Die oberste Dokumentfenster behält jedoch immer eine lose Auswahl. Obwohl der Schwerpunkt in einem Toolfenster sein kann, zeigt das Dokumentfenster, das zuletzt aktiv war eine Auswahl auch in einen inaktiven Status. Hierdurch wird der Kontext des Benutzers im Dokument beibehalten, die sie bearbeitet haben, erfahren sie, dass Visual Studio Zustand beibehalten wurde, sodass sie zurückkehren und nahtlos zwischen Toolfenstern und Dokumentfenstern verschieben können.  
  
### <a name="text-selection"></a>Textauswahl  
 Visual Studio-Editoren, die ausschließlich Text, z. B. die integrierte Text-Editor, verwenden Sie die gleichen Auswahl Textmodell und Darstellung beschrieben, der [Tastatur- und Zeiger](https://msdn.microsoft.com/en-us/library/dn742466.aspx) auf Windows User Experience Interaction Guidelines auf der Seite MSDN. Der Eingabefokus im Texteditor wird durch einen vertikalen Balken wird aufgerufen, die Einfügemarke angegeben. Die Einfügemarke wird ein einzelnes Pixel thick und farbige als Umkehrwert des was dahinter angezeigt wird. Es blinkt, gemäß der Rate festlegen, indem die **Cursor BlinkRate** festlegen in der **Geschwindigkeit** auf der Registerkarte die **Tastatur** Applet in der Systemsteuerung.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Die Auswahl zusammenhängenden und zusammenhanglosen  
 Auswahl in den Text-Editor ist fortlaufend. Nicht zusammenhängende Auswahl sind nicht zulässig, jedoch sollten im Objekt-Editor behandelt werden. Wenn der Benutzer den Mauszeiger über einen Textbereich befindet, nimmt der Cursor ein i-Balken dargestellt. Einem einzigen Mausklick platziert die Einfügemarke im Texteditor an der Position auf. Halten die Maustaste gedrückt startet eine auswahlmarkierung und die auswahlmarkierung die Maustaste loslassen endet.  
  
#### <a name="region-selection-box-selection"></a>Die Auswahl der Region (Auswahl)  
 Visual Studio unterstützt Region Auswahl im Texteditor, und dies wird als Auswahl bezeichnet. Auswahl kann der Benutzer einen Bereich von Text auszuwählen, die nicht die reguläre Textstream folgt. Wie bei der Auswahl der standard-Text, muss die Auswahl zusammenhängend sein. Auswahl wird gestartet, indem Sie die Alt-Taste gedrückt halten, während Sie mit der Maus ziehen. Auswahl kann auch durch gedrückter Alt-Taste oder der UMSCHALTTASTE mithilfe der Pfeiltasten an den Bereich der Auswahl initiiert werden. Auswahl verwendet die Markierung der normalen und der Einfügepunkt blinkt, am Ende den Auswahlbereich zeigt.  
  
 ![Regionale &#40; Feld &#41; Auswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713 04_BoxSelection")  
  
 **Die Auswahl der Region (Feld) in Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Darstellung von Text Auswahl  
 Die Farben für aktive und inaktive Auswahl im Editor können angepasst werden. Um die visuelle Darstellung des Editors anzupassen, kann Benutzer zu wechseln **Tools > Optionen**, und schauen Sie unter **Umgebung > Schriftarten und Farben > Text-Editor**.  
  
### <a name="graphical-selection"></a>Grafische Auswahl  
  
#### <a name="interaction"></a>Interaktion  
 Grafische Objektauswahl kann komplex sein und hängt von einer Reihe von Faktoren ab:  
  
-   **Der Editor primäre Auswahl-Modell.** Editoren, die grafische Objekte enthalten können auch verwendet werden, um Text oder Rastern zu bearbeiten. Z. B. möglicherweise Editor einer textbasierten Editor, der ebenfalls die Platzierung der grafische Objekte, z. B. Visual Studio XAML-Designer unterstützt. Unterstützen mehrere Objekttypen kann beeinflussen, wie der Benutzer Gruppen setzt sich aus verschiedenen Typen von Objekten auswählt.  
  
-   **Unterstützung für Primär- und sekundärauswahl Status.** Ein Editor bieten Primär- und sekundärauswahl Status miteinander zusammen, und so weiter angepasst, damit Objekte zeitgleich bearbeitet werden können ausgerichtet.  
  
-   **Unterstützung für das direkte Bearbeiten.** Editoren können auch den Inhalt ihrer grafische Objekte bearbeitet werden. Beispielsweise könnte eine rechteckige Form auch Text innerhalb enthalten, die vom Benutzer geändert werden können. Darüber hinaus konnte Text zentriert oder im Blocksatz ausgerichtet werden. Direkte Bearbeitung der Benutzerinteraktion eine detailliertere Ebene umfasst und benötigt daher einen entsprechenden Satz von visuellen Hinweise zum Darstellen von Statusinformationen für den Benutzer.  
  
#### <a name="mouse-interaction"></a>Mausinteraktion  
  
|Eingabe|Ergebnis|  
|-----------|------------|  
|Klicken Sie auf eine nicht ausgewählte Objekt|Wählt das Objekt aus, und eine gestrichelte Linie und Ziehpunkte, angezeigt, wenn das Objekt geändert werden.|  
|Klicken Sie auf ein ausgewähltes Objekt|Aktiviert die direkte Bearbeitung, wenn das Objekt unterstützt. Klicken außerhalb des-Objekts deaktiviert den Bearbeitungsmodus für die direkte.|  
|Doppelklicken Sie auf ein Objekt|Öffnet den Code für das Objekt zur Bearbeitung und kann einen Standardereignishandler einzufügen, falls zutreffend.|  
|Zeigen Sie auf ein Objekt|Ändert den Mauszeiger in den Cursor verschieben. Darstellung des Objekts, z. B. die Brillanz oder die Farbe, kann sich ändern.|  
|Zeigen Sie auf ein Auswahlkästchen|Ändert den Mauszeiger in die ostwest. Für Objekte, die Drehung unterstützen, können einige Auswahlpunkte den Zeiger auf einen Cursor drehen ändern, wenn der Zeiger in Bezug auf das Auswahlkästchen anders (z. B. Abstand verschoben) positioniert ist.|  
|Ziehen Sie|Auch wenn das Objekt nicht bereits ausgewählt ist, ändert sich der Zeiger auf den Cursor verschieben, und verschiebt das Objekt.|  
|Editor den Fokus verliert.|Direktes Bearbeitungsmodus deaktiviert, auch wenn das Objekt besetzt, Inhalt und Darstellung, die während der letzten Vorgang/Auswahlzustand wurde.|  
|Objektauswahl|Durch einen Rahmen, gepunktete Linie oder anderen visuell Behandlung, markieren Sie die Grenze des Objekts gekennzeichnet.|  
|Ändern Sie die Größe eines ausgewählten Objekts|Durch Auswahl Handles angegeben.<br /><br /> Ein Objekt in der Größe veränderbaren verfügt über acht Ziehpunkte, jede Richtung, in dem angepasst werden kann, die darstellt. Weniger Handles können verwendet werden, wenn das Objekt nur in bestimmten Richtungen angepasst werden kann. Wenn der Benutzer die Größe eines Objekts an, in denen acht Handles nicht interaktive wäre, möglicherweise vier Handles verwendet werden. Handle Größen sollten gebunden werden, um das Fenster Rahmen und Rand Metriken mit der **GetSystemMetrics** Größe proportional zur Auflösung-API-Funktion.<br /><br /> ![Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713 05_ResizeHandles")|  
|Drehen eines ausgewählten Objekts|![Handles zum Drehen](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713 06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Tastaturinteraktion  
  
|Eingabe|Ergebnis|  
|-----------|------------|  
|Registerkarte|Verschiebt den Fokusindikator für die logische Reihenfolge der Objekte im Editor. Dies ist möglicherweise links-nach-rechts oder oben nach unten, je nach **TabIndex** (oder gleichwertigen) Eigenschaftswert, Reihenfolge der objekterstellung und der den Zweck des Editors. Umschalt + Tab kehrt die Richtung des Indikators, den Fokus.|  
|LEERTASTE|Schwenkmodus aktiviert, während Tastatureingabe verwaltet wird. Zusätzliche Mauseingabe ist erforderlich, um die Position der Viewport schwenkt.|  
|STRG+LEERTASTE|Zoommodus aktiviert, während Tastatureingabe verwaltet wird. Zusätzliche Mauseingabe ist erforderlich, um zu- oder abnimmt den Zoomfaktor.|  
|Strg + Alt + Minuszeichen ()|Verringert den Zoomfaktor durch eine Ebene.|  
|Strg + Alt + Pluszeichen|Erhöht den Zoomfaktor durch eine Ebene.|  
|UMSCHALT oder STRG|Fügt das Objekt der Auswahlgruppe hinzu. STRG können Sie Objekte einzeln aus der Auswahlgruppe zu entfernen.|  
|Eingabe|Führt den Standardbefehl für das Objekt (in der Regel öffnen oder zu bearbeiten).|  
|F2|Aktiviert die direkte Bearbeitung für das Objekt.|  
|Pfeiltasten|Verschiebt die ausgewählten Objekte in der die Richtung der Pfeiltaste gedrückt, in kleinen Schritten (z. B. 1 Pixel zu einem Zeitpunkt)|  
|STRG + Pfeiltasten|Verschiebt die ausgewählten Objekte in der die Richtung der Pfeiltaste gedrückt, in größeren Schritten (z. B. 10 Pixel zu einem Zeitpunkt)|  
|UMSCHALT + nach-Schlüssel|Ändert die Größe der ausgewählten Objekte in der jeweiligen Richtung, in kleinen Schritten (z. B. 1 Pixel zu einem Zeitpunkt)|  
|STRG + UMSCHALT + Pfeiltasten|Ändert die Größe der ausgewählten Objekte in der jeweiligen Richtung, in größeren Schritten (z. B. 10 Pixel zu einem Zeitpunkt)|  
  
 Wenn Benutzer Kontrollen bearbeiten, kann es sinnvoll sein, wenn Objekte, um die Größe von Benutzereingaben automatisch sinnvoll. Z. B. wenn der Benutzer ein Bezeichnungsfeld-Steuerelement bearbeitet, soll klicken Sie dann die Bezeichnung vergrößert werden um den Text anzuzeigen, den der Benutzer gerade eingegeben haben. Wenn dies nicht erfolgt, muss der Benutzer manuell die Größe des Steuerelements nach dem Bearbeiten von Text. Wenn der Benutzer viele Steuerelemente verfügt, wird diese Eigenschaft einen routinemäßigen und Ausfallzeitraum Aufgabe.  
  
#### <a name="graphical-containers"></a>Grafische Container  
 In einigen Fällen stellen grafische-Editoren Container für andere grafische Objekte, z. B. Windows Forms-Bereichssteuerelement oder das Steuerelement Rasterlayout im HTML-Designer. Wenn der Editor Container für andere grafische Objekte enthält, sollte die folgende Auswahlmodell für den Container nur (Objekte innerhalb der Container führen Sie das standard-Modell als oben beschrieben) verwendet werden:  
  
|Eingabe|Ergebnis|  
|-----------|------------|  
|Klicken Sie einfaches für den container|Wählt die Container-Objekt ohne das Kontrollkästchen direkt die darin enthaltenen Objekte. Der Container möglicherweise verschoben und/oder Größe mit standard Maus- und Tastatureingaben (wie oben beschrieben) geändert werden. Enthaltenen Objekte in Bezug auf den Container verschoben werden, aber enthaltenen Objekte werden nicht geändert werden, es sei denn, sie auch direkt ausgewählt werden.|  
|Zeigen Sie auf den Container Grenze region|Aktiviert die Maus in die Move-Cursor, gibt an, dass der Container verschoben werden kann.|  
|Ziehen Sie den Container Grenze region|Ändert den Mauszeiger auf den Cursor verschieben, und verschiebt den Container (und die enthaltenen Objekte in). Der Container kann nicht verschoben werden, ohne zuerst mit einem einzigen Mausklick aktiviert wird.|  
|Klicken Sie einfaches auf ein Objekt innerhalb des Containers|Hebt die Auswahl des Containers (sofern aktiviert), und wählt nur die angeklickte Objekt.|  
|UMSCHALT + klicken oder STRG + Klicken Sie auf einem darin enthaltenen Objekte und/oder container|Einem vorhandenen Auswahl oder Auswahlgruppe hinzugefügt jedoch stattdessen das geklickt wurde. Wenn das Objekt geklickt wurde bereits ein Mitglied der Auswahlgruppe ist, wird er aus der Auswahlgruppe entfernt.|  
  
 Die enthaltenen Objekte sollten das Auswahlmodell der einfachen entsprechen, wie im vorherigen Abschnitt beschrieben. Aus Nutzbarkeitstests von Windows Forms-Designer, erwartet Benutzer nahtlosen Zugriff auf die enthaltenen Objekte ohne Zwischenschritte (auferlegt werden durch die Containment-Objekt).  
  
#### <a name="disjoint-and-region-selections"></a>Zusammenhanglose und Region-Auswahl  
 Objekt-Editoren sollten nicht zusammenhängende Auswahlbereiche unterstützt. Beachten Sie, dass diese Abbildung die Darstellung des Steuerelements für Visual Studio nicht angezeigt wird. Finden Sie unter [Grafikobjekt Auswahl Darstellung](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) für detaillierte visual-Spezifikationen.  
  
 ![Zusammenhanglose zusammenhängender Bereiche und Regionen](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713 07_DisjointRegionSelectors")  
  
 **Nicht zusammenhängende Auswahl**  
  
 Außerdem sollten die grafische-Editoren Region Auswahl mit einer Auswahl Laufschrift-Typindikator bereitstellen. Wenn der grafische Editor andere Objekttypen (z. B. Text) unterstützt, ggf. Region Auswahl nicht möglich, je nach den Einschränkungen dieser anderen Typen von Objekt.  
  
 ![Laufschriftauswahl](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713 08_MarqueeSelection")  
  
 **Auswahlrahmen**  
  
#### <a name="primary-and-secondary-selections"></a>Primäre und sekundäre Auswahl  
 Editoren Objekt ermöglicht dem Benutzer zu bearbeiten oder Objekte in Gruppen ausrichten. In diesem Fall muss das Konzept der primären und sekundären Auswahl eingeführt werden. Die primäre Auswahl ist das Objekt, zu dem alle anderen Objekte für das Gruppieren von Operationen reagieren. Das Objekt, das der Benutzer zuerst wählt wird primäres Steuerelement, und nachfolgende Auswahl werden die sekundären Auswahl. Primäre Auswahl verfügt über eine unterschiedliche visuelle Behandlung aus, um anzugeben, welches Objekt ein Primärschlüssel ist die sekundäre Auswahlen:  
  
 ![Primär- und sekundärauswahl](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713 09_PrimarySecondary")  
  
 **Primäre Auswahl mit zwei sekundäre Auswahl**  
  
####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a>Darstellung der Objekt-Auswahl  
 Ziehpunkte sind Quadrate, die in einem rechteckmuster, um das umgebende Feld des Objekts gezeichnet wird. Das folgende Diagramm zeigt Beispiele für die verschiedenen Status, die ein Objekt mit Handle, Größe und direkte Bearbeitung Darstellung haben kann. Die Größe der Handles gebunden werden sollte, Fensterrahmens und Edge Metriken mithilfe der **GetSystemMetrics** API.  
  
|Zustand|Darstellung|Visuelle details|  
|-----------|----------------|--------------------|  
|**Nicht ausgewählt**|Standard|![Schaltfläche Standardstatus](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713 10_DefaultState")||  
|**Primäre Auswahl**|In der Größe veränderbar|![Primäre Auswahl mit Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713 11_PrimaryResize")|![Primäre Auswahl mit Größe Handles &#40; vergrößert &#41; ] (../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713 12_PrimaryResizeZoom")|  
|**Primäre Auswahl**|Nicht geändert werden kann|![Primäre Auswahl ohne Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713 13_PrimaryNoResize")|![Primäre Auswahl ohne Ändern der Größe Handles &#40; vergrößert &#41; ] (../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713 14_PrimaryNoResizeZoom")|  
|**Primäre Auswahl**|Gesperrt|![Primäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713 15_PrimaryLocked")|![Primäre Auswahl gesperrt &#40; vergrößert &#41; ] (../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713 16_PrimaryLockedZoom")|  
|**Sekundäre Auswahl**|In der Größe veränderbar|![Sekundäre Auswahl mit Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713 17_SecondaryResize")|![Sekundäre Auswahl mit Größe Handles &#40; vergrößert &#41; ] (../../extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713 18_SecondaryResizeZoom")|  
|**Sekundäre Auswahl**|Nicht geändert werden kann|![Sekundäre Auswahl ohne Handles zur Größenänderung](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713 19_SecondaryNoResize")|![Sekundäre Auswahl ohne Größenänderung &#40; vergrößert &#41; ] (../../extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713 20_SecondaryNoResizeZoom")|  
|**Sekundäre Auswahl**|Gesperrt|![Sekundäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713 21_SecondaryLocked")|![Sekundäre Auswahl gesperrt &#40; vergrößert &#41; ] (../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713 22_SecondaryLockedZoom")|  
|**UI aktiv**|Standard|![Benutzeroberfläche im aktiven Status](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713 23_UIActive")|![UI Zustand "aktiv" &#40; vergrößert &#41; ] (../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713 24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Die Auswahlmodelle anzeigen  
  
#### <a name="tree-view"></a>Strukturansicht  
 Mit einer einfachen Hervorhebung wird die Auswahl in einer Strukturansicht angezeigt. Wenn der Benutzer auf einen Knotennamen oder ein Symbol "Knoten" klickt, wird der Knoten ausgewählt. Die dreieckigen Symbole auf der linken Seite des Knotens erweitern oder Verkleinern des Strukturansicht-Steuerelements jedoch wirken sich nicht auf die Auswahl des Benutzers, mit einer Ausnahme: auf einen übergeordneten Knoten reduzieren, wenn die Auswahl auf ein untergeordnetes Element dieses Knotens ist, verschiebt die Auswahl zum übergeordneten Element.  
  
 ![Typische Strukturansicht in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713 25_TreeView")  
  
 **Typische Strukturansicht in Visual Studio**  
  
 Strukturansichten unterstützen zusammenhängenden und nicht zusammenhängenden Auswahl, sogar über mehrere Ebenen in der Struktur. Zusammenhängend sein oder nicht zusammenhängenden Mehrfachauswahl sichtbaren Strukturknoten ausgeführt werden müssen. Wenn ein Knoten reduziert ist, die nicht zusammenhängende Auswahl verloren gegangen ist, und der Knoten, der reduziert wurde, erhält der Auswahl. Auf diese Weise kann der Benutzer Knoten anzuzeigen, die von einem Vorgang betroffen sind. Wenn der Knoten reduziert werden, wird es unklar welche Knoten betroffen sein könnten.  
  
 Wenn ein übergeordneter Knoten aktiviert ist, sollten der Vorgang an das übergeordnete Element anwenden, obwohl es gibt möglicherweise Fälle, in denen es für einen Vorgang an, das übergeordnete Element und alle untergeordneten sinnvoll ist. Geben Sie in diesem Fall weitere Benutzeroberfläche während des Vorgangs, z. B. ein Kontrollkästchen oder ein Bestätigungsdialogfeld auf die Option "gelten für alle untergeordneten Elemente" für dem Benutzer explizit zu machen.  
  
##### <a name="renaming"></a>Umbenennen  
 Umbenennen von Knoten in der Struktur zu unterstützen, sollten umbenennen bei direkten erfolgen. Der direkte Vorgang sollte der Standard für alle Struktursteuerelemente in Visual Studio. Geben Sie einen Rename-Befehl, der den Bearbeitungsmodus des direkten sofort mit der Textauswahl abdecken den gesamten Namen des Knotens bereit zur Annahme von Benutzereingaben aktiviert. Wenn der Knoten eine Datei darstellt, sollte der Dateinamen die Erweiterung enthalten. Die auswahlmarkierung sollte nur der Text, der den Dateinamen und nicht die Erweiterung enthalten.  
  
|Eingabe|Ergebnis|  
|-----------|------------|  
|Eingabetaste|Führt einen Commit für die Umbenennung|  
|ESC-Taste|Bricht die Umbenennung|  
|Klicken außerhalb des Bearbeitungsbereichs direktes|Führt einen Commit für die Umbenennung|  
|Rückgängig|Geben Sie einfach rückgängig, um die Umbenennung abzubrechen.|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Auswahl in Listen und Datenraster-Steuerelemente  
 Das Kernkonzept in Listenauswahl besteht, dass zeilenbasierten, d. h. wenn eine Auswahl, die gesamte Zeile getroffen wurde ausgewählt ist, als eine Einheit. Im Gegensatz dazu können Rastern bestimmte Zellen ausgewählt werden, ohne Auswirkungen auf andere Aspekte der Zeile. Raster können zudem eine Hierarchie von geschachtelten Zeilen (z. B. in einem TreeGrid) enthalten, mit denen gesamte Zweige der Hierarchie ausgewählt und durch die Interaktion mit der übergeordneten Zeilen deaktiviert werden. Auswahl in Listen wird durch eine einfache Hervorhebungsfarbe auf die gesamte Datenzeile angezeigt. Fokus wird durch einen gepunkteten Single-Pixel-Rahmen um die aktuelle bearbeitbare Zeile oder Zelle (Zeile, wenn Sie alle Zellen schreibgeschützt sind) angezeigt.  
  
> [!NOTE]
>  **Fokus** und **Auswahl** werden verschiedene Konzepte. *Fokus* ist ein Hinweis auf die Benutzeroberfläche Element als Ziel verwendet wird um Eingaben, die nicht explizit richtet sich an einem anderen Objekt zu empfangen, während er sich *Auswahl* bezieht sich auf den Zustand eines Objekts Aufnahme in einen Satz von Objekten auf dem nachfolgenden Vorgänge stattfinden können.  
  
 Auswahl der in Listen möglicherweise zusammenhängenden, zusammenhanglos, oder der Region. Wenn mehrere Auswahlmöglichkeiten zulässig festgelegt ist, zusammenhängend sind und nicht zusammenhängenden Auswahl sollte immer unterstützt werden, und bei der Unterstützung für die Auswahl der Region (Feld) ist optional. Region-Auswahl werden durch Ziehen in den Leerraum des Textkörpers Liste initiiert.  
  
|Objekt|Auswahl|  
|------------|---------------|  
|Liste|zusammenhängenden|Immer unterstützt (wenn die Mehrfachauswahl zulässig sind).|  
|Liste|Zusammenhanglose|Immer unterstützt (wenn die Mehrfachauswahl zulässig sind).|  
|Liste|Region|Die Unterstützung ist optional. Durch Ziehen der Maus in den Leerraum des Textkörpers Liste initiiert.|  
  
 Klicken einmal auf eine Liste zur Auswahl der Zeile, in dem der Klick aufgetreten ist. Falls der Benutzer in einer Listenzelle auf, die direkte Bearbeitung unterstützt, wird die Zelle für die direkte Bearbeitung auch sofort aktiviert. Andernfalls wird die ganze Zeile sofort aktiviert ist und zeigt eine Markierung.  
  
 Ziehen in der Liste Text ist eines von drei Dingen:  
  
-   Initiiert eine Auswahl auch treffen, wenn die Liste unterstützt und der Maus aus in Leerzeichen  
  
-   Initiiert einen Drag & Drop-Vorgang, wenn die Zelle oder Zeile unterstützt eine Quelle des Ziehvorgangs wird  
  
-   Markiert die aktuelle Zeile  
  
##### <a name="in-place-editing"></a>Direktes Bearbeiten  
 Wenn direkte Bearbeitung zulässig ist, es gibt zwei grundlegende Modelle: Auswahl einer einfachen bearbeiten-Steuerelement und -Eigenschaft. Befindet sich der Inhalt mit einem einfachen Edit-Steuerelement hervorgehoben und bereit für Benutzereingaben als direkte Bearbeitung aktiviert wird. Bei eine Auswahl einer Eigenschaft implementiert wird, wird die Schaltfläche, die die Auswahl einer Eigenschaft aufruft angezeigt, sobald direktes Bearbeitungsmodus aktiviert ist, und die aktuelle Auswahl nicht hervorgehoben ist. Die Schaltfläche "Datumsauswahl" sollte in der Zelle rechtsbündig sein. Direkte Bearbeitung Beispiele finden Sie in der **Fenster "Eigenschaften"** und **Aufgabenliste** in Visual Studio.  
  
##### <a name="keyboard-support"></a>Unterstützung der Tastatur  
 Tastatur-Unterstützung für die Auswahl in Listen und Rastern folgt standardmäßigen Windows-Konventionen:  
  
-   Pfeiltasten wechseln Sie die Liste, die jede Zeile/Zelle auswählen, wie der Fokus verschoben wird.  
  
-   UMSCHALT + nach-führt eine zusammenhängende Auswahl in die Richtung der Pfeiltasten an.  
  
-   STRG + LEERTASTE Schaltet zwischen hinzufügen und Entfernen von Elementen aus der Auswahl, und erstellen eine nicht zusammenhängende Auswahl gefolgt-Taste.  
  
-   Raster, die geschachtelte Hierarchien, rechts-Taste wird eine übergeordnete Zeile erweitert und links-Taste reduziert eine.  
  
-   Die Tab-Taste verschiebt den Fokus zwischen den Zellen in der aktuellen Zeile, wenn die Zellen bearbeitet werden.  
  
-   Die EINGABETASTE führt den Standardbefehl für das Element in der Liste (häufig **öffnen**).  
  
-   Die F2-Taste wird die direkte Bearbeitung für die derzeit ausgewählte Zelle aktiviert.  
  
##  <a name="BKMK_PersistenceAndSavingSettings"></a>Persistenz und Speichern der Einstellungen  
  
### <a name="overview"></a>Übersicht  
 Obwohl jede Softwarekomponente in Visual Studio in der Regel für einen eigenen Status und Persistenz zuständig ist, speichert Visual Studio-Einstellungen in einigen Fällen wie z. B. mit Fenstergrößen und Positionen. In der folgenden Tabelle ist eine Kombination von Einstellungen, die automatisch gespeichert und Einstellungen, die erfordern, dass einen explizite Benutzer auszuführende Aktion programmiert.  
  
|Objekt|Was speichern|Beim Speichern|Speicherort|  
|------------|------------------|------------------|-------------------|  
|Auswählbare Objekt (z. B. eine Codezeile)|Einen Haltepunkt in einer Zeile des Codes<br /><br /> Eine Benutzer-Verknüpfung, die die Zeile des Codes zugeordnet|Wenn das Projekt gespeichert ist|Die **Benutzeroptionen (.suo)** Datei für das Projekt|  
|Dialogfeld|Der Speicherort des Dialogs, wenn es verschoben wurde, hatte<br /><br /> Die Ansicht, die der Benutzer in das Dialogfeld "zuletzt verwendet|Wenn das Dialogfeld geschlossen wird<br /><br /> Wenn das Ende der Visual Studio-Sitzung|Im Arbeitsspeicher<br /><br /> Registrierung in **HKEY_Current_User**|  
|Fenster|Die Größe und Position des Fensters|Wenn das Fenster geschlossen wird<br /><br /> Wenn das Visual Studio den Modus geändert<br /><br /> Wenn das Ende der Visual Studio-Sitzung|Die **Benutzeroptionen (.suo)** Datei für das Projekt<br /><br /> Benutzerdefinierte Optionsdatei für Fenster-Einstellungen|  
|Dokument|Die aktuelle Auswahl im Dokument<br /><br /> Die Ansicht des Dokuments<br /><br /> Der letzte an mehreren Stellen der Benutzer besucht hat|Wenn das Dokument gespeichert wird|Die **Benutzeroptionen (.suo)** Datei für das Projekt|  
|Projekt|Verweise auf Dateien<br /><br /> Verweise auf Verzeichnisse auf dem Datenträger<br /><br /> Verweise auf andere software<br /><br /> Komponenten<br /><br /> Statusinformationen über das Projekt selbst|Wenn das Projekt gespeichert ist|Die Projektdatei|  
|Lösung|Verweise auf Projekte<br /><br /> Verweise auf Dateien|Wenn das Projekt oder die Projektmappe gespeichert wird|Die **Projektmappendatei (sln)** Datei|  
|Einstellungen im **Tools > Optionen**|Anpassungen der Tastatur<br /><br /> Symbolleiste-Anpassungen<br /><br /> Farbschema|Wenn die **Tools > Optionen** Dialogfeld geschlossen wird<br /><br /> Wenn das Ende der Visual Studio-Sitzung|Registrierung in **HKEY_Current_User**|  
  
 Was der Benutzer wird auf diese Weise, und wenn sie es, auf diese Weise werden bestimmt, ob eine Einstellung im Arbeitsspeicher (während der Sitzung), (sitzungsübergreifend als registrierungseinstellung), auf dem Datenträger gespeichert gespeichert wird, wird als Teil des Projekts oder der Projektmappe Datei selbst als Teil des der **Lösung Optionen (.suo)** -Datei ein, oder wie eine benutzerdefinierte, die nur diese Softwarekomponente Einstellungsdatei kennt. Der Tabelle oben werden mehrere Ereignisse, die an denen Einstellungen gespeichert werden können. Es gibt jedoch auch anderen Zeiten, in denen Sie möglicherweise Zustand speichern möchten:  
  
-   Wenn der Benutzer die Position in einem Dialogfeld oder Fenster ändert  
  
-   Wenn der Benutzer den Fokus auf ein anderes Fenster übertragen  
  
-   Wenn der Benutzer vom Entwurf bis zur den Debugmodus wechselt.  
  
-   Wenn Sie ihrem Konto meldet den Benutzer  
  
-   Wenn der Computer in den Ruhezustand wechselt oder heruntergefahren  
  
-   Wenn die Computer/Festplatte steht, werden neu formatiert und erneut einrichten  
  
### <a name="window-configurations"></a>Fensterkonfigurationen  
 Eine Fensterkonfiguration ist die grundlegende Darstellung der Entwicklungsumgebung – es ist ein Schema, bestehend aus der Liste der Toolfenster vorhanden und die Möglichkeit, in der sie angeordnet sind. Für Windows von der IDE (IDE-Fenster) verwaltet wird Layoutinformationen pro Benutzer und beibehalten, damit bei einem Benutzer gestartet wird, die IDE das Fensterlayout identisch angezeigt wird, wenn sie andauern Visual Studio beendet. Den Status und die Position des IDE-Fenster wird in einer benutzerdefinierten Optionsdatei im XML-Format beibehalten. Toolfenster, die von Paketen, die in der IDE geladen erstellt werden, behalten ihren Status in der Registrierung und möglicherweise oder möglicherweise nicht pro Benutzer.  
  
#### <a name="profile-specific-layouts"></a>Profil-spezifische layouts  
 Jedes Profil enthält Tool-Fensterlayouts, auf eine bestimmte Developer Personas vertraut Weise organisiert (Visual C++-Entwickler erwarten die **Projektmappen-Explorer** auf der linken Seite der IDE, während die C#-Entwickler erwarten, dass die findenSieunter **Projektmappen-Explorer** auf der rechten Seite). Profil-spezifische Fensterlayouts werden geladen, nachdem ein Profil beim Start Betätigung. Der Paketautor eines sollte das Fensterlayout für ihre benutzerfreundlichkeit am besten geeigneten bestimmen und zu wissen, dass Änderungen, die der Benutzer auf die Fensterkonfiguration stellt dann persistent ist.  
  
##  <a name="BKMK_TouchInput"></a>Fingereingabe  
 Benutzer werden zunehmend Produkte für die Entwicklung von Microsoft auf Touch-Geräte verwenden. Es gibt jedoch Barrieren, die Verwenden von Entwicklungstools für Touch-Geräte erschweren. Benutzer erwarten, dass unsere Produkte eine zuverlässige und präzise Toucheingabe zu ermöglichen. Der Zweck dieser Richtlinien besteht darin, Entscheidungen über die Touch-Funktionen integriert und zur Förderung der einer konsistente Touch-Erfahrung in Visual Studio und verwandte Produkte zu informieren.  
  
### <a name="levels-of-experience"></a>Ebenen der Benutzeroberfläche  
 Die folgenden Ebenen Erfahrung dienen zur dienen als Leitfaden für entscheiden, können mit Touch-Funktionen anbieten auf ihre gewünschte Maß an Zinsen in Verbindung setzen basieren.  
  
-   Die **Grundkenntnisse** für Teams,, geben Sie möchten, Funktionen berühren, daher gibt es keine Warteschlange für unzustellbare Nachrichten enden in der gesamten Arbeit ist.  
  
-   Die **optimierte Erfahrung** ist für die Teams, die allgemeine berührungs--Funktionen (z. B. die in der Regel im Internet-Browser-Anwendungen verfügbar) bieten möchten.  
  
-   Die **Erfahrung erhöhten** ist für Teams, die solche Funktionen hinzufügen möchten, die als Aktionen oder andere optionale Funktionen, die ihrer Anwendung vornehmen können Touch-First-angezeigter.  
  
||Grundkenntnisse|Optimierte Erfahrung|Erfahrung mit erhöhten rechten|  
|-|----------------------|--------------------------|-------------------------|  
|Ermöglicht es Benutzern...|Beheben von Code und Lösung/Projektebene ohne endet der Warteschlange für unzustellbare Nachrichten lesen|Aufgaben der Wartung, umgestaltungen und navigation|Arbeiten Sie in eine konsistente, intuitive und flexible Erfahrung mit vertrauen|  
|Editor|Touch-Schwenken und Auswahl<br /><br /> Bildlaufleiste Toucheingabe zu springen, und drücken + ziehen|Zwei-Finger-zoom<br /><br /> Schnelle scroll<br /><br /> Auswahl<br /><br /> Einfache Verwendung des Kontextmenüs||  
|Oberste Toolfenster|Liste Schwenken<br /><br /> Elementauswahl<br /><br /> Bildlaufleiste Toucheingabe zu springen, und drücken + ziehen|Einfache Element durchführen eines Bildlaufs und Auswahl||  
|Fensterfunktionen||Größe des Fensters<br /><br /> Schnellzugriff||  
|Dokumentursprung||Einfache Navigation zwischen geöffneten Dateien||  
|Gesten||Stellen Sie sicher, dass allgemeine Gesten in der IDE funktionieren|Gestenhandler-basierte Aktionen<br /><br /> Unterstützung von Drag-and-Drop und Designern|  
|Andere Überlegungen|||Benutzerdefinierte Bildschirmtastatur verwenden|  
  
#### <a name="gestures"></a>Gesten  
 Gesten bieten Benutzern eine Verknüpfung mit Befehlen, die andernfalls möglicherweise eine kompliziertere Aktivität erfordern. Die Windows-Richtlinien finden Sie unter [gemeinsamen Fingereingabe für Desktopanwendungen](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx), und befolgen Sie diese Anleitung für die meisten Gesten, einschließlich einfache Gesten wie z. B. Schwenken und zoomen.