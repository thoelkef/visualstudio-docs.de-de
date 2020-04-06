---
title: Allgemeine Steuerelementmuster für Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698716"
---
# <a name="common-control-patterns-for-visual-studio"></a>Allgemeine Steuerelementmuster für Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Gemeinsame Kontrollen

### <a name="overview"></a>Übersicht
Allgemeine Steuerelemente machen den Großteil der Benutzeroberfläche in Visual Studio aus. Die gängigsten Steuerelemente, die in der Visual Studio-Benutzeroberfläche verwendet werden, sollten den [Windows Desktop-Interaktionsrichtlinien](/windows/desktop/uxguide/controls)folgen. Dieses Thema ist spezifisch für Visual Studio und behandelt spezielle Situationen oder Details, die diese Windows-Richtlinien erweitern.

#### <a name="common-controls-in-this-topic"></a>Allgemeine Steuerelemente in diesem Thema

- [Scrollleisten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Eingabefelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Combo-Boxen und Dropdown-Listen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Kontrollkästchen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Optionsfelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Gruppenrahmen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Schaltflächen und Hyperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Strukturansichten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Visueller Stil
Beim Styling von Steuerelementen ist zunächst zu berücksichtigen, ob die Steuerelemente in der thematischen Benutzeroberfläche verwendet werden. Steuerelemente in der Standardbenutzeroberfläche sind nicht thematisch benutzeroberfläche und müssen dem [normalen Windows-Desktopstil](/windows/desktop/uxguide/controls)folgen, d. h., sie werden nicht neu erstellt und sollten in ihrer Standardsteuerelementdarstellung angezeigt werden.

- **Standarddialoge (Dienstprogramm):** nicht thematisiert. Nicht erneut vorlage. Verwenden Sie grundlegende Steuerelementstilstandards.

- **Werkzeugfenster, Dokumenteditoren, Designflächen und Themendialoge:** Verwenden Sie ein spezielles thematisches Erscheinungsbild mithilfe des Farbdienstes.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>Scrollleisten
 Bildlaufleisten sollten [gängigen Interaktionsmustern für Windows-Bildlaufleisten](/windows/desktop/Controls/about-scroll-bars) folgen, es sei denn, sie werden mit Inhaltsinformationen ergänzt, wie im Code-Editor.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Eingabefelder
 Befolgen Sie die [Windows Desktop-Richtlinien für Textfelder](/windows/desktop/uxguide/ctrl-text-boxes), um ein typisches Interaktionsverhalten zu erhalten.

#### <a name="visual-style"></a>Visueller Stil

- Eingabefelder sollten nicht in Dienstprogrammdialogfeldern formatiert werden. Verwenden Sie den grundlegenden Stil, der dem Steuerelement eigenist.

- Themaierte Eingabefelder sollten nur in Themendialogen und Werkzeugfenstern verwendet werden.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen

- Schreibgeschützte Felder haben einen grauen (deaktivierten) Hintergrund, aber standardmäßig (aktiv) Vordergrund.

- Erforderliche Felder sollten ** \<erforderliche>** als Wasserzeichen enthalten. Sie sollten die Farbe des Hintergrunds nur in seltenen Situationen ändern.

- Fehlerüberprüfung: Siehe [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Eingabefelder sollten so dimensioniert werden, dass sie an den Inhalt angepasst werden, nicht an die Breite des Fensters, in dem sie angezeigt werden, oder an die Länge eines langen Felds, wie ein Pfad, angepasst werden. Die Länge kann dem Benutzer Einschränkungen darüber anzeigen, wie viele Zeichen im Feld zulässig sind.

     ![Falsche Eingabefeldlänge: Es ist unwahrscheinlich, dass der Name so lang ist.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Falsche Eingabefeldlänge: Es ist unwahrscheinlich, dass der Name so lang ist.

     ![Korrekte Eingabefeldlänge: Das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Korrekte Eingabefeldlänge: Das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Combo-Boxen und Dropdown-Listen
Befolgen Sie für ein typisches Interaktionsverhalten die [Windows Desktop-Richtlinien für Dropdownlisten und Kombinationsfelder](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Visueller Stil

- Erstellen Sie das Steuerelement in Dienstprogrammdialogfeldern nicht erneut. Verwenden Sie den grundlegenden Stil, der dem Steuerelement eigenist.

- In der themenübergreifenden Benutzeroberfläche folgen Kombinationsfelder und Dropdowns der Standard-Themen für die Steuerelemente.

#### <a name="layout"></a>Layout
Combo-Boxen und Dropdowns sollten so dimensioniert werden, dass sie an den Inhalt angepasst werden, nicht an die Breite des Fensters, in dem sie angezeigt werden, oder um willkürlich der Länge eines langen Feldes wie einem Pfad zu entsprechen.

![Falsch: Die Dropdown-Breite ist zu lang für den Angezeigten Inhalt.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Falsch: Die Dropdown-Breite ist zu lang für den Angezeigten Inhalt.

![Richtig: Die Dropdown-Liste ist so dimensioniert, dass sie ein Übersetzungswachstum ermöglicht, aber nicht unnötig lang.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Richtig: Die Dropdown-Liste ist so dimensioniert, dass sie ein Übersetzungswachstum ermöglicht, aber nicht unnötig lang.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Kontrollkästchen
Befolgen Sie die [Windows Desktop-Richtlinien für Kontrollkästchen](/windows/desktop/uxguide/ctrl-check-boxes), um ein typisches Interaktionsverhalten zu erhalten.

#### <a name="visual-style"></a>Visueller Stil

- Erstellen Sie das Steuerelement in Dienstprogrammdialogfeldern nicht erneut. Verwenden Sie den grundlegenden Stil, der dem Steuerelement eigenist.

- In der themengebundenen Benutzeroberfläche folgen Kontrollkästchen der Standard-Themenfürstisierung für die Steuerelemente.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen

- Die Interaktion mit einem Kontrollkästchen darf niemals ein Dialogfeld öffnen oder zu einem anderen Bereich navigieren.

- Richten Sie Kontrollkästchen an der Grundlinie der ersten Textzeile aus.

     ![Falsch: Das Kontrollkästchen ist auf dem Text zentriert.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Falsch: Das Kontrollkästchen ist auf dem Text zentriert.

     ![Korrekt: Das Kontrollkästchen ist an der ersten Zeile des Textes ausgerichtet.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Korrekt: Das Kontrollkästchen ist an der ersten Zeile des Textes ausgerichtet.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Radiotasten
Befolgen Sie für ein typisches Interaktionsverhalten die [Windows Desktop-Richtlinien für Optionsfelder](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Visueller Stil
Stylen Sie in Dienstprogrammdialogfeldern keine Optionsfelder. Verwenden Sie den grundlegenden Stil, der dem Steuerelement eigenist.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen
Es ist nicht erforderlich, einen Gruppenrahmen zu verwenden, um Funkoptionen einzuschließen, es sei denn, Sie müssen die Gruppendifferenzierung in einem engen Layout beibehalten.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Gruppenrahmen
Befolgen Sie die [Windows Desktop-Richtlinien für Gruppenframes](/windows/desktop/uxguide/ctrl-group-boxes), um ein typisches Interaktionsverhalten zu erhalten.

#### <a name="visual-style"></a>Visueller Stil
Stylen Sie in Dienstprogrammdialogfeldern keine Gruppenrahmen. Verwenden Sie den grundlegenden Stil, der dem Steuerelement eigenist.

#### <a name="layout"></a>Layout

- Es ist nicht erforderlich, einen Gruppenrahmen zu verwenden, um Funkoptionen einzuschließen, es sei denn, Sie müssen die Gruppendifferenzierung in einem engen Layout beibehalten.

- Verwenden Sie niemals einen Gruppenrahmen für ein einzelnes Steuerelement.

- Manchmal ist es akzeptabel, eine horizontale Regel anstelle eines Gruppenrahmencontainers zu verwenden.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Textsteuerelemente

### <a name="static-text-fields"></a>Statische Textfelder

Ein statisches Textfeld enthält schreibgeschützte Informationen und kann vom Benutzer nicht ausgewählt werden. Vermeiden Sie es, ihn für Text zu verwenden, den der Benutzer möglicherweise in die Zwischenablage kopieren möchte. Der schreibgeschützte statische Text kann sich jedoch ändern, um eine Zustandsänderung widerzuspiegeln. Im folgenden Beispiel ändert sich der statische Text Ausgabename unter der Gruppe Information, um alle Änderungen widerzuspiegeln, die am Textfeld Stammnamespace darüber vorgenommen wurden.

Es gibt zwei Möglichkeiten, statische Textinformationen anzuzeigen.

Statischer Text kann sich in einem Dialogfeld ohne Eindämmung befinden, wenn kein Gruppierungskonflikt besteht. Entscheiden Sie, ob die zusätzlichen Zeilen einer Box wirklich notwendig sind. Ein Beispiel ist die Anzeige eines Verzeichnispfads unter einem Abschnitt, der von einer Gruppenzeile erstellt wurde, wie unten gezeigt:

![Statische Textinformationen in Textsteuerelementen](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "AnzeigenvonStaticText.png")<br />Statische Textinformationen in Textsteuerelementen

In einem Dialogfeld, in dem andere gruppierte Bereiche vorhanden sind und die Informationen enthalten, wird **Properties window** die Lesbarkeit hilfreich, und wenn ein Abschnitt ausgeblendet oder angezeigt werden kann (wie im Beschreibungsbereich Eigenschaftenfenster), oder Wenn Sie mit einer ähnlichen Benutzeroberfläche konsistent sein möchten, platzieren Sie den statischen Text in einem Feld. Dieses Gruppenfeld sollte eine einzelne Regel `ButtonShadow`sein und mit der Farbe:

![Statischer Text im Eigenschaftenfenster](../../extensibility/ux-guidelines/media/PropertiesWindow.png "EigenschaftenFenster.png")<br />Statischer Text im Eigenschaftenfenster

### <a name="read-only-text-box"></a>Schreibgeschütztes Textfeld

Dadurch kann der Benutzer den Text innerhalb des Felds auswählen, aber nicht bearbeiten. Diese Textfelder werden durch den üblichen 3-D-Meißel mit einer `ButtonShadow` Füllung umrandet.

Ein Textfeld kann aktiv werden (bearbeitbar), wenn ein Benutzer ein zugeordnetes Steuerelement ändert, z. B. ein Kontrollkästchen aktivieren/deaktivieren oder ein Optionsfeld auswählen/deaktivieren. Beispielsweise wird auf der Seite **Extraoptionen &gt; ** unten das Textfeld **Startseite** aktiv, wenn das Kontrollkästchen **Standard verwenden** deaktiviert ist.

![Schreibgeschütztes Textfeld mit inaktiven und aktiven Zuständen](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Schreibgeschütztes Textfeld mit inaktiven und aktiven Zuständen

### <a name="using-text-in-dialogs"></a>Verwenden von Text in Dialogfeldern

Die wichtigsten Richtlinien für Text in Dialogfeldern:

- Beschriftungen für Textfelder, Listenfelder und Rahmen in nicht themed-Dialogfeldern beginnen mit einem Verb, haben nur ein Anfangskapital für das erste Wort und enden mit einem Doppelpunkt.

    > Textsteuerelemente in thematischen Dialogfeldern folgen den [Windows-Desktop-UX-Richtlinien](/windows/desktop/uxguide/top-violations) und nehmen keine Endpunktion an, mit Ausnahme von Fragezeichen in Hilfelinks.

- Beschriftungen für Kontrollkästchen und Optionsfelder beginnen mit einem Verb, einem Anfangskapital nur für das erste Wort, und haben keine Endpunktituation.

- Beschriftungen für Schaltflächen, Menüs, Menüelemente und Registerkarten haben Anfangsbuchstaben für jedes Wort (Titelfall).

- Die Beschriftungsterminologie sollte mit ähnlichen Beschriftungen in anderen Dialogfeldern konsistent sein.

- Wenn möglich, lassen Sie einen Writer/Editor den Text schreiben oder genehmigen, bevor er zur Implementierung an den Entwickler geht.

- Alle Steuerelemente sollten Beschriftungen haben, außer in besonderen Fällen, in denen Das Tabbing ausreichend ist.
Verwenden Sie ggf. Hilfstext.

### <a name="helper-text"></a>Hilfstext

In Dialogfeldern enthalten, damit der Benutzer den Zweck des Dialogfelds versteht oder um anzugeben, welche Aktion ergriffen werden soll. Hilfstext sollte nur verwendet werden, wenn dies erforderlich ist, um unübersichtliche einfache Dialoge zu vermeiden. Die beiden Varianten des Hilfstextes sind Dialog und Wasserzeichen.

Folgen Sie allgemeinen Speicherorten für Hilfstext und sind Sie selektiv bei der Einführung neuer Bereiche. Häufige Szenarien für Hilfstext sind:

- Hilfstext in Dialogfeldern, um zusätzliche Anweisungen zur Interaktion mit einem komplexen Dialogfeld zu geben.

- Wasserzeichentext in leeren Werkzeugfenstern oder Dialogfeldern, um zu erklären, warum kein Inhalt sichtbar ist.

- Ein Beschreibungsbereich, z. B. am unteren Rand des **Eigenschaftenfensters**.

- Wasserzeichentext in einem leeren Editor, um zu erklären, welche Aktion der Benutzer ergreifen sollte, um loszulegen.

### <a name="dialog-helper-text"></a>Dialogfeld-Hilfetext

Ein Benutzererfahrungsdesigner kann dabei helfen, zu bestimmen, wann Hilfstext geeignet ist. Der Designer kann definieren, wo Hilfstext angezeigt wird, sowie seinen allgemeinen Inhalt. Die Benutzerunterstützung kann den eigentlichen Text schreiben/bearbeiten.

### <a name="watermarks"></a>Wasserzeichen

Dialoge profitieren von leicht unterschiedlichen Wasserzeichenrichtlinien. Da ein Dialogfeld mit vielen UI-Elementen (Beschriftungen, Hinweistext, Schaltflächen und andere Containersteuerelemente mit Text) ausgelastet sein kann, zeichnen sich Wasserzeichen in Dunkelgrau besser ab (VSColor: `ButtonShadow`). In der Regel wird ein Wasserzeichen in einem Steuerelement wie `Window`ein Listenfeld mit weißem Hintergrund (VSColor: ) angezeigt.

- Der Text wird in dunkelgrau `ButtonShadow`(VSColor: ) angezeigt. Wenn das Wasserzeichen jedoch auf einem mittleren grauen oder `ButtonFace`anderen farbigen (VSColor: ) Hintergrund angezeigt wird und `WindowText`Bedenken hinsichtlich seiner Lesbarkeit bestehen, gehen Sie mit schwarzem Text (VSColor: ).

- Wasserzeichen können zentriert oder bündig links sein. Wenden Sie Standardentwurfsregeln an, wenn Sie Ausrichtungsentscheidungen treffen. Das Wasserzeichen kann im Hintergrund nicht ausgewählt werden.

![Beispiel für Wasserzeichentext](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Beispiel für Wasserzeichentext

### <a name="context-specific-dynamic-text"></a>Kontextspezifischer (dynamischer) Text

Dynamischer Text kann auf zwei Arten in einer dialogfreien oder moduslosen Benutzeroberfläche verwendet werden: entweder als dynamische Bezeichnung oder als dynamischer Inhalt.

- Dynamische Bezeichnung: Eine häufige Verwendung von dynamischem Text ist in beschreibenden Bereichen, die mehr Informationen für das ausgewählte Element bieten, z. B. in einem Dialogfeld, das eine Liste von Elementen und Eigenschaften für die Elemente enthält, die in einem Raster auf der rechten Seite angezeigt werden. Die Bezeichnung für das Eigenschaftenraster kann dynamisch sein, sodass, wenn ein Element auf der linken Seite ausgewählt ist, das Raster rechts Informationen für dieses bestimmte Element anzeigt.

- Dynamischer Text: kann in Fällen nützlich sein, in denen Sie bestimmte Informationen und nicht allgemeine Informationen auf diese Weise anzeigen müssen, aber es sollte darauf geachtet werden, dass sie nicht überverwendet werden.

Wenn Sie möchten, dass Benutzer die Informationen kopieren können, sollte sich dynamischer Text in einem schreibgeschützten Textfeld befinden.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Schaltflächen und Hyperlinks

### <a name="overview"></a>Übersicht
Schaltflächen und Linksteuerelemente (Hyperlinks) sollten [den grundlegenden Windows Desktop-Anleitungen](/windows/desktop/uxguide/ctrl-links) zu Hyperlinks für Die Verwendung, den Wortlaut, die Größe und den Abstand folgen.

### <a name="choosing-between-buttons-and-links"></a>Auswählen zwischen Schaltflächen und Links
Traditionell wurden Schaltflächen für Aktionen verwendet und Hyperlinks wurden für die Navigation reserviert. Schaltflächen können in allen Fällen verwendet werden, aber die Rolle der Verknüpfungen wurde in Visual Studio erweitert, sodass Schaltflächen und Verknüpfungen unter bestimmten Bedingungen austauschbarer sind.

Verwendung von Befehlsschaltflächen:

- Primäre Befehle

- Anzeigen von Fenstern, die zum Sammeln von Eingaben oder zum Treffen von Entscheidungen verwendet werden, auch wenn es sich um sekundäre Befehle handelt

- Destruktive oder irreversible Aktionen

- Bindungsschaltflächen in Assistenten und Seitenflüssen

Vermeiden Sie Befehlsschaltflächen in Toolfenstern oder wenn Sie mehr als zwei Wörter für die Beschriftung benötigen. Links können längere Beschriftungen aufweisen.

 Zeitpunkt der Verwendung von Links:

- Navigation zu einem anderen Fenster, Dokument oder einer anderen Webseite

- Situationen, die eine längere Bezeichnung oder einen kurzen Satz erfordern, um die Absicht der Aktion zu beschreiben

- Enge Räume, in denen eine Schaltfläche die Benutzeroberfläche überfordern würde, vorausgesetzt, dass die Aktion nicht destruktiv oder irreversibel ist

- De-Hervorhebung sekundärer Befehle in Situationen, in denen es viele Befehle gibt

#### <a name="examples"></a>Beispiele
![Befehlslinks, die in der Infoleiste nach einer Statusmeldung verwendet werden](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Befehlslinks, die in der Infoleiste nach einer Statusmeldung verwendet werden

![Links im CodeLens-Popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Links im CodeLens-Popup

![Links, die für sekundäre Befehle verwendet werden, bei denen Schaltflächen zu viel Aufmerksamkeit auf sich ziehen würden](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Links, die für sekundäre Befehle verwendet werden, bei denen Schaltflächen zu viel Aufmerksamkeit auf sich ziehen würden

### <a name="common-buttons"></a>Gemeinsame Schaltflächen

#### <a name="text"></a>Text
Befolgen Sie die Schreibrichtlinien in [UI-Text und Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Visueller Stil

##### <a name="standard-unthemed"></a>Standard (unthematisch)
Die meisten Schaltflächen in Visual Studio werden in Dienstprogrammdialogfeldern angezeigt und sollten nicht formatiert werden. Sie sollten das Standardbild von Schaltflächen widerspiegeln, wie vom Betriebssystem diktiert.

##### <a name="themed"></a>Themen
In einigen Fällen können Schaltflächen innerhalb der gestylten Benutzeroberfläche verwendet werden, und diese Schaltflächen müssen entsprechend formatiert werden. Weitere Informationen zu thematischen Steuerelementen finden Sie unter [Dialogfelder.](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

### <a name="special-buttons"></a>Spezielle Tasten

#### <a name="browse-buttons"></a>Durchsuchen... Schaltflächen
**[Durchsuchen...]** Schaltflächen werden in Rastern, Dialogfeldern und Toolfenstern und anderen moduslosen UI-Elementen verwendet. Sie zeigen eine Auswahl an, die den Benutzer beim Ausfüllen eines Werts in ein Steuerelement unterstützt. Es gibt zwei Varianten dieser Taste, lang und kurz.

![Die lange [Browse...] Schaltfläche](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Die lange [Browse...] Schaltfläche

![Die Nur-Ellipsen-kurze [...] Taste](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Die Nur-Ellipsen-kurze [...] Taste

Wann Sie die kurzlelipsis-kurze Taste verwenden:

- Wenn es mehr als eine lange **[Browse...]** Schaltfläche in einem Dialoggibt gibt, z. B. wenn mehrere Felder das Browsen zulassen. Verwenden Sie die kurze **[...]** Taste für jeden, um die verwirrenden Zugriffstasten zu vermeiden, die durch diese Situation erstellt werden** (&Durchsuchen** und **B&Zeilen** im selben Dialog).

- In einem engen Dialog, oder wenn es keinen vernünftigen Ort, um die lange Taste zu setzen.

- Wenn die Schaltfläche in einem Rastersteuerelement angezeigt wird.

Richtlinien für die Verwendung der Schaltfläche:

- Verwenden Sie keinen Zugriffsschlüssel. Um über die Tastatur darauf zuzugreifen, muss der Benutzer eine Registerkarte über das benachbarte Steuerelement ausführen. Stellen Sie sicher, dass die Registerkartenreihenfolge so ist, dass jede Suchschaltfläche unmittelbar nach dem Feld fällt, das sie ausfüllen wird. Verwenden Sie niemals einen Unterstrich unterhalb der ersten Periode.

- Legen Sie die Microsoft Active Accessibility (MSAA) **Name-Eigenschaft** auf **Durchsuchen...** (einschließlich der Auslassungspunkte) fest, damit Bildschirmleser sie als "Durchsuchen" und nicht als "Punkt-Punkt-Punkt" oder "Periodenperiode" lesen. Für verwaltete Steuerelemente bedeutet dies, dass die **AccessibleName-Eigenschaft** gesetzt wird.

- Verwenden Sie niemals eine Ellipse **[...]** Taste für irgendetwas außer einer Suchaktion. Wenn Sie z. B. eine **Schaltfläche [Neu...]** benötigen, aber nicht genügend Platz für den Text haben, muss das Dialogfeld neu gestaltet werden.

##### <a name="sizing-and-spacing"></a>Größe und Abstand
![Größe [Browse...] Tasten: Standardversion ist 75x23 Pixel, Kurzversion ist 26x23 Pixel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Festlegen der Größe für Schaltfläche [Durchsuchen...]

![Abstand [Browse...] Schaltflächen: Abstand zwischen zugehörigem Steuerelement und Standard-Schaltfläche durchsuchen 7 Pixel, Abstand zwischen dem zugehörigen Steuerelement und der kurzen Schaltfläche durchsuchen 5 Pixel](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Festlegen der Abstände für Schaltfläche [Durchsuchen...]

#### <a name="graphical-buttons"></a>Grafische Schaltflächen
Einige Schaltflächen sollten immer ein grafisches Bild verwenden und niemals Text enthalten, um Platz zu sparen und Lokalisierungsprobleme zu vermeiden. Diese werden häufig in Feldauswahlen und anderen sortierbaren Listen verwendet.

> [!NOTE]
> Benutzer müssen auf diese Schaltflächen tab (es gibt keine Zugriffstasten), so platzieren Sie sie in einer vernünftigen Reihenfolge. Ordnen `name` Sie die Eigenschaft der Schaltfläche der Aktion zu, die sie ausführt, damit Bildschirmleser die Schaltflächenaktion korrekt interpretieren.

| Funktion | Schaltfläche |
| --- | --- |
| Hinzufügen | ![Grafische Schaltfläche "Hinzufügen"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Remove (Entfernen) | ![Grafische Schaltfläche "Entfernen"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Alle hinzufügen | ![Grafische Schaltfläche "Alles hinzufügen"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Alle entfernen | ![Grafische Schaltfläche "Alle entfernen"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Nach oben | ![Grafische Schaltfläche "Nach oben"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Nach unten | ![Grafische Schaltfläche "Nach unten"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Löschen | ![Grafische Schaltfläche "Löschen"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Größe und Abstand
Die Größe für grafische Schaltflächen ist die gleiche wie für die Kurzversion der **[Browse...]-Schaltfläche** (26x23 Pixel):

![Darstellung eines grafischen Bildes auf Knopf, mit und ohne transparente Farbdarstellung](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Darstellung eines grafischen Bildes auf Knopf, mit und ohne transparente Farbdarstellung

### <a name="hyperlinks"></a>Links
Hyperlinks eignen sich gut für navigationsbasierte Aktionen, z. B. das Öffnen eines Hilfethemas, eines modalen Dialogfelds oder eines Assistenten. Wenn ein Hyperlink für einen Befehl verwendet wird, sollte immer eine sichtbare und spürbare Änderung an der Benutzeroberfläche angezeigt werden. Im Allgemeinen werden Aktionen, die zu einer Aktion verpflichten (z. B. Speichern, Abbrechen und Löschen), besser über eine Schaltfläche kommuniziert.

#### <a name="writing-style"></a>Schreibstil
Befolgen Sie die [Windows Desktop-Anleitung für Benutzeroberflächentext](/windows/desktop/uxguide/text-ui). Verwenden Sie nicht "Erfahren Sie mehr darüber", "Erzählen Sie mir mehr darüber" oder "Hilfe erhalten Sie dabei" Phrasierung. Stattdessen wird der Aussatz Hilfetext in Bezug auf die primäre Frage verknüpft, die vom Hilfeinhalt beantwortet wird. Beispiel: "**Wie füge ich dem Server-Explorer einen Server hinzu?**"

#### <a name="visual-style"></a>Visueller Stil

- Hyperlinks sollten immer [den VSColor-Dienst](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)verwenden. Wenn ein Hyperlink nicht richtig formatiert ist, blinkt er rot, wenn er aktiv ist, oder zeigt nach dem Besuch eine andere Farbe an.

- Schließen Sie keine Unterstreichungen im Ruhezustand der Steuerung ein, es sei denn, die Verknüpfung ist ein Satzfragment innerhalb eines vollständigen Satzes, wie in einem Wasserzeichen.

- Unterstreichungen sollten nicht auf dem Mauszeiger angezeigt werden. Stattdessen ist das Feedback an den Benutzer, dass der Link aktiv ist, eine leichte Farbänderung und der entsprechende Linkcursor.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Baumansichten

Strukturansichten bieten eine Möglichkeit, komplexe Listen in Parent-Child-Gruppen zu organisieren. Ein Benutzer kann übergeordnete Gruppen erweitern oder reduzieren, um zugrunde liegende untergeordnete Elemente anzuzeigen oder auszublenden. Jedes Element in einer Strukturansicht kann ausgewählt werden, um weitere Aktionen bereitzustellen.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Visueller Stil der Baumansicht

#### <a name="expanders"></a>Expander
Strukturansichtssteuerelemente sollten dem von Windows und Visual Studio verwendeten Erweiterungsentwurf entsprechen. Jeder Knoten verwendet ein Expander-Steuerelement, um zugrunde liegende Elemente anzuzeigen oder auszublenden. Die Verwendung eines Expandersteuerelements bietet Konsistenz für Benutzer, die möglicherweise auf unterschiedliche Strukturansichten in Windows und Visual Studio stoßen.

![Korrekt: richtiger Stil des Baumansichtsknotens mithilfe eines Expandersteuerelements](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Korrekt: richtiger Stil des Baumansichtsknotens mithilfe eines Expandersteuerelements

![Falsch: unsachgemäßer Stil des Baumansichtsknotens](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Falsch: unsachgemäßer Stil des Baumansichtsknotens

#### <a name="selection"></a>Auswahl
Wenn ein Knoten in der Strukturansicht ausgewählt ist, sollte die Hervorhebung auf die volle Breite des Strukturansichtssteuerelements erweitert werden. Auf diese Weise können Benutzer eindeutig erkennen, welches Element sie ausgewählt haben. Auswahlfarben sollten das aktuelle Visual Studio-Design widerspiegeln.

![Korrekt: Die Hervorhebung des ausgewählten Knotens passt die gesamte Breite des Strukturansichtssteuerelements an.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Korrekt: Die Hervorhebung des ausgewählten Knotens passt die gesamte Breite des Strukturansichtssteuerelements an.

![Falsch: Die Hervorhebung des ausgewählten Knotens passt nicht zur gesamten Breite des Strukturansichtssteuerelements.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Falsch: Die Hervorhebung des ausgewählten Knotens passt nicht zur gesamten Breite des Strukturansichtssteuerelements.

#### <a name="icons"></a>Symbole
Symbole sollten nur in Strukturansichtssteuerelementen verwendet werden, wenn sie bei der visuellen Identifizierung von Unterschieden zwischen Elementen hilfreich sind. Im Allgemeinen sollten Symbole nur in heterogenen Listen verwendet werden, in denen die Symbole Informationen enthalten, um die Elementtypen zu unterscheiden. In einer homogenen Liste kann die Verwendung von Symbolen häufig als Rauschen angesehen werden und sollte vermieden werden. In diesem Fall kann das Gruppensymbol (übergeordnetes Element) den Typ der Elemente in ihm vermitteln. Die Ausnahme von dieser Regel wäre, wenn das Symbol dynamisch ist und verwendet wird, um den Status anzugeben.

#### <a name="scroll-bars"></a>Bildlaufleisten
Bildlaufleisten sollten immer ausgeblendet werden, wenn der Inhalt in das Strukturansichtssteuerelement passt. Es ist akzeptabel, dass Bildlaufleisten in einem scrollbaren Fenster ausgeblendet oder halbtransparent angezeigt werden, wenn das Fenster mit der Baumansicht den Fokus hat, oder wenn sie den Mauszeiger auf die Baumansicht selbst bewegen.

![Sowohl vertikale als auch horizontale Bildlaufleisten werden angezeigt, da der Inhalt die Grenzen des Baumansichtssteuerelements überschritten hat.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Sowohl vertikale als auch horizontale Bildlaufleisten werden angezeigt, da der Inhalt die Grenzen des Baumansichtssteuerelements überschritten hat.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Baumansichtsinteraktionen

#### <a name="context-menus"></a>Kontextmenüs
Ein Baumansichtsknoten kann Untermenüoptionen in einem Kontextmenü anzeigen. In der Regel tritt dies auf, wenn ein Benutzer mit der rechten Maustaste auf ein Element geklickt oder die Menütaste auf einer Windows-Tastatur gedrückt hat, wobei das Element ausgewählt ist. Es ist wichtig, dass der Knoten den Fokus erhält und ausgewählt wird. Auf diese Weise kann der Benutzer ermitteln, zu welchem Element das Untermenü gehört.

![Das Element, das das Kontextmenü generiert hat, erhält den Fokus, um den Benutzer zu benachrichtigen, welches Element ausgewählt wurde.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Das Element, das das Kontextmenü generiert hat, erhält den Fokus, um den Benutzer zu benachrichtigen, welches Element ausgewählt wurde.

#### <a name="keyboard"></a>Tastatur
Die Strukturansicht sollte die Möglichkeit bieten, Elemente auszuwählen und Knoten mithilfe der Tastatur zu erweitern/reduzieren. Dadurch wird sichergestellt, dass die Navigation unseren Barrierefreiheitsanforderungen entspricht.

##### <a name="tree-view-control"></a>Baumansichtssteuerelement
Visual Studio-Struktursteuerelemente sollten der allgemeinen Tastaturnavigation folgen:

- **Pfeil nach oben:** Auswählen von Elementen, indem Sie den Baum nach oben verschieben

- **Abwärtspfeil:** Auswählen von Elementen, indem Sie den Baum nach unten verschieben

- **Rechter Pfeil:** Erweitern eines Knotens in der Struktur

- **Linker Pfeil:** Reduzieren eines Knotens in der Struktur

- **Schlüssel eingeben:** Initiieren, Laden, Ausführen ausgewählter Elemente

##### <a name="trid-tree-view-and-grid-view"></a>Trid (Baumansicht und Rasteransicht)
Ein Trid-Steuerelement ist ein komplexes Steuerelement, das eine Strukturansicht innerhalb eines Rasters enthält. Beim Erweitern, Reduzieren und Navigieren in der Struktur sollten dieselben Tastaturbefehle wie eine Baumansicht mit den folgenden Hinzufügungen beachtet werden:

- **Rechter Pfeil:** Erweitern Sie einen Knoten. Nachdem der Knoten erweitert wurde, sollte er weiterhin zur nächsten Spalte auf der rechten Seite navigieren. Die Navigation sollte am Ende der Zeile angehalten werden.

- **Tab:** Navigiert zur nächstgelegenen Zelle auf der rechten Seite.  Am Ende der Zeile wird die Navigation zur nächsten Zeile fortgesetzt.

- **Umschalt + Tab:** Navigiert zur nächsten Zelle auf der linken Seite.  Am Anfang der Zeile wird die Navigation zur rechten Zelle in der vorherigen Zeile fortgesetzt.

![Ein Trid-Steuerelement in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Ein Trid-Steuerelement in Visual Studio
