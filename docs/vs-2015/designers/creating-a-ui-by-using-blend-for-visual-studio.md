---
title: Erstellen einer Benutzeroberfläche mit Blend für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 565eac18d4cbf74453335963817e6b5e655268ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820732"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Erstellen einer Benutzeroberfläche mit Blend für Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Blend für Visual Studio können Sie XAML-basierte Windows-Desktop-, Web-, [Windows Phone-](http://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx),und [Windows Store](http://msdn.microsoft.com/library/windows/apps/jj129478.aspx)-Apps entwerfen. Es bietet die gleiche einfache XAML-Entwurfsumgebung wie Visual Studio und fügt visuelle Designer für erweiterte Aufgaben hinzu, z. B. Animationen und Verhalten.  

 Blend für Visual Studio ist Teil von Visual Studio und muss daher nicht separat heruntergeladen werden. Sie müssen es jedoch im Visual Studio-Installationsprogramm auswählen, um es auf Ihrem System installieren zu können.  

 Wenn Sie mit Blend für Visual Studio nicht vertraut sind, nehmen Sie sich einen Moment Zeit, um die besonderen Funktionen des Arbeitsbereichs kennenzulernen. In diesem Abschnitt erhalten Sie eine kurze Führung.  

> [!NOTE]
>  Informationen zu den freigegebenen Entwurfsfunktionen wie die Zeichenfläche, das Dokumentgliederungsfenster und das Gerätefenster finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer in Visual Studio](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  

 **In diesem Thema**:  

-   [Überblick über die Werkzeuge](#Tools)  

-   [Überblick über den Objektbereich](#Assets)  

-   [Überblick über die Bereiche Objekte und Zeitachse](#Objects)  

-   [Überblick über den Bereich Eigenschaften](#Properties)  

##  <a name="Tools"></a>Überblick über die Werkzeuge  
 Mithilfe des Bereichs **Werkzeuge** in Blend für Visual Studio können Sie in Ihrer Anwendung Objekte erstellen und ändern. Die Objekte werden erstellt, indem Sie ein Werkzeug auswählen und die Objekte mit der Maus auf die Zeichenfläche ziehen.  

 ![Werkzeugbereich](../designers/media/blend5toolspanel.png "Blend5Toolspanel")  

|||||  
|-|-|-|-|  
|![](../designers/media/b1-1.png "B1_1")|**Auswahlwerkzeuge** Wählen Sie Objekte und Pfade aus.<br /><br /> Verwenden Sie das Werkzeug **Direktauswahl**, um geschachtelte Objekte und Pfadsegmente auszuwählen.|![Legende A](../designers/media/b5-label-a.png "b5_label_A")|**Pinsel mit Farbverlauf und die Werkzeuge**|  
|![](../designers/media/b1-2.png "B1_2")|**Ansichtswerkzeuge** Mit diesen Werkzeugen kann die Ansicht der Zeichenfläche beispielsweise zum Schwenken und Zoomen verwendet werden.|![Legende B](../designers/media/b5-label-b.png "b5_label_B")|**Pfadwerkzeuge**|  
|![](../designers/media/b1-3.png "B1_3")|**Pinselwerkzeuge** Sie dienen zum Bearbeiten der visuellen Attribute eines Objekts, beispielsweise Pinseltransformationen, Zeichnen eines Objekts oder Auswählen der Attribute eines Objekts zur Übertragung auf ein anderes Objekt.|![Legende C](../designers/media/b5-label-c.png "b5_label_C")|**Formenwerkzeuge**|  
|![](../designers/media/b1-4.png "B1_4")|**Objektbibliothekswerkzeuge** Sie dienen zum Zeichnen der gängigsten Objekte auf der Zeichenfläche, z.B. Pfade, Formen, Layoutbereiche, Text und Steuerelemente.|![Legende D](../designers/media/b5-label-d.png "b5_label_D")|**Layoutbereiche**|  
|![](../designers/media/b1-5.png "B1_5")|**Objektwerkzeuge** Sie ermöglichen den Zugriff auf den **Objektbereich** und die Anzeige des zuletzt verwendeten Objekts aus der Bibliothek.|![Legende E](../designers/media/b5-label-e.png "b5_label_E")|**Textsteuerelemente**|  
|||![Legende F](../designers/media/b5-label-f.png "b5_label_E")|**Allgemeine Steuerelemente**|  

 **Sehen Sie sich ein kurzes Video (in englischer Sprache) an:** ![Konfigurieren installierter Funktionen ](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Die Symbolleiste](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).  

##  <a name="Assets"></a>Überblick über den Objektbereich  
 Sie finden alle Steuerelemente im **Objektbereich**, das der **Toolbox** in Visual Studio ähnelt. Zusätzlich zu den Steuerelementen befinden sich alle zur Zeichenfläche hinzufügbaren Objekte im **Objektbereich**, einschließlich Stile, Medien, Verhalten und Effekte.  

 ![Objektbereich](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")  

|||  
|-|-|  
|![](../designers/media/b1-1.png "B1_1")|**Suchfeld** Verwenden Sie das Feld **Suchen** zum Filtern der Liste der Objekte.|  
|![](../designers/media/b1-2.png "B1_2")|**Gittermodus und Listenmodus** Wechseln Sie zwischen der Ansicht **Gittermodus** und **Listenmodus** der Objekte.|  
|![](../designers/media/b1-3.png "B1_3")|**Objektkategorien** Klicken Sie auf eine Kategorie oder Unterkategorie, um die Liste der Objekte in dieser Kategorie anzuzeigen.|  
|![](../designers/media/b1-4.png "B1_4")|**Formatvorlagen** Zeigt alle Stile an, die im Ressourcenverzeichnis enthalten sind.|  
|![](../designers/media/b1-5.png "B1_5")|**Beschreibung** Zeigen Sie eine Beschreibung der ausgewählten Objektkategorie oder Unterkategorie an.|  

##  <a name="Objects"></a>Überblick über die Bereiche Objekte und Zeitachse  
 Verwenden Sie diesen Bereich, um die Objekte auf der Zeichenfläche zu organisieren und gegebenenfalls zu animieren.  

 ![Objekt- und Zeitachsenbereich im Animationsmodus](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")  

|||  
|-|-|  
|![](../designers/media/b1-1.png "B1_1")|**Objektansicht** Zeigt die visuelle Struktur eines Dokuments an. Sie können einen Drilldown zu verschiedenen Detailebenen durchführen. Sie können auch zum Organisieren von Objekten auf der Zeichenfläche weitere Ebenen hinzufügen. Auf diese Weise können Sie sie sperren und als Gruppe ausblenden.|  
|![](../designers/media/b1-2.png "B1_2")|**Anzeige für Aufzeichnungsmodus** Zeigt an, wenn Sie Eigenschaftenänderungen in einer Zeitachse aufzeichnen.|  
|![](../designers/media/b1-3.png "B1_3")|**Storyboardauswahl** Zeigt eine Liste der von Ihnen erstellten Storyboards an.|  
|![](../designers/media/b1-4.png "B1_4")|**Storyboard schließen** Schließt das aktuelle Storyboard.|  
|![](../designers/media/b1-5.png "B1_5")|**Storyboard-Optionen** Erstellen, Kopieren, Umkehren, Löschen, Umbenennen oder Schließen eines Storyboards.|  
|![](../designers/media/b1-6.png "B1_6")|**Wiedergabesteuerelemente** Navigieren durch die Zeitachse. Sie können die Position auch ziehen, um auf der Zeitachse zu navigieren oder *Scrubbing* auszuführen.|  
|![](../designers/media/b1-7.png "B1_7")|**Bereich zurücksetzen auf** Setzt die Objektansicht wieder zurück zum vorherigen Stammobjekt oder Bereich. Dies ist nur beim Ändern von Stilen oder Vorlagen möglich.|  
|![](../designers/media/b1-8.png "B1_8")|**Keyframe aufzeichnen** Zeichnet einen Snapshot der Eigenschaften des ausgewählten Objekts zum aktuellen Zeitpunkt auf.|  
|![](../designers/media/b1-9.png "B1_9")|**Andockoptionen** Legt Andock-Zeitachse, Andockauflösung fest und deaktiviert das Andocken der Zeitachse.|  
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Einblenden/Ausblenden**, **Sperren/Entsperren** Zeigt die Sichtbarkeits- und Sperroptionen für die Objektansicht oder blendet sie aus.|  
|![](../designers/media/b1-11.png "B1_11")|**Position auf der Zeitachse** zeigt die aktuelle Zeit in Millisekunden an. Wenn Sie zu einem bestimmten Zeitpunkt springen möchten, können Sie auch direkt einen Zeitwert in dieses Feld eingeben. Die Präzision ist von der unter **Andockoptionen** festgelegten Auflösung zum Andocken abhängig.|  
|![](../designers/media/b1-12.png "B1_12")|**Position** Zeigt den Zeitpunkt der Animation an. Sie können die Position über die Zeitachse ziehen, um eine Vorschau der Animation anzuzeigen.|  
|![](../designers/media/b1-13.png "B1_13")|**Für Zeitachsen festgelegte Keyframes** Ändert den Wert einer Eigenschaftsänderung zu einem bestimmten Zeitpunkt.|  
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Änderungsreihenfolge von Objekten** Legt die Anzeigereihenfolge von Objekten fest. Klicken Sie auf diese Schaltfläche, um Objekte in der Strukturansicht gemäß der Z-Reihenfolge (von vorne nach hinten) oder gemäß der Markupreihenfolge (entspricht der Reihenfolge in der **XAML**-Ansicht) anzuordnen.|  
|![](../designers/media/b1-15.png "B1_15")|**Zeitachsenzoom** Legt die Zoomauflösung der Zeitachse fest. Durch Vergrößern können Sie eine detailliertere Animation bearbeiten, während Sie beim Verkleinern eine Übersicht der Ereignisse über einen längeren Zeitraum hinweg anzeigen können. Wenn Sie beim Vergrößern kein Keyframe zum gewünschten Zeitpunkt festlegen können, stellen Sie sicher, dass die Auflösung zum Andocken hoch genug eingestellt ist.|  
|![Legende 16](../designers/media/b5-label-16.png "b5_label_16")|**Zeitachsen-Erfassungsbereich** Zeigt die Zeitachse an und ermöglicht Ihnen das Verschieben der Keyframes durch Ziehen oder Verwenden der Kontextmenüs.|  

##  <a name="Properties"></a>Überblick über den Bereich Eigenschaften  
 Verwenden Sie diesen Bereich, um die Eigenschaften eines Objekts anzuzeigen und zu ändern. Sie können sie auch direkt auf der Zeichenfläche festlegen. Wenn Sie dies tun, werden die Änderungen im Bereich **Eigenschaften** angezeigt.  

 ![Bereich „Eigenschaften“](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")  

 **Kategorien** Erweitern und Reduzieren der Kategorien von Eigenschaften. Klicken Sie auf **Erweitern** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") und **Reduzieren** ![Reduzieren](../designers/media/b5-collapse-button.png "Schaltfläche_Reduzieren"), um Kategoriedetails anzuzeigen oder auszublenden.  


|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **Name und Typ** Zeigt das Symbol, den Namen und den Typ des ausgewählten Objekts an.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **Anordnen nach** Ordnet Eigenschaften alphabetisch nach Namen, Quelle oder Kategorie an.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **Pinseleigenschaften** Legt die visuellen Eigenschaften für Pinselarten (Füllung, Strich und Vordergrund) fest.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **Farb-Editor** Wird für Volltonfarben- und Farbverlaufspinsel verwendet.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **Farbauswahl** Wählt eine Farbe aus.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **Farbchips** Zeigt die Ausgangsfarbe, die aktuelle Farbe und die letzte Farbe an.                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **Formatpipetten** Verwendet die Farbe eines Elements auf dem Bildschirm. Die **Verlaufspipette** ist verfügbar, wenn der **Pinsel mit Volltonfarbe** ausgewählt ist. Die **Verlaufspipette** ist verfügbar, wenn der **Farbverlaufspinsel** ausgewählt ist. |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **Eigenschaften und Ereignisse** Legt Eigenschaften oder Ereignisse für ein ausgewähltes Element fest.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **Suchfeld** Sucht nach Eigenschaften. Filtert die Eigenschaften, die angezeigt werden, durch die Eingabe in das Feld **Suche**.                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **Pinsel-Editor-Registerkarten** Zum Auswählen eines Pinsel-Editors. Sie können **Keine Pinsel**, **Mit Volltonfarbe**, **Farbverlaufspinsel**, **Kacheleffekt** und/oder **Pinselressource** auswählen.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **Farbressourcen** Wendet genau dieselbe Farbe auf verschiedene Eigenschaften an. Die Registerkarte **Farbressourcen** enthält **Lokale Ressourcen** und **Systemressourcen**.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **RGB-Farbspektrum** Sie können die Farbe ändern, indem Sie die Werte für **R**-, **G**- oder **B**-Zahlen-Editoren (Rot, Grün, Blau) anpassen.                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **Alphakanal** Ändern Sie den Alphawert, indem Sie den Zahleneditor neben **A** verwenden.                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **Farbe in Ressource konvertieren** Konvertiert die ausgewählte Farbe in eine Farbressource. Farbressourcen sind verfügbar, wenn Sie auf die Farbressourcenregisterkarte klicken.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **Farbtonwert** Zeigt den hexadezimalen Wert der angezeigten Farbe an.                                                                                 |
|                     ![Legende 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **Schieberegler für Farbverlauf** Erscheint nur, wenn ein Farbverlaufspinsel ausgewählt ist.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **Erweiterte Eigenschaften einblenden** Zeigt Kategorien von Eigenschaften an, die weniger häufig verwendet werden.                                                                      |

 **Sehen Sie sich ein kurzes Video (in englischer Sprache) an:** ![Konfigurieren installierter Funktionen ](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Bereich „Eigenschaften“](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).  

## <a name="see-also"></a>Siehe auch  
 [Einfügen von Steuerelementen und Ändern des Verhaltens](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)   
 [Animieren von Objekten](../designers/animate-objects-in-xaml-designer.md)   
 [Zeichnen von Formen und Pfaden](../designers/draw-shapes-and-paths.md)   
 [Designing XAML in Visual Studio and Blend for Visual Studio (Entwerfen von XAML-Code in Visual Studio und Blend für Visual Studio)](../designers/designing-xaml-in-visual-studio.md)



