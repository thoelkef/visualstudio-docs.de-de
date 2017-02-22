---
title: "Allgemeine Steuerelementmuster f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Allgemeine Steuerelementmuster f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> Allgemeine Steuerelemente  
  
### Übersicht  
 Allgemeine Steuerelemente stellen den Großteil der Benutzeroberfläche in Visual Studio. Am häufigsten verwendeten Steuerelemente, die in der Visual Studio\-Schnittstelle verwendet befolgen die [Richtlinien für Windows\-Desktop\-Interaktion](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Dieses Dokument bezieht sich auf Visual Studio und umfasst spezielle Situationen oder Informationen, die die Windows\-Richtlinien zu erweitern.  
  
#### Allgemeine Steuerelemente in diesem Thema  
  
-   [Bildlaufleisten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Eingabefelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Kombinationsfelder und Dropdown-Listen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Kontrollkästchen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Optionsfelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Gruppe frames](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Schaltflächen und hyperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Strukturansichten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### Visueller Stil  
 Berücksichtigen beim Formatieren von Steuerelementen als Erstes ist, ob die Steuerelemente in Design\-Benutzeroberfläche verwendet werden. Steuerelemente in Benutzeroberflächen\-Design\-Benutzeroberfläche werden und muss [Windows\-Desktop\-Formatvorlage](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), was bedeutet, dass sie nicht auf Vorlagen basierende Re und ihre Darstellung des Standard\-Steuerelements angezeigt werden soll.  
  
-   **Standard \(Hilfsprogramm\) Dialoge:** nicht Design. Führen Sie keine Re\-Vorlage. Die verwenden Sie grundlegende Steuerelement Stil Standardeinstellungen.  
  
-   **Toolfenstern, Dokument\-Editoren, Entwurfsoberflächen und versehene Dialoge:** spezielle versehene Darstellung, die mit dem Dienst Farbe verwenden.  
  
###  <a name="BKMK_Scrollbars"></a> Bildlaufleisten  
 Bildlaufleisten befolgen [Allgemeine Interaktion Muster für Windows\-Bildlaufleisten](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) wenn sie mit Informationen zum Inhalt, z. B. im Code\-Editor ergänzt werden.  
  
###  <a name="BKMK_InputFields"></a> Eingabefelder  
 Bei normalen Interaktionsverhalten ergibt, befolgen Sie die [Windows\-Desktop\-Richtlinien für die Textfelder](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### Visueller Stil  
  
-   Felder sollten nicht im Hilfsprogramm Dialoge formatiert werden. Verwenden Sie das grundlegende Format, das an das Steuerelement.  
  
-   Design Eingabefelder sollte nur in versehene Dialogfelder und Toolfenster verwendet werden.  
  
#### Spezielle Aktivitäten  
  
-   Schreibgeschützte Felder müssen einen Hintergrund grau \(deaktiviert\), aber Vordergrund als Standardeinstellung \(aktiv\).  
  
-   Erforderliche Felder müssen **\< erforderlich \>** als Wasserzeichen darin zu speichern. Sie sollten die Farbe des Hintergrunds außer in seltenen Fällen nicht ändern.  
  
-   Fehler\-Überprüfung: finden Sie unter [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Eingabefelder sollte Größe geändert werden, um den Inhalt nicht auf die Breite des Fensters in der sie angezeigt werden und die Länge von einem langen Feld, z. B. einen Pfad nach dem Zufallsprinzip entsprechend anpassen. Länge ist möglicherweise ein Anzeichen für den Benutzer beschränkt, wie viele Zeichen im Feld zulässig sind.  
  
     ![Incorrect input field control width](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707\-01\_IncorrectInputFieldControl")   
     **Falsche Eingabe Feldlänge: Es ist unwahrscheinlich, dass der Name dieser Länge.**  
  
     ![Correct input field control width](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707\-02\_CorrectInputFieldControl")   
     **Eingabefeld Länge zu beheben: das Eingabefeld für den erwarteten Inhalt eine angemessene Breite ist.**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Kombinationsfelder und Dropdown\-Listen  
 Bei normalen Interaktionsverhalten ergibt, befolgen Sie die [Windows\-Desktop\-Richtlinien für Listenfelder und Kombinationsfelder](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### Visueller Stil  
  
-   Führen Sie im Hilfsprogramm\-Dialogfelder nicht Re\-Vorlage des Steuerelements. Verwenden Sie das grundlegende Format, das an das Steuerelement.  
  
-   Führen Sie in der Benutzeroberfläche, Kombinationsfelder und Dropdownlisten die standard\-Designs für Steuerelemente aus.  
  
#### Layout  
 Auswahllisten und Kombinationsfelder sollten Größe geändert werden, den Inhalt, nicht auf die Breite des Fensters in der sie angezeigt werden und die Länge von einem langen Feld, z. B. einen Pfad nach dem Zufallsprinzip entsprechend angepasst.  
  
 ![Incorrect drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707\-03\_IncorrectDropDownLayout")  
  
 **Falsche Feldlänge für ein Dropdown\-Steuerelement**  
  
 ![Correct drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707\-04\_CorrectDropDownLayout")  
  
 **Richtige Feldlänge für ein Dropdown\-Steuerelement**  
  
###  <a name="BKMK_CheckBoxes"></a> Kontrollkästchen  
 Bei normalen Interaktionsverhalten ergibt, befolgen Sie die [Windows\-Desktop\-Richtlinien für das Kontrollkästchen](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### Visueller Stil  
  
-   Führen Sie im Hilfsprogramm\-Dialogfelder nicht Re\-Vorlage des Steuerelements. Verwenden Sie das grundlegende Format, das an das Steuerelement.  
  
-   Kontrollkästchen folgen Design\-Benutzeroberfläche die standard\-Designs für Steuerelemente.  
  
#### Spezielle Aktivitäten  
  
-   Interaktion mit einem Kontrollkästchen muss nie ein Dialogfeld angezeigt, oder navigieren Sie zu einem anderen Bereich.  
  
-   Richten Sie die Kontrollkästchen an der Grundlinie der ersten Zeile des Texts.  
  
     ![Incorrect check box alignment](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707\-05\_IncorrectCheckBoxAlign")   
     **Ausrichtung für Kontrollkästchen falsch: das Kontrollkästchen wird der Text zentriert.**  
  
     ![Correct check box alignment](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707\-06\_CorrectCheckBoxAlign")   
     **Beheben Sie das Kontrollkästchen Ausrichtung: das Kontrollkästchen die Grundlinie der ersten Textzeile ausgerichtet ist.**  
  
###  <a name="BKMK_RadioButtons"></a> Optionsfelder  
 Bei normalen Interaktionsverhalten ergibt, befolgen Sie die [Windows\-Desktop\-Richtlinien für die Optionsfelder](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### Visueller Stil  
 Führen Sie im Hilfsprogramm\-Dialogfelder nicht Stil Optionsfelder. Verwenden Sie das grundlegende Format, das an das Steuerelement.  
  
#### Spezielle Aktivitäten  
 Es ist nicht erforderlich, einen Gruppenrahmen zu verwenden, um Sender Auswahlmöglichkeiten einzuschließen.  
  
###  <a name="BKMK_GroupFrames"></a> Gruppe frames  
 Bei normalen Interaktionsverhalten ergibt, befolgen Sie die [Windows\-Desktop\-Richtlinien für die Gruppe Frames](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### Visueller Stil  
 Führen Sie im Hilfsprogramm\-Dialogfelder nicht Stil Gruppe Frames. Verwenden Sie das grundlegende Format, das an das Steuerelement.  
  
#### Layout  
  
-   Es ist nicht erforderlich, einen Gruppenrahmen zu verwenden, Radio\-Optionen einschließen, wenn Sie die Unterscheidung der Gruppe in einem engen Layout beibehalten müssen.  
  
-   Verwenden Sie niemals einen Gruppenrahmen für ein einzelnes Steuerelement.  
  
-   Manchmal ist es akzeptabel, eine horizontale Linie statt Gruppen Frame\-Container zu verwenden.  
  
##  <a name="BKMK_TextControls"></a> Textsteuerelemente  
  
### Bezeichnungen  
  
#### Status der aktiven Beschriftung  
  
##### Utility \(standard\) Dialogfelder\)  
  
-   Im Allgemeinen befolgen Sie die Windows\-Desktop\-Anleitung für Bezeichnungen.  
  
-   Dienstprogramm\-Dialoge sollte Bezeichnungen nicht fett, in der standard\-Umgebung Schriftart und Farbe angezeigt werden. Siehe [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
-   Ellipsen sollten immer Bezeichnungen folgen.  
  
##### Signatur \(Design\) Dialogfelder\)  
 Label\-Steuerelemente möglicherweise fett oder hellgrau.  
  
#### Deaktivierte Bezeichnung Status  
 Bezeichnungen sollte es sich um die Darstellung des Steuerelements entsprechen, denen sie zugeordnet sind. Z. B. wenn das zugeordnete Steuerelement deaktiviert ist, werden dann die Bezeichnung grau und deaktiviert angezeigt. Dies erfolgt normalerweise durch das Betriebssystem und erfordert keine besondere Behandlung.  
  
#### Dynamische Beschriftung  
 Dynamische Bezeichnungen ändern sich abhängig von der aktuellen Auswahl. Verwenden Sie nach Möglichkeit dynamische Bezeichnungen in Master\/Detail\-Layouts, um Sie besser verstehen, dass die angezeigte Informationen für eine bestimmte Auswahl und nicht allgemeine Informationen relevant ist.  
  
 ![Dynamic label used with dynamic content](../../extensibility/ux-guidelines/media/070702-01_dynamiclabel.png "070702\-01\_DynamicLabel")  
  
 **Beispiel für eine dynamische Beschriftung mit dynamischen Inhalten**  
  
#### Hinweistext  
 Einige Elemente der Benutzeroberfläche profitieren von Hinweistext den Benutzeroberfläche wozu Benutzer oder die Aktion anzugeben.  
  
-   Hinweistext kann ist am häufigsten am Anfang der Dialogfelder, aber in anderen Bereichen für ein komplexes Steuerelement Grouping\-Anweisung ein.  
  
-   Hinweistext ist nicht interaktiv, jedoch möglicherweise Links zu Hilfethemen.  
  
-   Verwenden von Hinweistext sparsam und nur bei Bedarf.  
  
##### Formatierung  
 Hinweistext sollte Umgebungsschriftart, standard \(nicht\-Design\) Steuerelementtext. Siehe [Schriftarten und Formatierungen für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
 Weitere Informationen zum Schreiben von Hinweistext finden Sie unter [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
 ![Instructional text formatting](../../extensibility/ux-guidelines/media/070702-02_instructionaltextformatting.png "070702\-02\_InstructionalTextFormatting")  
  
 **Hinweistext in einem Visual Studio\-Dialogfeld**  
  
#### Informationstext  
 Informationstext ist Text, der der Benutzer zusätzliche Informationen zu erhalten. Es kann statische oder dynamische oder als eine Benachrichtigung verwendet werden. Ist immer schreibgeschützt, aber wenn der Benutzer die Möglichkeit haben, kopieren Sie die Informationen hilfreich ist, sollten dynamischer Text in einem Steuerelementcontainer wie z. B. ein nur\-Lese Text\-Feld platziert werden.  
  
##### Dynamische \(kontextspezifische\) text  
 Dynamischer Informationstext ändert sich je nach Kontext, z. B. wenn der Benutzer den Fokus wechselt. Häufig, aber nicht immer, dynamischer Inhalt mit einer dynamischen Bezeichnung zugeordnet wird.  
  
 ![Dynamic information text](../../extensibility/ux-guidelines/media/070702-03_informationaldynamictext.png "070702\-03\_InformationalDynamicText")  
  
 **Dynamische Informationstext ändert sich je nach Kontext.**  
  
##### Formatierung  
 Es gibt zwei Möglichkeiten schreibgeschützten Text\-Felder angezeigt werden sollen: entweder direkt auf die Benutzeroberfläche Fläche \(siehe oben\) oder in einem anderen Steuerelement, z. B. eine Gruppe Frame oder das Textfeld enthalten sind. Entweder ist je nach Situation korrekt. Es obliegt dem Funktions\-Designer bestimmen, wie die Informationen schreibgeschützt angezeigt.  
  
 Text kann in einem schreibgeschützten Textfeld sein. Dies gibt im Allgemeinen, dass der Inhalt ausgewählt und kopiert werden kann, obwohl sie bearbeitet werden kann.  
  
 ![Informational text formatting for read&#45;only fields](../../extensibility/ux-guidelines/media/070702-04_informationalformatting.png "070702\-04\_InformationalFormatting")  
  
 **Formatierung von Informationstext für schreibgeschützte Felder**  
  
#### Wasserzeichen  
 Während die Formulierung identisch ist, ist der Unterschied zwischen Wasserzeichen und Hinweistext, Wasserzeichen mit Inhalt ersetzt werden, wenn das Steuerelementfenster nicht leer ist und zu jedem Zeitpunkt Hinweistext bleibt sichtbar.  
  
 Wasserzeichen sollte verwendet werden, wenn ein Fenster oder eine\-Steuerelement leer ist. Sie angeben, welche Schritte durchgeführt werden, um den Bereich zu füllen und Aktionslinks zum Öffnen der entsprechenden Windows, z. B. eine Ziehquelle einschließen.  
  
##### Visueller Stil  
  
-   Wasserzeichen sollten im Fenster horizontal zentriert werden soll.  
  
-   Wasserzeichen sollte zentriert nicht ausgerichtet.  
  
-   Wasserzeichen können vertikal zentriert oder im oberen Bereich positioniert werden. Wenn im oberen Bereich des Bereichs befindet, muss genügend Speicherplatz sein vorhanden oben, damit das Wasserzeichen abhebt.  
  
-   Verwenden der `Environment.GrayText` Schriftfarbe der token und standard\-Umgebung. Hyperlinks verwenden, sollten die standardmäßigen Hyperlink shared\-Token: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, und `Environment.PanelHyperlinkDisabled`.  
  
-   Wasserzeichen können nicht auf den Hintergrund ausgewählt werden  
  
-   Wenn möglich, enthalten Sie Links in das Wasserzeichen der Benutzer beginnen kann.  
  
 ![Watermark text in a designer window](../../extensibility/ux-guidelines/media/070702-05_watermark1.png "070702\-05\_Watermark1")  
  
 ![Watermark text in a tool window](../../extensibility/ux-guidelines/media/070702-06_watermark2.png "070702\-06\_Watermark2")  
  
 **Wasserzeichentext in Visual Studio\-Beispiele**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Schaltflächen und hyperlinks  
  
### Übersicht  
 Schaltflächen und Link\-Steuerelemente \(links\) befolgen [grundlegende Windows\-Desktop Anleitungen auf Hyperlinks](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) für die Verwendung, Text, Größe und Abstände.  
  
### Auswählen zwischen Schaltflächen und links  
 In der Vergangenheit wurden Schaltflächen für Aktionen verwendet und Hyperlinks wurden für die Navigation reserviert. Schaltflächen in allen Fällen verwendet werden, aber die Rolle des Links wurde in Visual Studio erweitert, sodass Schaltflächen und Links unter bestimmten Umständen mehr austauschbar sind.  
  
 Wann Befehlsschaltflächen verwenden:  
  
-   Primäre Befehle  
  
-   Anzeigen von Windows verwendet, um die Eingabe zu erfassen oder die entsprechende Auswahl treffen, auch wenn sie sekundäre Befehle sind  
  
-   Destruktive Aktionen nicht rückgängig gemacht werden  
  
-   Engagement\-Schaltflächen im Assistenten und Seite fließt.  
  
 Vermeiden Sie Befehlsschaltflächen im Toolfenster, oder wenn Sie mehr als zwei Wörter für die Bezeichnung. Links können mehr Bezeichnungen sein.  
  
 Wenn Links zu verwenden:  
  
-   Navigation zu einem anderen Fenster, ein Dokument oder eine Webseite  
  
-   Situationen, in denen eine längere Bezeichnung oder einen kurzen Satz beschreiben Sie den Zweck der jeweiligen Aktion erforderlich  
  
-   Raum, in dem eine Schaltfläche die Benutzeroberfläche überlasten würden, vorausgesetzt, dass die Aktion nicht destruktiven oder nicht rückgängig gemacht werden  
  
-   Deduplizierung Hervorhebungseffekt sekundäre Befehle in Situationen, in denen viele Befehle bestehen  
  
#### Beispiele  
 ![Infobar command links following a status message](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703\-01\_CommandLinkInfobar")  
  
 **Befehl Links im Infoleiste Statusmeldung**  
  
 ![Links used in the CodeLens popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703\-02\_LinksInCodeLens")  
  
 **Links im CodeLens\-Popup**  
  
 ![Links used as secondary commands](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703\-03\_LinksAsSecondaryCommands")  
  
 **Links, die für sekundäre Befehle Schaltflächen würde, in denen zu viel Aufmerksamkeit gewinnen.**  
  
### Allgemeine Schaltflächen  
  
#### Text  
 Befolgen Sie die Richtlinien Schreiben in [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### Visueller Stil  
  
##### Standarddialogfelder  
 Die meisten Schaltflächen in Visual Studio werden im Standarddialogfelder angezeigt und sollte nicht formatiert werden. Sie sollten die standard\-Darstellung der Schaltflächen widerspiegeln, wie vom Betriebssystem vorgegeben.  
  
##### Design  
 In einigen Fällen Schaltflächen formatiertes Benutzeroberfläche verwendet werden können, und diese Schaltflächen entsprechend formatiert werden müssen. Finden Sie unter [Dialogfelder](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) Informationen auf Steuerelemente mit Design.  
  
### Spezielle Schaltflächen  
  
#### Durchsuchen... Schaltflächen  
 **\[Durchsuchen...\]** Schaltflächen werden im Raster, Dialogfelder und Toolfenster und andere Elemente der Benutzeroberfläche nicht modalen verwendet. Sie zeigen eine Auswahl, die den Benutzer einen Wert in ein Steuerelement auszufüllen unterstützt. Es gibt zwei Varianten dieser Schaltfläche, die lange und kurze.  
  
 ![Long &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703\-04\_BrowseLong")  
  
 **Long \[durchsuchen...\] Schaltfläche**  
  
 ![Short ellipsis&#45;only &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703\-05\_BrowseShort")  
  
 **Die Schaltfläche mit den Auslassungspunkten nur kurze \[...\]**  
  
 Wenn die kurze nur Auslassungszeichen\-Schaltfläche verwenden:  
  
-   Wenn es mehr als eine lange **\[durchsuchen...\]** Schaltfläche in einem Dialogfeld, z. B. wenn mehrere Felder Browsen zu ermöglichen. Verwenden Sie die kurze **\[...\]** auswählen, die verwirrend Zugriffsschlüssel erstellt, indem diese Situation zu vermeiden \(**& Durchsuchen** und **B & amen** im selben Dialogfeld\).  
  
-   In einem engen Dialogfeld, oder wenn es keine angemessenen zum Einfügen der lange Schaltfläche.  
  
-   Wenn die Schaltfläche in einem Datenraster\-Steuerelement angezeigt wird.  
  
 Richtlinien für die Verwendung der Schaltfläche:  
  
-   Verwenden Sie eine Zugriffstaste. Um mithilfe der Tastatur zuzugreifen, muss der Benutzer aus dem benachbarte Steuerelement Registerkarte. Sicherstellen Sie, dass die Aktivierreihenfolge ist, dass Schaltfläche "Durchsuchen" unmittelbar nach dem Feld liegt, der ausgefüllt werden. Verwenden Sie niemals einen Unterstrich unter dem ersten Zeitraum.  
  
-   Legen Sie die Microsoft Active Accessibility \(MSAA\) **Namen** \-Eigenschaft **Durchsuchen...** \(einschließlich der mit den drei Punkten\) damit Bildschirm liest Leser es als "Durchsuchen" und nicht "Punkt\-Punkt\-Punkt" oder "Punkt\-Punkt\-Period." Dies bedeutet für verwaltete Steuerelemente, die Einstellung der **AccessibleName** Eigenschaft.  
  
-   Verwenden Sie niemals ein Auslassungszeichen **\[...\]** Schaltfläche für alles außer einer Aktion "Durchsuchen". Angenommen, Sie müssen eine **\[Neu\]** Schaltfläche aber nicht ausreichend Platz für den Text ein, und klicken Sie dann im Dialogfeld muss geändert werden.  
  
##### Anpassen der Größe und Abstand  
 ![Sizing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703\-06\_BrowseSizing")  
  
 **Größe \[durchsuchen...\] Schaltflächen**  
  
 ![Spacing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703\-07\_BrowseSpacing")  
  
 **Abstand \[durchsuchen...\] Schaltflächen**  
  
#### Grafische Schaltflächen  
 Einige Schaltflächen sollte immer eine Grafik und nie enthalten Text zum Einsparen von Speicherplatz und Lokalisierung Probleme zu vermeiden. Diese werden häufig in Feld\-Steuerelementen und anderen sortierbaren Listen verwendet.  
  
> [!NOTE]
>  Benutzer müssen diese Schaltflächen \(es gibt keine Zugriffstasten\) die Registerkarte, daher platzieren Sie sie in einer sinnvollen Reihenfolge. Ordnen Sie die Name\-Eigenschaft der Schaltfläche, auf die Aktion, die es dauert, sodass Bildschirmsprachausgaben die Schaltflächenaktion richtig interpretiert.  
  
|||  
|-|-|  
|Hinzufügen|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703\-08\_ButtonAdd")|  
|Remove|![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703\-09\_ButtonRemove")|  
|Alle hinzufügen|![Graphical "Add All" button](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703\-10\_ButtonAddAll")|  
|Alle entfernen|![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703\-11\_ButtonRemoveAll")|  
|Nach oben|![Graphical "Move Up" button](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703\-12\_ButtonMoveUp")|  
|Nach unten|![Graphical "Move Down" button](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703\-13\_ButtonMoveDown")|  
|Löschen|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703\-14\_ButtonDelete")|  
  
##### Anpassen der Größe und Abstand  
 Größe anpassen, grafische Schaltflächen genauso wie bei die kurze Version ist die **\[durchsuchen...\]** Schaltfläche \(26 x 23 Pixel\):  
  
 ![Button with and without transparent color showing](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703\-15\_GraphicalButtonSpacing")  
  
 **Darstellung der eine Grafik auf die Schaltfläche mit und ohne transparenter Farbe**  
  
### Hyperlinks  
 Hyperlinks eignen sich gut zum navigationsbasierte Aktionen, z. B. ein Hilfethema, ein modales Dialogfeld oder Assistenten öffnen. Wenn ein Link für einen Befehl verwendet wird, sollten immer sichtbare und merkliche Änderung der Benutzeroberfläche angezeigt werden. Im Allgemeinen werden Aktionen, die einer Aktion \(z. B. speichern, "Abbrechen", und löschen\) commit besser kommuniziert mithilfe einer Schaltfläche.  
  
#### Schreibstil  
 Führen Sie die [Windows\-Desktop\-Leitfaden für Texte für die Benutzeroberfläche](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). Verwenden Sie nicht "Erfahren Sie mehr über," "Teilen Sie mir mehr über" oder "Get\-Help mit diesem" Formulierung entsprechen. Stattdessen Ausdruck Link Hilfetext in Bezug auf die primäre Frage beantwortet werden, indem der Inhalt der Hilfe. Z. B. "**Wie füge ich einen Server zum Server\-Explorer?**"  
  
#### Visueller Stil  
  
-   Hyperlinks sollten immer verwenden [Der Dienst VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Wenn ein Hyperlink nicht richtig formatiert ist, blinkt Rot, wenn der aktive oder zeigt eine andere Farbe nach aufgerufen wird.  
  
-   Schließen Sie nicht unterstrichen am Zustand befindet, es sei denn, der Link ein Satz Fragment in einem vollständigen Satz, z. B. in einem Wasserzeichen ist\-Steuerelement.  
  
-   Unterstrichen nicht Daraufzeigen angezeigt werden soll. Stattdessen wird das Feedback an den Benutzer, dass die Verbindung aktiv ist eine leichte Farbe ändern und den entsprechenden Link\-Cursor.  
  
##  <a name="BKMK_TreeViews"></a> Strukturansichten  
  
### Übersicht  
 Strukturansichten bieten eine Möglichkeit zum Organisieren von komplexen in Parent\-Child\-Gruppen aufgeführt. Ein Benutzer kann erweitert oder reduziert übergeordneten Gruppen zum Anzeigen oder Ausblenden von zugrunde liegenden untergeordneten Elemente. Jedes Element in einer Strukturansicht kann ausgewählt werden, in dem weitere Aktion bereitgestellt.  
  
 Dieses Thema behandelt die akzeptable Nutzung, entworfen und Funktionalität von Strukturansichten.  
  
#### In diesem Thema  
  
-   [Visueller Stil](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [Interaktionen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Visueller Stil  
  
#### Erweiterungen  
 Strukturansicht\-Steuerelemente sollte das Expander\-Design, die von Windows und Visual Studio entsprechen. Jeder Knoten verwendet ein Expander\-Steuerelement zum Anzeigen oder Ausblenden von zugrunde liegenden Elementen. Mit Expander\-Steuerelements ist die Konsistenz für Benutzer, die verschiedenen Ansichten in Windows und Visual Studio auftreten können.  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Richtig: ordnungsgemäßes Format der Strukturansichtsknoten mit Expander\-Steuerelements**  
  
 ![Incorrect tree view nodes](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705\-2\_TreeViewIncorrect1")  
  
 **Falsch: falsche Darstellung Strukturansichtsknoten**  
  
#### Auswahl  
 Wenn ein Knoten in der Strukturansicht ausgewählt ist, sollte die Markierung auf die gesamte Breite des Strukturansicht\-Steuerelement erweitern. Dies hilft Benutzern, die eindeutig welches Element sie ausgewählt haben. Farben Auswahl sollte das aktuelle Visual Studio\-Design entsprechen.  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Richtig: Hervorheben des ausgewählten Knotens wird die gesamte Breite des Strukturansicht\-Steuerelement.**  
  
 ![Incorrect tree view highlighting](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705\-3\_TreeViewIncorrect2")  
  
 **Falsch: Hervorheben des ausgewählten Knotens passt nicht die gesamte Breite des Strukturansicht\-Steuerelement.**  
  
#### Symbole  
 Symbole sollte nur im Strukturansicht\-Steuerelemente verwendet werden, wenn sie bei der Unterschiede zwischen Elementen visuell identifizieren. Im Allgemeinen sollten Symbole nur in heterogenen Listen verwendet werden, die Symbole Informationen, um die Typen von Elementen unterscheiden ausführen. In einer homogenen Liste mit Symbolen kann häufig als Füllwörter betrachtet werden und sollte vermieden werden. In diesem Fall kann das Symbol für die Gruppe \(übergeordnet\) den Typ der Elemente in diesem übermitteln. Die Ausnahme von dieser Regel wäre, wenn das Symbol dynamisch ist und zur Angabe des Status dient.  
  
#### Bildlaufleisten  
 Bildlaufleisten sollen immer ausgeblendet werden, wenn der Inhalt in der Strukturansicht passt. Es ist ausgeblendet oder halbtransparente in einem bildlauffähigen Fenster und angezeigt werden, wenn das Fenster mit der Strukturansicht den Fokus besitzt, oder beim Bewegen der Struktur anzeigen, selbst für Bildlaufleisten akzeptabel.  
  
 ![Tree view with scroll bars](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705\-4\_Scrollbars")  
  
 **Sowohl vertikale und horizontale Bildlaufleisten werden angezeigt, da der Inhalt die Grenzen des Strukturansicht\-Steuerelements überschritten haben.**  
  
###  <a name="BKMK_TreeViewInteractions"></a> Interaktionen  
  
#### Kontextmenüs  
 Knoten einer Strukturansicht kann Optionen des Untermenüs in einem Kontextmenü anzuzeigen. Dies tritt in der Regel, wenn ein Benutzer mit der rechten Maustaste ein Element oder auf einer Windows\-Tastatur mit das ausgewählte Element im Menü gedrückt wurde. Es ist wichtig, dass der Fokus und aktiviert ist. Dadurch wird den Benutzer ermitteln, zu welchem Element im Untermenü gehört.  
  
 ![Selected tree node and context menu](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705\-5\_ContextMenu")  
  
 **Das Element, das dem Kontext Menü Gewinne Fokus zur Benachrichtigung des Benutzers Element generiert wurde, wurde ausgewählt.**  
  
#### Tastatur  
 Die Strukturansicht sollte die Möglichkeit bieten Elemente und Knoten mithilfe der Tastatur erweitern\/reduzieren. Dadurch wird sichergestellt, dass es sich bei Navigation unsere Anforderungen an Eingabehilfen entspricht.  
  
##### Strukturansicht\-Steuerelement  
 Visual Studio\-Struktur\-Steuerelemente sollten allgemeine Tastaturnavigation befolgen:  
  
-   **\-Oben\-Taste:** Elemente auswählen, indem Sie die Struktur nach oben verschieben  
  
-   **Unten:** Elemente auswählen, indem Sie in der Struktur nach unten verschieben  
  
-   **Rechts:** erweitern Sie einen Knoten in der Struktur  
  
-   **Links:** Reduzieren eines Knotens in der Struktur  
  
-   **Enter\-Taste:** initiieren, laden und Ausführen des ausgewählten Elements  
  
##### Trid \(Strukturansicht und Rasteransicht\)  
 Ein Rastersteuerelement ist ein komplexes Steuerelement enthält eine Strukturansicht, in einem Raster an. Erweitern und reduzieren die Struktur navigieren sollte die gleichen Tastaturbefehle als Baumstruktur, mit folgenden Besonderheiten beachten:  
  
-   **Rechts:** einen Knoten zu erweitern. Nachdem der Knoten erweitert ist, soll er weiterhin in die nächste Spalte auf der rechten Seite navigieren. Navigation sollte am Ende der Zeile beenden.  
  
-   **Registerkarte:** Werkzeug dient zum Navigieren zur nächsten Zelle auf der rechten Seite.  Am Ende der Zeile auf die nächste Zeile weiterhin Navigation.  
  
-   **Umschalt \+ Tab:** Werkzeug dient zum Navigieren zur nächsten Zelle auf der linken Seite.  Am Anfang der Zeile weiterhin Navigationsbereich der äußersten rechten Zelle in der vorherigen Zeile.  
  
 ![Trid control in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705\-6\_Trid")  
  
 **Ein Rastersteuerelement in Visual Studio**