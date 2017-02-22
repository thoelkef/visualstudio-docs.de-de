---
title: "Gewusst wie: Festlegen von IDE-Barrierefreiheitsoptionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eingabehilfen [Visual Studio]"
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Festlegen von IDE-Barrierefreiheitsoptionen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umfasst Features zur Unterstützung von Personen mit eingeschränktem Seh\- und Schreibvermögen.  Zu diesen Features gehören unter anderem das Anpassen von Schriftgröße und \-farbe in Editoren, das Ändern der Größe von Text und Schaltflächen in Symbolleisten sowie die automatische Vervollständigung von Methoden\- und Parameternamen.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt außerdem Dvorak\-Tastaturlayouts, die den Zugriff auf die am häufigsten eingetippten Zeichen vereinfachen.  Sie können auch die Standardtastenkombinationen anpassen, die in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügbar sind.  Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Editoren, Dialogfelder und Toolfenster  
 Standardmäßig wird in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für Dialogfelder und Toolfenster die gleiche Schriftgröße und Schriftfarbe wie für das Betriebssystem verwendet.  Die Farbeinstellungen für den Rahmen der IDE, die Dialogfelder, Symbolleisten und Toolfenster basieren auf einem Farbschema: hell oder dunkel.  Sie können das aktuelle Farbschema im [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md) ändern.  
  
 Sie können auch festlegen, dass in der Codeansicht des Editors Popupfenster angezeigt werden.  Diese Fenster zeigen Ihnen möglicherweise verfügbare Member für das aktuelle Objekt und die Parameter, die für eine Funktion oder Anweisung benötigt werden.  Sie können besonders hilfreich sein, wenn Sie Schwierigkeiten bei der Eingabe über die Tastatur haben.  Allerdings kollidiert diese Funktion mit dem Fokus im Code\-Editor, was für manche Benutzer problematisch sein kann.  Sie können diese Fenster deaktivieren, indem Sie das Dialogfeld **Optionen** öffnen und **Member automatisch auflisten** sowie **Parameterinformationen** im **Text\-Editor** auf der Seite **Alle Sprachen** unter **Allgemein** löschen.  Weitere Informationen finden Sie unter [How to: Set General Editor Options](http://msdn.microsoft.com/de-de/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Sie können die Fenster in der IDE \(Integrated Development Environment, Integrierte Entwicklungsumgebung\) so anordnen, dass sie Ihrer individuellen Arbeitsweise entgegenkommen.  Sie können jedes Toolfenster andocken, verschieben, ausblenden oder automatisch ausblenden.  
  
 Weitere Informationen über das Ändern von Fensterlayouts finden Sie unter [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### Ändern der Textgröße  
 Sie können die Einstellungen für textbasierte Toolfenster, z. B. das Fenster **Befehl**, das Fenster **Direkt** und das Fenster **Ausgabe**, im Bereich **Schriftarten und Farben** der Optionen unter **Umgebung** im Dialogfeld **Extras** ändern.  Wenn in der Dropdownliste **Einstellungen anzeigen für** der Eintrag **\[Alle Texttoolfenster\]** ausgewählt wurde, wird in den Dropdownlisten **Elementvordergrund** und **Elementhintergrund** die Standardeinstellung **Standard** angezeigt.  Sie können auch festlegen, wie Text im Editor angezeigt werden soll.  
  
##### So ändern Sie die Textgröße in textbasierten Toolfenstern und Editoren  
  
1.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
2.  Wählen Sie im Ordner **Umgebung** die Option **Schriftarten und Farben** aus.  
  
3.  Wählen Sie im Dropdownmenü **Einstellungen anzeigen für** eine Option aus.  
  
     Um die Schriftgröße von Text in einem Editor zu ändern, wählen Sie die Option **Text\-Editor** aus.  
  
     Um die Schriftgröße von Text in textbasierten Toolfenstern zu ändern, wählen Sie die Option **\[Alle Texttoolfenster\]** aus.  
  
     Um die Schriftgröße von QuickInfos in einem Editor zu ändern, wählen Sie die Option **Editor\-QuickInfo** aus.  
  
     Um die Schriftgröße von Text in den Popup\-Fenstern für die automatische Vervollständigung von Anweisungen zu ändern, wählen Sie die Option **Anweisungsvervollständigung** aus.  
  
4.  Wählen Sie unter **Elemente anzeigen** die Option **Nur Text** aus.  
  
5.  Wählen Sie in der Dropdownliste **Schriftart** eine andere Schriftart aus.  
  
6.  Wählen Sie in der Dropdownliste **Schriftgrad** eine andere Schriftgröße aus.  
  
    > [!NOTE]
    >  Um die Textgröße für textbasierte Toolfenster und Editoren zurückzusetzen, wählen Sie die Option **Standard verwenden** aus.  
  
7.  Klicken Sie auf **OK**.  
  
### Ändern der in der IDE verwendeten Farben  
 Sie können auch die Standardfarben für Text, Indikatorränder, Leerstellen und Codeelemente im Editor anpassen.  
  
> [!NOTE]
>  Um in allen Anwendungsfenstern des Betriebssystems kontrastreiche Farben zu verwenden, drücken Sie Linke **ALT\+**Linke **UMSCHALT\+DRUCK**.  Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet ist, schließen und öffnen Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], damit die hohen Kontraste ordnungsgemäß übernommen werden.  
  
##### So ändern Sie die Farbe von Elementen im Editor  
  
1.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
2.  Wählen Sie im Ordner **Umgebung** die Option **Schriftarten und Farben** aus.  
  
3.  Wählen Sie unter **Einstellungen anzeigen für** die Option **Text\-Editor** aus.  
  
4.  Wählen Sie unter **Elemente anzeigen** das Element aus, das Sie anpassen möchten, z. B. **Nur Text**, **Indikatorrand**, **Sichtbare Leerstellen**, **HTML\-Attributname** oder **XML\-Attribut**.  
  
5.  Wählen Sie in den folgenden Steuerelementen Anzeigeoptionen aus: **Elementvordergrund**, **Elementhintergrund** und **Fett**.  
  
6.  Klicken Sie auf **OK**.  
  
## Symbolleisten  
 Zur Verbesserung der Benutzerfreundlichkeit und Barrierefreiheit der Symbolleisten können Sie Text zu den Symbolleisten\-Schaltflächen hinzufügen.  
  
#### So weisen Sie Symbolleisten\-Schaltflächen Text zu  
  
1.  Wählen Sie im Menü **Extras** die Option **Anpassen**.  
  
2.  Wählen Sie im Dialogfeld **Anpassen** die Registerkarte **Befehle** aus.  
  
3.  Wählen Sie die Option **Symbolleiste** und anschließend den Namen der Symbolleiste aus, in der sich die Schaltfläche befindet, für die Text angezeigt werden soll.  
  
4.  Wählen Sie in der Liste den Befehl aus, den Sie ändern möchten.  
  
5.  Wählen Sie **Auswahl ändern** aus.  
  
6.  Wählen Sie **Symbol und Text** aus.  
  
#### So ändern Sie den von der Schaltfläche angezeigten Text  
  
1.  Wählen Sie erneut **Auswahl ändern** aus.  
  
2.  Geben Sie direkt neben **Name** eine neue Beschriftung für die ausgewählte Schaltfläche ein.  
  
## Siehe auch  
 [Barrierefreiheitsfunktionen in Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Ressourcen für das Entwerfen von Anwendungen mit Barrierefreiheit](../../ide/reference/resources-for-designing-accessible-applications.md)