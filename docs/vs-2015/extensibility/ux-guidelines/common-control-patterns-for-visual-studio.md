---
title: Allgemeine Steuerelementmuster
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 246464baea7e07e4d97e3483b423d200cf2b960c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430043"
---
# <a name="common-control-patterns-for-visual-studio"></a>Allgemeine Steuerelementmuster für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_CommonControls"></a> Allgemeine Steuerelemente

### <a name="overview"></a>Übersicht
 Allgemeine Steuerelemente bilden zusammen den Großteil der Benutzeroberfläche in Visual Studio. Führen Sie die am häufigsten verwendeten Steuerelemente in Visual Studio-Benutzeroberfläche verwendet sollte die [Richtlinien für Windows Desktop-Interaktion](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). In diesem Dokument bezieht sich auf Visual Studio und behandelt Situationen oder Details, die die Windows-Richtlinien zu verbessern.

#### <a name="common-controls-in-this-topic"></a>Allgemeine Steuerelemente in diesem Thema

- [Scrollbars](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Felder für die Eingabe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Kombinationsfelder und Dropdown-Listen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Kontrollkästchen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Optionsfelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Gruppe frames](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Schaltflächen und Links](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Strukturansichten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Visuellen Stil
 Die erste, was beim Formatieren von Steuerelementen zu berücksichtigen ist, gibt an, ob die Steuerelemente im Design der Benutzeroberfläche verwendet werden. Steuerelemente in Benutzeroberflächen-Design-Benutzeroberfläche werden und müssen [Schriftschnitt "normal" Windows-Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), was bedeutet, dass sie nicht erneut auf und sollte in ihrer standarddarstellung des Steuerelements angezeigt werden.

- **Standard (Hilfsprogramm) Dialogfelder:** nicht mit Design. Führen Sie keine erneute-Vorlage. Die verwenden Sie grundlegende Steuerelement Style-Standardeinstellungen.

- **Toolfenster, Dokument-Editoren, Entwurfsoberflächen und mit Design Dialogfelder:** Verwenden Sie spezielle Design Darstellung, die mit dem Dienst für die Farbe an.

### <a name="BKMK_Scrollbars"></a> Scrollleisten
 Bildlaufleisten sollte folgen [allgemeine Interaktionsmuster für Windows-Bildlaufleisten](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) , wenn sie mit Informationen zum Inhalt, z. B. im Code-Editor ergänzt werden.

### <a name="BKMK_InputFields"></a> Felder für die Eingabe
 Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für die Textfelder](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visuellen Stil

- Felder sollten nicht im Hilfsprogramm-Dialogfelder formatiert werden. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.

- Design Eingabefelder sollte nur in Design Dialog- und Toolfenster verwendet werden.

#### <a name="specialized-interactions"></a>Spezielle Interaktionen

- Schreibgeschützte Felder müssen einen Hintergrund grau (deaktiviert), aber Standardvordergrund-(aktiv).

- Erforderliche Felder müssen  **\<erforderlichen >** als Wasserzeichen darin. Sie sollten die Farbe des Hintergrunds außer in seltenen Fällen nicht ändern.

- Fehler-Überprüfung: Finden Sie unter [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Größe Eingabefelder müssen entsprechend den Inhalt, der nicht auf die Breite des Fensters in der sie angezeigt werden, noch die Zeitdauer in einem langen Feld, z. B. einen Pfad nach dem Zufallsprinzip entsprechend angepasst werden. Länge kann darauf hinweisen, dass für den Benutzer Einschränkungen hinsichtlich der Anzahl der Zeichen in das Feld zulässig sind.

     ![Breite des Steuerelements falsche Eingabefeld](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl") **falsche Eingabe Feldlänge: Es ist unwahrscheinlich, dass der Name dieser Länge ist.**

     ![Korrigieren Sie die Breite für Eingabefeld-Steuerelement](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl") **richtig Eingabe der Feldlänge: Das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.**

### <a name="BKMK_ComboBoxesAndDropDowns"></a> Kombinationsfelder und Dropdown-Listen
 Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für Dropdownlisten und Kombinationsfelder](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visuellen Stil

- Dienstprogramm-Dialogfeldern verwenden Sie nicht Re-Vorlage des Steuerelements. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.

- Führen Sie die standard-Designs für Steuerelemente, in Design-Benutzeroberfläche, Kombinationsfelder und Dropdown-Elemente.

#### <a name="layout"></a>Layout
 Kombinationsfelder und Dropdownlisten sollte Größe angepasst werden, um den Inhalt nicht auf die Breite des Fensters in der sie angezeigt werden, noch die Zeitdauer in einem langen Feld, z. B. einen Pfad nach dem Zufallsprinzip entsprechend anpassen.

 ![Falsche Drop&#45;unten Layout](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")

 **Falsche Feldlänge für ein Dropdown-Steuerelement**

 ![Richtige Drop&#45;unten Layout](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707-04_CorrectDropDownLayout")

 **Richtige Feldlänge für ein Dropdown-Steuerelement**

### <a name="BKMK_CheckBoxes"></a> Kontrollkästchen
 Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für Kontrollkästchen](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visuellen Stil

- Dienstprogramm-Dialogfeldern verwenden Sie nicht Re-Vorlage des Steuerelements. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.

- Design-Benutzeroberfläche führen Sie die Kontrollkästchen der standard-Designs für Steuerelemente.

#### <a name="specialized-interactions"></a>Spezielle Interaktionen

- Interaktion mit einem Kontrollkästchen muss nie ein Dialogfeld angezeigt, oder navigieren Sie zu einem anderen Bereich.

- Richten Sie die Kontrollkästchen mit der Baseline der ersten Zeile des Texts.

     ![Ausrichtung für falschen Kontrollkästchen](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign") **Ausrichtung für falschen Kontrollkästchen: Aktivieren Sie das Kontrollkästchen wird auf der Text zentriert.**

     ![Korrigieren Sie die Ausrichtung für Kontrollkästchen](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign") **Ausrichtung für Kontrollkästchen zu beheben: Aktivieren Sie das Kontrollkästchen wird die Grundlinie der ersten Textzeile ausgerichtet.**

### <a name="BKMK_RadioButtons"></a> Optionsfelder
 Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für die Optionsfelder](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visuellen Stil
 Führen Sie im Hilfsprogramm-Dialogfeldern nicht Stil Optionsfelder aus. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.

#### <a name="specialized-interactions"></a>Spezielle Interaktionen
 Es ist nicht erforderlich, einen Gruppen Frame zum Einschließen von Optionsfeld-Optionen zu verwenden.

### <a name="BKMK_GroupFrames"></a> Gruppe frames
 Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für die Gruppe Frames](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visuellen Stil
 Führen Sie im Hilfsprogramm-Dialogfeldern nicht Stil Gruppe Frames. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.

#### <a name="layout"></a>Layout

- Es ist nicht erforderlich, einen Gruppen Frame zu verwenden, zum Einschließen von Optionsfeld-Optionen, es sei denn, die Unterscheidung der Gruppe in einem engen Layout beibehalten werden sollen.

- Verwenden Sie niemals einen Gruppenrahmen für ein einzelnes Steuerelement an.

- Manchmal ist es akzeptabel, eine horizontale Trennlinie statt Gruppen Frame-Container zu verwenden.

## <a name="BKMK_TextControls"></a> Textsteuerelemente

### <a name="labels"></a>Bezeichnungen

#### <a name="active-label-state"></a>Status der aktiven Beschriftung

##### <a name="utility-standard-dialogs"></a>Dialogfelder für Utility (standard))

- Im Allgemeinen führen Sie den Windows-Desktop-Leitfaden für Bezeichnungen aus.

- Im Hilfsprogramm-Dialogfeldern sollten Bezeichnungen nicht fett, in der standardumgebung Schriftart und Farbe angezeigt. Finden Sie unter [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Ellipsen sollte immer Bezeichnungen folgen.

##### <a name="signature-themed-dialogs"></a>Signatur (Design) Dialogfelder)
 Label-Steuerelemente möglicherweise fett oder hellgrau.

#### <a name="disabled-label-state"></a>Deaktivierte Bezeichnung-Status
 Bezeichnungen sollte es sich um die Darstellung des Steuerelements entsprechen, die, denen Sie zugeordnet sind. Z. B. wenn das zugeordnete Steuerelement deaktiviert ist, sollte Sie dann die Bezeichnung zu ausgrauen und deaktiviert angezeigt werden. Dies erfolgt normalerweise durch das Betriebssystem und erfordert keine besondere Behandlung.

#### <a name="dynamic-labels"></a>Dynamische Bezeichnungen
 Dynamische Bezeichnungen ändern sich abhängig von der aktuellen Auswahl. Verwenden Sie nach Möglichkeit dynamische Bezeichnungen in Master/Detail-Layouts, um Sie besser verstehen, dass die angezeigte Informationen für eine bestimmte Auswahl und nicht allgemeine Informationen relevant ist.

 ![Dynamische Beschriftung mit dynamischen Inhalten](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702-01_DynamicLabel")

 **Beispiel für eine dynamische Beschriftung mit dynamischen Inhalten**

#### <a name="instructional-text"></a>Hinweistext
 Einige Elemente der Benutzeroberfläche profitieren von Anweisungstext, um den Benutzer, der den UI-Zweck zu verstehen oder die auszuführende Aktion an.

- Anweisungstext ist am häufigsten verwendeten am oberen Rand der Dialogfelder, aber in anderen Bereichen, geben Sie die Anweisung, um ein komplexes Steuerelement Gruppierung angezeigt werden kann.

- Anweisungstext ist nicht interaktiv, aber Sie können Softwareupdates enthalten Hyperlinks zu Hilfethemen.

- Verwenden von Anweisungstext nur sparsam und nur bei Bedarf.

##### <a name="formatting"></a>Formatierung
 Anweisungstext sollte Umgebungsschriftart, standard (nicht-Design) Steuerelementtext. Finden Sie unter [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Weitere Informationen zum Schreiben von Anweisungstext finden Sie unter [UI Text und die Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Formatierung von Anweisungstext](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Hinweistext in einem Visual Studio-Dialogfeld**

#### <a name="informational-text"></a>Informationstext
 Informationstext ist Text, der die Benutzer zusätzliche Informationen zu erhalten. Sie können statische oder dynamische oder als eine Benachrichtigung verwendet werden. Es ist immer schreibgeschützt, aber ist es nützlich sein, damit der Benutzer die Möglichkeit haben, kopieren Sie die Informationen, muss dynamischer Text in einem Steuerelementcontainer, z. B. ein nur-Lese Textfeld platziert werden.

##### <a name="dynamic-context-specific-text"></a>Text der dynamischen (Kontext-spezifisch)
 Dynamischer Informationstext ändert sich je nach Kontext, z. B. wenn der Benutzer den Fokus wechselt. Oft, jedoch nicht immer, dynamischer Inhalt eine dynamische Bezeichnung zugeordnet ist.

 ![Dynamischer Informationstext](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702-03_InformationalDynamicText")

 **Dynamischer Informationstext ändert sich je nach Kontext.**

##### <a name="formatting"></a>Formatierung
 Es gibt zwei Möglichkeiten zum Anzeigen von schreibgeschützten Textfeldern: entweder direkt auf der Benutzeroberfläche Oberfläche (siehe oben) oder in ein anderes Steuerelement, z. B. eine Gruppe Frame oder das Textfeld enthalten sind. Entweder ist je nach Situation korrekt. Es ist Aufgabe der Funktions-Designer, um zu bestimmen, wie Sie die schreibgeschützte Informationen zu präsentieren.

 Text kann in einem schreibgeschützten Textfeld sein. Dies gibt im Allgemeinen, dass der Inhalt kopiert, und ausgewählt werden kann, obwohl es nicht bearbeitet werden kann.

 ![Zum Lesen Formatierung von Informationstext&#45;nur Felder](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702-04_InformationalFormatting")

 **Für schreibgeschützte Felder Formatierung von Informationstext**

#### <a name="watermarks"></a>Wasserzeichen
 Während die Formulierung identisch sein kann, ist der Unterschied zwischen Wasserzeichen und Anweisungstext an, dass es sich bei Wasserzeichen mit Inhalt ersetzt werden, wenn das Steuerelement/Fenster nicht leer ist und Anweisungstext bleibt sichtbar zu jeder Zeit.

 Wasserzeichen sollte verwendet werden, wenn ein Fenster oder das Steuerelement leer ist. Sie geben, was muss ausgeführt werden, um den Bereich zu füllen und herausgeberkontos ausgewiesenen Form Aktionslinks, um relevante Fenster, z. B. eine Ziehquelle zu öffnen.

##### <a name="visual-style"></a>Visuellen Stil

- Wasserzeichen sollte im Fenster horizontal zentriert werden soll.

- Wasserzeichen sollte zentriert ausgerichtet, nicht linksbündig ausgerichtet.

- Wasserzeichen können vertikal zentriert oder im oberen Bereich des Bereichs positioniert werden. Wenn im oberen Bereich des Bereichs befindet, muss genügend Speicherplatz sein vorhanden oben, damit das Wasserzeichen abhebt.

- Verwenden der `Environment.GrayText` token "und" standard Umgebungsschriftart Farbe. Links sollten die standardmäßigen freigegebenen Link-Token verwenden: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, und `Environment.PanelHyperlinkDisabled`.

- Wasserzeichen können im Hintergrund nicht ausgewählt werden

- Falls möglich, sollten Sie Links in der Grenzwert auf die Benutzer beginnen können.

  ![Wasserzeichen von Text in einem Designer-Fenster](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702-05_Watermark1")

  ![Wasserzeichen von Text in einem Toolfenster](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702-06_Watermark2")

  **Beispiele für Wasserzeichentext in Visual Studio**

## <a name="BKMK_ButtonsAndHyperlinks"></a> Schaltflächen und Links

### <a name="overview"></a>Übersicht
 Führen Sie die Schaltflächen und Link-Steuerelemente (links) sollten [grundlegende Windows-Desktop-Hinweise zu Links](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) für die Nutzung formulierungen, Skalierung und Abstand.

### <a name="choosing-between-buttons-and-links"></a>Auswählen zwischen Schaltflächen und links
 In der Vergangenheit wurden Schaltflächen für Aktionen verwendet, und Links für die Navigation reserviert wurde. Schaltflächen können in allen Fällen verwendet werden, aber die Rolle des Links wurde in Visual Studio erweitert, damit Schaltflächen und Links unter bestimmten Umständen mehr austauschbar sind.

 Wann sollte die Befehlsschaltflächen verwenden?

- Primären Befehle

- Anzeigen von Windows verwendet, um Eingaben zu erfassen oder Entscheidungen, auch wenn sie sekundäre Befehle

- Destruktive oder Rückgängig-Aktionen

- Engagement-Schaltflächen im Assistenten und Seite-flows

  Vermeiden Sie die Schaltflächen im Toolfenster, oder wenn Sie mehr als zwei Wörter für die Bezeichnung benötigen. Links können längere Beschriftungen haben.

  Wann sollte die Links zu verwenden?

- Navigation zu einem anderen Fenster, ein Dokument oder eine Webseite

- Situationen, in denen eine längere Bezeichnung oder einen kurzen Satz zum Beschreiben der Zweck der jeweiligen Aktion erforderlich.

- Raum, in denen eine Schaltfläche die Benutzeroberfläche überlasten würden, vorausgesetzt, dass die Aktion nicht destruktive oder nicht umkehrbar ist

- Aufhebung Hervorhebungseffekt sekundäre Befehle in Situationen mit zahlreichen Befehlen

#### <a name="examples"></a>Beispiele
 ![Links für infoleistenbefehle nach Statusmeldung](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703-01_CommandLinkInfobar")

 **-Befehl verwendet wird, in der Statusmeldung Infoleiste links**

 ![Links im CodeLens-Popup](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703-02_LinksInCodeLens")

 **Links im CodeLens-popup**

 ![Links als sekundäre Befehle](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")

 **Links, die für sekundäre Befehle Schaltflächen würden, in denen zu viel Aufmerksamkeit gewinnen.**

### <a name="common-buttons"></a>Allgemeine Schaltflächen

#### <a name="text"></a>Text
 Führen Sie die Richtlinien für das Schreiben in [UI Text und die Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Visuellen Stil

##### <a name="standard-dialogs"></a>Standard-Dialogfelder
 Die meisten Schaltflächen in Visual Studio werden in Standarddialogfelder angezeigt und sollte nicht formatiert werden. Sie sollten die standard-Darstellung der Schaltflächen widerspiegeln, wie vom Betriebssystem vorgegebenen.

##### <a name="themed"></a>Design
 In einigen Fällen in der formatierten UI können Schaltflächen verwendet werden, und diese Schaltflächen müssen ordnungsgemäß formatiert werden. Finden Sie unter [Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) Informationen zu Design-Steuerelementen.

### <a name="special-buttons"></a>Besondere Schaltflächen

#### <a name="browse-buttons"></a>Suchen... Schaltflächen
 **[Durchsuchen...]**  Schaltflächen werden im Raster, Dialogfelder und Toolfenster und andere Elemente der Benutzeroberfläche für das nicht modale verwendet. Sie zeigen eine Auswahl, die den Benutzer beim Ausfüllen der eines Werts in ein Steuerelement hilft. Es gibt zwei Varianten dieser Schaltfläche, lange und kurze.

 ![Long &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703-04_BrowseLong")

 **Die lange Schaltfläche [durchsuchen...]**

 ![Kurze Schaltfläche&#45;nur &#91;durchsuchen... &#93; Schaltfläche](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703-05_BrowseShort")

 **Die Schaltfläche mit den Auslassungspunkten nur kurze [...]**

 Wenn die kurze nur mit den Auslassungszeichen-Schaltfläche verwenden:

- Wenn es mehr als eine lange **[durchsuchen...]**  Schaltfläche in einem Dialogfeld an, wie z. B., wenn mehrere Felder für das Durchsuchen von zulässt. Verwenden Sie die kurzfristige **[...]**  klicken, die verwirrend Zugriffsschlüssel erstellt diese Situation zu vermeiden (**& Durchsuchen** und **du & rchsuchen** im gleichen Dialogfeld "").

- In einem engen Dialogfeld, oder wenn besteht keine angemessene Möglichkeit, auf die Schaltfläche "lange" abgelegt.

- Wenn die Schaltfläche in einem Datenraster-Steuerelement angezeigt wird.

  Richtlinien für die mithilfe der Schaltfläche:

- Verwenden Sie keinen Zugriffsschlüssel. Mithilfe der Tastaturfokus für den Zugriff auf muss der Benutzer aus dem angrenzenden Steuerelement Registerkarte. Stellen Sie sicher, dass die Aktivierreihenfolge ist, dass Schaltfläche "Durchsuchen" sofort nach dem Feld liegt, die sie eingeben wird. Verwenden Sie niemals einen Unterstrich, unter dem ersten Zeitraum.

- Legen Sie die Microsoft Active Accessibility (MSAA) **Namen** Eigenschaft **durchsuchen...**  (einschließlich der drei Punkte) damit, die Bildschirm Leser liest es als "Durchsuchen" und nicht "Punkt-Punkt-Punkt" oder "Punkt-Punkt-Punkt." Für verwaltete Steuerelemente, bedeutet dies die Einstellung der **Control.AccessibleName** Eigenschaft.

- Verwenden Sie niemals ein Auslassungszeichen **[...]**  Schaltfläche für alle Elemente mit Ausnahme von einer Aktion "Durchsuchen". Angenommen, Sie müssen eine **[Neu]**  Schaltfläche aber nicht ausreichend Platz für den Text ein, und klicken Sie dann das Dialogfeld muss geändert werden.

##### <a name="sizing-and-spacing"></a>Größenanpassung und Abstand
 ![Ändern der Größe &#91;durchsuchen... &#93; Schaltflächen](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703-06_BrowseSizing")

 **Größe der Schaltfläche [durchsuchen...]**

 ![Der Abstand &#91;durchsuchen... &#93; Schaltflächen](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703-07_BrowseSpacing")

 **Abstand der Schaltfläche [durchsuchen...]**

#### <a name="graphical-buttons"></a>Grafische Schaltflächen
 Einige Schaltflächen sollten immer ein Bild und nie enthalten Text zum Einsparen von Speicherplatz und Lokalisierung-Probleme zu vermeiden. Diese werden häufig in Feld dateiöffnungs- und andere sortierbaren Listen verwendet.

> [!NOTE]
> Benutzer müssen diese Schaltflächen (es gibt keine Zugriffsschlüssel) die Registerkarte, daher platzieren Sie sie in einer sinnvollen Reihenfolge. Ordnen Sie die Name-Eigenschaft der Schaltfläche, um die Aktion, die es dauert, sodass Bildschirmsprachausgaben richtig Schaltflächenaktion interpretiert.

|||
|-|-|
|Hinzufügen|![Grafische Schaltfläche "hinzufügen"](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|Remove|![Grafische Schaltfläche "Entfernen",](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|Alle hinzufügen|![Grafische "Schaltfläche"Alles hinzufügen](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703-10_ButtonAddAll")|
|Entfernen Sie alle|![Grafische "Schaltfläche"Alle entfernen](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|Nach oben|![Grafische Schaltfläche "Nach oben"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703-12_ButtonMoveUp")|
|Nach unten|![Grafische Schaltfläche "Nach unten"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703-13_ButtonMoveDown")|
|Löschen|![Grafische Schaltfläche "Löschen",](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Größenanpassung und Abstand
 Ändern der Größe für grafische Schaltflächen, die identisch mit der Kurzversion des ist der **[durchsuchen...]**  Schaltfläche (26 x 23 Pixel):

 ![Schaltfläche mit und ohne transparenter Farbe](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")

 **Darstellung der ein Bild auf die Schaltfläche mit und ohne transparenter Farbe**

### <a name="hyperlinks"></a>Hyperlinks
 Hyperlinks eignen sich gut für die Navigation-basierten Aktionen, z. B. Öffnen eines Hilfethemas, modales Dialogfeld, oder -Assistenten. Wenn ein Link für einen Befehl verwendet wird, sollten sie immer eine sichtbare und merkliche Änderung an der Benutzeroberfläche anzeigen. Aktionen, die auf eine Aktion (z. B. speichern, auf "Abbrechen", und löschen) werden im Allgemeinen besser kommuniziert mithilfe einer Schaltfläche.

#### <a name="writing-style"></a>Schreibstil
 Führen Sie die [Windows-Desktop-Leitfaden für den Text der Benutzeroberfläche](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). Verwenden Sie nicht "Erfahren Sie mehr über," "Erzählen mir Weitere Informationen zu" oder "Get-Help dabei"-Ausdruck. Stattdessen einen Ausdruck Link Hilfetext in Bezug auf die primäre Frage beantwortet, indem der Inhalt der Hilfe. Z. B. "**wie füge ich einen Server zum Server-Explorer?**"

#### <a name="visual-style"></a>Visuellen Stil

- Links sollten immer verwenden [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Wenn Sie ein Link nicht richtig formatiert wird, blinkt Rot, wenn aktive oder eine andere Farbe angezeigt, nachdem der aufgerufen wird.

- Fügen Sie keine unterstreichungen am Zustand gespeichert, es sei denn, der Link ein Satz Fragment innerhalb eines vollständigen Satzes an, wie z. B. in einem Wasserzeichen ist-Steuerelement.

- Unterstreichungen nicht bei einer mauszeigerbewegung über angezeigt werden soll. Stattdessen wird das Feedback für den Benutzer, dass die Verbindung aktiv ist eine geringfügige Farbe ändern und den entsprechenden Link-Cursor.

## <a name="BKMK_TreeViews"></a> Strukturansichten

### <a name="overview"></a>Übersicht
 Strukturansichten bieten eine Möglichkeit zum Organisieren von komplexen in übergeordneten / untergeordneten Gruppen aufgeführt. Ein Benutzer kann erweitern oder reduzieren die übergeordnete Gruppen zum Anzeigen oder Ausblenden von zugrunde liegenden untergeordneten Elemente. Jedes Element in einer Strukturansicht kann ausgewählt werden, um weitere Aktion bereitzustellen.

 Dieses Thema behandelt die akzeptable Nutzung, richtig zu entwerfen und Funktionalität von Strukturansichten.

#### <a name="in-this-topic"></a>In diesem Thema

- [Visuellen Stil](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interaktionen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="BKMK_TreeViewVisualStyle"></a> Visuellen Stil

#### <a name="expanders"></a>Erweiterungen
 Strukturansicht-Steuerelemente müssen auf die Expander-Steuerelement von Windows und Visual Studio verwendet werden, entsprechen. Ein Expander-Steuerelement wird von jedem Knoten verwendet, um ein- oder Ausblenden von zugrunde liegenden Elementen. Verwenden eines Expander-Steuerelements ist die Konsistenz für Benutzer, die verschiedenen Ansichten in Windows und Visual Studio auftreten können.

 ![Korrigieren Sie die Strukturansicht-Steuerelement](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Richtig: ordnungsgemäßes Format Strukturansichtsknotens mithilfe eines Expander-Steuerelements**

 ![Falsche Strukturansichtsknoten](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705-2_TreeViewIncorrect1")

 **Falsche: falsche Darstellung Strukturansichtsknoten**

#### <a name="selection"></a>Auswahl
 Wenn ein Knoten in der Strukturansicht ausgewählt ist, sollten die Hervorhebung um die gesamte Breite des Strukturansicht-Steuerelement erweitern. Dadurch können Benutzer, die eindeutig auf welches Element identifizieren sie ausgewählt haben. Farben Auswahl sollte es sich um das aktuelle Visual Studio-Design entsprechen.

 ![Korrigieren Sie die Strukturansicht-Steuerelement](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Richtig: Hervorheben des ausgewählten Knotens passt die gesamte Breite des Strukturansicht-Steuerelement.**

 ![Falsche Hervorhebung für Strukturansicht](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705-3_TreeViewIncorrect2")

 **Falsche: Hervorheben des ausgewählten Knotens passt nicht die gesamte Breite des Strukturansicht-Steuerelement.**

#### <a name="icons"></a>Symbole
 Symbole sollte nur in der Strukturansicht-Steuerelemente verwendet werden, wenn sie bei der Unterschiede zwischen Elementen visuell zu identifizieren. Symbole sollten im Allgemeinen nur in heterogenen Listen verwendet werden in denen die Symbole Informationen zur Unterscheidung von den Typ der Elemente enthalten. In einer homogenen Liste mithilfe von Symbolen kann häufig als Rauschen betrachtet werden und sollte vermieden werden. In diesem Fall kann das Symbol für die Gruppe (übergeordnet) den Typ der Elemente im vermitteln. Die Ausnahme von dieser Regel wäre, wenn das Symbol dynamisch ist und verwendet wird, um den Status anzugeben.

#### <a name="scroll-bars"></a>Bildlaufleisten
 Bildlaufleisten soll immer ausgeblendet werden, wenn der Inhalt in der Strukturansicht-Steuerelement passt. Es ist ausgeblendet oder semitransparente in einem bildlauffähigen Fenster und angezeigt werden, wenn das Fenster mit der Strukturansicht den Fokus besitzt, oder bei einer mauszeigerbewegung über die der Struktur anzeigen, selbst für Bildlaufleisten zulässig.

 ![Strukturansicht mit Bildlaufleisten](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705-4_Scrollbars")

 **Da der Inhalt die Grenzen des Strukturansicht-Steuerelement überschritten haben, werden beide vertikalen und horizontalen Bildlaufleisten angezeigt.**

### <a name="BKMK_TreeViewInteractions"></a> Interaktionen

#### <a name="context-menus"></a>Kontextmenüs
 Knoten einer Strukturansicht kann es sich um die Optionen des Untermenüs in einem Kontextmenü offenlegen. Das tritt in der Regel auf, wenn ein Benutzer ein Element mit der rechten Maustaste, oder drücken die Menütaste auf einer Windows-Tastatur mit das ausgewählte Element. Es ist wichtig, dass der Knoten den Fokus erhält, und aktiviert ist. Dadurch wird den Benutzer, welches Element identifizieren das Untermenü, angehört.

 ![Ausgewählte strukturmenü Kontextmenü](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705-5_ContextMenu")

 **Das Element, das dem Kontext-Menü Gewinne Fokus zur Benachrichtigung des Benutzers welches Element generiert hat wurde ausgewählt.**

#### <a name="keyboard"></a>Tastatur
 Die Strukturansicht sollte die Möglichkeit bieten, wählen Sie Elemente, und Erweitern/Reduzieren von Knoten, die mithilfe der Tastatur. Dadurch wird sichergestellt, dass Navigation unsere Anforderungen zur Barrierefreiheit erfüllt.

##### <a name="tree-view-control"></a>Strukturansicht-Steuerelement
 Visual Studio-Struktur-Steuerelemente sollten allgemeine Tastaturnavigation ausführen:

- **Pfeil nach oben:** Wählen Sie Elemente aus, indem Sie der Struktur nach oben verschieben

- **Pfeil nach unten:** Wählen Sie Elemente aus, indem Sie in der Struktur nach unten verschieben

- **Pfeil nach rechts:** Erweitern Sie den Knoten in der Struktur

- **Pfeil nach links:** Reduzieren eines Knotens in der Struktur

- **Geben Sie Schlüssel aus:** Initiieren, laden, das ausgewählte Element ausführen

##### <a name="trid-tree-view-and-grid-view"></a>Trid (Strukturansicht und Rasteransicht)
 Ein Rastersteuerelement ist ein komplexes Steuerelement enthält eine Strukturansicht, in einem Raster an. Erweitern reduzieren, und Navigieren durch die Struktur sollte die gleichen Tastenkombinationen Befehle als eine Strukturansicht mit den folgenden Ergänzungen beachten:

- **Pfeil nach rechts:** Erweitern Sie den Knoten aus. Nachdem der Knoten erweitert ist, soll er weiterhin auf die nächste Spalte auf der rechten Seite navigieren. Navigation sollte am Ende der Zeile zu beenden.

- **Tab:** Wechselt zur nächsten Zelle auf der rechten Seite.  Am Ende der Zeile wird Sie Navigation zur nächsten Zeile fortgesetzt.

- **Umschalt + Tab:** Wechselt zur nächsten Zelle auf der linken Seite.  Navigation weiterhin am Anfang der Zeile, aus der äußersten rechten Zelle in der vorherigen Zeile.

  ![Rastersteuerelement in Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705-6_Trid")

  **Ein Rastersteuerelement in Visual Studio**
