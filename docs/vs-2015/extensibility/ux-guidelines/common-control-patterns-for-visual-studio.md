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
ms.openlocfilehash: dd2b2723a5ecfe66e9471cfea1e8eb55ed7ced59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547445"
---
# <a name="common-control-patterns-for-visual-studio"></a>Allgemeine Steuerelementmuster für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Allgemeine Steuerelemente

### <a name="overview"></a>Übersicht
 Allgemeine Steuerelemente bilden die Mehrzahl der Benutzeroberfläche in Visual Studio. Die meisten allgemeinen Steuerelemente, die in der Visual Studio-Benutzeroberfläche verwendet werden, sollten den [Windows-Desktop Interaktions Richtlinien](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx) Dieses Dokument ist für Visual Studio spezifisch und behandelt spezielle Situationen oder Details, die diese Windows-Richtlinien ergänzen.

#### <a name="common-controls-in-this-topic"></a>Allgemeine Steuerelemente in diesem Thema

- [Bild Lauf leisten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Eingabefelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Kombinations Felder und Dropdown Listen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Kontrollkästchen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Optionsfelder](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Gruppieren von Frames](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Schaltflächen und Hyperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Strukturansichten](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Visueller Stil
 Beim Formatieren von Steuerelementen sollten Sie zunächst beachten, ob die Steuerelemente in der Benutzeroberfläche verwendet werden. Steuerelemente auf der Standardbenutzer Oberfläche sind eine Benutzeroberfläche ohne Design und müssen dem [normalen Windows-Desktop Stil](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)folgen, d. h., Sie werden nicht erneut mit Vorlagen versehen und sollten in Ihrer Standard Steuerelement Darstellung angezeigt werden.

- **Standard Dialogfelder (Hilfsprogramm):** nicht mit dem Design. Nicht neu erstellen. Standardeinstellungen für Steuerelement Stil verwenden.

- **Tool Fenster, Dokument-Editoren, Entwurfs Oberflächen und Themen Dialogfelder:** Verwenden Sie eine spezielle Darstellung des Designs mit dem Farb Dienst.

### <a name="scrollbars"></a><a name="BKMK_Scrollbars"></a>Bild Lauf leisten
 Scrollleisten sollten [gängige Interaktionsmuster für Windows-Scrollleisten](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) befolgen, es sei denn, Sie werden mit Inhaltsinformationen ergänzt, z. b. im Code-Editor.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Eingabefelder
 Befolgen Sie für ein typisches Interaktions Verhalten die [Windows-Desktop Richtlinien für Textfelder](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visueller Stil

- Eingabefelder sollten nicht in hilfsprogrammdialogfeldern formatiert werden. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

- Themen Eingabefelder sollten nur in Themen Dialogfeldern und Tool Fenstern verwendet werden.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen

- Schreibgeschützte Felder haben einen grauen (deaktivierten) Hintergrund, aber den Standard-Vordergrund (aktiv).

- Erforderliche Felder müssen **\<Required>** als Wasserzeichen enthalten sein. Sie sollten die Hintergrundfarbe nur in seltenen Fällen ändern.

- Fehlerüberprüfung: siehe [Benachrichtigungen und Fortschritt für Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md) .

- Eingabefelder sollten an den Inhalt angepasst werden, sodass Sie nicht an die Breite des Fensters angepasst werden, in dem Sie angezeigt werden, und auch nicht auf die Länge eines Langenfelds, wie z. b. einen Pfad. Die Länge ist möglicherweise ein Hinweis für den Benutzer von Einschränkungen, die angibt, wie viele Zeichen im Feld zulässig sind.

     Falsche Eingabefeld Länge für ungültige ![Eingabefeld-Steuerelement Breite](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl") **: Es ist unwahrscheinlich, dass der Name so lang ist.**

     Korrekte Länge des Eingabe Felds für die Eingabe ![Feld Steuerung](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl") **: das Eingabefeld ist eine angemessene Breite für den erwarteten Inhalt.**

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Kombinations Felder und Dropdown Listen
 Befolgen Sie für ein typisches Interaktions Verhalten die [Windows-Desktop Richtlinien für Dropdown Listen und Kombinations Felder](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visueller Stil

- Ordnen Sie das Steuerelement in den hilfsprogrammdialogfeldern nicht neu an. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

- In der Benutzeroberfläche für die Benutzeroberfläche folgen Kombinations Felder und Dropdown Listen den Standarddesigns für die Steuerelemente.

#### <a name="layout"></a>Layout
 Kombinations Felder und Dropdown Listen sollten entsprechend dem Inhalt angepasst werden, sodass Sie nicht an die Breite des Fensters angepasst werden können, in dem Sie angezeigt werden, und die Länge eines Langenfelds (z. b. eines Pfades) beliebig zu vergleichen.

 ![Falsches Dropdown&#45;Layout](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")

 **Falsche Feldlänge für ein Dropdown-Steuerelement.**

 ![Richtige Dropdown&#45;Layout](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707-04_CorrectDropDownLayout")

 **Richtige Feldlänge für ein Dropdown-Steuerelement**

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Kontrollkästchen
 Für ein typisches Interaktions Verhalten befolgen Sie die [Windows-Desktop Richtlinien für Kontrollkästchen](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visueller Stil

- Ordnen Sie das Steuerelement in den hilfsprogrammdialogfeldern nicht neu an. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

- In der Benutzeroberfläche für die Benutzeroberfläche folgen Kontrollkästchen den Standarddesigns für die Steuerelemente.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen

- Wenn Sie mit einem Kontrollkästchen interagieren, darf kein Dialogfeld angezeigt werden, oder Sie navigieren zu einem anderen Bereich.

- Richten Sie Kontrollkästchen mit der Baseline der ersten Textzeile aus.

     ![Falsche Kontrollkästchen Ausrichtung](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign") **falsch Kontrollkästchen Ausrichtung: das Kontrollkästchen ist auf den Text ausgerichtet.**

     ![Richtige](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign") Kontrollkästchen Ausrichtung richtige Kontroll **Kästchen Ausrichtung: das Kontrollkästchen ist an der Baseline der ersten Textzeile ausgerichtet.**

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Options Felder
 Befolgen Sie für ein typisches Interaktions Verhalten die [Windows-Desktop Richtlinien für](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx)Options Felder.

#### <a name="visual-style"></a>Visueller Stil
 Formatieren Sie in hilfsprogrammdialogfeldern keine Options Felder. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

#### <a name="specialized-interactions"></a>Spezialisierte Interaktionen
 Es ist nicht erforderlich, einen Gruppen Rahmen zu verwenden, um Options Felder zu schließen.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Gruppieren von Frames
 Befolgen Sie für ein typisches Interaktions Verhalten die [Windows-Desktop Richtlinien für Gruppen Frames](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Visueller Stil
 In hilfsprogrammdialogfeldern dürfen Sie keine Gruppen Rahmen formatieren. Verwenden Sie die intrinsische grundlegende Formatvorlage für das Steuerelement.

#### <a name="layout"></a>Layout

- Es ist nicht erforderlich, einen Gruppen Rahmen zu verwenden, um Options Felder einzuschließen, es sei denn, Sie müssen die Gruppen Unterscheidung in einem engen Layout beibehalten.

- Verwenden Sie niemals einen Gruppen Rahmen für ein einzelnes Steuerelement.

- Es ist manchmal akzeptabel, anstelle eines Gruppen Frame Containers eine horizontale Regel zu verwenden.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Text Steuerelemente

### <a name="labels"></a>Bezeichnungen

#### <a name="active-label-state"></a>Status der aktiven Bezeichnung

##### <a name="utility-standard-dialogs"></a>Hilfsprogrammdialogfelder (Standard))

- Im allgemeinen befolgen Sie die Anleitungen zum Windows-Desktop für Steuerelement Bezeichnungen.

- In hilfsprogrammdialogfeldern sollten Bezeichnungen in der Schriftart und Textfarbe der Standardumgebung nicht fett angezeigt werden. Informationen finden Sie unter [Schriftarten und Formatierung für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Ellipsen sollten immer Bezeichnungen folgen.

##### <a name="signature-themed-dialogs"></a>Signatur Dialogfelder (mit Themen))
 Bezeichnungs Steuerelemente sind möglicherweise Fett oder hellgrau.

#### <a name="disabled-label-state"></a>Aktivierter Bezeichnungs Status
 Bezeichnungen sollten die Darstellung des Steuer Elements widerspiegeln, dem Sie zugeordnet sind. Wenn das zugeordnete Steuerelement z. b. deaktiviert ist, sollte die Bezeichnung grau und deaktiviert angezeigt werden. Dies wird in der Regel vom Betriebssystem verarbeitet und erfordert keine besondere Behandlung.

#### <a name="dynamic-labels"></a>Dynamische Bezeichnungen
 Dynamische Bezeichnungen ändern sich basierend auf der aktuellen Auswahl. Verwenden Sie nach Möglichkeit dynamische Bezeichnungen in Master/Detail-Layouts, um dem Benutzer zu helfen, zu verstehen, dass die angezeigten Informationen für eine bestimmte Auswahl relevant sind und keine allgemeinen Informationen.

 ![Dynamische Beschriftung mit dynamischen Inhalten](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702-01_DynamicLabel")

 **Beispiel für eine dynamische Bezeichnung, die mit dynamischem Inhalt verwendet wird**

#### <a name="instructional-text"></a>Anweisungs Text
 Einige Schnittstellen Elemente profitieren von Anweisungs Text, um dem Benutzer zu helfen, den Zweck der Benutzeroberfläche nachzuvollziehen oder anzugeben, welche Aktion ausgeführt werden soll.

- Der Anweisungs Text wird am oberen Rand der Dialoge am häufigsten angezeigt, kann aber auch in anderen Bereichen angezeigt werden, um einer komplexen Steuerelement Gruppierung Anweisungen zu erteilen.

- Der Anweisungs Text ist nicht interaktiv, kann jedoch Hyperlinks zu Hilfe Themen enthalten.

- Verwenden Sie Anweisungs Text nur selten und nur bei Bedarf.

##### <a name="formatting"></a>Formatierung
 Der Anweisungs Text sollte Umgebungs Schriftart und Standard Steuerelement Text (ohne Design) sein. Informationen finden Sie unter [Schriftarten und Formatierung für Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Ausführliche Informationen zum Schreiben von Anweisungs Text finden Sie unter [UI-Text und-Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Formatierung von Anweisungstext](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Anweisungs Text in einem Visual Studio-Dialogfeld**

#### <a name="informational-text"></a>Informationstext
 Informationstext ist Text, der dem Benutzer zusätzliche Informationen liefert. Sie kann statisch oder dynamisch sein oder als Benachrichtigung verwendet werden. Sie ist immer schreibgeschützt. wenn der Benutzer jedoch die Möglichkeit hat, die Informationen zu kopieren, sollte dynamischer Text in einem Steuerelement Container platziert werden, z. b. in einem schreibgeschützten Textfeld.

##### <a name="dynamic-context-specific-text"></a>Dynamischer (Kontext spezifischer) Text
 Der Text für dynamische Informationen ändert sich abhängig vom Kontext, z. b. wenn der Benutzer den Fokus wechselt. Häufig, aber nicht immer, wird dynamischer Inhalt mit einer dynamischen Bezeichnung kombiniert.

 ![Dynamischer Informationstext](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702-03_InformationalDynamicText")

 **Der dynamische Informationstext ändert sich je nach Kontext.**

##### <a name="formatting"></a>Formatierung
 Es gibt zwei Möglichkeiten, schreibgeschützte Textfelder anzuzeigen: entweder direkt auf der UI-Oberfläche (siehe oben) oder in einem anderen Steuerelement, z. b. in einem Gruppen Rahmen oder Textfeld. Beide sind abhängig von der Situation richtig. Der Funktions-Designer kann festlegen, wie die schreibgeschützten Informationen angezeigt werden.

 Text kann sich in einem schreibgeschützten Textfeld befinden. Dies gibt im Allgemeinen an, dass der Inhalt ausgewählt und kopiert werden kann, obwohl er nicht bearbeitet werden kann.

 ![Informationstext Formatierung für Lese&#45;Felder](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702-04_InformationalFormatting")

 **Formatierung von Informationstext für schreibgeschützte Felder**

#### <a name="watermarks"></a>Wasserzeichen
 Obwohl der Wortlaut identisch sein könnte, besteht der Unterschied zwischen Wasserzeichen und Anweisungs Text darin, dass Wasserzeichen durch Inhalte ersetzt werden, wenn das Steuerelement/Fenster nicht leer ist und der Anweisungs Text jederzeit sichtbar bleibt.

 Wasserzeichen sollten verwendet werden, wenn ein Fenster oder ein Steuerelement leer ist. Sie geben an, welche Schritte zum Auffüllen des Bereichs durchgeführt werden müssen, und enthalten möglicherweise Aktions Links zum Öffnen relevanter Fenster, z. b. eine Zieh Quelle.

##### <a name="visual-style"></a>Visueller Stil

- Wasserzeichen sollten horizontal innerhalb des Fensters zentriert werden.

- Wasserzeichen sollten zentriert ausgerichtet und nicht linksbündig ausgerichtet sein.

- Wasserzeichen können vertikal zentriert oder am oberen Rand des Bereichs positioniert werden. Wenn Sie sich am oberen Rand des Bereichs befinden, muss genügend Speicherplatz vorhanden sein, damit das Wasserzeichen aussteht.

- Verwenden Sie die `Environment.GrayText` Schriftart farbtoken und Standardumgebung. Hyperlinks sollten die standardmäßigen freigegebenen Hyperlink-Token verwenden: `Environment.PanelHyperlink` , `Environment.PanelHyperlinkHover` , `Environment.PanelHyperlinkPressed` und `Environment.PanelHyperlinkDisabled` .

- Wasserzeichen können nicht im Hintergrund ausgewählt werden.

- Schließen Sie nach Möglichkeit links in das Wasserzeichen ein, um den Benutzer zu unterstützen.

  ![Wasserzeichentext in einem Designer-Fenster](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702-05_Watermark1")

  ![Wasserzeichentext in einem Toolfenster](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702-06_Watermark2")

  **Beispiele für Wasserzeichen Text in Visual Studio**

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Schaltflächen und Hyperlinks

### <a name="overview"></a>Übersicht
 Schaltflächen und Link Steuerelemente (Hyperlinks) müssen [grundlegende Windows-Desktop-Anleitungen](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) für die Verwendung, die Formulierung, die Größenanpassung und den Abstand befolgen.

### <a name="choosing-between-buttons-and-links"></a>Auswählen zwischen Schaltflächen und Links
 Normalerweise wurden Schaltflächen für Aktionen verwendet, und Hyperlinks wurden für die Navigation reserviert. Schaltflächen können in allen Fällen verwendet werden, aber die Rolle von Verknüpfungen wurde in Visual Studio erweitert, sodass Schaltflächen und Verknüpfungen unter bestimmten Bedingungen austauschbar sind.

 Verwendung von Befehls Schaltflächen:

- Primäre Befehle

- Anzeigen von Fenstern, die verwendet werden, um Eingaben zu erfassen oder auszuwählen, selbst wenn es sich um sekundäre Befehle handelt

- Zerstörerische oder nicht rückgängig-Aktionen

- Verpflichtungs Schaltflächen innerhalb von Assistenten und Seiten Flüssen

  Vermeiden Sie Befehls Schaltflächen in Tool Fenstern oder, wenn Sie mehr als zwei Wörter für die Bezeichnung benötigen. Links können über längere Bezeichnungen verfügen.

  Verwendung von Verknüpfungen:

- Navigation zu einem anderen Fenster, Dokument oder einer Webseite

- Situationen, die eine längere Bezeichnung oder einen kurzen Satz zum Beschreiben der Absicht der Aktion erfordern

- Enge Bereiche, in denen eine Schaltfläche die Benutzeroberfläche überlastet, vorausgesetzt, dass die Aktion nicht destruktiv oder nicht rückgängig

- Aufheben der hervorgehoben sekundärer Befehle in Situationen, in denen viele Befehle vorhanden sind

#### <a name="examples"></a>Beispiele
 ![Links für Infoleistenbefehle nach Statusmeldung](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703-01_CommandLinkInfobar")

 **Befehls Verknüpfungen, die in der Info Leiste nach einer Statusmeldung verwendet werden**

 ![Links im CodeLens-Popup](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703-02_LinksInCodeLens")

 **Links im CodeLens-Popup**

 ![Links als sekundäre Befehle](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")

 **Links, die für sekundäre Befehle verwendet werden, bei denen Schaltflächen zu viel Aufmerksamkeit erregen**

### <a name="common-buttons"></a>Allgemeine Schaltflächen

#### <a name="text"></a>Text
 Befolgen Sie die Richtlinien zum Schreiben von [Benutzeroberflächen Text und-Terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Visueller Stil

##### <a name="standard-dialogs"></a>Standard Dialogfelder
 Die meisten Schaltflächen in Visual Studio werden in Standard Dialogfeldern angezeigt und sollten nicht formatiert werden. Sie sollten die Standarddarstellung von Schaltflächen entsprechend der von dem Betriebssystem vorgegebenen Schaltflächen widerspiegeln.

##### <a name="themed"></a>Artikeln
 In einigen Fällen können Schaltflächen in der formatierten Benutzeroberfläche verwendet werden, und diese Schaltflächen müssen entsprechend formatiert werden. Weitere Informationen zu Design Steuerelementen finden Sie unter [Dialog](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) Felder.

### <a name="special-buttons"></a>Sonderschaltflächen

#### <a name="browse-buttons"></a>Durchsuchen... Schaltflächen
 **[Durchsuchen...]** Schaltflächen werden in Raster, Dialogfeldern und Tool Fenstern und anderen Benutzeroberflächen Elementen verwendet. Sie zeigen eine Auswahl an, die dem Benutzer beim Ausfüllen eines Werts in ein Steuerelement hilft. Es gibt zwei Variationen dieser Schaltfläche: Long und Short.

 ![Lange &#91;durchsuchen... &#93; Schaltfläche](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703-04_BrowseLong")

 **Die lange Schaltfläche [Durchsuchen...]**

 ![Kurze Ellipsen&#45;nur &#91;Schaltfläche "Durchsuchen"... &#93;](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703-05_BrowseShort")

 **Die Schaltfläche mit den Auslassungs Punkten, nur kurz [...]**

 Verwendung der kurzen Schaltfläche mit Auslassungs Punkten:

- , Wenn mehr als eine lange **[Browse...]** -Schaltfläche in einem Dialogfeld vorhanden ist, z. b., wenn mehrere Felder zum Durchsuchen zugelassen werden. Verwenden Sie die Schaltfläche Short **[...]** , um die verwirrenden Zugriffstasten zu vermeiden, die in dieser Situation erstellt wurden (**&Browse** und **B&URCHSUCHEN** im gleichen Dialogfeld).

- In einem engen Dialogfeld oder wenn es keinen sinnvollen Platz zum Platzieren der Long-Schaltfläche gibt.

- , Wenn die Schaltfläche in einem Raster Steuerelement angezeigt wird.

  Richtlinien für die Verwendung der Schaltfläche:

- Verwenden Sie keine Zugriffstaste. Um über die Tastatur darauf zuzugreifen, muss der Benutzer die Tab-Taste aus dem angrenzenden Steuerelement aufrufen. Stellen Sie sicher, dass die Aktivier Reihenfolge ist, dass jede Schaltfläche Durchsuchen unmittelbar nach dem Feld fällt, das Sie ausfüllen wird Verwenden Sie niemals einen Unterstrich unterhalb des ersten Zeitraums.

- Legen Sie die Eigenschaft **Name** des Microsoft-Active Accessibility (MSAA) auf **Durchsuchen...** (einschließlich der Auslassungs Punkte) fest, damit Sprachausgaben Sie als "Durchsuchen" und nicht als "Punkt-Punkt-Punkt" oder "Zeitraum-Zeitraum-Periode" lesen. Bei verwalteten Steuerelementen bedeutet dies, dass die **AccessibleName** -Eigenschaft festgelegt wird.

- Verwenden Sie niemals eine Schaltfläche mit den Auslassungs Punkten **[...]** , außer eine Aktion zum Durchsuchen. Wenn Sie z. b. eine Schaltfläche **[New...]** benötigen, aber nicht genug Platz für den Text, muss das Dialogfeld neu gestaltet werden.

##### <a name="sizing-and-spacing"></a>Größe und Abstand
 ![Größenänderung &#91;durchsuchen... &#93; Schaltflächen](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703-06_BrowseSizing")

 **Größenanpassung [Durchsuchen...]-Schaltflächen**

 ![Abstand &#91;Schaltflächen zum Durchsuchen... &#93;](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703-07_BrowseSpacing")

 **Abstands Schaltflächen [Durchsuchen...]**

#### <a name="graphical-buttons"></a>Grafische Schaltflächen
 Einige Schaltflächen sollten immer ein grafisches Bild verwenden und nie Text enthalten, um Speicherplatz zu sparen und Lokalisierungs Probleme zu vermeiden. Diese werden häufig in Feld-pickern und anderen sortierbaren Listen verwendet.

> [!NOTE]
> Benutzer müssen zu diesen Schaltflächen wechseln (es sind keine Zugriffstasten vorhanden). Platzieren Sie Sie daher in einer sinnvollen Reihenfolge. Ordnen Sie die Name-Eigenschaft der Schaltfläche der Aktion zu, die Sie annimmt, damit die Sprachausgabe die Schaltflächen Aktion korrekt interpretiert.

|Name|Image|
|-|-|
|Add|![Grafische Schaltfläche "Hinzufügen"](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|Entfernen|![Grafische Schaltfläche "Entfernen"](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|Alle hinzufügen|![Grafische Schaltfläche "Alles hinzufügen"](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703-10_ButtonAddAll")|
|Alle entfernen|![Grafische Schaltfläche "Alle entfernen"](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|Nach oben|![Grafische Schaltfläche "Nach oben"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703-12_ButtonMoveUp")|
|Nach unten|![Grafische Schaltfläche "Nach unten"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703-13_ButtonMoveDown")|
|Löschen|![Grafische Schaltfläche "Löschen"](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Größe und Abstand
 Die Größenanpassung für grafische Schaltflächen ist identisch mit der Kurzversion der Schaltfläche **[Durchsuchen...]** (26x23 Pixel):

 ![Schaltfläche mit und ohne transparenter Farbe](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")

 **Darstellung eines grafischen Bilds auf der Schaltfläche mit und ohne transparente Farbe**

### <a name="hyperlinks"></a>Links
 Hyperlinks sind gut für Navigations basierte Aktionen geeignet, wie z. b. das Öffnen eines Hilfe Themas, eines modalen Dialog Felds oder eines Assistenten. Wenn ein Hyperlink für einen Befehl verwendet wird, sollte immer eine sichtbare und spürbare Änderung der Benutzeroberfläche angezeigt werden. Im Allgemeinen werden Aktionen, die sich auf eine Aktion (z. b. speichern, Abbrechen und löschen) anwenden, mithilfe einer Schaltfläche besser kommuniziert.

#### <a name="writing-style"></a>Schreibstil
 Befolgen Sie die [Anleitungen zum Windows-Desktop für die Benutzeroberfläche](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). Verwenden Sie nicht "Weitere Informationen zu", "Weitere Informationen zu" oder "Hilfe zu diesem" formulieren. Stattdessen können Sie Text in Bezug auf die primäre Frage des Hilfe Inhalts verknüpfen. Beispiel: "**Gewusst wie Hinzufügen eines Servers zum Server-Explorer?**"

#### <a name="visual-style"></a>Visueller Stil

- Hyperlinks sollten immer [den vscolor-Dienst](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)verwenden. Wenn ein Hyperlink nicht ordnungsgemäß formatiert ist, blinkt er nach der aktiven oder nach dem Besuch eine andere Farbe.

- Schließen Sie Unterstriche nicht in den Ruhezustand des Steuer Elements ein, es sei denn, der Link ist ein Satz Fragment innerhalb eines vollen Satzes, z. b. in einem Wasserzeichen.

- Unterstriche sollten nicht auf dem Mauszeiger angezeigt werden. Stattdessen ist das Feedback an den Benutzer, dass der Link aktiv ist, eine geringfügige Farbänderung und der entsprechende Link Cursor.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Struktur Ansichten

### <a name="overview"></a>Übersicht
 Struktur Ansichten bieten eine Möglichkeit, komplexe Listen in über-und untergeordneten Gruppen zu organisieren. Ein Benutzer kann übergeordnete Gruppen erweitern oder reduzieren, um zugrunde liegende untergeordnete Elemente anzuzeigen oder auszublenden. Alle Elemente in einer Strukturansicht können ausgewählt werden, um weitere Aktionen bereitzustellen.

 In diesem Thema werden die akzeptable Verwendung, der richtige Entwurf und die Funktionalität von Struktur Ansichten behandelt.

#### <a name="in-this-topic"></a>In diesem Thema

- [Visueller Stil](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interaktionen](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Visueller Stil

#### <a name="expanders"></a>Expander
 Strukturansicht-Steuerelemente sollten dem Expander-Entwurf entsprechen, der von Windows und Visual Studio verwendet wird. Jeder Knoten verwendet ein Expander-Steuerelement, um zugrunde liegende Elemente anzuzeigen oder auszublenden. Die Verwendung eines Expander-Steuer Elements bietet Konsistenz für Benutzer, die möglicherweise unterschiedliche Struktur Ansichten in Windows und Visual Studio sehen.

 ![Steuerelement "Strukturansicht" (richtig)](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Richtig: ordnungsgemäße Art des Struktur Ansichts Knotens mithilfe eines Expander-Steuer Elements**

 ![Steuerelement „Strukturansichtsknoten“ (falsch)](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705-2_TreeViewIncorrect1")

 **Falsch: falscher Stil des Struktur Ansichts Knotens**

#### <a name="selection"></a>Auswahl
 Wenn ein Knoten innerhalb der Strukturansicht ausgewählt ist, sollte die Hervorhebung auf die gesamte Breite des Strukturansicht-Steuer Elements erweitert werden. Dadurch können Benutzer die ausgewählten Elemente eindeutig identifizieren. Auswahl Farben sollten das aktuelle Visual Studio-Design widerspiegeln.

 ![Steuerelement "Strukturansicht" (richtig)](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Richtig: die Hervorhebung des ausgewählten Knotens ist für die gesamte Breite des Strukturansicht-Steuer Elements geeignet.**

 ![Falsche Hervorhebung für Strukturansicht](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705-3_TreeViewIncorrect2")

 **Falsch: die Hervorhebung des ausgewählten Knotens passt nicht zur gesamten Breite des Strukturansicht-Steuer Elements.**

#### <a name="icons"></a>Symbole
 Symbole sollten nur in Strukturansicht-Steuerelementen verwendet werden, wenn Sie bei der visuellen Identifizierung von Unterschieden zwischen Elementen helfen. Im Allgemeinen sollten Symbole nur in heterogenen Listen verwendet werden, in denen die Symbole Informationen enthalten, um die Elementtypen zu unterscheiden. In einer homogenen Liste können Symbole häufig als Rauschen angesehen werden und sollten vermieden werden. In diesem Fall kann das Gruppensymbol (übergeordnetes Element) den Typ der darin enthaltenen Elemente übermitteln. Eine Ausnahme von dieser Regel wäre, wenn das Symbol dynamisch ist und verwendet wird, um den Zustand anzugeben.

#### <a name="scroll-bars"></a>Bildlaufleisten
 Scrollleisten sollten immer ausgeblendet werden, wenn der Inhalt in das Strukturansicht-Steuerelement passt. Scrollleisten können in einem Bild lauffähigen Fenster ausgeblendet oder semitransparent sein und angezeigt werden, wenn das Fenster, das die Strukturansicht enthält, den Fokus besitzt, oder wenn der Mauszeiger auf die Strukturansicht zeigt.

 ![Strukturansicht mit Bildlaufleisten](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705-4_Scrollbars")

 **Vertikale und horizontale Schiebe leisten werden angezeigt, da der Inhalt die Begrenzungen des Strukturansicht-Steuer Elements überschritten hat.**

### <a name="interactions"></a><a name="BKMK_TreeViewInteractions"></a>Wechsel

#### <a name="context-menus"></a>Kontextmenüs
 In einem Struktur Ansichts Knoten können Untermenüoptionen in einem Kontextmenü angezeigt werden. Dies tritt normalerweise auf, wenn ein Benutzer mit der rechten Maustaste auf ein Element geklickt oder die Menü Taste auf einer Windows-Tastatur gedrückt hat, auf der das Element ausgewählt ist. Es ist wichtig, dass der Knoten den Fokus erhält und ausgewählt wird. Dadurch kann der Benutzer identifizieren, zu welchem Element das Untermenü gehört.

 ![Ausgewählter Strukturknoten mit Kontextmenü](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705-5_ContextMenu")

 **Das Element, das das Kontextmenü generiert hat, erhält den Fokus, um den Benutzer zu benachrichtigen, welches Element ausgewählt wurde.**

#### <a name="keyboard"></a>Tastatur
 Die Strukturansicht sollte die Möglichkeit bieten, Elemente auszuwählen und Knoten mithilfe der Tastatur zu erweitern bzw. zu reduzieren. Dadurch wird sichergestellt, dass die Navigation unsere Barrierefreiheits Anforderungen erfüllt.

##### <a name="tree-view-control"></a>Strukturansicht-Steuerelement
 Visual Studio-Struktur Steuerelemente sollten der allgemeinen Tastaturnavigation folgen:

- **Pfeil nach oben:** Elemente durch Verschieben der Struktur auswählen

- **Pfeil nach unten:** Elemente durch Verschieben in der Struktur auswählen

- **Rechter Pfeil:** Erweitern eines Knotens in der Struktur

- **Pfeil nach links:** Reduzieren eines Knotens in der Struktur

- **EINGABETASTE:** Initiieren, laden, ausgewähltes Element ausführen

##### <a name="trid-tree-view-and-grid-view"></a>"Did" (Strukturansicht und Rasteransicht)
 Ein-Steuerelement ist ein komplexes Steuerelement, das eine Strukturansicht innerhalb eines Rasters enthält. Beim erweitern, reduzieren und Navigieren in der Struktur sollten dieselben Tastaturbefehle wie für eine Strukturansicht berücksichtigt werden, mit den folgenden Ergänzungen:

- **Rechter Pfeil:** Erweitern Sie einen Knoten. Nachdem der Knoten erweitert wurde, sollte er weiterhin zur nächsten Spalte auf der rechten Seite navigieren. Die Navigation sollte am Ende der Zeile angehalten werden.

- **Registerkarte:** Navigiert zur nächsten Zelle auf der rechten Seite.  Am Ende der Zeile wird die Navigation mit der nächsten Zeile fortgesetzt.

- **UMSCHALT + TAB:** Navigiert zur nächsten Zelle auf der linken Seite.  Am Anfang der Zeile wird die Navigation mit der äußersten rechten Zelle in der vorherigen Zeile fortgesetzt.

  ![Rastersteuerelement in Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705-6_Trid")

  **Ein-Steuerelement in Visual Studio**
