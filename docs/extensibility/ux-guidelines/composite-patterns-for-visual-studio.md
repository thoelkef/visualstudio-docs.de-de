---
title: Zusammengesetzte Muster für Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698618"
---
# <a name="composite-patterns-for-visual-studio"></a>Zusammengesetzte Muster für Visual Studio
Zusammengesetzte Muster kombinieren Interaktions- und Designelemente in unterschiedlichen Konfigurationen. Einige der wichtigsten zusammengesetzten Muster in Visual Studio in Bezug auf Konsistenz sind:

- [Datenvisualisierung](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [On-Object-Benutzeroberfläche und Gucken](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Auswahlmodelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistenz- und Speichereinstellungen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Touch-Eingang](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>Datenvisualisierung

### <a name="overview"></a>Übersicht
 Diagramme sind eine visuelle Möglichkeit, Daten zu aggregieren und zu visualisieren, um die Entscheidungsfindung zu verbessern. Sie können Benutzern helfen, mit vielen Daten konfrontiert, aber wenig Bedeutung zu sehen, was Aufmerksamkeit verdient und was eine Aktion benötigen könnte.

 Der Benutzer profitiert von einem Diagramm, wenn eine der folgenden Bedingungen zutrifft:

- Hilft das Diagramm benutzern, Aufgaben zu identifizieren, auf die sie reagieren können?

- Wird das Diagramm es Benutzern ermöglichen, die Folgen möglicher Änderungen vorherzusagen?

- Wird das Diagramm Benutzern helfen, Trends zu erkennen und Muster zu identifizieren?

- Wird das Diagramm es Benutzern ermöglichen, bessere Entscheidungen zu treffen?

- Hilft das Diagramm bei der Beantwortung einer bestimmten Frage, die Benutzer im angegebenen Kontext haben können?

#### <a name="general-rules-for-charts"></a>Allgemeine Regeln für Diagramme

- Eindeutige Kennzeichnung von Daten. Illustrationen ohne Erklärung sind nur hübsche Bilder.

- Starten Sie Achsen bei Null, um schiefe Proportionen zu vermeiden. Linienlänge und Balkengröße sind wichtige visuelle Hinweise zum Verständnis der Beziehungen zwischen Datenpunkten.

- Erstellen Sie Diagramme, keine Infografiken. Infografiken sind künstlerische Darstellungen von Daten, und ihr primäres Ziel ist visuelles Geschichtenerzählen. Diagramme können (und sollten) visuell ansprechend sein, aber lassen Sie die Daten für sich sprechen.

- Vermeiden Sie Skeumorphismus, bildliche Balkendiagramme, Kontrasthashmarkierungen und andere Infografiken.

- Verwenden Sie keine 3D-Effekte als dekoratives Element. Verwenden Sie sie nur, wenn sie wirklich integraler Bestandteil der Fähigkeit des Benutzers sind, die Informationen zu verstehen.

- Vermeiden Sie die Verwendung mehrerer Zeilen und Füllungen, da mehr als zwei Farben das Lesen und Interpretieren dieses Diagrammtyps erschweren können.

- Verwenden Sie kein Diagramm (oder eine Abbildung) als einziges Mittel zum Verständnis eines Konzepts oder zur Interaktion mit Daten. Dies stellt für Nutzer mit Sehbehinderungen vor Schwierigkeiten.

- Verwenden Sie Diagramme nicht als unentgeltliche oder dekorative Elemente auf einer Seite. Mit anderen Worten: Wenn ein Diagramm keinen Wert hinzufügt oder Benutzern hilft, ein Problem zu lösen, verwenden Sie es nicht.

### <a name="chart-types"></a>Diagrammtypen
 Zu den in Visual Studio verwendeten Diagrammtypen gehören Balkendiagramme, Liniendiagramme, ein geändertes Kreisdiagramm, das als Ringdiagramm oder "Donut-Diagramm" bezeichnet wird, Zeitachsen, Streudiagramme (auch als "Clusterdiagramme" bezeichnet) und Gantt-Diagramme. Jeder Diagrammtyp ist nützlich, um einen anderen Informationstyp zu kommunizieren.

### <a name="other-charting-considerations"></a>Andere Diagrammüberlegungen

#### <a name="color"></a>Color
 Für die Verwendung in Visual Studio ist eine bestimmte Palette von Diagrammfarben definiert. Die Palette ist für die wichtigsten Arten der Farbblindheit zugänglich, und die Farben können auch dann unterschieden werden, wenn sie als sehr schmale Farbsegmente verwendet werden. Sie können diese Farben in jeder Kombination für jeden Diagrammtyp oder Diagramm in der Benutzeroberfläche verwenden. Sie müssen nicht alle sieben Farben verwenden, wenn Sie nicht so viele unterschiedliche Farben benötigen. Diese Farben wurden nicht für die Verwendung mit Vordergrundelementen entwickelt, daher platzieren Sie keinen Text oder Glyphen über diesen Farben. Diese Farbtöne sollten hartcodiert sein und der Benutzeranpassung unter **Tools > Optionen** zur Verfügung gestellt werden (siehe [Offenlegen von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Swatch|Hexadezimal|RGB|
|------------|---------|---------|
|![Farbmuster 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Farbmuster BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Farbmuster FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Farbmuster 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Farbmuster 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Farbmuster 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Farbmuster B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>On-Object-Benutzeroberfläche und Gucken
 Dieser Abschnitt gibt Kontext zum Gucken, auch als Codepeek-Ansicht bezeichnet, einer Art von Objektbenutzeroberfläche, die für Visual Studio eindeutig ist.

### <a name="overview"></a>Übersicht

- Die Benutzeroberfläche auf dem Objekt sollte dem Benutzer mehr Informationen oder Interaktivität geben, ohne von seiner Hauptaufgabe abzulenken.

- Das Hauptmuster für die Objektbenutzeroberfläche in Visual Studio wird als "Information im Mittelpunkt" bezeichnet.

- Die Objektbenutzeroberfläche in Visual Studio ist entweder inline oder unverankert und dauerhaft oder vorübergehend.

  - Die Code-Peek-Ansicht, eine Art objektübergreifende Benutzeroberfläche in Visual Studio, ist inline und dauerhaft.

  - CodeLens, eine Art on-object UI in Visual Studio, ist unverankert und

  Wenn Sie verstehen, wie ein Code funktioniert, oder um Details zu diesem Code zu finden, muss ein Entwickler häufig den Kontext wechseln und zu einem anderen Inhalt oder einem anderen Fenster wechseln. Diese Kontextverschiebungen können störend sein, da Benutzer den Fokus auf ihre ursprüngliche Aufgabe verlieren können, wenn sie ihr Hauptfenster verlassen. Darüber hinaus kann es schwierig sein, diesen ursprünglichen Kontext zurückzubekommen, insbesondere wenn das Wechseln von Fenstern dazu führte, dass der ursprüngliche Code durch andere Benutzeroberflächen verdeckt wurde.

  Die Benutzeroberfläche des Objekts folgt einem Muster, das als "Information am Point of Attention" bezeichnet wird. Diese Nachrichten, Popupfenster und Dialogfelder geben Benutzern zusätzliche, relevante Informationen, die Klarheit oder Interaktivität hinzufügen, ohne den Fokus auf ihre Hauptaufgabe zu verlieren. Beispiele für die Benutzeroberfläche von Objekten sind Popupfenster, die angezeigt werden, wenn ein Benutzer den Mauszeiger über ein Symbol im Benachrichtigungsbereich bewegt, die rote Wellenlinie unter einem falsch geschriebenen Wort und die in Visual Studio 2013 eingeführte Ansicht.

### <a name="decision-points"></a>Entscheidungspunkte
 In Visual Studio gibt es mehrere Möglichkeiten, dieses Informationsmuster zum Point of Attention zu verwenden. Die Wahl des richtigen Mechanismus und seine konsequente und vorhersehbare Implementierung sind für das Gesamterlebnis von entscheidender Bedeutung. Andernfalls wird Benutzern möglicherweise eine verwirrende oder inkonsistente Erfahrung angezeigt, die den Fokus vom Inhalt selbst ablenkt.

#### <a name="relationships-between-master-and-detail-content"></a>Beziehungen zwischen Master- und Detailinhalten
 Informationen am Point of attention werden verwendet, um eine Beziehung zwischen Inhalten anzuzeigen, auf die sich der Benutzer konzentriert (der "Master"-Inhalt) und zusätzlichen verwandten Inhalten (der "Detail"-Inhalt). In diesem Muster ist der Detailinhalt eindeutig mit dem Inhalt verknüpft, mit dem der Benutzer arbeitet, und kann in der Nähe des Masterinhalts angezeigt werden. Zusätzliche Informationen oder Informationen, die nicht zusammengefasst werden können, ohne den Masterinhalt zu überfordern, sollten einem anderen Muster folgen, z. B. einem Toolfenster.

- **Zeigen Sie** den Detailinhalt immer in unmittelbarer Nähe zum Masterinhalt an.

- Stellen **Sie immer** sicher, dass der Detailinhalt es einem Benutzer weiterhin ermöglicht, sich auf den Masterinhalt zu konzentrieren. Häufig ist der beste Weg, dies zu erreichen, die Detailinhalte so nah wie möglich am Masterinhalt zu rendern. Dies kann durch Rendern des Detailinhalts in einem Popupfenster neben dem Masterinhalt oder durch Rendern des Detailinhalts inline unter dem Masterinhalt erfolgen.

- Verwenden **Sie niemals** Informationen an dem Punkt der Aufmerksamkeit, der den Benutzer vom Masterinhalt wegnimmt. Wenn Benutzer den Detailinhalt separat anzeigen müssen, machen Sie eine explizite Aktion verfügbar, die es dem Benutzer ermöglicht, dies zu tun.

#### <a name="design-details"></a>Designdetails
 Nachdem Sie festgestellt haben, dass die Benutzeroberfläche des Objekts die richtige Wahl ist, gibt es vier Hauptentwurfsüberlegungen:

1. **Persistenz:** Ist erwartet, dass der Inhalt dauerhaft oder vorübergehend ist?
   Möchten Benutzer die Informationen sichtbar halten, auf die sie verweisen oder mit denen sie interagieren können? Oder möchten Benutzer schnell einen Blick auf die Informationen werfen und dann mit ihrer Hauptaufgabe fortfahren?

2. **Inhaltstyp:** Wird der Inhalt informationsfähig, umsetzbar oder navigationsfähig sein?
   Benötigt der Benutzer zusätzliche Details zum Masterinhalt? Muss der Benutzer eine Aufgabe ausführen, die sich auf den Masterinhalt auswirkt? Oder muss der Benutzer zu einer anderen Ressource weitergeleitet werden?

3. **Indikatortyp:** Ist ein Umgebungsindikator sinnvoll?
   Können die Informationen sinnvoll zusammengefasst und angezeigt werden, ohne den Masterinhalt zu überfordern?

4. **Gesten:** Welche Gesten werden verwendet, um die Benutzeroberfläche aufzurufen und zu entlassen?
   Wie wird der Benutzer den Detailinhalt aufden und verschicken? Ist es wert, eine Geste hinzuzufügen, z. B. das Anheften, um zwischen transienten und dauerhaften Zuständen zu wechseln?

   Jeder dieser vier Entscheidungspunkte wirkt sich auf die hauptwichtigsten Komponenten der Objektbenutzeroberfläche aus.

### <a name="on-object-ui-components"></a>On-Object-UI-Komponenten

1. Containertyp (Inhaltsreferent)

    - Gleitkomma

    - Inline

2. Inhaltstyp

    - Informational: Daten, die statisch oder dynamisch sein können

    - Umsetzbar: Befehle, die den Masterinhalt ändern

    - Navigation: Links, die den Benutzer zu einem anderen Fenster oder einer anderen Anwendung führen, z. B. MSDN

3. Gesten

    - Aufruf

    - Entlassung

    - Anheften

    - Andere Wechselwirkungen

4. Persistenz- und Commitmodell

    - Kurzlebig

    - Durable

    - Automatic

    - Bei Bedarf

5. Umgebungsanzeiger (optional)

    - Squiggle-Unterstreichung

    - Smarttag-Symbol

    - Andere Umgebungsindikatoren

#### <a name="container-content-presenter-type"></a>Containertyp (Inhaltsreferent)
 Es stehen zwei Hauptoptionen zur Verfügung, um Inhalte zum Zeitpunkt der Aufmerksamkeit darzustellen:

1. **Inline:** Ein Inline-Moderator, z. B. die Im Visual Studio 2013-Code-Editor eingeführte Ansicht, macht Platz für neue Inhalte, indem vorhandener Inhalt verschoben wird.

    - **Bevorzugen Sie** Inline-Moderatoren, wenn Sie erwarten, dass Benutzer viel Zeit damit verbringen möchten, sich auf die von Ihnen präsentierten Inhalte zu beziehen oder mit ihnen zu interagieren.

    - **Vermeiden Sie** Inline-Moderatoren, wenn Sie erwarten, dass Benutzer einen Blick auf die von Ihnen präsentierten Informationen werfen und dann mit ihrer Hauptaufgabe mit minimaler Unterbrechung fortfahren möchten.

2. **Floating:** Ein unverankerter Moderator wird so nah wie möglich am ausgewählten Inhalt positioniert, ändert jedoch nicht das Layout des vorhandenen Inhalts. Es können verschiedene Strategien verwendet werden, z. B. das Anzeigen eines unverankerten Inhaltsbereichs über dem nächstgelegenen verfügbaren Leerraum zum ausgewählten Symbol.

    - **Bevorzugen Sie** schwebende Präsentatoren, wenn Sie erwarten, dass Benutzer einen Blick auf die informationen werfen möchten, die Sie präsentieren, und dann mit ihrer Hauptaufgabe mit minimaler Unterbrechung fortfahren möchten.

    - **Vermeiden Sie** unverankerte Referenten, wenn Sie davon ausgehen, dass Benutzer viel Zeit damit verbringen möchten, sich auf die von Ihnen präsentierten Inhalte zu beziehen oder mit ihnen zu interagieren.

#### <a name="content-type"></a>Inhaltstyp
 Es gibt drei Haupttypen von Inhalten, die in jedem Objekt-UI-Container angezeigt werden können. Eine beliebige Kombination dieser Arten von Informationen kann angezeigt werden. Die drei Typen sind:

1. **Informational:** Die meisten Objekt-UI-Container zeigen eine Art Informationsinhalt an. Der Inhalt kann Informationen über den aktuellen Zustand der Umgebung oder Informationen über einen potenziellen zukünftigen Zustand der Umgebung darstellen. Es könnte z. B. verwendet werden, um die Auswirkungen eines bestimmten Befehls, z. B. einer Umgestaltung, auf den vorhandenen Code anzuzeigen.

    - Verwenden **Sie immer** die kanonische Darstellung der angezeigten Informationen. Code sollte z. B. wie Code aussehen, komplett mit Syntaxhervorhebung, und alle Schriftarten und andere Umgebungseinstellungen respektieren, die der Benutzer festgelegt hat.

    - **Erwägen Sie immer,** Aktionen über den Informationsinhalt zu unterstützen, die möglich wären, wenn dieselben Informationen als Masterinhalt dargestellt werden. Wenn Sie z. B. vorhandenen Code in einem Objekt-UI-Container darstellen, sollten Sie die Möglichkeit zum Durchsuchen und Ändern dieses Codes dringend unterstützen.

    - **Erwägen Sie immer,** eine andere Hintergrundfarbe zu verwenden, wenn Sie Informationsinhalte darstellen, die einen potenziellen zukünftigen Status darstellen.

2. Umsetzbar: Einige Objekt-UI-Container bieten die Möglichkeit, Aktionen über den Masterinhalt auszuführen, z. B. einen Umgestaltungsvorgang.

    - **Positionieren Sie** umsetzbare Befehle immer getrennt vom Informationsinhalt.

    - Aktivieren und deaktivieren Sie Aktionen **immer,** wenn dies angebracht ist.

    - Beziehen Sie sich **immer** auf die Standardrichtlinien für die Darstellung von Befehlen in Dialogfeldern.

    - Halten Sie die Anzahl der Aktionen, die in einem Objekt-UI-Container verfügbar gemacht werden, **immer** auf ein absolutes Minimum. Die Interaktion mit der Benutzeroberfläche auf dem Objekt sollte ein leichtes und schnelles Erlebnis sein. Der Benutzer sollte keine Energie für die Verwaltung des Objekt-UI-Containers selbst aufwenden müssen.

    - **Berücksichtigen Sie immer,** wie und wann ein Objekt-UI-Container geschlossen oder verworfen wird. Als bewährte Methode sollte jede Aktion, die den Dialog zwischen dem Master- und Detailinhalt abschließt, auch den Objekt-UI-Container schließen, wenn diese Aktion aufgerufen wird.

3. **Navigation:** Einige Objekt-UI-Container enthalten Links, die den Benutzer zu einem anderen Fenster oder einer anderen Anwendung führen, z. B. das Öffnen eines MSDN-Artikels im Webbrowser des Benutzers.

    - **Stellen Sie** jedem Navigationslink immer "Öffnen" vor, damit Benutzer nicht überrascht werden, wenn sie zu anderen Inhalten navigiert werden.

    - Trennen **Sie Navigationslinks immer** von umsetzbaren Links.

#### <a name="ambient-indicators-optional"></a>Umgebungsanzeiger (optional)
 Umgebungsindikatoren können subtil sein, einschließlich Text, der in einer kontrastierenden Farbe vom Rest des Codes dargestellt wird, oder offensichtlich, einschließlich Tickler-Symbole wie Squiggle-Unterstreichungen und Smarttag-Symbole. Umgebungsindikatoren kommunizieren die Verfügbarkeit zusätzlicher, relevanter Informationen. Im Idealfall liefern sie nützliche Informationen, auch ohne dass der Benutzer mit ihnen interagieren muss.

- **Positionieren Sie immer** eine Umgebungsanzeige, damit sie den Benutzer nicht ablenkt oder überwältigt. Wenn es unmöglich ist, einen Umgebungsindikator auf diese Weise zu positionieren, sollten Sie eine andere Lösung in Betracht ziehen.

- **Positionieren Sie** den Umgebungsindikator immer so nah wie möglich an dem Inhalt, mit dem er zusammenhängt.

- Versuchen **Sie immer,** einen Indikator zu erstellen, der die verfügbaren Informationen zusammenfasst. Erwägen Sie, die Anzahl der verfügbaren Datenelemente (z. B. "3 Referenzen" anstelle von "Referenzen") anzurechnen oder sich eine andere Möglichkeit zum Zusammenfassen der Daten zu überlegen.

  - In Fällen, in denen die Daten für einen Indikator nicht immer berechnet und angezeigt werden können, sollten Sie sofort in Betracht ziehen, progressives Feedback bereitzustellen, während die Werte berechnet werden. Betrachten Sie beispielsweise das Animieren von Änderungen, die Aktualisierungen der verfügbaren Daten widerspiegeln, ähnlich der Art und Weise, wie die E-Mail-Livekachel unter Windows Phone aktualisiert wird, wenn die Anzahl der ungelesenen E-Mails zunimmt.

- **Fügen Sie niemals** mehr Indikatoren hinzu, als ein Benutzer vernünftigerweise für einen bestimmten Inhalt aufnehmen kann. Umgebungsindikatoren sollten nützlich sein, ohne dass der Benutzer eine Interaktion erfordert. Indikatoren verlieren ihr Ambiente, wenn sie Überlauf- und andere Managementkontrollen benötigen, um sie ins Blickfeld zu rücken.

#### <a name="gestures"></a>Gesten
 Ein wichtiger Aspekt, der es dem Benutzer ermöglicht, den Fokus auf den Masterinhalt zu behalten, besteht darin, die richtigen Gesten zum Öffnen und Ablehnen des zusätzlichen Detailinhalts zu unterstützen.

- **Es** ist immer erforderlich, dass der Benutzer eine explizite Geste ausführt, um den zusätzlichen Inhalt zu öffnen. Zu den allgemeinen offenen Gesten gehören:

  - **Hover:** QuickInfos oder nicht interaktive reine Informationsinhalte

  - **Expliziter Befehl:** Inline-Moderator

  - **Doppelklicken Sie auf die Umgebungsanzeige:** CodeLens-Popupfenster

- **Schließen Sie** den Detailinhalt immer dann ab, wenn der Benutzer die Esc-Taste drückt.

- **Berücksichtigen Sie immer** den Kontext der Objektbenutzeroberfläche. Bei Inhaltspräsentanten, die eine Interaktion innerhalb des Containers ermöglichen, sollten Sie sorgfältig überlegen, ob zusätzliche Informationen zum Mauszeiger angezeigt werden sollen, was den Workflow des Benutzers beeinträchtigen dürfte.

- **Zeigen Sie niemals** Inhalte auf dem Mauszeiger an, die bearbeitbar zu sein scheinen oder zur Benutzerinteraktion einlädt. Dieses Verhalten kann Benutzer frustrieren, wenn sie versuchen, den Cursor über den Detailinhalt zu bewegen, da das Standardverhalten für eine QuickInfo darin besteht, sofort zu schließen, wenn sich der Cursor nicht mehr über den Masterinhalt befindet, der sie erstellt hat.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>Auswahlmodelle

### <a name="overview"></a>Übersicht
 Ein Auswahlmodell ist der Mechanismus, der zum Anzeigen und Bestätigen von Vorgängen an einem oder mehreren Objekten verwendet wird, die innerhalb der Benutzeroberfläche von Interesse sind. In diesem Thema werden Auswahlinteraktionsmuster in Visual Studio-Dokumenteditoren erläutert: Texteditoren, Entwurfsflächen und Modellierungsflächen.

 Benutzer müssen eine Möglichkeit haben, Visual Studio anzugeben, woran sie arbeiten, und Visual Studio muss vorhersagbar mit Feedback an Benutzer reagieren, woran es arbeitet. Unterschiede oder eine Fehlkommunikation zwischen dem Benutzer und der Benutzeroberfläche können dazu führen, dass der Benutzer eine Aktion nicht bemerkt, was unbeabsichtigte Folgen haben kann. Oft bleibt der Fehler unbemerkt, bis der Benutzer sieht, dass etwas fehlt oder sich geändert hat. Auswahlmodelle gehören daher zu den kritischsten Elementen des User Interface Designs. Obwohl Auswahlmodelle in Visual Studio mit Windows konsistent sind, gibt es geringfügige Abweichungen.

 In Visual Studio, wie auch in Windows, unterscheiden sich Auswahlmodelle je nach Kontext, in dem die Interaktion stattfindet. Die Auswahl kann in vier Objekttypen erfolgen:

- Text

- Grafikobjekte

- Listen und Bäume

- Raster

  Innerhalb dieser Objekte gibt es drei Arten von Auswahlen:

- Zusammenhängenden

- Dijunkt

- Region

#### <a name="scope"></a>Bereich
 Die wichtigste Komponente der Auswahl besteht darin, sicherzustellen, dass der Benutzer weiß, in welchem Fenster er arbeitet (Aktivierung) und wo sich der Fokus befindet (Auswahl). Visual Studio erweitert die Fensterverwaltungsfunktionalität in Windows, aber das Aktivierungsschema ist das gleiche: Die Interaktion mit einem Fenster bringt den Fokus auf das Fenster. Visual Studio verfügt über zwei Indikatoren für die Aktivierung: einen für Dokumentfenster und einen für Toolfenster.

 Bei Dokumentfenstern wird das aktive Fenster durch eine Registerkarte des Dokumentfensters angezeigt, die nach vorne kommt und die Hintergrundfarbe ändert:

 ![Aktive Registerkartenauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Aktive Tab-Auswahl**

 Bei Werkzeugfenstern wird das aktive Fenster durch eine Änderung der Farbe des Titelleistenbereichs des Werkzeugfensters angezeigt:

 ![Aktive Toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Aktives Werkzeugfenster mit der primären Auswahl eines Knotens**

 ![Inaktive Toolfensterauswahl in Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Inaktives Werkzeugfenster, in dem die latente Auswahl des Knotens angezeigt wird**

 Sobald ein Fenster aktiv ist, wird sein Fokus entsprechend den in diesem Abschnitt der Richtlinien beschriebenen Auswahlmodellen angezeigt.

#### <a name="context"></a>Kontext
 Visual Studio wurde entwickelt, um ein starkes Kontextkonzept beizubehalten und den Arbeitsort des Benutzers nachzuverfolgen. Es ist nur ein Fenster aktiv, unabhängig davon, ob es sich um ein Werkzeug- oder Dokumentfenster handelt. Das oberste Dokumentfenster behält jedoch immer eine latente Auswahl bei. Obwohl sich der Fokus möglicherweise in einem Werkzeugfenster befindet, zeigt das Dokumentfenster, das zuletzt aktiv war, eine Auswahl an, auch in einem inaktiven Zustand. Dadurch wird der Kontext des Benutzers in dem Dokument beibehalten, das er bearbeitet hat, und zeigt ihnen an, dass Visual Studio seinen Status beibehalten hat, sodass visual Studio nahtlos zwischen Toolfenstern und Dokumentfenstern zurückkehren und wechseln kann.

### <a name="text-selection"></a>Markieren von Text
 Visual Studio-Editoren, die streng textlich sind, z. B. der integrierte Texteditor, verwenden dasselbe Textauswahlmodell und die gleiche Darstellung, die auf der Seite [Maus und Zeiger](/windows/desktop/uxguide/inter-mouse) der Windows-Richtlinien für die Benutzerfreundlichkeit von MSDN beschrieben sind. Der Eingabefokus im Texteditor wird durch eine vertikale Leiste, die Einfügemarke, angezeigt. Die Einfügemarke ist ein einzelnes Pixel dick und als Umkehrung von dem, was dahinter erscheint, gefärbt. Es blinkt entsprechend der Rate, die durch die **Cursor-Blinkrate-Einstellung** in der **Registerkarte Geschwindigkeit** des Tastatur-Applets in der Systemsteuerung festgelegt wird. **Keyboard**

#### <a name="contiguous-and-disjoint-selection"></a>Zusammenhängende und unzusammenhängende Auswahl
 Die Auswahl innerhalb des Texteditors ist nur zusammenhängend. Unzusammenhängende Textauswahlen sind nicht zulässig, sollten aber in grafischen Objekteditoren behandelt werden. Wenn sich der Mauszeiger des Benutzers über einem Textbereich befindet, ändert sich der Cursor in einen I-Träger. Mit einem einzigen Klick wird die Einfügemarke im Texteditor an der Klickposition platziert. Wenn Sie die Maustaste gedrückt halten, wird eine Auswahlhervorhebung gestartet, und das Loslassen der Maustaste beendet die Auswahl-Hervorhebung.

#### <a name="region-selection-box-selection"></a>Regionsauswahl (Feldauswahl)
 Visual Studio unterstützt die Bereichsauswahl im Texteditor, und dies wird als Feldauswahl bezeichnet. Durch die Feldauswahl kann der Benutzer einen Textbereich auswählen, der nicht dem regulären Textstream folgt. Wie bei der Standardtextauswahl muss die Auswahl zusammenhängend sein. Die Boxauswahl wird initiiert, indem Sie die Alt-Taste gedrückt halten, während Sie mit der Maus ziehen. Die Feldauswahl kann auch initiiert werden, indem Sie die Alt- und Shift-Tasten gedrückt halten, während Sie die Pfeiltasten verwenden, um den Auswahlbereich anzuzeigen. Bei der Feldauswahl wird die normale Auswahlhervorhebung verwendet und der Einfügepunktcursor blinkt am Ende des Auswahlbereichs.

 ![Regionale &#40;-Feldauswahl&#41; in Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Regionsauswahl (Box) in Visual Studio**

#### <a name="text-selection-appearance"></a>Darstellung der Textauswahl
 Die Farben, die für die aktive und inaktive Auswahl im Editor verwendet werden, können angepasst werden. Um die visuelle Darstellung des Editors anzupassen, kann ein Benutzer zu **Tools > Optionen**wechseln und dann unter Umgebung > **Schriftarten und Farben > Texteditor**suchen.

### <a name="graphical-selection"></a>Grafische Auswahl

#### <a name="interaction"></a>Interaktion
 Die grafische Objektauswahl kann komplex sein und hängt von einer Reihe von Faktoren ab:

- **Das primäre Auswahlmodell des Editors.** Editoren, die grafische Objekte enthalten, können auch zum Bearbeiten von Text oder Rastern verwendet werden. Der Editor kann z. B. ein textbasierter Editor sein, der auch die Platzierung von grafischen Objekten unterstützt, z. B. des Visual Studio XAML-Designers. Die Unterstützung mehrerer Objekttypen kann sich darauf auswirken, wie der Benutzer Gruppen aus verschiedenen Objekttypen auswählt.

- **Unterstützung für primäre und sekundäre Auswahlzustände.** Ein Editor kann primäre und sekundäre Auswahlzustände bereitstellen, sodass Objekte gemeinsam bearbeitet, aufeinander ausgerichtet, gemeinsam in der Größe geändert usw. bearbeitet werden können.

- **In-Place-Bearbeitungsunterstützung.** Editoren können auch die Bearbeitung des Inhalts ihrer grafischen Objekte zulassen. Beispielsweise kann eine Rechteckform auch Text auf der Innenseite enthalten, der vom Benutzer geändert werden kann. Darüber hinaus könnte dieser Text zentriert oder gerechtfertigt werden. Die direkte Bearbeitung umfasst eine detailliertere Ebene der Benutzerinteraktion und erfordert daher einen geeigneten Satz visueller Hinweise für die Darstellung von Statusinformationen für den Benutzer.

#### <a name="mouse-interaction"></a>Mausinteraktion

|Eingabe|Ergebnis|
|-----------|------------|
|Klicken Sie auf ein nicht ausgewähltes Objekt|Wählt das Objekt aus und zeigt eine gestrichelte Linie und Auswahlpunkte an, wenn das Objekt in der Geänderten Position geändert werden kann.|
|Klicken auf ein ausgewähltes Objekt|Aktiviert die ortsspezifische Bearbeitung, wenn das Objekt sie unterstützt. Wenn Sie außerhalb des Objekts klicken, wird der direkt bearbeitende Modus deaktiviert.|
|Doppelklicken auf ein Objekt|Öffnet den Code hinter dem Objekt zur Bearbeitung, und fügt ggf. einen Standardereignishandler ein.|
|Zeigen auf ein Objekt|Ändert den Zeiger auf den Bewegungscursor. Das Erscheinungsbild des Objekts, z. B. seine Leuchtkraft oder Farbe, kann sich ändern.|
|Zeigen Sie auf ein Auswahlhandle|Ändert den Zeiger auf den Änderungs-/Größencursor. Bei Objekten, die die Drehung unterstützen, können einige Auswahlpunkte den Zeiger in einen Drehcursor ändern, da der Zeiger in Bezug auf den Auswahlpunkt anders positioniert (z. B. weiter entfernt verschoben) wird.|
|Ziehen|Auch wenn das Objekt nicht zuvor ausgewählt ist, ändert der Zeiger auf den Verschiebungscursor und verschiebt das Objekt.|
|Editor verliert den Fokus|Deaktiviert den direkt stattfindenden Bearbeitungsmodus, obwohl das Objekt den Inhalt und das Erscheinungsbild beibehält, die es während des letzten Vorgangs/Auswahlzustands hatte.|
|Objektauswahl|Wird durch einen Rahmen, eine gepunktete Linie oder eine andere visuell unterschiedliche Behandlung angezeigt, um die Grenze des Objekts hervorzuheben.|
|Ändern der Größe eines ausgewählten Objekts|Angezeigt durch Auswahlgriffe.<br /><br /> Ein in der Größe geändertes Objekt verfügt über acht Ziehpunkte, die jede Richtung darstellen, in der es in der Größe geändert werden kann. Es können weniger Handles verwendet werden, wenn die Größe des Objekts nur in bestimmten Richtungen geändert werden kann. Wenn der Benutzer ein Objekt bis zu dem Punkt vergrößert, an dem acht Handles nicht interaktiv sind, können vier Handles verwendet werden. Griffgrößen sollten mit der **GetSystemMetrics-API-Funktion** an den Fensterrahmen und die Kantenmetriken gebunden werden, um die Größe proportional zur Anzeigeauflösung zu erreichen.<br /><br /> ![Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Drehen eines ausgewählten Objekts|![Handles zum Drehen](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Tastaturinteraktion

|Eingabe|Ergebnis|
|-----------|------------|
|Registerkarte|Verschiebt den Fokusindikator zwischen der logischen Reihenfolge der Objekte im Editor. Dies kann von links nach rechts oder von **TabIndex** oben nach unten sein, abhängig vom TabIndex-Eigenschaftswert (oder gleichwertigen Eigenschaftswert), der Reihenfolge der Objekterstellung und dem Gesamtzweck des Editors. Shift+Tab kehrt die Richtung des Fokusindikators um.|
|LEERTASTE|Aktiviert den Schwenkmodus, während der Tastenanschlag beibehalten wird. Zum Schwenken der Ansichtsfensterposition ist eine zusätzliche Mauseingabe erforderlich.|
|STRG+LEERTASTE|Aktiviert den Zoommodus, während der Tastenanschlag beibehalten wird. Zusätzliche Mauseingabe ist erforderlich, um den Zoomfaktor zu erhöhen und zu verringern.|
|Strg+Alt+Minus-Zeichen|Verringert den Zoomfaktor um eine Ebene.|
|Strg+Alt+Plus-Zeichen|Erhöht den Zoomfaktor um eine Ebene.|
|Shift ODER Strg|Fügt das Objekt der Auswahlgruppe hinzu. Mit Strg können Sie Objekte auch einzeln aus der Auswahlgruppe entfernen.|
|EINGABETASTE|Führt den Standardbefehl für das Objekt aus (normalerweise Öffnen oder Bearbeiten).|
|F2|Aktiviert die ortsspezifische Bearbeitung des Objekts.|
|Pfeiltasten|Verschiebt das ausgewählte Objekt(n) in Richtung der gedrückten Pfeiltaste in kleinen Schritten (z. B. 1 Pixel gleichzeitig)|
|Strg+Pfeiltasten|Verschiebt das ausgewählte Objekt(n) in Richtung der gedrückten Pfeiltaste in größeren Schritten (z. B. 10 Pixel gleichzeitig)|
|Shift+Pfeiltasten|Ändert die Größe der ausgewählten Objekte in der jeweiligen Richtung, in kleinen Schritten (z. B. 1 Pixel pro Wert)|
|Strg+Umschalt+Pfeiltasten|Ändert die Größe der ausgewählten Objekte in der jeweiligen Richtung, in größeren Schritten (z. B. 10 Pixel gleichzeitig)|

 Wenn Benutzer Steuerelemente an Ort und Stelle bearbeiten, kann es sinnvoll sein, dass Objekte die Größe automatisch mit Benutzereingaben ändern. Wenn der Benutzer z. B. ein Beschriftungssteuerelement benimmt, sollte die Beschriftung vergrößert werden, um den Text anzuzeigen, den der Benutzer gerade eingegeben hat. Wenn dies nicht geschieht, muss der Benutzer die Größe des Steuerelements manuell ändern, nachdem er den Text bearbeitet hat. Wenn der Benutzer über viele Steuerelemente verfügt, wird dies zu einer roten und unproduktiven Aufgabe.

#### <a name="graphical-containers"></a>Grafische Container
 In einigen Fällen stellen grafische Editoren Container für andere grafische Objekte bereit, z. B. das Windows Forms Panel-Steuerelement oder das Rasterlayout-Steuerelement im HTML-Designer. Wenn Ihr Editor Container für andere grafische Objekte bereitstellt, sollte das folgende Auswahlmodell nur für den Container verwendet werden (Objekte innerhalb des Containers folgen dem oben beschriebenen Standardmodell):

|Eingabe|Ergebnis|
|-----------|------------|
|Ein-Klick auf den Container|Wählt das Containerobjekt aus, ohne eines der enthaltenen Objekte direkt auszuwählen. Der Container kann mit Standard-Maus- und Tastatureingabe (wie oben beschrieben) verschoben und/oder in der Größe geändert werden. Enthaltene Objekte werden in Bezug auf den Container verschoben, enthaltene Objekte werden jedoch nur dann geändert, wenn sie direkt ausgewählt sind.|
|Bewegen Sie den Mauszeiger über den Grenzbereich des Containers|Schaltet die Maus in den Bewegungscursor, was darauf hinweist, dass der Container verschoben werden kann.|
|Ziehen sie den Begrenzungsbereich des Containers|Ändert die Maus auf den Bewegungscursor und verschiebt den Container (und die enthaltenen Objekte darin). Der Container kann nicht verschoben werden, ohne vorher mit einem einzigen Klick ausgewählt zu werden.|
|Ein-Klick auf ein Objekt im Container|Deaktiviert den Container (falls ausgewählt) und wählt nur das angeklickte Objekt aus.|
|Shift+Click OR Strg+Klicken Sie auf ein enthaltenes Objekt und/oder einen Container|Fügt das angeklickte Objekt einer vorhandenen Auswahl- oder Auswahlgruppe hinzu. Wenn das angeklickte Objekt bereits Mitglied der Auswahlgruppe ist, wird es aus der Auswahlgruppe entfernt.|

 Die enthaltenen Objekte sollten dem grundlegenden Auswahlmodell entsprechen, wie im vorherigen Abschnitt beschrieben. Von Usability-Tests des Windows Forms-Designers erwarteten Benutzer nahtlosen Zugriff auf die enthaltenen Objekte ohne dazwischen liegende Schritte (durch das Containment-Objekt auferlegt).

#### <a name="disjoint-and-region-selections"></a>Unzusammenhängende und Regionsauswahl
 Grafische Objekteditoren sollten getrennte Auswahlen unterstützen. Bitte beachten Sie, dass in dieser Grafik die Steuerelementdarstellung für Visual Studio nicht angezeigt wird. Detaillierte visuelle Spezifikationen finden Sie unter [Darstellung der grafischen Objektauswahl.](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance)

 ![Auswahl nicht zusammenhängender Bereiche und Regionen](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Unzusammenhängende Auswahl**

 Grafische Editoren sollten auch regionsspezifische Auswahlmiteinem tenat-Typ Auswahlindikator zur Verfügung stellen. Wenn der grafische Editor andere Objekttypen (z. B. Text) unterstützt, ist eine Bereichsauswahl je nach den Einschränkungen dieser anderen Objekttypen möglicherweise nicht möglich.

 ![Laufschriftauswahl](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Laufschriftauswahl**

#### <a name="primary-and-secondary-selections"></a>Primäre und sekundäre Auswahl
 Einige grafische Objekteditoren ermöglichen es dem Benutzer, Objekte in Gruppen zu bearbeiten oder auszurichten. In diesem Fall muss das Konzept der primären und sekundären Auswahl eingeführt werden. Die primäre Auswahl ist das Objekt, auf das alle anderen Objekte für Gruppenoperationen reagieren. Das Objekt, das der Benutzer zuerst auswählt, wird zum primären Steuerelement, und nachfolgende Auswahlen werden zur sekundären Auswahl. Die primäre Auswahl hat eine andere visuelle Behandlung von der sekundären Auswahl(en), um anzugeben, welches Objekt primär ist:

 ![Primär- und Sekundärauswahl](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Primäre Auswahl mit zwei sekundären Auswahlen**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Darstellung der grafischen Objektauswahl
 Bei den Auswahlgriffen handelt es sich um Quadrate, die in einem rechteckigen Muster um den Begrenzungsrahmen des Objekts gezeichnet werden. Das folgende Diagramm zeigt Beispiele für die verschiedenen Zustände, die ein grafisches Objekt mit Handle, Größe und direkter Bearbeitungsdarstellung haben kann. Die Größe der Handles sollte mithilfe der **GetSystemMetrics-API** an Fensterrahmen- und Edge-Metriken gebunden werden.

| State | Darstellung | Visuelle Details |
|-------------------------|---------------| - |
| **Nicht markiert** | Standard | ![Status der Standardschaltfläche](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Primäre Auswahl** | Resizable | ![Primäre Auswahl mit Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Primäre Auswahl** | Nicht beserbar | ![Primäre Auswahl ohne Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Primäre Auswahl** | Gesperrt | ![Primäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Sekundärauswahl** | Resizable | ![Sekundäre Auswahl mit Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Sekundärauswahl** | Nicht beserbar | ![Sekundäre Auswahl ohne Handles zum Ändern der Größe](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Sekundärauswahl** | Gesperrt | ![Sekundäre Auswahl gesperrt](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **UI aktiv** | Standard | ![Benutzeroberfläche im aktiven Status](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Auswahlmodelle anzeigen

#### <a name="tree-view"></a>Baumansicht
 Die Auswahl in einer Baumansicht wird mit einer einfachen Hervorhebung angezeigt. Wenn der Benutzer auf einen Knotennamen oder ein Knotensymbol klickt, wird der Knoten ausgewählt. Die dreieckigen Glyphen links vom Knoten erweitern oder vereinigen das Struktursteuerelement, wirken sich jedoch nicht auf die Auswahl des Benutzers aus, mit einer Ausnahme: Beim Reduzieren eines übergeordneten Knotens, wenn sich die Auswahl auf einem untergeordneten Element dieses Knotens befindet, wird die Auswahl zum übergeordneten Knoten verschoben.

 ![Typische Strukturansicht in Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Typische Strukturansicht in Visual Studio**

 Baumansichten können zusammenhängende und unzusammenhängende Auswahlen unterstützen, auch über mehrere Ebenen in der Struktur. Angrenzende oder unzusammenhängende Mehrfachauswahlen müssen auf sichtbaren Baumknoten vorgenommen werden. Wenn ein Knoten reduziert wird, geht die getrennte Auswahl verloren, und der knoten, der reduziert wurde, erhält die Auswahl. Auf diese Weise kann der Benutzer die Knoten sehen, die von einem Vorgang betroffen sind. Wenn Knoten reduziert werden, wird unklar, welche Knoten betroffen sein könnten.

 Wenn ein übergeordneter Knoten ausgewählt ist, sollte der Vorgang für das übergeordnete Element gelten, obwohl es Fälle geben kann, in denen es sinnvoll ist, dass ein Vorgang auf das übergeordnete Element und alle untergeordneten Elemente angewendet wird. Stellen Sie in diesem Fall während des Vorgangs eine zusätzliche Benutzeroberfläche bereit, z. B. ein Kontrollkästchen oder ein Bestätigungsdialogfeld, um die Option "Auf alle untergeordneten Elemente anwenden" für den Benutzer explizit zu machen.

##### <a name="renaming"></a>Umbenennen
 Wenn Knoten in der Struktur eine Umbenennung unterstützen, sollte die Umbenennung erfolgen. Der ortsbezogene Vorgang sollte der Standard für alle Struktursteuerelemente in Visual Studio sein. Geben Sie einen Umbenennungsbefehl an, der sofort den direkt stattfindenden Bearbeitungsmodus aktiviert, wobei die Textauswahl den gesamten Namen des Knotens abdeckt und Benutzereingaben akzeptieren kann. Wenn der Knoten eine Datei darstellt, sollte der Dateiname die Erweiterung enthalten. Die Auswahlhervorhebung sollte nur den Text des Dateinamens und nicht die Erweiterung enthalten.

|Eingabe|Ergebnis|
|-----------|------------|
|Eingabetaste|Verpflichtet den Umbenennungsvorgang|
|Esc-Schlüssel|Bricht den Umbenennungsvorgang ab|
|Klicken Außerhalb des direkt eingerichteten Bearbeitungsbereichs|Verpflichtet den Umbenennungsvorgang|
|Rückgängig|Einfaches Rückgängigmachen zum Abbrechen des Umbenennungsvorgangs|

#### <a name="selection-within-lists-and-grid-controls"></a>Auswahl innerhalb von Listen und Rastersteuerelementen
 Das Schlüsselkonzept bei der Listenauswahl ist, dass es zeilenbasiert ist, was bedeutet, dass, wenn eine Auswahl getroffen wird, die gesamte Zeile als Einheit ausgewählt wird. Im Gegensatz dazu können Raster die Auswahl bestimmter Zellen ermöglichen, ohne dass sich dies auf einen anderen Aspekt der Zeile auswirkt. Raster können auch eine Hierarchie von verschachtelten Zeilen (z. B. in einem TreeGrid) enthalten, die es ermöglichen, ganze Zweige der Hierarchie auszuwählen und zu deaktivieren, indem sie mit den übergeordneten Zeilen interagieren. Die Auswahl in Listen wird durch eine einfache Hervorhebungsfarbe in der gesamten Datenzeile angezeigt. Der Fokus wird durch einen gepunkteten Rahmen mit einem Pixel um die aktuelle bearbeitbare Zeile oder Zelle angezeigt (Zeile, wenn alle Zellen schreibgeschützt sind).

> [!NOTE]
> **Fokus** und **Auswahl** sind unterschiedliche Konzepte. *Focus* ist ein Hinweis darauf, welches UI-Element darauf abzielt, Eingaben zu empfangen, die nicht explizit auf ein anderes Objekt gerichtet sind, während die *Auswahl* auf den Zustand der Aufnahme eines Objekts in eine Gruppe von Objekten verweist, auf denen nachfolgende Vorgänge ausgeführt werden können.

 Auswahlen in Listen können zusammenhängend, unzusammenhängend oder region sein. Wenn mehrere Auswahlen zulässig sind, sollte die zusammenhängende und unzusammenhängende Auswahl immer unterstützt werden, während die Unterstützung für Bereichsauswahlen optional ist. Die Regionsauswahl wird durch Ziehen im Leerraum des Listentexts initiiert.

| Object | Auswahl |
|--------|------------|
| List | Zusammenhängenden |
| List | Dijunkt |
| List | Region |

 Wenn Sie einmal in einer Liste klicken, wird die Zeile ausgewählt, in der der Klick aufgetreten ist. Wenn der Benutzer zufällig in eine Listenzelle klickt, die die direkte Bearbeitung unterstützt, wird die Zelle auch sofort für die direkte Bearbeitung aktiviert. Andernfalls wird die gesamte Zeile sofort ausgewählt und zeigt eine Hervorhebung an.

 Das Ziehen im Listentext führt zu einem der drei Folgenden:

- Initiiert eine Regionsauswahl, wenn die Liste sie unterstützt und sich die Maus nach unten im Leerraum befindet

- Initiiert einen Drag/Drop-Vorgang, wenn die Listenzelle oder -zeile eine Ziehquelle unterstützt

- Wählt die aktuelle Zeile aus

##### <a name="in-place-editing"></a>In-Place-Bearbeitung
 Wenn die ortsspezifische Bearbeitung zulässig ist, gibt es zwei grundlegende Modelle: einfache Bearbeitungssteuerung und Eigenschaftenauswahl. Mit einem einfachen Bearbeitungssteuerelement wird der Inhalt hervorgehoben und bereit für Benutzereingaben, sobald die ortsgesteuerte Bearbeitung aktiviert ist. Wenn eine Eigenschaftsauswahl implementiert ist, wird die Schaltfläche, die die Eigenschaftenauswahl aufruft, angezeigt, sobald der direkt vorgenommene Bearbeitungsmodus aktiviert ist und die aktuelle Auswahl nicht hervorgehoben wird. Die Auswahltaste sollte in der Zelle rechtsbegründet sein. Beispiele für die ortsspezifische Bearbeitung finden Sie im **Eigenschaftenfenster** und in der **Aufgabenliste** in Visual Studio.

##### <a name="keyboard-support"></a>Tastaturunterstützung
 Die Tastaturunterstützung für die Auswahl in Listen und Rastern folgt den Windows-Standardkonventionen:

- Mit den Pfeiltasten navigieren Sie durch die Liste und wählen jede Zeile/Zelle aus, wenn der Fokus verschoben wird.

- Shift + Pfeil führt eine zusammenhängende Auswahl in Richtung der Pfeiltasten durch.

- Strg + Pfeil gefolgt von Leertaste schaltet zwischen dem Hinzufügen und Entfernen von Listenelementen aus der Auswahl um, wodurch eine getrennte Auswahl erstellt wird.

- Bei Rastern, die verschachtelte Hierarchien enthalten, wird mit der Rechten Pfeiltaste eine übergeordnete Zeile erweitert, und die linke Pfeiltaste reduziert eine.

- Die Tabulatortaste verschiebt den Fokus zwischen den Zellen in der aktuellen Zeile, wenn die Zellen bearbeitet werden können.

- Die Eingabetaste führt den Standardbefehl für das Element in der Liste aus (häufig **offen**).

- Die F2-Taste aktiviert die ortsspezifische Bearbeitung für die aktuell ausgewählte Zelle.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Persistenz- und Speichereinstellungen

### <a name="overview"></a>Übersicht
 Obwohl jede Softwarekomponente in Visual Studio in der Regel für ihren eigenen Status und ihre Persistenz verantwortlich ist, speichert Visual Studio in einigen Fällen automatisch Einstellungen, z. B. mit Fenstergrößen und Positionen. Die folgende Tabelle enthält eine Kombination aus automatisch gespeicherten Einstellungen und Einstellungen, die eine explizite Benutzer- oder programmierte Aktion erfordern.

|Object|Was zu sparen|Wann zu speichern|Wo zu sparen|
|------------|------------------|------------------|-------------------|
|Wählbares Objekt (z. B. eine Codezeile)|Ein Haltepunkt in einer Codezeile<br /><br /> Eine Benutzerverknüpfung, die der Codezeile zugeordnet ist|Wenn das Projekt gespeichert wird|Die **Datei "Benutzeroptionen" (.suo)** für das Projekt|
|Dialog|Die Position des Dialogs, wenn er verschoben wurde<br /><br /> Die Ansicht, die der Benutzer zuletzt im Dialogfeld verwendet hat|Wenn das Dialogfeld geschlossen wird<br /><br /> Wenn die Visual Studio-Sitzung endet|Im Gedächtnis<br /><br /> Registrierung in **HKEY_Current_User**|
|Fenster|Größe und Position des Fensters|Wenn das Fenster geschlossen wird<br /><br /> Wenn sich der Visual Studio-Modus ändert<br /><br /> Wenn die Visual Studio-Sitzung endet|Die **Datei "Benutzeroptionen" (.suo)** für das Projekt<br /><br /> Benutzerdefinierte Optionsdatei für Fenstereinstellungen|
|Dokument|Die aktuelle Auswahl im Dokument<br /><br /> Ansicht des Dokuments<br /><br /> Die letzten Orte, die der Benutzer besucht hat|Wenn das Dokument gespeichert wird|Die **Datei "Benutzeroptionen" (.suo)** für das Projekt|
|Project|Verweise auf Dateien<br /><br /> Verweise auf Verzeichnisse auf dem Datenträger<br /><br /> Verweise auf andere Software<br /><br /> Komponenten<br /><br /> Staatliche Informationen über das Projekt selbst|Wenn das Projekt gespeichert wird|Die Projektdatei.|
|Lösung|Verweise auf Projekte<br /><br /> Verweise auf Dateien|Wenn das Projekt oder die Projektmappe gespeichert wird|Die **Lösungsdatei (.sln)**|
|Einstellungen in **Tools > Optionen**|Tastaturanpassungen<br /><br /> Toolbar-Anpassungen<br /><br /> Farbschemata|Wenn das Dialogfeld **Tools > Options** geschlossen wird<br /><br /> Wenn die Visual Studio-Sitzung endet|Registrierung in **HKEY_Current_User**|

 Was der Benutzer tut und wann er es tut, bestimmt, ob eine Einstellung im Arbeitsspeicher gespeichert wird (während der Sitzung), auf dem Datenträger gespeichert (über Sitzungen als Registrierungseinstellung), als Teil der Projekt- oder Projektmappendatei selbst, als Teil der **Lösungsoptionendatei (.suo)** oder als benutzerdefinierte Einstellungsdatei, die nur diese Softwarekomponente kennt. Die obige Tabelle zeigt mehrere Ereignisse, bei denen Einstellungen gespeichert werden können. Es gibt jedoch andere Zeiten, in denen Sie den Status speichern möchten:

- Wenn der Benutzer den Speicherort in einem Dialogfeld oder Fenster ändert

- Wenn der Benutzer den Fokus auf ein anderes Fenster überträgt

- Wenn der Benutzer vom Entwurf in den Debugmodus wechselt

- Wenn sich der Benutzer von seinem Konto abmeldet

- Wenn der Computer in den Ruhezustand wechselt oder heruntergefahren wird

- Wenn der Computer/die Festplatte neu formatiert und neu eingerichtet wird

### <a name="window-configurations"></a>Fensterkonfigurationen
 Eine Fensterkonfiguration ist die grundlegende Darstellung der Entwicklungsumgebung - es ist ein Schema, das aus der Liste der vorhandenen Werkzeugfenster und der Art und Weise, wie sie angeordnet sind, besteht. Bei Fenstern, die von der IDE (IDE-Fenster) verwaltet werden, werden Layoutinformationen pro Benutzer beibehalten, sodass das Fensterlayout beim starten der IDE mit dem beim letzten Beenden von Visual Studio identisch ist. Der Status und die Position von IDE-Fenstern werden in einer benutzerdefinierten Optionsdatei im XML-Format beibehalten. Toolfenster, die von Paketen erstellt werden, die in die IDE geladen werden, verbleiben ihre Statusinformationen in der Registrierung und können pro Benutzer sein oder auch nicht.

#### <a name="profile-specific-layouts"></a>Profilspezifische Layouts
 Jedes Profil enthält Toolfensterlayouts, die in einer Weise organisiert sind, die bestimmten Entwickler-Personas vertraut ist (Visual C++-Entwickler erwarten, dass der **Projektmappen-Explorer** auf der linken Seite der IDE angezeigt wird, während c-Entwickler erwarten, dass der **Projektmappen-Explorer** auf der rechten Seite angezeigt wird). Profilspezifische Fensterlayouts werden geladen, nachdem der Benutzer beim Start ein Profil auswählt. Ein Paketautor sollte das Fensterlayout bestimmen, das für die Benutzererfahrung seiner Kunden am besten geeignet ist, da er weiß, dass Änderungen, die der Benutzer an der Fensterkonfiguration vornimmt, dann beibehalten werden.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>Touch-Eingang
 Benutzer verwenden zunehmend Microsoft-Entwicklungsprodukte auf Touch-Geräten. Es gibt jedoch Barrieren, die die Verwendung von Entwicklungstools auf Touch-Geräten erschweren. Die Anwender erwarten von unseren Produkten ein zuverlässiges und präzises Touch-Erlebnis. Diese Richtlinien sollen Entscheidungen darüber informieren, welche Touch-Funktionen integriert werden sollen, und eine konsistente Touch-Erfahrung in Visual Studio und verwandten Produkten fördern.

### <a name="levels-of-experience"></a>Erfahrungsstufen
 Die folgenden Erfahrungsstufen sollen als Leitfaden dienen, um Teams bei der Entscheidung zu unterstützen, welche Touch-Fähigkeiten auf der Grundlage ihres gewünschten Investitionsinteresses in Kontakt angeboten werden sollen.

- Die **grundlegende Erfahrung** ist für Teams, die Touch-Fähigkeiten bereitstellen möchten, so dass es keine Sackgassen während ihrer Arbeit gibt.

- Die **optimierte Erfahrung** ist für Teams, die die gängigsten Touch-Funktionen bereitstellen möchten (z. B. die in der Regel in Internetbrowseranwendungen verfügbaren).

- Die **erhöhte Erfahrung** ist für Teams, die Funktionen wie Gesten oder andere optionale Funktionen hinzufügen möchten, die ihre Anwendung touch-first freundlich machen können.

||Grundlegende Erfahrung|Optimierte Erfahrung|Erhöhte Erfahrung|
|-|----------------------|--------------------------|-------------------------|
|Ermöglicht es Benutzern, ...|Fixcode und Lösungs-/Projektebene-Lesung ohne Sackgassen|Durchführen von Wartungs-, Refaktoren- und Navigationsaufgaben|Arbeiten Sie in einer konsistenten, intuitiven und flüssigen Erfahrung mit Vertrauen|
|Editor|Touch-Schwenken und Auswählen<br /><br /> Scrollbar-Touch zum Springen und Drücken+Ziehen|Pinch-Zoom<br /><br /> Schneller Scroll<br /><br /> Auswahl<br /><br /> Einfache Verwendung des Kontextmenüs||
|Top-Werkzeugfenster|Listenschwenken<br /><br /> Elementauswahl<br /><br /> Scrollbar-Touch zum Springen und Drücken+Ziehen|Einfaches Scrollen und Auswählen von Gegenständen||
|Windowing||Fenster "Größe ändern"<br /><br /> Schnellzugriff||
|Dokument gut||Einfache Navigation zwischen geöffneten Dateien||
|Gesten||Sicherstellen, dass allgemeine Gesten in der gesamten IDE funktionieren|Gestenbasierte Aktionen<br /><br /> Unterstützung Drag-and-Drop und Designer|
|Weitere Überlegungen|||Benutzerdefinierte Bildschirmtastatur|

#### <a name="gestures"></a>Gesten
 Gesten bieten Benutzern eine Verknüpfung zu Befehlen, die andernfalls eine kompliziertere Interaktion erfordern könnten. Lesen Sie die Windows-Richtlinien zu [allgemeinen Touchgesten für Desktopanwendungen](/windows/desktop/wintouch/windows-touch-gestures-overview), und befolgen Sie diese Anleitung für die meisten Gesten, einschließlich einfacher Gesten wie Schwenken und Zoomen.
