---
title: "Erstellen einer Benutzeroberfl&#228;che mit Blend f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Blend.Start.Dev12"
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 31
caps.handback.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Erstellen einer Benutzeroberfl&#228;che mit Blend f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Blend für Visual Studio unterstützt Sie beim Entwerfen von XAML\-basierten Apps für Windows\-Desktop, Web, [Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx) und [Windows Store](http://msdn.microsoft.com/library/windows/apps/jj129478.aspx).  Es bietet die gleiche einfache XAML\-Entwurfsumgebung wie Visual Studio und fügt visuelle Designer für erweiterte Aufgaben hinzu, z. B. Animationen und Verhalten.  
  
 Wenn Sie mit Blend für Visual Studio nicht vertraut sind, nehmen Sie sich einen Moment Zeit, um die besonderen Funktionen des Arbeitsbereichs kennenzulernen.  In diesem Abschnitt erhalten Sie eine kurze Führung.  
  
> [!NOTE]
>  Informationen zu den freigegebenen Entwurfsfunktionen wie die Zeichenfläche, das Dokumentgliederungsfenster und das Gerätefenster finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML\-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
 **In diesem Abschnitt**:  
  
-   [Überblick über die Werkzeuge](#Tools)  
  
-   [Überblick über den Objektbereich](#Assets)  
  
-   [Überblick über die Bereiche Objekte und Zeitachse](#Objects)  
  
-   [Überblick über den Bereich Eigenschaften](#Properties)  
  
##  <a name="Tools"></a> Überblick über die Werkzeuge  
 Mithilfe des Bereichs **Werkzeuge** in Visual Studio können Sie in Ihrer Anwendung Objekte erstellen und ändern.  Die Objekte werden erstellt, indem Sie ein Werkzeug auswählen und die Objekte mit der Maus auf die Zeichenfläche ziehen.  
  
|||||  
|-|-|-|-|  
||**Auswahlwerkzeuge** Wählen Sie Objekte und Pfade.<br /><br /> Verwenden Sie das Werkzeug **Direktauswahl** wird verwendet, um geschachtelte Objekte und Pfadsegmente auszuwählen.|![Legende A](../designers/media/b5_label_a.png "b5\_label\_A")|**Pinsel mit Farbverlauf und die Werkzeuge**|  
||**Ansichtswerkzeuge** Mit diesen Werkzeugen kann die Ansicht der Zeichenfläche beispielsweise zum Schwenken und Zoomen verwendet werden.|![Legende B](../designers/media/b5_label_b.png "b5\_label\_B")|**Pfadwerkzeuge**|  
||**Pinselwerkzeuge** Dienen zum Bearbeiten der visuellen Attribute eines Objekts, beispielsweise Pinseltransformationen, Zeichnen eines Objekts oder Auswählen der Attribute eines Objekts zur Übertragung auf ein anderes Objekt.|![Legende C](../designers/media/b5_label_c.png "b5\_label\_C")|**Formenwerkzeuge**|  
||**Objektbibliothekswerkzeuge** Dienen zum Zeichnen der gängigsten Objekte auf der Zeichenfläche, z. B. Pfade, Formen, Layoutbereiche, Text und Steuerelemente.|![Legende D](../designers/media/b5_label_d.png "b5\_label\_D")|**Layoutbereiche**|  
||**Objektwerkzeuge** Ermöglichen den Zugriff auf das **Objektepanel** und die Anzeige des zuletzt verwendeten Objekts aus der Bibliothek.|![Legende E](../designers/media/b5_label_e.png "b5\_label\_E")|**Textsteuerelemente**|  
|||![Legende F](../designers/media/b5_label_f.png "b5\_label\_F")|**Allgemeine Steuerelemente**|  
  
 **Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Die Symbolleiste](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).  
  
##  <a name="Assets"></a> Überblick über den Objektbereich  
 Sie finden alle Steuerelemente im **Objektepanel**, das der **Toolbox** in Visual Studio ähnelt.  Zusätzlich zu Steuerelementen befinden sich alle zur Zeichenfläche hinzufügbaren Objekte im **Objektepanel**, einschließlich Stile, Medien, Verhalten und Effekte.  
  
|||  
|-|-|  
|![](../designers/media/b1_1.png "B1\_1")|**Suchfeld** Verwenden Sie das Feld **Suchen** zum Filtern der Liste der Objekte.|  
|![](../designers/media/b1_2.png "B1\_2")|**Gittermodus und Listenmodus** Wechseln Sie zwischen der Ansicht **Gittermodus** und **Listenmodus** der Objekte.|  
|![](../designers/media/b1_3.png "B1\_3")|**Objektkategorien** Klicken Sie auf eine Kategorie oder Unterkategorie, um die Liste der Objekte in dieser Kategorie anzuzeigen.|  
|![](../designers/media/b1_4.png "B1\_4")|**Formatvorlagen** Zeigt alle Stile an, die im Ressourcenverzeichnis enthalten sind.|  
|![](../designers/media/b1_5.png "B1\_5")|**Beschreibung** Zeigen Sie eine Beschreibung der ausgewählten Objektkategorie oder Unterkategorie an.|  
  
##  <a name="Objects"></a> Überblick über die Bereiche Objekte und Zeitachse  
 Verwenden Sie diesen Bereich, um die Objekte auf der Zeichenfläche zu organisieren und gegebenenfalls zu animieren.  
  
|||  
|-|-|  
||**Objektansicht** Zeigt die visuelle Struktur eines Dokuments an.  Sie können einen Drilldown zu verschiedenen Detailebenen durchführen.  Sie können auch zum Organisieren von Objekten auf der Zeichenfläche weitere Ebenen hinzufügen.  Auf diese Weise können Sie sie sperren und als Gruppe ausblenden.|  
||**Anzeige für Aufzeichnungsmodus** Zeigt an, wenn Sie Eigenschaftenänderungen in einer Zeitachse aufzeichnen.|  
||**Storyboardauswahl** Zeigt eine Liste der von Ihnen erstellten Storyboards an.|  
||**Storyboard schließen** Schließt das aktuelle Storyboard.|  
||**Storyboard\-Optionen** Erstellen, Kopieren, Umkehren, Löschen, Umbenennen oder Schließen eines Storyboards.|  
||**Wiedergabesteuerelemente** Navigieren durch die Zeitachse.  Sie können die Position auch ziehen, um auf der Zeitachse zu navigieren oder *Scrubbing* auszuführen.|  
||**Bereich zurücksetzen auf** Setzt die Objektansicht wieder zurück zum vorherigen Stammobjekt oder Bereich.  Dies ist nur beim Ändern von Stilen oder Vorlagen möglich.|  
||**Keyframe aufzeichnen** Zeichnet einen Snapshot der Eigenschaften des ausgewählten Objekts zum aktuellen Zeitpunkt auf.|  
||**Andockoptionen** Legt Andock\-Zeitachse, Andockauflösung fest und deaktiviert das Andocken der Zeitachse.|  
||**Einblenden\/Ausblenden**, **Sperren\/Entsperren** Zeigt die Sichtbarkeits\- und Sperroptionen für die Objektansicht oder blendet sie aus.|  
||**Position auf der Zeitachse** zeigt die aktuelle Zeit in Millisekunden an.  Wenn Sie zu einem bestimmten Zeitpunkt springen möchten, können Sie auch direkt einen Zeitwert in dieses Feld eingeben.  Die Präzision ist von der unter **Andockoptionen** festgelegten Auflösung zum Andocken abhängig.|  
||**Position** Zeigt den Zeitpunkt der Animation an.  Sie können die Position über die Zeitachse ziehen, um eine Vorschau der Animation anzuzeigen.|  
||**Für Zeitachsen festgelegte Keyframes** Ändert den Wert einer Eigenschaftsänderung zu einem bestimmten Zeitpunkt.|  
||**Änderungsreihenfolge von Objekten** Legt die Anzeigereihenfolge von Objekten fest.  Klicken Sie auf diese Schaltfläche, um Objekte in der Strukturansicht gemäß der Z\-Reihenfolge \(von vorne nach hinten\) oder gemäß der Markupreihenfolge \(entspricht der Reihenfolge in der **XAML**\-Ansicht\) anzuordnen.|  
||**Zeitachsenzoom** Legt die Zoomauflösung der Zeitachse fest.  Durch Vergrößern können Sie eine detailliertere Animation bearbeiten, während Sie beim Verkleinern eine Übersicht der Ereignisse über einen längeren Zeitraum hinweg anzeigen können.  Wenn Sie beim Vergrößern kein Keyframe zum gewünschten Zeitpunkt festlegen können, stellen Sie sicher, dass die Auflösung zum Andocken hoch genug eingestellt ist.|  
||**Zeitachsen\-Erfassungsbereich** Zeigt die Zeitachse an und ermöglicht Ihnen das Verschieben der Keyframes durch Ziehen oder Verwenden der Kontextmenüs.|  
  
##  <a name="Properties"></a> Überblick über den Bereich Eigenschaften  
 Verwenden Sie diesen Bereich, um die Eigenschaften eines Objekts anzuzeigen und zu ändern.  Sie können sie auch direkt auf der Zeichenfläche festlegen.  Wenn Sie dies tun, werden die Änderungen im Bereich **Eigenschaften** angezeigt.  
  
 **Kategorien** Erweitert und Reduziert Kategorien von Eigenschaften.  Klicken Sie auf **Erweitern** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d\-074c\-421a\-bbb3\-6f5055b67b64") und auf **Reduzieren** ![Reduzieren](../designers/media/b5_collapse_button.png "b5\_collapse\_button"), um Kategoriedetails anzuzeigen oder auszublenden.  
  
|||  
|-|-|  
||**Name und Typ** Zeigt das Symbol, den Namen und den Typ des ausgewählten Objekts an.|  
||**Anordnen nach** Anordnet Eigenschaften alphabetisch nach Namen, Quelle oder Kategorie an.|  
||**Pinseleigenschaften** Legt die visuellen Eigenschaften für Pinselarten \(Füllung, Strich und Vordergrund\) fest.|  
||**Farb\-Editor** Wird für Volltonfarben\- und Farbverlaufspinsel verwendet.|  
||**Farbauswahl** Wählt eine Farbe aus.|  
||**Farbchips** Zeigt die Ausgangsfarbe, aktuelle Farbe und letzte Farbe an.|  
||**Formatpipetten** Verwenden die Farbe eines Elements auf dem Bildschirm.  Die **Verlaufspipette** ist verfügbar, wenn der **Farbverlaufspinsel** ausgewählt ist.  Die **Verlaufspipette** ist verfügbar, wenn der **Farbverlaufspinsel** ausgewählt ist.|  
||**Eigenschaften und Ereignisse** Legt Eigenschaften oder Ereignisse für ein ausgewähltes Element fest.|  
||**Suchfeld** Sucht nach Eigenschaften.  Filtert die Eigenschaften, die angezeigt werden, durch die Eingabe in das Feld **Suche**.||  
||**Pinsel\-Editor\-Registerkarten** Zum Auswählen eines Pinsel\-Editors.  Sie können **Keine Pinsel**, **Mit Volltonfarbe**, **Farbverlaufspinsel**, **Kacheleffekt** und\/oder **Pinselressource** auswählen.|  
||**Farbressourcen** Wendet genau dieselbe Farbe auf verschiedene Eigenschaften an.  Die Registerkarte **Farbressourcen** enthält **Lokale Ressourcen** und **Systemressourcen**.|  
||**RGB\-Farbspektrum** Sie können die Farbe ändern, indem Sie die Werte für **R**\-, **G**\- oder **B**\-Zahlen\-Editoren \(Rot, Grün, Blau\) anpassen.|  
||**Alphakanal** Ändern Sie den Alphawert, indem Sie den Zahleneditor neben **A** verwenden.|  
||**Farbe in Ressource konvertieren** Konvertiert die ausgewählte Farbe in eine Farbressource.  Farbressourcen sind verfügbar, wenn Sie auf die Farbressourcenregisterkarte klicken.|  
||**Farbtonwert** Zeigt den hexadezimalen Wert der angezeigten Farbe an.|  
||**Schieberegler für Farbverlauf** Erscheint nur, wenn ein Farbverlaufspinsel ausgewählt ist.|  
||**Erweiterte Eigenschaften einblenden** Zeigt Kategorien von Eigenschaften an, die weniger häufig verwendet werden.|  
  
 **Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Eigenschaftenbereich](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).  
  
## Siehe auch  
 [Einfügen von Steuerelementen und Ändern des Verhaltens](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)   
 [Animieren von Objekten](../designers/animate-objects-in-xaml-designer.md)   
 [Zeichnen von Formen und Pfaden](../designers/draw-shapes-and-paths.md)   
 [Designing XAML in Visual Studio and Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)