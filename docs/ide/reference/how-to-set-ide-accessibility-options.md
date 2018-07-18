---
title: 'Vorgehensweise: Festlegen von IDE-Barrierefreiheitsoptionen'
description: Informationen zum Festlegen von Barrierefreiheitsoptionen in Visual Studio, die die Verwendung der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) für jeden vereinfachen, auch für Benutzer mit eingeschränktem Seh- und Schreibvermögen
ms.date: 08/22/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f977c30f1f4d6db7ce165de8483c8fd1977922d8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31952102"
---
# <a name="how-to-set-ide-accessibility-options"></a>Vorgehensweise: Festlegen von IDE-Barrierefreiheitsoptionen

> [!TIP]
> Weitere Informationen zu aktuellen Barrierefreiheitupdates finden Sie im Blogbeitrag [Accessibility improvements in Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Verbesserungen der Barrierefreiheit in Visual Studio 2017 [Version 15.3]).

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umfasst Features zur Unterstützung von Personen mit eingeschränktem Seh- und Schreibvermögen. Zu diesen Features gehören unter anderem das Anpassen von Schriftgröße und -farbe in Editoren, das Ändern der Größe von Text und Schaltflächen in Symbolleisten sowie die automatische Vervollständigung von Methoden- und Parameternamen.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt außerdem Dvorak-Tastaturlayouts, die den Zugriff auf die am häufigsten eingetippten Zeichen vereinfachen. Sie können auch die Standardtastenkombinationen anpassen, die in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügbar sind. Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="editors-dialogs-and-tool-windows"></a>Editors, Dialogfelder und Toolfenster

 Standardmäßig wird in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für Dialogfelder und Toolfenster die gleiche Schriftgröße und Schriftfarbe wie für das Betriebssystem verwendet. Die Farbeinstellungen für den Rahmen der IDE, die Dialogfelder, Symbolleisten und Toolfenster basieren auf einem Farbschema: hell oder dunkel. Sie können das aktuelle Farbschema unter [Allgemein, Umgebung, Dialogfeld „Optionen“](../../ide/reference/general-environment-options-dialog-box.md) ändern.

 Sie können auch festlegen, dass in der Codeansicht des Editors Popupfenster angezeigt werden. Diese Fenster zeigen Ihnen möglicherweise verfügbare Member für das aktuelle Objekt und die Parameter, die für eine Funktion oder Anweisung benötigt werden. Sie können besonders hilfreich sein, wenn Sie Schwierigkeiten bei der Eingabe über die Tastatur haben. Allerdings kollidiert diese Funktion mit dem Fokus im Code-Editor, was für manche Benutzer problematisch sein kann. Sie können diese Fenster deaktivieren, indem Sie das Dialogfeld **Optionen** öffnen und **Member automatisch auflisten** sowie **Parameterinformationen** im **Text-Editor** auf der Seite **Alle Sprachen** unter **Allgemein** löschen.

 Sie können die Fenster in der IDE (Integrated Development Environment, Integrierte Entwicklungsumgebung) so anordnen, dass sie Ihrer individuellen Arbeitsweise entgegenkommen. Sie können jedes Toolfenster andocken, verschieben, ausblenden oder automatisch ausblenden.

 Weitere Informationen zum Ändern des Fensterlayouts finden Sie unter [Anpassen von Fensterlayouts in Visual Studio](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Ändern der Textgröße

 Sie können die Einstellungen für textbasierte Toolfenster, z.B. das Fenster **Befehl**, das Fenster **Direkt** und das Fenster **Ausgabe**, im Bereich **Schriftarten und Farben** der Optionen unter **Umgebung** im Dialogfeld **Extras** ändern. Wenn in der Dropdownliste **Einstellungen anzeigen** der Eintrag **[Alle Texttoolfenster]** ausgewählt wurde, wird in den Dropdownlisten **Elementvordergrund** und **Elementhintergrund** die Standardeinstellung **Standard** angezeigt. Sie können auch festlegen, wie Text im Editor angezeigt werden soll.

##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>So ändern Sie die Textgröße in textbasierten Toolfenstern und Editoren

1.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.

2.  Wählen Sie im Ordner **Umgebung** die Option **Schriftarten und Farben** aus.

3.  Wählen Sie im Dropdownmenü **Einstellungen anzeigen für** eine Option aus.

     Um die Schriftgröße von Text in einem Editor zu ändern, klicken Sie auf den **Text-Editor**.

     Um die Schriftgröße von Text in textbasierten Toolfenstern zu ändern, wählen Sie die Option **[Alle Texttoolfenster]** aus.

     Um die Schriftgröße von QuickInfos in einem Editor zu ändern, wählen Sie die Option **Editor-QuickInfo** aus.

     Um die Schriftgröße von Text in den Popupfenstern für die automatische Vervollständigung von Anweisungen zu ändern, wählen Sie die Option **Anweisungsvervollständigung** aus.

4.  Wählen Sie unter **Elemente anzeigen** die Option **Nur Text** aus.

5.  Wählen Sie in der Dropdownliste **Schriftart** eine andere Schriftart aus.

6.  Wählen Sie in der Dropdownliste Schriftgrad eine andere **Schriftgröße** aus.

    > [!NOTE]
    >  Um die Textgröße für textbasierte Toolfenster und Editoren zurückzusetzen, wählen Sie die Option **Standard verwenden** aus.

7.  Klicken Sie auf **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Ändern der Farben, die in der IDE verwendet werden

 Sie können auch die Standardfarben für Text, Indikatorränder, Leerstellen und Codeelemente im Editor anpassen.

> [!NOTE]
> Um in allen Anwendungsfenstern des Betriebssystems kontrastreiche Farben zu verwenden, drücken Sie Linke **ALT+** Linke **UMSCHALT+DRUCK**. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet ist, schließen und öffnen Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], damit die hohen Kontraste ordnungsgemäß übernommen werden.


##### <a name="to-change-the-color-of-items-in-the-editor"></a>So ändern Sie die Farbe von Elementen im Editor

1.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.

2.  Klicken Sie im Ordner **Umgebung** auf die Option **Schriftarten und Farben**.

3.  Wählen Sie unter **Einstellungen anzeigen** für die Option **Text-Editor** aus.

4.  Wählen Sie unter **Elemente anzeigen** das Element aus, das Sie anpassen möchten, z.B. **Nur Text**, **Indikatorrand**, **Sichtbare Leerstellen**, **HTML-Attributname** oder **XML-Attribut**.

5.  Wählen Sie in den folgenden Steuerelementen Anzeigeoptionen aus: **Elementvordergrund**, **Elementhintergrund** und **Fett**.

6.  Klicken Sie auf **OK**.

## <a name="toolbars"></a>Symbolleisten

 Zur Verbesserung der Benutzerfreundlichkeit und Barrierefreiheit der Symbolleisten können Sie Text zu den Symbolleisten-Schaltflächen hinzufügen.

#### <a name="to-assign-text-to-toolbar-buttons"></a>So weisen Sie Symbolleisten-Schaltflächen Text zu

1.  Wählen Sie im Menü **Extras** die Option **Anpassen**.

2.  Wählen Sie im Dialogfeld **Anpassen** die Registerkarte **Befehle** aus.

3.  Wählen Sie die Option **Symbolleiste** und anschließend den Namen der Symbolleiste aus, in der sich die Schaltfläche befindet, für die Text angezeigt werden soll.

4.  Wählen Sie in der Liste den Befehl aus, den Sie ändern möchten.

5.  Wählen Sie **Auswahl ändern** aus.

6.  Wählen Sie **Symbol und Text** aus.

#### <a name="to-modify-the-displayed-text-in-a-button"></a>So ändern Sie den in einer Schaltfläche angezeigten Text

1.  Wählen Sie erneut **Auswahl ändern** aus.

2.  Geben Sie direkt neben **Name** eine neue Beschriftung für die ausgewählte Schaltfläche ein.

## <a name="see-also"></a>Siehe auch

* [Barrierefreiheitsfeatures in Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Ressourcen für das Entwerfen von Anwendungen mit Barrierefreiheit](../../ide/reference/resources-for-designing-accessible-applications.md)
