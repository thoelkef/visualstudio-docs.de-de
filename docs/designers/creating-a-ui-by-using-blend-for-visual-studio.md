---
title: Erstellen einer Benutzeroberfläche mit Blend für Visual Studio
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66addedc32c7023e774cd28f340f8216516c3fb7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Erstellen einer Benutzeroberfläche mit Blend für Visual Studio

Blend für Visual Studio unterstützt Sie beim Erstellen von XAML-basierten Windows- und Web-Anwendungen. Es bietet die gleiche einfache XAML-Entwurfsumgebung wie Visual Studio und fügt visuelle Designer für erweiterte Aufgaben hinzu, z. B. Animationen und Verhalten. Einen Vergleich zwischen Blend und Visual Studio finden Sie unter [Entwerfen von XAML in Visual Studio und Blend für Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Blend für Visual Studio ist eine Komponente von Visual Studio. Wählen Sie für die Installation von Blend im **Visual Studio-Installer** entweder die Workload **Entwicklung für die universelle Windows-Plattform** oder **.NET Desktopentwicklung**. Beide Workloads umfassen die Komponente „Blend für Visual Studio“.

![Komponenten der UWP-Workload](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Komponenten der Workload „.NET Desktopentwicklung“](media/installer-dotnet-desktop.png)

Wenn Sie mit Blend für Visual Studio nicht vertraut sind, nehmen Sie sich einen Moment Zeit, um die besonderen Funktionen des Arbeitsbereichs kennenzulernen. In diesem Abschnitt erhalten Sie eine kurze Führung.

> [!NOTE]
> Informationen zu den freigegebenen Entwurfsfunktionen wie die Zeichenfläche, das Dokumentgliederungsfenster und das Gerätefenster finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer in Visual Studio](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tour-of-the-tools-panel"></a>Überblick über die Werkzeuge

Mithilfe des Bereichs **Werkzeuge** in Blend für Visual Studio können Sie in Ihrer Anwendung Objekte erstellen und ändern. Die Objekte werden erstellt, indem Sie ein Werkzeug auswählen und die Objekte mit der Maus auf die Zeichenfläche ziehen.

![Werkzeugbereich](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|||||
|-|-|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Auswahlwerkzeuge** Wählen Sie Objekte und Pfade aus.<br /><br /> Verwenden Sie das Werkzeug **Direktauswahl**, um geschachtelte Objekte und Pfadsegmente auszuwählen.|![Legende A](../designers/media/b5_label_a.png "b5_label_A")|**Pinsel mit Farbverlauf und die Werkzeuge**|
|![](../designers/media/b1_2.png "B1_2")|**Ansichtswerkzeuge** Mit diesen Werkzeugen kann die Ansicht der Zeichenfläche beispielsweise zum Schwenken und Zoomen verwendet werden.|![Legende B](../designers/media/b5_label_b.png "b5_label_B")|**Pfadwerkzeuge**|
|![](../designers/media/b1_3.png "B1_3")|**Pinselwerkzeuge** Sie dienen zum Bearbeiten der visuellen Attribute eines Objekts, beispielsweise Pinseltransformationen, Zeichnen eines Objekts oder Auswählen der Attribute eines Objekts zur Übertragung auf ein anderes Objekt.|![Legende C](../designers/media/b5_label_c.png "b5_label_C")|**Formenwerkzeuge**|
|![](../designers/media/b1_4.png "B1_4")|**Objektbibliothekswerkzeuge** Sie dienen zum Zeichnen der gängigsten Objekte auf der Zeichenfläche, z.B. Pfade, Formen, Layoutbereiche, Text und Steuerelemente.|![Legende D](../designers/media/b5_label_d.png "b5_label_D")|**Layoutbereiche**|
|![](../designers/media/b1_5.png "B1_5")|**Objektwerkzeuge** Sie ermöglichen den Zugriff auf den **Objektbereich** und die Anzeige des zuletzt verwendeten Objekts aus der Bibliothek.|![Legende E](../designers/media/b5_label_e.png "b5_label_E")|**Textsteuerelemente**|
|||![Legende F](../designers/media/b5_label_f.png "b5_label_E")|**Allgemeine Steuerelemente**|

**Sehen Sie sich ein kurzes Video (in englischer Sprache) an:** ![Konfigurieren installierter Funktionen ](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Die Symbolleiste](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a>Überblick über den Objektbereich

Sie finden alle Steuerelemente im **Objektbereich**, das der **Toolbox** in Visual Studio ähnelt. Zusätzlich zu den Steuerelementen befinden sich alle zur Zeichenfläche hinzufügbaren Objekte im **Objektbereich**, einschließlich Stile, Medien, Verhalten und Effekte.

![Objektbereich](../designers/media/blend5_assets_panel.png "Blend5_Assets_panel")

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Suchfeld** Verwenden Sie das Feld **Suchen** zum Filtern der Liste der Objekte.|
|![](../designers/media/b1_2.png "B1_2")|**Gittermodus und Listenmodus** Wechseln Sie zwischen der Ansicht **Gittermodus** und **Listenmodus** der Objekte.|
|![](../designers/media/b1_3.png "B1_3")|**Objektkategorien** Klicken Sie auf eine Kategorie oder Unterkategorie, um die Liste der Objekte in dieser Kategorie anzuzeigen.|
|![](../designers/media/b1_4.png "B1_4")|**Formatvorlagen** Zeigt alle Stile an, die im Ressourcenverzeichnis enthalten sind.|
|![](../designers/media/b1_5.png "B1_5")|**Beschreibung** Zeigen Sie eine Beschreibung der ausgewählten Objektkategorie oder Unterkategorie an.|

## <a name="tour-of-the-objects-and-timeline-panel"></a>Überblick über die Bereiche Objekte und Zeitachse

Verwenden Sie diesen Bereich, um die Objekte auf der Zeichenfläche zu organisieren und gegebenenfalls zu animieren.

![Objekt- und Zeitachsenbereich im Animationsmodus](../designers/media/b5_object_timeline_animation.png "b5_object_timeline_animation")

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Objektansicht** Zeigt die visuelle Struktur eines Dokuments an. Sie können einen Drilldown zu verschiedenen Detailebenen durchführen. Sie können auch zum Organisieren von Objekten auf der Zeichenfläche weitere Ebenen hinzufügen. Auf diese Weise können Sie sie sperren und als Gruppe ausblenden.|
|![](../designers/media/b1_2.png "B1_2")|**Anzeige für Aufzeichnungsmodus** Prüfen Sie, ob Sie Eigenschaftenänderungen in einer Zeitachse aufzeichnen.|
|![](../designers/media/b1_3.png "B1_3")|**Storyboardauswahl** Zeigen Sie eine Liste der von von Ihnen erstellten Storyboards an.|
|![](../designers/media/b1_4.png "B1_4")|**Storyboard schließen** Schließt das aktuelle Storyboard.|
|![](../designers/media/b1_5.png "B1_5")|**Storyboard-Optionen** Erstellen, Kopieren, Umkehren, Löschen, Umbenennen oder Schließen eines Storyboards.|
|![](../designers/media/b1_6.png "B1_6")|**Wiedergabesteuerelemente** Navigieren durch die Zeitachse. Sie können die Position auch ziehen, um auf der Zeitachse zu navigieren oder *Scrubbing* auszuführen.|
|![](../designers/media/b1_7.png "B1_7")|**Bereich zurücksetzen auf** Setzt die Objektansicht wieder zurück zum vorherigen Stammobjekt oder Bereich. Dies ist nur beim Ändern von Stilen oder Vorlagen möglich.|
|![](../designers/media/b1_8.png "B1_8")|**Keyframe aufzeichnen** Zeichnet einen Snapshot der Eigenschaften des ausgewählten Objekts zum aktuellen Zeitpunkt auf.|
|![](../designers/media/b1_9.png "B1_9")|**Andockoptionen** Legt Andock-Zeitachse, Andockauflösung fest und deaktiviert das Andocken der Zeitachse.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Einblenden/Ausblenden**, **Sperren/Entsperren** Zeigt die Sichtbarkeits- und Sperroptionen für die Objektansicht oder blendet sie aus.|
|![](../designers/media/b1_11.png "B1_11")|**Position auf der Zeitachse** zeigt die aktuelle Zeit in Millisekunden an. Wenn Sie zu einem bestimmten Zeitpunkt springen möchten, können Sie auch direkt einen Zeitwert in dieses Feld eingeben. Die Präzision ist von der unter **Andockoptionen** festgelegten Auflösung zum Andocken abhängig.|
|![](../designers/media/b1_12.png "B1_12")|**Position** Zeigt den Zeitpunkt der Animation an. Sie können die Position über die Zeitachse ziehen, um eine Vorschau der Animation anzuzeigen.|
|![](../designers/media/b1_13.png "B1_13")|**Für Zeitachsen festgelegte Keyframes** Ändert den Wert einer Eigenschaftsänderung zu einem bestimmten Zeitpunkt.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Änderungsreihenfolge von Objekten** Legt die Anzeigereihenfolge von Objekten fest. Klicken Sie auf diese Schaltfläche, um Objekte in der Strukturansicht gemäß der Z-Reihenfolge (von vorne nach hinten) oder gemäß der Markupreihenfolge (entspricht der Reihenfolge in der **XAML**-Ansicht) anzuordnen.|
|![](../designers/media/b1_15.png "B1_15")|**Zeitachsenzoom** Legt die Zoomauflösung der Zeitachse fest. Durch Vergrößern können Sie eine detailliertere Animation bearbeiten, während Sie beim Verkleinern eine Übersicht der Ereignisse über einen längeren Zeitraum hinweg anzeigen können. Wenn Sie beim Vergrößern kein Keyframe zum gewünschten Zeitpunkt festlegen können, stellen Sie sicher, dass die Auflösung zum Andocken hoch genug eingestellt ist.|
|![Legende 16](../designers/media/b5_label_16.png "b5_label_16")|**Zeitachsen-Erfassungsbereich** Zeigt die Zeitachse an und ermöglicht Ihnen das Verschieben der Keyframes durch Ziehen oder Verwenden der Kontextmenüs.|

## <a name="tour-of-the-properties-panel"></a>Überblick über den Bereich Eigenschaften

Verwenden Sie diesen Bereich, um die Eigenschaften eines Objekts anzuzeigen und zu ändern. Sie können sie auch direkt auf der Zeichenfläche festlegen. Wenn Sie dies tun, werden die Änderungen im Bereich **Eigenschaften** angezeigt.

![Bereich „Eigenschaften“](../designers/media/blend5_properties_panel.png "Blend5_properties_panel")

**Kategorien** Erweitern und Reduzieren der Kategorien von Eigenschaften. Klicken Sie auf **Erweitern** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") und **Reduzieren** ![Reduzieren] (../designers/media/b5_collapse_button.png "Schaltfläche_Reduzieren"), um Kategoriedetails anzuzeigen oder auszublenden.

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Name und Typ** Zeigt das Symbol, den Namen und den Typ des ausgewählten Objekts an.|
|![](../designers/media/b1_2.png "B1_2")|**Anordnen nach** Ordnet Eigenschaften alphabetisch nach Namen, Quelle oder Kategorie an.|
|![](../designers/media/b1_3.png "B1_3")|**Pinseleigenschaften** Legt die visuellen Eigenschaften für Pinselarten (Füllung, Strich und Vordergrund) fest.|
|![](../designers/media/b1_4.png "B1_4")|**Farb-Editor** Wird für Volltonfarben- und Farbverlaufspinsel verwendet.|
|![](../designers/media/b1_5.png "B1_5")|**Farbauswahl** Wählt eine Farbe aus.|
|![](../designers/media/b1_6.png "B1_6")|**Farbchips** Zeigt die Ausgangsfarbe, die aktuelle Farbe und die letzte Farbe an.|
|![](../designers/media/b1_7.png "B1_7")|**Formatpipetten** Verwendet die Farbe eines Elements auf dem Bildschirm. Die **Verlaufspipette** ist verfügbar, wenn der **Pinsel mit Volltonfarbe** ausgewählt ist. Die **Verlaufspipette** ist verfügbar, wenn der **Farbverlaufspinsel** ausgewählt ist.|
|![](../designers/media/b1_8.png "B1_8")|**Eigenschaften und Ereignisse** Legt Eigenschaften oder Ereignisse für ein ausgewähltes Element fest.|
|![](../designers/media/b1_9.png "B1_9")|**Suchfeld** Sucht nach Eigenschaften. Filtert die Eigenschaften, die angezeigt werden, durch die Eingabe in das Feld **Suche**.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Pinsel-Editor-Registerkarten** Zum Auswählen eines Pinsel-Editors. Sie können **Keine Pinsel**, **Mit Volltonfarbe**, **Farbverlaufspinsel**, **Kacheleffekt** und/oder **Pinselressource** auswählen.|
|![](../designers/media/b1_11.png "B1_11")|**Farbressourcen** Wendet genau dieselbe Farbe auf verschiedene Eigenschaften an. Die Registerkarte **Farbressourcen** enthält **Lokale Ressourcen** und **Systemressourcen**.|
|![](../designers/media/b1_12.png "B1_12")|**RGB-Farbspektrum** Sie können die Farbe ändern, indem Sie die Werte für **R**-, **G**- oder **B**-Zahlen-Editoren (Rot, Grün, Blau) anpassen.|
|![](../designers/media/b1_13.png "B1_13")|**Alphakanal** Ändern Sie den Alphawert, indem Sie den Zahleneditor neben **A** verwenden.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Farbe in Ressource konvertieren** Konvertiert die ausgewählte Farbe in eine Farbressource. Farbressourcen sind verfügbar, wenn Sie auf die Farbressourcenregisterkarte klicken.|
|![](../designers/media/b1_15.png "B1_15")|**Farbtonwert** Zeigt den hexadezimalen Wert der angezeigten Farbe an.|
|![Legende 16](../designers/media/b5_label_16.png "b5_label_16")|**Schieberegler für Farbverlauf** Erscheint nur, wenn ein Farbverlaufspinsel ausgewählt ist.|
|![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8")|**Erweiterte Eigenschaften einblenden** Zeigt Kategorien von Eigenschaften an, die weniger häufig verwendet werden.|

**Sehen Sie sich ein kurzes Video (in englischer Sprache) an:** ![Konfigurieren installierter Funktionen ](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Bereich „Eigenschaften“](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Siehe auch

- [Insert controls and modify their behavior (Einfügen von Steuerelementen und Ändern des Verhaltens)](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Animate objects (Animieren von Objekten)](../designers/animate-objects-in-xaml-designer.md)
- [Zeichnen von Formen und Pfaden](../designers/draw-shapes-and-paths.md)
- [Designing XAML in Visual Studio and Blend for Visual Studio (Entwerfen von XAML-Code in Visual Studio und Blend für Visual Studio)](../designers/designing-xaml-in-visual-studio.md)