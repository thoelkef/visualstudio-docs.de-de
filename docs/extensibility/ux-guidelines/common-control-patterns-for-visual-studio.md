---
title: "Allgemeine Steuerelementmuster für Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 185fc30458fed4303eb0cf6d59b5e6784840f89e
ms.contentlocale: de-de
ms.lasthandoff: 05/04/2017

---
# <a name="common-control-patterns-for-visual-studio"></a>Allgemeine Steuerelementmuster für Visual Studio
##  <a name="BKMK_CommonControls"></a>Allgemeine Steuerelemente  
  
### <a name="overview"></a>Übersicht  
Allgemeine Steuerelemente bilden zusammen den Großteil der Benutzeroberfläche in Visual Studio. In Visual Studio-Benutzeroberfläche verwendeten am häufigsten verwendeten Steuerelemente sollten folgen der [Richtlinien für Windows-Desktop-Interaktion](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Dieses Thema bezieht sich auf Visual Studio und umfasst spezielle Situationen oder Details, die die Windows-Richtlinien zu erweitern.  
  
#### <a name="common-controls-in-this-topic"></a>Allgemeine Steuerelemente in diesem Thema  
  
-   [Bildlaufleisten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Eingabefelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Kombinationsfelder und Dropdown-Listen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Kontrollkästchen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Optionsfelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Gruppe frames](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Schaltflächen und Links](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Strukturansichten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Der visuelle Stil  
Als erstes beim Formatieren von Steuerelementen berücksichtigt wird, ob die Steuerelemente in Benutzeroberflächen mit Designs verwendet werden. Steuerelemente in Standardoberfläche Benutzeroberflächen mit nicht-Designs sind, und folgen [normalen Windows-Desktop-Stil](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), was bedeutet, dass sie nicht auf Vorlagen basierende Re sind und ihre Darstellung des Standard-Steuerelements angezeigt werden soll.  
  
-   **Standard (Hilfsprogramm) Dialoge:** nicht Designs. Keine Vorlage neu erstellt. Verwenden Sie Standardwerte für grundlegende Steuerelement-Stil.  
  
-   **Toolfenstern, Dokument-Editoren, Entwurfsoberflächen und Designs Dialoge:** spezielle Designs Darstellung, die mit dem Dienst Farbe verwenden.  
  
###  <a name="BKMK_Scrollbars"></a>Bildlaufleisten  
 Führen Sie die Bildlaufleisten sollten [allgemeine interaktionsmustern für Windows-Bildlaufleisten](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) , wenn sie mit der Inhaltsinformationen erweitert sind, wie Sie im Code-Editor.  
  
###  <a name="BKMK_InputFields"></a>Eingabefelder  
 Für typische Interaktionsverhalten, befolgen Sie die [Windows-Desktop-Richtlinien für Textfelder](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Der visuelle Stil  
  
-   Eingabefelder darf nicht im Hilfsprogramm Dialoge formatiert werden. Verwenden Sie das grundlegende Format für das Steuerelement.  
  
-   Designs Eingabefelder sollte nur in Designs Dialogfelder und Toolfenster verwendet werden.  
  
#### <a name="specialized-interactions"></a>Spezielle Aktivitäten  
  
-   Schreibgeschützte Felder müssen jedoch (aktiv) standardmäßige Vordergrund-Hintergrund grau (deaktiviert).  
  
-   Erforderliche Felder müssen  **\<erforderlich >** als Wasserzeichen darin. Sie sollten die Farbe des Hintergrunds außer in seltenen Fällen Anwendung nicht ändern.  
  
-   Fehler-Überprüfung: finden Sie unter [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Eingabefelder sollte angepasst werden, um den Inhalt nicht auf die Breite des Fensters in der sie angezeigt werden, noch die Zeitdauer in einem langen Feld, z. B. einen Pfad nach dem Zufallsprinzip entsprechend anpassen. Länge möglicherweise ein Hinweis darauf sein, die dem Benutzer Einschränkungen hinsichtlich der Anzahl der Zeichen in das Feld zulässig sind.  
  
     ![Falsche Eingabe Feldlänge: Es ist unwahrscheinlich, dass der Name diesem lang kann.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Falsche Eingabe Feldlänge: Es ist unwahrscheinlich, dass der Name diesem lang kann.
  
     ![Beheben Sie die Eingabe der Feldlänge: das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Beheben Sie die Eingabe der Feldlänge: das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a>Kombinationsfelder und Dropdown-Listen  
Für typische Interaktionsverhalten, befolgen Sie die [Windows-Desktop-Richtlinien für Dropdownlisten und Kombinationsfelder](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Der visuelle Stil  
  
-   Im Hilfsprogramm-Dialogfelder nicht Re-Vorlage des Steuerelements. Verwenden Sie das grundlegende Format für das Steuerelement.  
  
-   Führen Sie die standard-Designs für die Steuerelemente, in Designs Benutzeroberflächen, Kombinationsfelder und Dropdownlisten.  
  
#### <a name="layout"></a>Layout  
Kombinationsfelder und Dropdownlisten sollte angepasst werden, um den Inhalt nicht auf die Breite des Fensters in der sie angezeigt werden, noch die Zeitdauer in einem langen Feld, z. B. einen Pfad nach dem Zufallsprinzip entsprechend anpassen.  
  
![Falsche: die Breite des Dropdown-Liste ist zu lang für den Inhalt, der angezeigt wird.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Falsche: die Breite des Dropdown-Liste ist zu lang für den Inhalt, der angezeigt wird.
  
![Richtig: der Dropdown-ist die Größe kann Übersetzung anwachsen, aber nicht unnötig lange.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Richtig: der Dropdown-ist die Größe kann Übersetzung anwachsen, aber nicht unnötig lange. 
  
###  <a name="BKMK_CheckBoxes"></a>Kontrollkästchen  
Für typische Interaktionsverhalten, befolgen Sie die [Windows-Desktop-Richtlinien für Kontrollkästchen](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Der visuelle Stil  
  
-   Im Hilfsprogramm-Dialogfelder nicht Re-Vorlage des Steuerelements. Verwenden Sie das grundlegende Format für das Steuerelement.  
  
-   In Benutzeroberflächen mit Designs führen Sie die Kontrollkästchen der standard-Designs für die Steuerelemente.  
  
#### <a name="specialized-interactions"></a>Spezielle Aktivitäten  
  
-   Interaktion mit einem Kontrollkästchen muss nie pop ein Dialogfeld oder navigieren Sie zu einem anderen Bereich.  
  
-   Richten Sie Kontrollkästchen die Grundlinie der ersten Zeile des Texts an.  
  
     ![Falsch: das Kontrollkästchen ist in der Text zentriert.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Falsch: das Kontrollkästchen ist in der Text zentriert.
  
     ![Richtig: dieses Kontrollkästchen ist mit der ersten Zeile des Texts ausgerichtet.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Richtig: dieses Kontrollkästchen ist mit der ersten Zeile des Texts ausgerichtet.
  
###  <a name="BKMK_RadioButtons"></a>Optionsfelder  
Für typische Interaktionsverhalten, befolgen Sie die [Windows-Desktop-Richtlinien für die Optionsfelder](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Der visuelle Stil  
Führen Sie im Hilfsprogramm-Dialogfelder nicht Stil Optionsfelder. Verwenden Sie das grundlegende Format für das Steuerelement.  
  
#### <a name="specialized-interactions"></a>Spezielle Aktivitäten  
Es ist nicht notwendig, einen Gruppe Frame zu verwenden, zum Einschließen von Optionsfeld-Optionen, sofern Sie für die Unterscheidung der Gruppe in einem enge Layout beibehalten müssen.  
  
###  <a name="BKMK_GroupFrames"></a>Gruppe frames  
Für typische Interaktionsverhalten, befolgen Sie die [Windows-Desktop-Richtlinien für die Gruppe Frames](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Der visuelle Stil  
Dienstprogramm-Dialogfelder formatieren Sie nicht im Rahmen der Gruppe. Verwenden Sie das grundlegende Format für das Steuerelement.  
  
#### <a name="layout"></a>Layout  
  
-   Es ist nicht notwendig, einen Gruppe Frame zu verwenden, zum Einschließen von Optionsfeld-Optionen, sofern Sie für die Unterscheidung der Gruppe in einem enge Layout beibehalten müssen.  
  
-   Verwenden Sie niemals einen Gruppenrahmen für ein einzelnes Steuerelement.  
  
-   Manchmal ist es zulässig, eine horizontale Regel verwenden, statt einen Container für die Gruppe Frames.  
  
##  <a name="BKMK_TextControls"></a>Textsteuerelemente

### <a name="static-text-fields"></a>Statischer Text-Felder

Ein statischer Text-Feld zeigt schreibgeschützte Informationen und kann nicht vom Benutzer ausgewählt werden. Vermeiden Sie es für Text, der Benutzer möglicherweise in die Zwischenablage kopieren möchten. Schreibgeschützten statischer Text kann jedoch eine Änderung am Zustand entsprechend ändern. Im folgenden Beispiel ist der Ausgabename statischer Text unter Änderungen der Informationen Änderungen an die Stamm-Namespace Textfeld oben entsprechend.

Es gibt zwei Möglichkeiten zum Anzeigen von statischem Textinformationen.

Statischer Text kann auf eine eigene in einem Dialog ohne Containment When keine Gruppierung Konflikt vorliegt. Entscheiden Sie, ob die zusätzlichen Zeilen eines Felds wirklich erforderlich sind. Ein Beispiel ist die Anzeige von einen Verzeichnispfad ein Abschnitt durch eine Gruppenlinie erstellt, wie unten dargestellt:  

![Statischer Text Informationen im Text-Steuerelemente](~/extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Statischer Text Informationen im Text-Steuerelemente

In einem Dialogfeld, in dem anderen gruppierten Bereichen vorhanden und Kapselung der Informationen würden Lesbarkeit und wenn ein Abschnitt ausgeblendet oder angezeigt werden kann (wie in der **Fenster "Eigenschaften"** Beschreibungsbereich) oder mit ähnlichen Benutzeroberfläche konsistent sein, platzieren Sie den statischen Text in einem Feld werden sollen. Diese Gruppenfeld muss eine einzelne Regel und gefärbt, mit der `ButtonShadow`:

![Statischer Text im Fenster Eigenschaften](~/extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Statischer Text im Fenster Eigenschaften

### <a name="read-only-text-box"></a>Nur-Lese Textfeld

Dies ermöglicht es dem Benutzer, wählen Sie den Text in das Feld jedoch nicht bearbeiten. Diese Felder sind umrandet, durch die üblichen 3D ziseliert mit einem `ButtonShadow` ausfüllen.

Ein Textfeld kann aktiv (bearbeitet werden), wenn ein Benutzer eine zugeordnete Steuerelement, z. B. ein Kontrollkästchen aktivieren bzw. deaktivieren oder ein Optionsfeld auswählen/aufheben ändert. Z. B. in der **Tools &gt; Optionen** Seite unten die **Startseite** Textfeld wird aktiviert, wenn die **Standard verwenden** das Kontrollkästchen deaktiviert ist.

![Nur-Lese Textfeld, inaktiven und den aktiven Status anzeigen](~/extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Nur-Lese Textfeld, inaktiven und den aktiven Status anzeigen

### <a name="using-text-in-dialogs"></a>Verwenden von Text in Dialogfeldern

Wichtigsten Richtlinien für Text in Dialogfeldern:

-   Bezeichnungen für Textfelder, Listenfelder und Bilder in Unthemed Dialoge mit ein Verb beginnen, haben auf das erste Wort nur einem großen Anfangsbuchstaben und enden mit einem Doppelpunkt.

    > Führen Sie die Text-Steuerelemente in Dialogfeldern Designs [Windows desktop-UX-Richtlinien](https://msdn.microsoft.com/library/windows/desktop/dn742479.aspx) und akzeptieren keine Interpunktion, mit Ausnahme von Fragezeichen in Links zu Hilfethemen.

-   Bezeichnungen für Kontrollkästchen und Optionsfelder beginnen mit einem Verb, auf das erste Wort nur einem großen Anfangsbuchstaben und ohne schließende Satzzeichen.

-   Bezeichnungen für Schaltflächen, Menüs und Menüelemente, Registerkarten über Wortanfang für jedes Wort (Anfangsbuchstaben) verfügen.

-   Label-Terminologie sollte mit ähnlichen Bezeichnungen in anderen Dialogfeldern konsistent sein.

-   Wenn möglich, verfügen über einen Writer/Editor schreiben oder den Text zu genehmigen, damit er dem Entwickler für die Implementierung wechselt.

-   Alle Steuerelemente verfügen sollte Bezeichnungen mit Ausnahme von besonderen Umständen in die TAB-Taste ausreichend ist.
Verwenden Sie ggf.-Hilfetext an.

### <a name="helper-text"></a>Hilfetext

Enthalten in Dialogfeldern, die den Benutzer das Dialogfeld "Zweck kennen, helfen oder um die Aktion anzugeben. Hilfetext sollte nur bei Bedarf verwendet werden, vermeiden, dass einfache Dialogfelder. Die zwei Variationen des Hilfetext sind Dialogfeld und der Grenzwert.

Führen Sie die allgemeine Speicherorte für Hilfetext und werden in der Einführung in neue Bereiche selektiven. Häufige Szenarios für die Hilfetext sind:

-   Hilfetext in Dialogfeldern, um zusätzliche Richtung zur Interaktion mit einem komplexen Dialogfeld zu gewähren.

-   Wasserzeichentext in leere Toolfenster oder Dialogfeldern, erläutern, warum kein Inhalt angezeigt wird.

-   Ein Beschreibungsbereich, in der am unteren Rand wie die **Fenster "Eigenschaften"**.

-   Wasserzeichen Sie in einem leeren Editor, um wird erläutert, welche Aktion der Benutzer ausführen sollten, um zu beginnen.
  
### <a name="dialog-helper-text"></a>Dialogfeld-Hilfetext

Ein Designer von Benutzerfunktionalität kann Ihnen helfen zu bestimmen, wann Hilfetext geeignet sind. Der Designer kann definieren, wo Hilfetext sowie allgemeine Inhalt angezeigt wird. Benutzerunterstützung kann Schreib-/den tatsächlichen Text bearbeiten.

### <a name="watermarks"></a>Wasserzeichen

Dialoge profitieren von etwas anderes Wasserzeichen Richtlinien. Da ein Dialogfeld mit vielen Benutzeroberflächenelemente (Bezeichnungen, Hinweistext, Schaltflächen und anderen Containersteuerelementen mit Text), ausgelastet besonders angezeigt werden kann, wenn diese auf Schwarz angezeigt, hervorzuheben Wasserzeichen besser in dunkelgrau (VSColor: `ButtonShadow`). In der Regel ein Wasserzeichen angezeigt wird, innerhalb eines Steuerelements, wie ein Listenfeld mit weißem Hintergrund (VSColor: `Window`).

-   Der Text in dunkelgrau angezeigt (VSColor: `ButtonShadow`). Jedoch, wenn der Grenzwert für eine mittlere Grau oder andere farbig angezeigt wird (VSColor: `ButtonFace`) im Hintergrund und ist über seine Lesbarkeit betreffen, fahren Sie mit schwarzem Text (VSColor: `WindowText`).

-   Wasserzeichen können linksbündig oder zentriert. Wenden Sie standard-Design-Regeln an, wenn Ausrichtung Entscheidungen zu treffen. Das Wasserzeichen kann nicht auf den Hintergrund ausgewählt werden.

![Wasserzeichen Text (Beispiel)](~/extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Wasserzeichen Text (Beispiel)

### <a name="context-specific-dynamic-text"></a>Kontextspezifisch (dynamisch) text

Dynamische Text verwendet eine von zwei Arten in einem Dialogfeld oder nicht modale Benutzeroberflächen werden kann: entweder als dynamische Bezeichnung oder als dynamische Inhalte.

-   Dynamische Beschriftung: eine häufige Verwendung der dynamischen Text befindet sich im beschreibenden Bereiche, die Informationen für das ausgewählte Element, z. B. in einem Dialog bieten enthält eine Liste von Elementen und Eigenschaften für diese Elemente in einem Raster rechts angezeigt. Die Bezeichnung für das Eigenschaftenraster kann dynamisch sein, damit im Raster rechts Informationen für dieses bestimmte Element angezeigt, wenn ein Element auf der linken Seite ausgewählt ist.

-   Dynamische Text: kann in Fällen, in dem Sie spezifische Informationen und nicht allgemein Informationen auf diese Weise anzeigen müssen, aber sollte darauf geachtet werden, nicht zu viele, hilfreich sein.

Wenn Sie Benutzer haben die Möglichkeit, die Informationen kopieren möchten, muss dynamischen Text in einem schreibgeschützten Textfeld.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a>Schaltflächen und Links  
  
### <a name="overview"></a>Übersicht  
Führen Sie die Schaltflächen und Link-Steuerelemente (links) sollten [grundlegende Windows-Desktop-Hinweise auf Hyperlinks](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) für die Verwendung, formulierungen, Größe und Abstand.  
  
### <a name="choosing-between-buttons-and-links"></a>Auswählen zwischen Schaltflächen und links  
Bisher wurden Schaltflächen für Aktionen verwendet und Links für die Navigation reserviert wurde. Schaltflächen in allen Fällen verwendet werden können, aber die Rolle des Links wurde in Visual Studio erweitert, damit die Schaltflächen und Links unter bestimmten Umständen mehr austauschbar sind.  
  
Wann Befehlsschaltflächen verwenden:  
  
-   Primäre Befehle  
  
-   Anzeigen von Windows verwendet, um die Eingabe zu erfassen oder die entsprechende Auswahl treffen, auch wenn sie sekundäre Befehle sind  
  
-   Destruktiven oder Rückgängig-Aktionen  
  
-   Verpflichtung Schaltflächen im Assistenten und Seite Arbeitsabläufe  
  
Vermeiden Sie die Befehlsschaltflächen in Toolfenstern, oder wenn Sie mehr als zwei Wörter für die Bezeichnung benötigen. Links können längere Bezeichnungen sein.  
  
 Wann Links zu verwenden:  
  
-   Navigation zu einem anderen Fenster, ein Dokument oder eine Webseite  
  
-   Situationen, in denen eine längere Bezeichnung oder einen kurzen Satz zum Beschreiben der Zweck der jeweiligen Aktion erforderlich  
  
-   Enge Leerzeichen, in dem eine Schaltfläche auf der Benutzeroberfläche überlasten würden, vorausgesetzt, dass die Aktion nicht destruktiver oder nicht umkehrbar ist  
  
-   Deduplizierung Hervorhebungseffekt sekundäre Befehle in Situationen viele Befehle vorhanden sind  
  
#### <a name="examples"></a>Beispiele  
![Befehl Links in der Statusmeldung Infoleiste verwendet](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Befehl Links in der Statusmeldung Infoleiste verwendet
  
![Links im CodeLens-popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Links im CodeLens-Popup
  
![Links zum sekundären Befehle Schaltflächen würden, in denen zu viel Aufmerksamkeit gewinnen.](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Links zum sekundären Befehle Schaltflächen würden, in denen zu viel Aufmerksamkeit gewinnen.
  
### <a name="common-buttons"></a>Allgemeine Schaltflächen  
  
#### <a name="text"></a>Text  
Führen Sie die Richtlinien für das Schreiben in [UI Text und Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Der visuelle Stil  
  
##### <a name="standard-unthemed"></a>Standard (Unthemed)  
Die meisten Schaltflächen in Visual Studio im Hilfsprogramm Dialogfelder angezeigt, und sollte nicht formatiert werden. Weisen sie die standard-Darstellung der Schaltflächen werden vom Betriebssystem bestimmt.  
  
##### <a name="themed"></a>Designs  
In einigen Fällen Schaltflächen mit formatierte Benutzeroberfläche verwendet werden können, und diese Schaltflächen müssen ordnungsgemäß formatiert sein. Finden Sie unter [Dialoge](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) Informationen zu Steuerelementen Designs.  
  
### <a name="special-buttons"></a>Spezielle Schaltflächen  
  
#### <a name="browse-buttons"></a>Durchsuchen von Schaltflächen  
**[Durchsuchen...]**  Schaltflächen werden im Raster, Dialogfelder und Toolfenster sowie andere Elemente der Benutzeroberfläche nicht modalen verwendet. Sie zeigen eine Auswahl, die den Benutzer beim Ausfüllen der eines Werts in ein Steuerelement hilft. Es gibt zwei Varianten dieser Schaltfläche, die lange und kurze.  
  
![Die lange [durchsuchen...]-Schaltfläche](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Die lange [durchsuchen...]-Schaltfläche
  
![Die Schaltfläche mit den Auslassungspunkten nur kurze [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Die Schaltfläche mit den Auslassungspunkten nur kurze [...]
  
Wenn Auslassungspunkte nur kurze Schaltfläche zu verwenden:  
  
-   Wenn es mehr als eine lange **[durchsuchen...]**  Schaltfläche in einem Dialogfeld, z. B. wenn mehrere Felder für das Durchsuchen von zulässt. Verwenden Sie die kurze **[...]**  Schaltfläche für jedes Element die verwirrend Zugriffsschlüssel erstellt, indem diese Situation zu vermeiden (**& Durchsuchen** und **B & amen** im gleichen Dialogfeld "").  
  
-   Eine enge im Dialogfeld ", oder wenn keine angemessene Möglichkeit, platzieren die Schaltfläche" long "vorhanden ist.  
  
-   Wenn die Schaltfläche in einem Datenraster-Steuerelement angezeigt wird.  
  
Richtlinien für die Verwendung der Schaltfläche:  
  
-   Verwenden Sie keine Zugriffstaste. Um mithilfe der Tastatur zuzugreifen, muss der Benutzer aus dem angrenzende Steuerelement Registerkarte. Stellen Sie sicher, dass die Reihenfolge der Registerkarten ist, dass Schaltfläche "Durchsuchen" sofort nach dem Feld fällt, die es ausgefüllt werden. Verwenden Sie niemals einen Unterstrich unterhalb der ersten Periode.  
  
-   Legen Sie die Microsoft Active Accessibility (MSAA) **Namen** Eigenschaft **durchsuchen...**  (einschließlich der mit den Auslassungspunkten) so Bildschirm wird eine Leseberechtigung es als "Durchsuchen" und nicht "Punkt-Punkt-Punkt" oder "Punkt-Punkt-Punkt." Für verwaltete Steuerelemente, bedeutet dies, die Einstellung der **Control.AccessibleName** Eigenschaft.  
  
-   Verwenden Sie niemals ein Auslassungszeichen **[...]**  Schaltfläche für nur eine Aktion "Durchsuchen". Angenommen, Sie müssen eine **[Neu]**  Schaltfläche, aber keine ausreichend Platz für den Text aus, und klicken Sie dann das Dialogfeld muss geändert werden.  
  
##### <a name="sizing-and-spacing"></a>Sizing und Abstand  
![Schaltflächen [durchsuchen...] Größe: Standardversion beträgt 75 x 23 Pixel, Kurzversion 26 x 23 Pixel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Festlegen der Größe für Schaltfläche [Durchsuchen...]
  
![Zeilenabstand [durchsuchen...] Schaltflächen: Abstände zwischen den dazugehörigen Steuerelement und standard Durchsuchen-Schaltfläche 7 Pixel, Abstand zwischen den dazugehörigen Steuerelement, und navigieren Sie kurze Schaltfläche 5 Pixel.](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Festlegen der Abstände für Schaltfläche [Durchsuchen...]
  
#### <a name="graphical-buttons"></a>Grafische Schaltflächen  
Einige Schaltflächen sollten immer eine Grafik und nie enthalten Text zum Einsparen von Speicherplatz und Lokalisierung Probleme zu vermeiden. Diese werden häufig in Feld Bildlaufbereich und anderen sortierbaren Listen verwendet.  
  
> **Hinweis:** Benutzer müssen diese Schaltflächen (es gibt keine Zugriffsschlüssel) die Registerkarte, speichern Sie sie in einer sinnvollen Reihenfolge. Zuordnung der `name` Eigenschaft der Schaltfläche auf die Aktion, die es dauert, sodass Sprachausgaben die Schaltflächenaktion richtig interpretieren.  
  
| Funktion | Schaltfläche |  
| --- | --- |  
| Hinzufügen | ![Grafische Schaltfläche ""Hinzufügen""](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Remove | ![Grafische Schaltfläche "Entfernen",](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Alle hinzufügen | ![Grafische Schaltfläche "Alle hinzufügen"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Alle entfernen | ![Grafische Schaltfläche "Alle entfernen"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Nach oben | ![Grafische Schaltfläche "Nach oben"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Nach unten | ![Grafische Schaltfläche "Nach unten"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Löschen | ![Grafische Schaltfläche "Löschen",](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Sizing und Abstand  
Ändern der Größe für grafische Schaltflächen genauso wie bei der Kurzversion des ist die **[durchsuchen...]**  Schaltfläche (26 x 23 Pixel):  
  
![Darstellung der eine Grafik auf die Schaltfläche mit und ohne transparenter Farbe](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Darstellung der eine Grafik auf die Schaltfläche mit und ohne transparenter Farbe
  
### <a name="hyperlinks"></a>Links  
Hyperlinks eignen sich gut für die Navigation basierende Aktionen, wie das Öffnen eines Hilfethemas, modales Dialogfeld, oder eines Assistenten. Ein Link für einen Befehl verwendet wird, sollten sie immer eine sichtbare und merkliche Änderung zu der Benutzeroberfläche angezeigt. Im Allgemeinen werden Aktionen, die Commits für eine Aktion (z. B. speichern, auf "Abbrechen", und löschen) besser übermittelt mithilfe einer Schaltfläche.  
  
#### <a name="writing-style"></a>Handschrift  
Führen Sie die [Windows-Desktop-Leitfaden für Texte für die Benutzeroberfläche](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). Verwenden Sie keine "Erfahren Sie mehr über," "Teilen Sie mir Weitere Informationen zu" oder "Get-Help mit diesem" phrasierungsinhalt. Stattdessen einen Ausdruck Link Hilfetext in Bezug auf die primäre Frage beantwortet haben, durch den Hilfeinhalt aus. Z. B. "**wie füge ich einen Server zum Server-Explorer hinzu?**"  
  
#### <a name="visual-style"></a>Der visuelle Stil  
  
-   Links zu verwendende immer [der VSColor Dienst](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Wenn der Link nicht ordnungsgemäß formatiert wird, blinkt Rot, wenn active oder zeigt eine andere Farbe nach der aufgerufen wird.  
  
-   Fügen Sie keine unterstreichungen an das Steuerelement Arbeitsfläche Zustand, wenn der Link ein Satz Fragment innerhalb eines vollständigen Satzes wie in ein Wasserzeichen enthalten sein ist.  
  
-   Wenn darauf gezeigt wird darf keine unterstrichen angezeigt. Stattdessen wird das Feedback für den Benutzer, dass die Verbindung aktiv ist, eine leichte Textfarbe ändern und den entsprechenden Link-Cursor.  
  
##  <a name="BKMK_TreeViews"></a>Strukturansichten  
  
Strukturansichten bieten eine Möglichkeit zum Organisieren von komplexen in übergeordneten / untergeordneten Gruppen aufgeführt. Ein Benutzer kann erweitert oder reduziert übergeordneten Gruppen zum Anzeigen oder Ausblenden von zugrunde liegenden untergeordneten Elemente. Jedes Element in einer Strukturansicht an kann ausgewählt werden, um weitere Aktion bereitzustellen.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a>Der visuelle Stil für Struktur anzeigen  
  
#### <a name="expanders"></a>Erweiterungen  
Strukturansicht-Steuerelemente sollten der Expander-Entwurf von Windows und Visual Studio verwendet, entsprechen. Jeder Knoten verwendet ein Expandersteuerelement zum Anzeigen oder Ausblenden von zugrunde liegenden Elementen. Verwenden ein Expandersteuerelement wird die Konsistenz für Benutzer, die verschiedene Strukturansichten in Windows und Visual Studio auftreten können.  
  
![Richtig: ordnungsgemäßes Format von Strukturansichtsknoten verwenden ein Expandersteuerelement](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Richtig: ordnungsgemäßes Format von Strukturansichtsknoten verwenden ein Expandersteuerelement
  
![Falsche: falsches Format des Strukturansichtsknoten](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Falsche: falsches Format des Strukturansichtsknoten
  
#### <a name="selection"></a>Auswahl  
Wenn ein Knoten in der Strukturansicht ausgewählt ist, sollte die Markierung auf die gesamte Breite des Strukturansicht-Steuerelement erweitert. Es hilft Benutzern, welches Element eindeutig sie ausgewählt haben. Die aktuelle Visual Studio-Designs sollten Auswahl Farben berücksichtigt werden.  
  
![Richtig: Hervorheben des ausgewählten Knotens passt die gesamte Breite des Strukturansicht-Steuerelement.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Richtig: Hervorheben des ausgewählten Knotens passt die gesamte Breite des Strukturansicht-Steuerelement.
  
![Falsche: Hervorheben des ausgewählten Knotens passt nicht die gesamte Breite des Strukturansicht-Steuerelement.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Falsche: Hervorheben des ausgewählten Knotens passt nicht die gesamte Breite des Strukturansicht-Steuerelement.
  
#### <a name="icons"></a>Symbole  
Symbole sollte nur in der Strukturansicht-Steuerelemente verwendet werden, wenn sie bei der Unterschiede zwischen Elementen visuell identifizieren. Symbole sollte im Allgemeinen nur in heterogenen Listen verwendet werden in denen die Symbole Informationen zum unterscheiden der Typen von Elementen ausführen. In einer homogenen Liste mit Symbolen kann häufig als Füllwörter betrachtet werden und sollte vermieden werden. In diesem Fall kann das Symbol "Gruppe" (übergeordneten) den Typ der Elemente im übermitteln. Die Ausnahme zu dieser Regel wäre, wenn das Symbol dynamisch ist und zur Angabe des Status dient.  
  
#### <a name="scroll-bars"></a>Bildlaufleisten  
Bildlaufleisten sollten immer ausgeblendet werden, wenn der Inhalt in der Strukturansicht-Steuerelement passt. Es ist ausgeblendet oder halbtransparente in einem bildlauffähigen Fenster und angezeigt werden, wenn das Fenster mit der Strukturansicht den Fokus besitzt, oder bei Hover der Struktur anzeigen, selbst für Bildlaufleisten akzeptabel.  
  
![Sowohl vertikale und horizontale Bildlaufleisten werden angezeigt, da der Inhalt die Grenzen des Strukturansicht-Steuerelements überschritten haben.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Sowohl vertikale und horizontale Bildlaufleisten werden angezeigt, da der Inhalt die Grenzen des Strukturansicht-Steuerelements überschritten haben.
  
###  <a name="BKMK_TreeViewInteractions"></a>Struktur anzeigen Interaktionen  
  
#### <a name="context-menus"></a>Kontextmenüs  
Knoten einer Strukturansicht kann im Untermenü Optionen in einem Kontextmenü offenlegen. Das tritt in der Regel auf, wenn ein Benutzer ein Element mit der rechten Maustaste, oder drücken die Menütaste auf einer Windows-Tastatur, mit das ausgewählte Element. Es ist wichtig, dass der Knoten den Fokus erhält, und aktiviert ist. Dadurch wird den Benutzer ermitteln, welches Element zu Untermenü gehört.  
  
![Das Element, das dem Fokus Kontext Menü Gewinne, um Benutzer zu benachrichtigen, welches Element generiert wurde, wurde ausgewählt.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Das Element, das dem Fokus Kontext Menü Gewinne, um Benutzer zu benachrichtigen, welches Element generiert wurde, wurde ausgewählt.
  
#### <a name="keyboard"></a>Tastatur  
Die Strukturansicht sollte die Möglichkeit, Elemente auswählen, und Erweitern/Reduzieren von Knoten mithilfe der Tastatur bereitzustellen. Dadurch wird sichergestellt, dass Navigation unsere Eingabehilfen-Anforderungen erfüllt.  
  
##### <a name="tree-view-control"></a>Strukturansicht-Steuerelement  
Visual Studio-Struktur-Steuerelemente sollten allgemeine Tastaturnavigation befolgen:  
  
-   **Pfeil nach oben:** Elemente auswählen, indem Sie die Struktur nach oben verschieben  
  
-   **Pfeil nach unten:** Elemente auswählen, indem Sie unten in der Struktur verschieben  
  
-   **Pfeil nach rechts:** erweitern Sie den Knoten in der Struktur  
  
-   **Pfeil nach links:** Reduzieren eines Knotens in der Struktur  
  
-   **Geben Sie die Schlüssel:** zu initiieren, laden, das ausgewählte Element ausführen  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (Strukturansicht und Rasteransicht)  
Ein Rastersteuerelement ist ein komplexes Steuerelement, das eine Strukturansicht, in einem Raster enthält. Erweitern und Reduzieren von Navigation in der Struktur sollte die gleichen Tastenkombinationen Befehle als eine Strukturansicht mit den folgenden Ergänzungen berücksichtigen:  
  
-   **Pfeil nach rechts:** erweitern Sie den Knoten. Nachdem der Knoten erweitert ist, soll er weiterhin auf die nächste Spalte auf der rechten Seite navigieren. Navigation beendet werden sollte am Ende der Zeile.  
  
-   **Registerkarte ":** Werkzeug dient zum Navigieren, auf die nächste Zelle auf der rechten Seite.  Am Ende der Zeile auf die nächste Zeile weiterhin Navigation.  
  
-   **Umschalt + Tab:** Werkzeug dient zum Navigieren, auf die nächste Zelle auf der linken Seite.  Navigation weiterhin am Anfang der Zeile, aus der äußersten rechten Zelle in der vorherigen Zeile.  
  
![Ein Rastersteuerelement in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Ein Rastersteuerelement in Visual Studio
