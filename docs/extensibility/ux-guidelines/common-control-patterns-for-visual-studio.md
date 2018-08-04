---
title: Allgemeine Steuerelementmuster für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e10fdcea9819c34735f285c78a0e2ebb0650f64a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512316"
---
# <a name="common-control-patterns-for-visual-studio"></a>Allgemeine Steuerelementmuster für Visual Studio
##  <a name="BKMK_CommonControls"></a> Allgemeine Steuerelemente  
  
### <a name="overview"></a>Übersicht  
Allgemeine Steuerelemente bilden zusammen den Großteil der Benutzeroberfläche in Visual Studio. Führen Sie die am häufigsten verwendeten Steuerelemente in Visual Studio-Benutzeroberfläche verwendet sollte die [Richtlinien für Windows Desktop-Interaktion](/windows/desktop/uxguide/controls). Dieses Thema bezieht sich auf Visual Studio und behandelt Situationen oder Details, die die Windows-Richtlinien zu verbessern.  
  
#### <a name="common-controls-in-this-topic"></a>Allgemeine Steuerelemente in diesem Thema  
  
-   [Bildlaufleisten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Felder für die Eingabe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Kombinationsfelder und Dropdown-Listen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Kontrollkästchen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Optionsfelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Gruppe frames](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Schaltflächen und Links](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Strukturansichten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Visuellen Stil  
Die erste, was beim Formatieren von Steuerelementen zu berücksichtigen ist, gibt an, ob die Steuerelemente im Design der Benutzeroberfläche verwendet werden. Steuerelemente in Benutzeroberflächen-Design-Benutzeroberfläche werden und müssen [Schriftschnitt "normal" Windows-Desktop](/windows/desktop/uxguide/controls), was bedeutet, dass sie nicht erneut auf und sollte in ihrer standarddarstellung des Steuerelements angezeigt werden.  
  
-   **Standard (Hilfsprogramm) Dialogfelder:** nicht mit Design. Nicht Re-Vorlage. Die verwenden Sie grundlegende Steuerelement Style-Standardeinstellungen.  
  
-   **Tools, Windows, Dokument-Editoren, Entwurfsoberflächen und mit Design Dialogfelder:** spezielle Design Darstellung, die mit dem Dienst Farbe verwenden.  
  
###  <a name="BKMK_Scrollbars"></a> Bildlaufleisten  
 Bildlaufleisten folgen, sollten Sie [allgemeine Interaktionsmuster für Windows-Bildlaufleisten](/windows/desktop/Controls/about-scroll-bars) es sei denn, sie durch Informationen erweitert sind, wie im Code-Editor.  
  
###  <a name="BKMK_InputFields"></a> Felder für die Eingabe  
 Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für die Textfelder](/windows/desktop/uxguide/ctrl-text-boxes).  
  
#### <a name="visual-style"></a>Visuellen Stil  
  
-   Felder für die Eingabe darf nicht im Hilfsprogramm-Dialogfelder formatiert werden. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.  
  
-   Design Eingabefelder sollte nur in Design Dialog- und Toolfenster verwendet werden.  
  
#### <a name="specialized-interactions"></a>Spezielle Interaktionen  
  
-   Schreibgeschützte Felder müssen einen Hintergrund grau (deaktiviert), aber Standardvordergrund-(aktiv).  
  
-   Erforderliche Felder müssen  **\<erforderlichen >** als Wasserzeichen darin. Sie sollten die Farbe des Hintergrunds außer in seltenen Fällen nicht ändern.  
  
-   Fehler-Überprüfung: finden Sie unter [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Größe Eingabefelder müssen entsprechend den Inhalt, der nicht auf die Breite des Fensters in der sie angezeigt werden, noch die Zeitdauer in einem langen Feld, z. B. einen Pfad nach dem Zufallsprinzip entsprechend angepasst werden. Länge kann darauf hinweisen, dass für den Benutzer Einschränkungen hinsichtlich der Anzahl der Zeichen in das Feld zulässig sind.  
  
     ![Falsche Eingabe Feldlänge: Es ist unwahrscheinlich, dass der Name dieser Länge ist. ] (../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Falsche Eingabe Feldlänge: Es ist unwahrscheinlich, dass der Name dieser Länge ist.
  
     ![Korrigieren Sie die Eingabe der Feldlänge: das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt. ] (../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Korrigieren Sie die Eingabe der Feldlänge: das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Kombinationsfelder und Dropdown-Listen  
Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für Dropdownlisten und Kombinationsfelder](/windows/desktop/uxguide/ctrl-drop).  
  
#### <a name="visual-style"></a>Visuellen Stil  
  
-   Im Hilfsprogramm-Dialogfeldern nicht Re-Vorlage des Steuerelements. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.  
  
-   Führen Sie die standard-Designs für Steuerelemente, in Design-Benutzeroberfläche, Kombinationsfelder und Dropdown-Elemente.  
  
#### <a name="layout"></a>Layout  
Kombinationsfelder und Dropdownlisten sollte Größe angepasst werden, um den Inhalt nicht auf die Breite des Fensters in der sie angezeigt werden, noch die Zeitdauer in einem langen Feld, z. B. einen Pfad nach dem Zufallsprinzip entsprechend anpassen.  
  
![Falsch: die Breite des Dropdown-Liste ist zu lang für den Inhalt, der angezeigt wird. ] (../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Falsch: die Breite des Dropdown-Liste ist zu lang für den Inhalt, der angezeigt wird.
  
![Richtig: der Dropdown-Liste ist die Größe kann Übersetzung anwachsen, aber nicht unnötig lange. ] (../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Richtig: der Dropdown-Liste ist die Größe kann Übersetzung anwachsen, aber nicht unnötig lange. 
  
###  <a name="BKMK_CheckBoxes"></a> Kontrollkästchen  
Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für Kontrollkästchen](/windows/desktop/uxguide/ctrl-check-boxes).  
  
#### <a name="visual-style"></a>Visuellen Stil  
  
-   Im Hilfsprogramm-Dialogfeldern nicht Re-Vorlage des Steuerelements. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.  
  
-   Design-Benutzeroberfläche führen Sie die Kontrollkästchen der standard-Designs für Steuerelemente.  
  
#### <a name="specialized-interactions"></a>Spezielle Interaktionen  
  
-   Interaktion mit einem Kontrollkästchen muss nie ein Dialogfeld angezeigt, oder navigieren Sie zu einem anderen Bereich.  
  
-   Richten Sie die Kontrollkästchen mit der Baseline der ersten Zeile des Texts.  
  
     ![Falsch: das Kontrollkästchen wird auf der Text zentriert. ] (../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Falsch: das Kontrollkästchen wird auf der Text zentriert.
  
     ![Richtig: das Kontrollkästchen wird mit der ersten Zeile des Texts ausgerichtet. ] (../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Richtig: das Kontrollkästchen wird mit der ersten Zeile des Texts ausgerichtet.
  
###  <a name="BKMK_RadioButtons"></a> Optionsfelder  
Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für die Optionsfelder](/windows/desktop/uxguide/ctrl-radio-buttons).  
  
#### <a name="visual-style"></a>Visuellen Stil  
Führen Sie im Hilfsprogramm-Dialogfeldern nicht Stil Optionsfelder aus. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.  
  
#### <a name="specialized-interactions"></a>Spezielle Interaktionen  
Es ist nicht erforderlich, einen Gruppen Frame zu verwenden, zum Einschließen von Optionsfeld-Optionen, es sei denn, die Unterscheidung der Gruppe in einem engen Layout beibehalten werden sollen.  
  
###  <a name="BKMK_GroupFrames"></a> Gruppe frames  
Führen Sie für typische Interaktionsverhalten ergibt, der [Windows-Desktop-Richtlinien für die Gruppe Frames](/windows/desktop/uxguide/ctrl-group-boxes).  
  
#### <a name="visual-style"></a>Visuellen Stil  
Im Hilfsprogramm formatieren-Dialogfeldern, nicht Gruppe Frames. Verwenden Sie das grundlegende Format systemintern auf das Steuerelement.  
  
#### <a name="layout"></a>Layout  
  
-   Es ist nicht erforderlich, einen Gruppen Frame zu verwenden, zum Einschließen von Optionsfeld-Optionen, es sei denn, die Unterscheidung der Gruppe in einem engen Layout beibehalten werden sollen.  
  
-   Verwenden Sie niemals einen Gruppenrahmen für ein einzelnes Steuerelement an.  
  
-   Manchmal ist es akzeptabel, eine horizontale Trennlinie statt Gruppen Frame-Container zu verwenden.  
  
##  <a name="BKMK_TextControls"></a> Textsteuerelemente

### <a name="static-text-fields"></a>Statischer Text-Felder

Ein statischer Text-Feld zeigt schreibgeschützte Informationen und kann nicht vom Benutzer ausgewählt werden. Vermeiden Sie es für alle Text, den der Benutzer in die Zwischenablage kopieren möchten. Schreibgeschützten statischer Text kann jedoch eine Änderung am Zustand entsprechend ändern. Im folgenden Beispiel wird das statischen Text unter Änderungen der Informationen in das Textfeld der Stamm-Namespace darüber vorgenommen Änderungen widergespiegelt werden.

Es gibt zwei Möglichkeiten, um statischen Textinformationen anzuzeigen.

Statischer Text kann auf einen eigenen in einem Dialogfeld, ohne alle Kapselung bei befindet sich kein Konflikt Gruppierung sein. Entscheiden Sie, ob die zusätzlichen Zeilen eines Felds wirklich erforderlich sind. Ein Beispiel ist die Anzeige von einen Verzeichnispfad ein Abschnitt durch eine Gruppenlinie erstellt, wie unten dargestellt:  

![Statischer Text Informationen in Textsteuerelementen](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Statischer Text-Informationen im Text-Steuerelemente

In einem Dialogfeld, in dem anderen gruppierten Bereiche vorhanden sind und die Kapselung der Informationen hilft Lesbarkeit und wenn ein Abschnitt ausgeblendet oder angezeigt werden kann (wie in der **Fenster "Eigenschaften"** Beschreibungsbereich) oder mit ähnlichen Benutzeroberfläche konsistent sein sollen Fügen Sie den statischen Text in ein Feld ein. Diese Gruppe muss eine einzelne Regel und farbig und die `ButtonShadow`:

![Statischer Text in das Fenster "Eigenschaften"](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Statischer Text in das Fenster "Eigenschaften"

### <a name="read-only-text-box"></a>Nur-Lese Textfeld

Dadurch können die Benutzer wählen Sie den Text in das Feld jedoch nicht bearbeiten. Diese Felder werden durch die üblichen 3D-ziseliert mit umrandet eine `ButtonShadow` füllen.

Ein Textfeld kann aktiv (bearbeitbar), wenn ein Benutzer eine zugeordnete Steuerelement, z. B. ein Kontrollkästchen aktivieren bzw. deaktivieren, oder ein Optionsfeld auswählen/Auswahl aufheben ändert. Z. B. in der **Tools &gt; Optionen** Seite wie unten beschrieben, die **Startseite** Textfeld wird aktiviert, wenn die **Standard verwenden** das Kontrollkästchen deaktiviert ist.

![Zeigt inaktive und aktive Zustände im Nur-Lese Textfeld](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Zeigt inaktive und aktive Zustände im Nur-Lese Textfeld

### <a name="using-text-in-dialogs"></a>Dabei wird Text in Dialogfeldern

Wichtige Richtlinien für den Text in Dialogfeldern:

-   Bezeichnungen für Textfelder, Listenfelder und Frames in Unthemed Dialogfeldern starten mit einem Verb, einem großen Anfangsbuchstaben auf nur das erste Wort haben und mit einem Doppelpunkt enden.

    > Führen Sie die Text-Steuerelemente in Dialogfeldern mit Design versehen [Windows-desktop-UX-Richtlinien](/windows/desktop/uxguide/top-violations) und akzeptieren keine Interpunktion, mit Ausnahme von Fragezeichen in Links zu Hilfethemen.

-   Bezeichnungen für Kontrollkästchen und Optionsfelder beginnen mit einem Verb, auf das erste Wort, einem großen Anfangsbuchstaben und ohne schließende Satzzeichen.

-   Bezeichnungen für Schaltflächen, Menüs, Menüelemente und Registerkarten über Großbuchstaben am Wortanfang für jedes Wort (in Versalien) verfügen.

-   Bezeichnung Terminologie sollte mit ähnlichen Bezeichnungen in anderen Dialogfeldern entsprechen.

-   Wenn möglich, damit einen Writer/Editor schreiben oder den Text zu genehmigen, bevor es dem Entwickler für die Implementierung wird.

-   Alle Steuerelemente müssen Bezeichnungen nur unter besonderen Umständen in die TAB-Taste ausreichend ist.
Verwenden Sie bei Bedarf-Hilfetext.

### <a name="helper-text"></a>Hilfstext

Enthalten in Dialogfeldern, um dem Benutzer das Dialogfeld zu verstehen oder die auszuführende Aktion an. Hilfstext sollte nur bei Bedarf verwendet werden, vermeiden, dass einfache Dialogfelder. Die zwei Varianten der Hilfetext sind Dialogfeld und Wasserzeichentext an.

Führen Sie gängige Speicherorte für Hilfetext und selektiv mit der Einführung neuer Bereiche. Häufige Szenarien für Hilfetext sind:

-   Der Hilfetext in Dialogfeldern, gerne weitere Richtung Informationen für die Interaktion mit einem komplexen Dialogfeld.

-   Wasserzeichentext in leere Toolfenster oder Dialogfeldern, zu erklären, warum kein Inhalt angezeigt wird.

-   Ein Beschreibungsbereich, in der am unteren Rand wie die **Fenster "Eigenschaften"**.

-   Wasserzeichen Sie in einem leeren-Editor, um wird erläutert, welche Aktion der Benutzer ergreifen sollte, um zu beginnen.
  
### <a name="dialog-helper-text"></a>Dialogfeld-Hilfetext

Ein Benutzer Experience Designer kann hilfreich sein zu bestimmen, wann Hilfetext geeignet ist. Der Designer kann definieren, wo Hilfetext sowie den allgemeinen Inhalt angezeigt wird. Benutzerunterstützung kann, schreiben und den tatsächlichen Text ändern.

### <a name="watermarks"></a>Wasserzeichen

Dialogfelder profitieren Sie von etwas anderes Wasserzeichen Richtlinien. Da ein Dialogfeld ausgelastet ist und viele Elemente der Benutzeroberfläche (Beschriftungen, Hinweistext, Schaltflächen und anderen Containersteuerelementen mit Text), insbesondere angezeigt werden kann, wenn diese in Schwarz angezeigt werden, stehen Wasserzeichen ggf. besser in dunkelgrau (VSColor: `ButtonShadow`). In der Regel ein Wasserzeichen angezeigt wird, in ein Steuerelement wie ein Listenfeld, das mit einem weißen Hintergrund (VSColor: `Window`).

-   Der Text wird angezeigt, in dunkelgrau (VSColor: `ButtonShadow`). Aber wenn der Grenzwert auf einem mittleren Grau oder andere farbig angezeigt wird (VSColor: `ButtonFace`) im Hintergrund und vorhanden ist, über die Lesbarkeit betreffen, fahren Sie mit schwarzem Text (VSColor: `WindowText`).

-   Wasserzeichen können linksbündig oder zentriert werden. Wenden Sie Regeln für standard, wenn Ausrichtung Entscheidungen treffen. Der Grenzwert kann nicht über die Hintergründe ausgewählt werden.

![Beispiel für Wasserzeichen](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Beispiel für Wasserzeichen

### <a name="context-specific-dynamic-text"></a>Kontextspezifische (dynamisch) text

Dynamischer Text kann verwendet zwei Arten in einem Dialogfeld oder nicht modale Benutzeroberfläche sein: entweder als eine dynamische Beschriftung oder als dynamische Inhalte.

-   Dynamische Beschriftung: eine häufige Verwendung des dynamischen Texts in aussagekräftigen Bereiche, die Informationen für das ausgewählte Element, z. B. in einem Dialogfeld zur Verfügung, und eine Liste von Elementen und Eigenschaften für diese Elemente in einem Raster auf der rechten Seite angezeigt enthält wird. Die Bezeichnung für das Eigenschaftenraster kann dynamisch sein, damit das Raster auf der rechten Seite Informationen für dieses bestimmte Element angezeigt, wenn ein Element auf der linken Seite ausgewählt ist, wird.

-   Dynamischer Text: kann in Fällen, in denen bestimmte Informationen und nicht allgemeine Informationen auf diese Weise angezeigt werden müssen, jedoch sollte geachtet werden, nicht zu viele, nützlich sein.

Wenn Sie Benutzer haben die Möglichkeit, die Informationen kopieren möchten, sollte die dynamischer Text in einem schreibgeschützten Textfeld.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Schaltflächen und Links  
  
### <a name="overview"></a>Übersicht  
Führen Sie die Schaltflächen und Link-Steuerelemente (links) sollten [grundlegende Windows-Desktop-Hinweise zu Links](/windows/desktop/uxguide/ctrl-links) für die Nutzung formulierungen, Skalierung und Abstand.  
  
### <a name="choosing-between-buttons-and-links"></a>Auswählen zwischen Schaltflächen und links  
In der Vergangenheit wurden Schaltflächen für Aktionen verwendet, und Links für die Navigation reserviert wurde. Schaltflächen können in allen Fällen verwendet werden, aber die Rolle des Links wurde in Visual Studio erweitert, damit Schaltflächen und Links unter bestimmten Umständen mehr austauschbar sind.  
  
Wann sollte die Befehlsschaltflächen verwenden?  
  
-   Primären Befehle  
  
-   Anzeigen von Windows verwendet, um Eingaben zu erfassen oder Entscheidungen, auch wenn sie sekundäre Befehle  
  
-   Destruktive oder Rückgängig-Aktionen  
  
-   Engagement-Schaltflächen im Assistenten und Seite-flows  
  
Vermeiden Sie die Schaltflächen im Toolfenster, oder wenn Sie mehr als zwei Wörter für die Bezeichnung benötigen. Links können längere Beschriftungen haben.  
  
 Wann sollte die Links zu verwenden?  
  
-   Navigation zu einem anderen Fenster, ein Dokument oder eine Webseite  
  
-   Situationen, in denen eine längere Bezeichnung oder einen kurzen Satz zum Beschreiben der Zweck der jeweiligen Aktion erforderlich.  
  
-   Raum, in denen eine Schaltfläche die Benutzeroberfläche überlasten würden, vorausgesetzt, dass die Aktion nicht destruktive oder nicht umkehrbar ist  
  
-   Aufhebung Hervorhebungseffekt sekundäre Befehle in Situationen mit zahlreichen Befehlen  
  
#### <a name="examples"></a>Beispiele  
![-Befehl verwendet werden, in der Statusmeldung Infoleiste](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />-Befehl verwendet wird, in der Statusmeldung Infoleiste links
  
![Links im CodeLens-Popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Links im CodeLens-Popup
  
![Für sekundäre Befehle verwendet werden sollen, in denen Schaltflächen zu viel Aufmerksamkeit gewinnen würde](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Links, die für sekundäre Befehle Schaltflächen würden, in denen zu viel Aufmerksamkeit gewinnen.
  
### <a name="common-buttons"></a>Allgemeine Schaltflächen  
  
#### <a name="text"></a>Text  
Führen Sie die Richtlinien für das Schreiben in [UI Text und die Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Visuellen Stil  
  
##### <a name="standard-unthemed"></a>Standard (Unthemed)  
Die meisten Schaltflächen in Visual Studio im Hilfsprogramm-Dialogfelder angezeigt, und sollte nicht formatiert werden. Sie sollten die standard-Darstellung der Schaltflächen widerspiegeln, wie vom Betriebssystem vorgegebenen.  
  
##### <a name="themed"></a>Design  
In einigen Fällen in der formatierten UI können Schaltflächen verwendet werden, und diese Schaltflächen müssen ordnungsgemäß formatiert werden. Finden Sie unter [Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) Informationen zu Design-Steuerelementen.  
  
### <a name="special-buttons"></a>Besondere Schaltflächen  
  
#### <a name="browse-buttons"></a>Durchsuchen Sie Schaltflächen für das...  
**[Durchsuchen...]**  Schaltflächen werden im Raster, Dialogfelder und Toolfenster und andere Elemente der Benutzeroberfläche für das nicht modale verwendet. Sie zeigen eine Auswahl, die den Benutzer beim Ausfüllen der eines Werts in ein Steuerelement hilft. Es gibt zwei Varianten dieser Schaltfläche, lange und kurze.  
  
![Die lange Schaltfläche [durchsuchen...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Die lange Schaltfläche [durchsuchen...]
  
![Die Schaltfläche mit den Auslassungspunkten nur kurze [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Die Schaltfläche mit den Auslassungspunkten nur kurze [...]
  
Wenn die kurze nur mit den Auslassungszeichen-Schaltfläche verwenden:  
  
-   Wenn es mehr als eine lange **[durchsuchen...]**  Schaltfläche in einem Dialogfeld an, wie wenn mehrere Felder für das Durchsuchen von zulässt. Verwenden Sie die kurzfristige **[...]**  klicken, die verwirrend Zugriffsschlüssel erstellt diese Situation zu vermeiden (**& Durchsuchen** und **du & rchsuchen** im gleichen Dialogfeld "").  
  
-   In einem engen Dialogfeld, oder wenn besteht keine angemessene Möglichkeit, auf die Schaltfläche "lange" abgelegt.  
  
-   Wenn die Schaltfläche in einem Datenraster-Steuerelement angezeigt wird.  
  
Richtlinien für die mithilfe der Schaltfläche:  
  
-   Verwenden Sie keine Zugriffstaste. Mithilfe der Tastaturfokus für den Zugriff auf muss der Benutzer aus dem angrenzenden Steuerelement Registerkarte. Stellen Sie sicher, dass die Aktivierreihenfolge ist, dass Schaltfläche "Durchsuchen" sofort nach dem Feld liegt, die sie eingeben wird. Verwenden Sie niemals einen Unterstrich, unter dem ersten Zeitraum.  
  
-   Legen Sie die Microsoft Active Accessibility (MSAA) **Namen** Eigenschaft **durchsuchen...**  (einschließlich der drei Punkte) damit, die Bildschirm Leser liest es als "Durchsuchen" und nicht "Punkt-Punkt-Punkt" oder "Punkt-Punkt-Punkt." Für verwaltete Steuerelemente, bedeutet dies die Einstellung der **Control.AccessibleName** Eigenschaft.  
  
-   Verwenden Sie niemals ein Auslassungszeichen **[...]**  Schaltfläche für alle Elemente mit Ausnahme von einer Aktion "Durchsuchen". Angenommen, Sie müssen eine **[Neu]**  Schaltfläche aber nicht ausreichend Platz für den Text ein, und klicken Sie dann das Dialogfeld muss geändert werden.  
  
##### <a name="sizing-and-spacing"></a>Größenanpassung und Abstand  
![Schaltflächen [durchsuchen...] größenanpassung: standard-Version beträgt 75 x 23 Pixel, die Kurzversion ist 26 x 23 Pixel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Festlegen der Größe für Schaltfläche [Durchsuchen...]
  
![Leerzeichen [durchsuchen...] Schaltflächen: der Abstand zwischen verwandten Steuerelement und standard Pixel der Durchsuchen-Schaltfläche "7", Abstand zwischen den dazugehörigen Steuerelement und kurze Durchsuchen-Schaltfläche 5 Pixel](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Festlegen der Abstände für Schaltfläche [Durchsuchen...]
  
#### <a name="graphical-buttons"></a>Grafische Schaltflächen  
Einige Schaltflächen sollten immer ein Bild und nie enthalten Text zum Einsparen von Speicherplatz und Lokalisierung-Probleme zu vermeiden. Diese werden häufig in Feld dateiöffnungs- und andere sortierbaren Listen verwendet.  
  
> **Hinweis:** Benutzer sich nicht auf diese Schaltflächen (es gibt keine Zugriffsschlüssel) Registerkarte, daher platzieren Sie sie in einer sinnvollen Reihenfolge. Zuordnung der `name` Eigenschaft der Schaltfläche auf die Aktion, die es dauert, sodass Bildschirmsprachausgaben richtig Schaltflächenaktion interpretiert.  
  
| Funktion | Schaltfläche |  
| --- | --- |  
| Hinzufügen | ![Grafische Schaltfläche "hinzufügen"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Remove | ![Grafische Schaltfläche "Entfernen",](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Alle hinzufügen | ![Grafische "Schaltfläche"Alles hinzufügen](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Entfernen Sie alle | ![Grafische "Schaltfläche"Alle entfernen](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Nach oben | ![Grafische Schaltfläche "Nach oben"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Nach unten | ![Grafische Schaltfläche "Nach unten"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Löschen | ![Grafische Schaltfläche "Löschen",](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Größenanpassung und Abstand  
Ändern der Größe für grafische Schaltflächen, die identisch mit der Kurzversion des ist der **[durchsuchen...]**  Schaltfläche (26 x 23 Pixel):  
  
![Darstellung der ein Bild auf die Schaltfläche mit und ohne transparenter Farbe](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Darstellung der ein Bild auf die Schaltfläche mit und ohne transparenter Farbe
  
### <a name="hyperlinks"></a>Hyperlinks  
Hyperlinks eignen sich gut für die Navigation-basierten Aktionen, wie das Öffnen eines Hilfethemas, modales Dialogfeld, oder -Assistenten. Wenn ein Link für einen Befehl verwendet wird, sollten sie immer eine sichtbare und merkliche Änderung an der Benutzeroberfläche anzeigen. Aktionen, die auf eine Aktion (z. B. speichern, auf "Abbrechen", und löschen) werden im Allgemeinen besser kommuniziert mithilfe einer Schaltfläche.  
  
#### <a name="writing-style"></a>Schreibstil  
Führen Sie die [Windows-Desktop-Leitfaden für den Text der Benutzeroberfläche](/windows/desktop/uxguide/text-ui). Verwenden Sie nicht "Erfahren Sie mehr über," "Erzählen mir Weitere Informationen zu" oder "Get-Help dabei"-Ausdruck. Stattdessen einen Ausdruck Link Hilfetext in Bezug auf die primäre Frage beantwortet, indem der Inhalt der Hilfe. Z. B. "**wie füge ich einen Server zum Server-Explorer?**"  
  
#### <a name="visual-style"></a>Visuellen Stil  
  
-   Links sollten immer verwenden [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Wenn Sie ein Link nicht richtig formatiert wird, blinkt Rot, wenn aktive oder eine andere Farbe angezeigt, nachdem der aufgerufen wird.  
  
-   Nehmen Sie die unterstreichungen an das Steuerelement mit dem Zustand gespeichert, es sei denn, der Link ein Satz Fragment innerhalb eines vollständigen Satzes an, wie in einem Wasserzeichen ist nicht.  
  
-   Unterstreichungen sollte nicht bei einer mauszeigerbewegung über angezeigt werden. Stattdessen wird das Feedback für den Benutzer, dass die Verbindung aktiv ist eine geringfügige Farbe ändern und den entsprechenden Link-Cursor.  
  
##  <a name="BKMK_TreeViews"></a> Strukturansichten  
  
Strukturansichten bieten eine Möglichkeit zum Organisieren von komplexen in übergeordneten / untergeordneten Gruppen aufgeführt. Ein Benutzer kann erweitern oder reduzieren die übergeordnete Gruppen zum Anzeigen oder Ausblenden von zugrunde liegenden untergeordneten Elemente. Jedes Element in einer Strukturansicht kann ausgewählt werden, um weitere Aktion bereitzustellen.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Struktur anzeigen visuellen Stil  
  
#### <a name="expanders"></a>Erweiterungen  
Strukturansicht-Steuerelemente müssen auf die Expander-Steuerelement von Windows und Visual Studio verwendet werden, entsprechen. Ein Expander-Steuerelement wird von jedem Knoten verwendet, um ein- oder Ausblenden von zugrunde liegenden Elementen. Verwenden eines Expander-Steuerelements ist die Konsistenz für Benutzer, die verschiedenen Ansichten in Windows und Visual Studio auftreten können.  
  
![Richtig: ordnungsgemäßes Format mithilfe eines Expander-Steuerelements Strukturansichtsknotens](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Richtig: ordnungsgemäßes Format Strukturansichtsknotens mithilfe eines Expander-Steuerelements
  
![Falsche: falsche Darstellung Strukturansichtsknoten](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Falsche: falsche Darstellung Strukturansichtsknoten
  
#### <a name="selection"></a>Auswahl  
Wenn ein Knoten in der Strukturansicht ausgewählt ist, sollten die Hervorhebung um die gesamte Breite des Strukturansicht-Steuerelement erweitern. Dadurch können Benutzer, die eindeutig auf welches Element identifizieren sie ausgewählt haben. Farben Auswahl sollte es sich um das aktuelle Visual Studio-Design entsprechen.  
  
![Richtig: Hervorheben des ausgewählten Knotens passt die gesamte Breite des Strukturansicht-Steuerelement. ] (../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Richtig: Hervorheben des ausgewählten Knotens passt die gesamte Breite des Strukturansicht-Steuerelement.
  
![Falsche: Hervorheben des ausgewählten Knotens passt nicht die gesamte Breite des Strukturansicht-Steuerelement. ] (../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Falsche: Hervorheben des ausgewählten Knotens passt nicht die gesamte Breite des Strukturansicht-Steuerelement.
  
#### <a name="icons"></a>Symbole  
Symbole sollte nur in der Strukturansicht-Steuerelemente verwendet werden, wenn sie bei der Unterschiede zwischen Elementen visuell zu identifizieren. Symbole sollten im Allgemeinen nur in heterogenen Listen verwendet werden in denen die Symbole Informationen zur Unterscheidung von den Typ der Elemente enthalten. In einer homogenen Liste mithilfe von Symbolen kann häufig als Rauschen betrachtet werden und sollte vermieden werden. In diesem Fall kann das Symbol für die Gruppe (übergeordnet) den Typ der Elemente im vermitteln. Die Ausnahme von dieser Regel wäre, wenn das Symbol dynamisch ist und verwendet wird, um den Status anzugeben.  
  
#### <a name="scroll-bars"></a>Bildlaufleisten  
Bildlaufleisten soll immer ausgeblendet werden, wenn der Inhalt in der Strukturansicht-Steuerelement passt. Es ist ausgeblendet oder semitransparente in einem bildlauffähigen Fenster und angezeigt werden, wenn das Fenster mit der Strukturansicht den Fokus besitzt, oder bei einer mauszeigerbewegung über die der Struktur anzeigen, selbst für Bildlaufleisten zulässig.  
  
![Da der Inhalt die Grenzen des Strukturansicht-Steuerelement überschritten haben, werden beide vertikalen und horizontalen Bildlaufleisten angezeigt. ] (../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Da der Inhalt die Grenzen des Strukturansicht-Steuerelement überschritten haben, werden beide vertikalen und horizontalen Bildlaufleisten angezeigt.
  
###  <a name="BKMK_TreeViewInteractions"></a> Struktur anzeigen Interaktionen  
  
#### <a name="context-menus"></a>Kontextmenüs  
Knoten einer Strukturansicht kann es sich um die Optionen des Untermenüs in einem Kontextmenü offenlegen. Das tritt in der Regel auf, wenn ein Benutzer ein Element mit der rechten Maustaste, oder drücken die Menütaste auf einer Windows-Tastatur mit das ausgewählte Element. Es ist wichtig, dass der Knoten den Fokus erhält, und aktiviert ist. Dadurch wird den Benutzer, welches Element identifizieren das Untermenü, angehört.  
  
![Das Element, das dem Kontext-Menü Gewinne Fokus zur Benachrichtigung des Benutzers welches Element generiert hat wurde ausgewählt. ] (../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Das Element, das dem Kontext-Menü Gewinne Fokus zur Benachrichtigung des Benutzers welches Element generiert hat wurde ausgewählt.
  
#### <a name="keyboard"></a>Tastatur  
Die Strukturansicht sollte die Möglichkeit bieten, wählen Sie Elemente, und Erweitern/Reduzieren von Knoten, die mithilfe der Tastatur. Dadurch wird sichergestellt, dass Navigation unsere Anforderungen zur Barrierefreiheit erfüllt.  
  
##### <a name="tree-view-control"></a>Strukturansicht-Steuerelement  
Visual Studio-Struktur-Steuerelemente sollten allgemeine Tastaturnavigation ausführen:  
  
-   **Oben-Taste:** Elemente auswählen, indem Sie der Struktur nach oben verschieben  
  
-   **Pfeil nach unten:** Elemente auswählen, indem Sie in der Struktur nach unten verschieben  
  
-   **Pfeil nach rechts:** erweitern Sie den Knoten in der Struktur  
  
-   **Pfeil nach links:** Reduzieren eines Knotens in der Struktur  
  
-   **Geben Sie Schlüssel:** zu initiieren, geladen werden, führen Sie die ausgewählten Elements  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (Strukturansicht und Rasteransicht)  
Ein Rastersteuerelement ist ein komplexes Steuerelement, das eine Strukturansicht, in einem Raster enthält. Erweitern reduzieren, und Navigieren durch die Struktur sollte die gleichen Tastenkombinationen Befehle als eine Strukturansicht mit den folgenden Ergänzungen beachten:  
  
-   **Pfeil nach rechts:** erweitern Sie den Knoten. Nachdem der Knoten erweitert ist, soll er weiterhin auf die nächste Spalte auf der rechten Seite navigieren. Navigation sollte am Ende der Zeile zu beenden.  
  
-   **Registerkarte ":** Werkzeug dient zum Navigieren zur nächsten Zelle auf der rechten Seite.  Am Ende der Zeile wird Sie Navigation zur nächsten Zeile fortgesetzt.  
  
-   **Umschalt + Tab:** Werkzeug dient zum Navigieren zur nächsten Zelle auf der linken Seite.  Navigation weiterhin am Anfang der Zeile, aus der äußersten rechten Zelle in der vorherigen Zeile.  
  
![Ein Rastersteuerelement in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Ein Rastersteuerelement in Visual Studio