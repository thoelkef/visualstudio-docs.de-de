---
title: Bilder und Symbole für Visual Studio | Microsoft-Dokumentation
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a49445445388a6db0e6dae9c09b50137c04c4ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954123"
---
# <a name="images-and-icons-for-visual-studio"></a>Bilder und Symbole für Visual Studio
##  <a name="BKMK_ImageUseInVisualStudio"></a> Image-Verwendung in Visual Studio  
 Berücksichtigen Sie vor dem Erstellen von Grafiken, Erstellung Verwendung von mehr als 1.000 Bildern in der [Visual Studio-Bildbibliothek](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Typen von Bildern  
  
-   **Symbole**. Kleine Bilder, die in Befehlen, Hierarchien, Vorlagen und So weiter angezeigt werden. Die Standardgröße-Symbol in Visual Studio verwendet, ist eine 16 x 16-PNG-Datei. Symbole, die der Image-Dienst automatisch erzeugten generieren, das XAML-Format für die HDPI-Unterstützung.  
  
     **HINWEIS:** Während der Images im Menüsystem verwendet werden, sollten Sie nicht, ein Symbol für jeden Befehl erstellen. Wenden Sie sich an [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) um festzustellen, ob der Befehl auf ein Symbol erhalten soll.  
  
-   **Miniaturansichten.** Bilder, die in den Vorschaubereich des ein Dialogfeld an, wie das Dialogfeld "Neues Projekt" verwendet werden.  
  
-   **Dialogfeld-Images.** Bilder, die in Dialogfeldern oder Assistenten, die als beschreibender Grafiken oder Nachricht Indikatoren angezeigt werden. Verwenden Sie nur selten und nur bei Bedarf ein schwieriges Konzept veranschaulichen oder erhalten die Aufmerksamkeit des Benutzers (Warnung).  
  
-   **Animierte Bilder.** Statusanzeigen, Statusleisten und Dialogfelder des Vorgangs verwendet.  
  
-   **Cursor.** Wird verwendet, um anzugeben, ob ein Vorgang zulässig ist, mit der Maus, in dem ein Objekt gelöscht werden kann und so weiter.  
  
##  <a name="BKMK_IconDesign"></a> Symbol entwerfen  
  
### <a name="overview"></a>Übersicht  
 Visual Studio verwendet moderne Symbole bereinigen Geometrie und eine 50/50 Balance zwischen positiv/negativ (hellen/dunklen), und direktere, verständliche Metaphern verwenden. Symbol für wichtige Design Punkte stehen im Mittelpunkt Klarheit, Vereinfachung und den Kontextinformationen.  
  
- **Klarheit:** die Core-Metapher, die ein Symbol den Sinn und wahren erhalten konzentrieren.  
  
- **Vereinfachung:** reduzieren Sie das Symbol auf seine Bedeutung Core – mit nur die erforderlichen Elemente und schnörkellos können Sie das Design auf.  
  
- **Kontext:** sollten Sie alle Aspekte der Symbole Rolle während der Entwicklung Konzept der entscheidend ist, bei der Entscheidung, welche Elemente auf das Symbol "Core Metapher bilden.  
  
  Mit Symbolen gibt es diverse Punkte beim Entwerfen, zu vermeiden:  
  
- Verwenden Sie keine Symbole, die UI-Elemente, außer bei Bedarf angeben. Wählen Sie einen eher abstrakte oder symbolischen Ansatz, wenn das Benutzeroberflächenelement weder allgemeine, offensichtlich noch eindeutig ist.  
  
- Nicht zu viele gemeinsame Elemente wie Dokumenten, Ordner, Pfeile und das Lupensymbol aus. Verwenden Sie solche Elemente nur dann, wenn für das Symbol "Bedeutung. Beispielsweise sollte das Lupensymbol nach rechts zeigenden angeben nur suchen, durchsuchen und ermitteln.  
  
- Obwohl einige Symbol für veraltet-Elemente, die Verwendung der Sicht beizubehalten, erstellen Sie keine neue Symbole mit Perspektive, wenn das Element verfügt nicht über die Klarheit, ohne ihn.  
  
- Nicht, die für Desktopmonitore zu viele Informationen in ein Symbol. Ein einfaches Image, das leicht erkannt und als erkennbar Symbol gelernt werden kann, ist viel nützlicher als ein Bild zu komplex. Ein Symbol kann nicht die ganze Geschichte zu erzählen.  
  
### <a name="icon-creation"></a>Symbol für Erstellung  
  
#### <a name="concept-development"></a>Concept-Entwicklung  
 Visual Studio bietet eine Vielzahl von Symboltypen in der Benutzeroberfläche aus. Überlegen Sie während der Entwicklung der Symboltyp. Verwenden Sie nicht unklar oder ungewöhnlich, dass UI-Objekte für die Symbol-Elemente. Sich für die symbolische in diesen Fällen, z. B. entscheiden Sie, mit dem Smart Tag-Symbol. Beachten Sie, dass die Bedeutung des abstrakten Tags auf der linken Seite noch deutlicher als die vage und UI-basierten Version auf der rechten Seite ist:  
  
|||  
|-|-|  
|**Richtige Verwendung von symbolischen Bilder**|**Falsche Verwendung von symbolischen Bilder**|  
|![Richtige Smarttag-Symbol](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Symbol für falsches Smarttag](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|  
  
 Es gibt Fälle, in denen standard, leicht zu erkennende UI-Elemente für Symbole gut funktionieren. Fügen Sie, dass das Fenster ein solches Beispiel hinzu:  
  
|||  
|-|-|  
|**Richtige UI-Element in einem Symbol**|**Falsche UI-Element in einem Symbol**|  
|![Richtige Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Falsche Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|  
  
 Verwenden Sie nicht, wird ein Dokument als Basiselement festgelegt, es sei denn, es wichtig, auf das Symbol "Bedeutung ist. Ohne das Dokument ist ein Element auf Dokument hinzufügen (siehe unten) die Bedeutung verloren geht, während der Aktualisierung das Dokumentelement nicht erforderlich, für die Kommunikation von Bedeutung ist.  
  
|||  
|-|-|  
|**Richtige Verwendung von Dokumentsymbol**|**Falsche Verwendung der Dokument-Symbol**|  
|![Richtige Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Falsches Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|  
  
 Das Konzept der "anzeigen" muss durch das Symbol dargestellt werden, die am besten geeignet ist, was angezeigt wird, z. B. wie bei den im Beispiel alle Dateien anzeigen. Eine Metapher Fokus kann verwendet werden, an das Konzept der "View", falls erforderlich, z. B. mit dem Beispiel für die Ressourcenansicht nutzen zu können.  
  
|||  
|-|-|  
|**"Show"**|**"View"**|  
|![Symbol "anzeigen"](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Symbol für die](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|  
  
 Die nach rechts zeigenden vergrößern klicken stellen nur suchen soll, suchen und durchsuchen. Die Variante nach links, mit dem Pluszeichen (+) oder Minuszeichen (-) sollten darstellen nur vergrößern / verkleinern.  
  
|||  
|-|-|  
|**"Search"**|**"Zoom"**|  
|![Symbol "Suche"](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Zoom icon](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|  
  
 Verwenden Sie in der Struktur nicht sowohl auf das Symbol "Ordner" als auch auf einen Modifizierer. Sofern verfügbar, verwenden Sie nur den Modifizierer.  
  
|||  
|-|-|  
|**Symbole der richtigen Struktur anzeigen**|**Symbole für falsche Struktur anzeigen**|  
|![Richtiges strukturansichtsymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![richtiges strukturansichtsymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Falsches strukturansichtsymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![falsches strukturansichtsymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_ TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Style-details  
  
#### <a name="layout"></a>Layout  
 Stapeln von Elementen wie für standard 16 x 16-Symbole dargestellt:  
  
 ![Layoutstack für 16 x 16-Symbole](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Layoutstack für 16x16-Symbole
  
 Status-Benachrichtigung-Elemente sind besser als eigenständige Symbole verwendet. Kontexte sind vorhanden, jedoch in denen eine Benachrichtigung des Basiselements, z. B. mit dem Task abgeschlossen Symbol gestapelt werden sollten:  
  
 ![Eigenständige Benachrichtigungen in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Eigenständige-Benachrichtigungssymbole
  
 ![Symbol für abgeschlossene Aufgabe](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Symbol für abgeschlossene Aufgabe
  
 Projektsymbole sind in der Regel die ICO-Dateien, die mehrere Größen enthalten. Die meisten 16 x 16-Symbole werden dieselben Elemente enthalten. Weitere Informationen sowie den Projekttyp ggf. über die 32 x 32-Versionen verfügen.  
  
 ![Symbole in Visual Studio Project](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Windows-Steuerelementbibliothek-Projekt VB-Symbole, 16 x 16 und 32 x 32 
  
 Ein Symbol in der pixelframes im Mittelpunkt. Wenn dies nicht möglich ist, richten Sie das Symbol an den Anfang bzw. rechts des Frames.  
  
 ![Innerhalb des pixelframes zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Innerhalb des Pixelframes zentriertes Symbol
  
 ![Symbol "ausgerichtet, die obere rechte Ecke des pixelframes](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Symbol oben ausgerichtet rechts von dem Frame
  
 ![Ausgerichtetes und zentriertes Symbol pixelframe oben ausgerichtet](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Ausgerichtetes und zentriertes Symbol Ausrichtung am oberen Rand des Frames
  
 Um die ideale Ausrichtung und Balance zu erzielen, vermeiden Sie sitzt das Symbol "-Basiselement mit Aktion aus. Ort des Symbols im oberen Bereich des grundlegenden Elements links. Wenn Sie ein weiteres Element hinzufügen möchten, sollten Sie die Ausrichtung und den Saldo des Symbols.  
  
|||  
|-|-|  
|**Richtige Ausrichtung und Lastenausgleich**|**Falsche Ausrichtung und Lastenausgleich**|  
|![Korrigieren Sie symbolverteilung und-Ausrichtung](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Falsche symbolverteilung und-Ausrichtung](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|  
  
 Stellen Sie sicher Größe Parität für Symbole, die Elemente in Gruppen verwendet werden. Beachten Sie, dass in die falschen Kopplung der Kreis und Pfeil groß sind, und stimmen nicht überein.  
  
|||  
|-|-|  
|**Richtige Größe Parität**|**Falsche Größe Parität**|  
|![Korrigieren Sie Symbolgröße und-Parität](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Falsche Symbolgröße und-Parität](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|  
  
 Verwenden Sie konsistente Zeile und visuelle Gewichtung. Werten Sie das Symbol, das Sie erstellen mit anderen Symbolen wie verglichen werden soll, mithilfe eines Vergleichs von Seite-an-Seite. Verwenden Sie niemals den gesamten Rahmen von 16 x 16, verwenden Sie 15 x 15 oder kleiner. Das Verhältnis der negativ, positiv (dunkel-hell) sollte 50/50.  
  
|||  
|-|-|  
|**Richtig negativ, positiv Verhältnis**|**Falsch negativ, positiv Verhältnis**|  
|![Korrigieren Sie optische Gewichtung für Symbole &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Korrigieren Sie optische Gewichtung für Symbole &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Korrigieren Sie optische Gewichtung für Symbole &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Falsche optische Gewichtung für Symbole](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|  
  
 Verwenden Sie einfache, vergleichbarer Formen und Komplementärfarbe Winkel, um Ihre Elemente zu erstellen, ohne Einbußen bei der Integrität des Elements. Verwenden Sie nach Möglichkeit 45° oder um 90°-Winkel.  
  
 ![Korrigieren Sie symbolwinkel](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Perspektive  
 Lassen Sie das Symbol, klar und verständlich. Verwenden Sie die Perspektive und einer Lichtquelle nur bei Bedarf. Obwohl Perspektive auf das Symbol für Elemente verwenden vermieden werden sollte, sind einige Elemente nicht erkennbar, ohne ihn. In solchen Fällen kommuniziert Standpunkt stilisierte Gründen der Übersichtlichkeit des Elements ab.  
  
 ![3-Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3-Punkt-Perspektive
  
 ![1-Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1-Punkt-Perspektive
  
 Die meisten Elemente sollten konfrontiert oder schräg nach rechts:  
  
 ![Symbole rechts angeschrägt](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")  
  
 Verwenden Sie Lichtquellen, nur beim Hinzufügen der erforderlichen Klarheit auf ein Objekt.  
  
|||  
|-|-|  
|**Richtige Lichtquelle**|**Falsche Lichtquelle**|  
|![Korrigieren von Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Falsche Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|  
  
 Verwenden Sie sind nur für die Lesbarkeit zu verbessern oder die Metapher Verbesserung der Kommunikation. Das Verhältnis der Negative positiv (Hell-Dunkel) sollte 50/50.  
  
|||  
|-|-|  
|**Richtige Verwendung von Konturen**|**Falsche Verwendung von Konturen**|  
|![Korrigieren von Konturen](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Falsche Konturen](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Symbol "-Typen  
 **Shell- und Befehlsleiste** Symbole bestehen aus nicht mehr als drei der folgenden Elemente: eine einzige Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Beispiele von Shell- und befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Beispiele von Shell- und befehlsleistensymbole
  
 **Symbolleiste für Fenster-Befehl** Symbole bestehen aus nicht mehr als drei der folgenden Elemente: eine einzige Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Beispiele für Toolfenster Befehlsleisten Symbole](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Beispiele für die Tool-Fenster/befehlsleistensymbole
  
 **Struktur anzeigen Disambiguator** Symbole bestehen aus nicht mehr als drei der folgenden Elemente: eine einzige Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Beispiele für die Struktur anzeigen Disambiguator Symbole](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Beispiele für die Struktur anzeigen Disambiguator-Symbole
  
 **Zustandsbasierte Wert Taxonomie** Symbole enthalten sind, in der folgenden Zustände: aktiv, deaktiviert aktive und inaktive deaktiviert.  
  
 ![Beispiele für die Symbole für statusbasierte Taxonomie](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Beispiele für die Symbole für statusbasierte Taxonomie
  
 **IntelliSense** Symbole bestehen aus nicht mehr als drei der folgenden Elemente: eine einzige Basis, einen Modifizierer und einen Status.  
  
 ![Beispiele für die IntelliSense-Symbole](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Beispiele für die IntelliSense-Symbole
  
 **Kleine (16 x 16)-Projekt** Symbole sollten nicht mehr als zwei Elemente verfügen: eine einzige Basis und einen Modifizierer.  
  
 ![Beispiele für kleine (16 x 16)-Projekt Symbole](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![Projektsymbol, 16 x 16 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![Projektsymbol, 16 x 16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Beispiele für kleine (16 x 16)-Projektsymbole
  
 **Groß (32 x 32)-Projekt** Symbole nicht mehr als vier aus den folgenden Elementen bestehen: eine einzige Basis, ein bis zwei Modifizierer und eine Sprache, die Überlagerung.  
  
 ![Beispiele für große (32 x 32)-Projekt Symbole](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Beispiele für große (32 x 32) Projektsymbole
  
### <a name="production-details"></a>Produktionsdetails  
 Alle neuen Elemente der Benutzeroberfläche mit Windows Presentation Foundation (WPF) erstellt werden soll, und alle neuen Symbole für WPF muss im 32-Bit-PNG-Format. Die 24-Bit-PNG-Datei ist ein legacy-Format, das Transparenz wird nicht unterstützt und sollte daher nicht für Symbole.  
  
 Speichern Sie die Lösung mit 96 DPI.  
  
#### <a name="file-types"></a>Dateitypen  
  
-   **32-Bit-PNG:** das bevorzugte Format für Symbole. Eine verlustfreie Komprimierung Datei Datenformat, das ein einzelnes Rasterbild (Pixel) speichern kann. 32-Bit-PNG-Dateien unterstützen Alphakanaltransparenz Gammakorrektur und Zeilensprung verwenden.  
  
-   **32-Bit-BMP:** für nicht-WPF-Steuerelemente. Auch als XP oder hoher Farbtiefe ist 32-Bit-BMP eine RGB/ein Abbildformat, ein True-Color-Image mit einer Alphakanaltransparenz. Der alpha-Kanal ist eine Ebene der Transparenz festgelegt, die in Adobe Photoshop überein, die innerhalb der Bitmap als eine zusätzliche (4) klicken Sie dann gespeichert wird Farbkanal. Erhält ein schwarzer Hintergrund wird während der Produktion von Vorlagen für alle 32-Bit-BMP-Dateien zu einer schnellen visuellen Hinweis auf die Farbtiefe hinzugefügt. Diese schwarze Hintergrund darstellt den Bereich, das Sie in der Benutzeroberfläche maskiert werden.  
  
-   **32-Bit-ICO-:** Projektsymbole "und" Element hinzufügen. Alle ICO-Dateien sind "true" 32-Bit-Farbe Alphakanaltransparenz (RGB/A). Da ICO-Dateien mehrere Größe und Farbe Tiefen speichern können, sind die Vista-Symbolen häufig eine ICO-Format mit 16 x 16, 32 x 32, 256 x 256 Bildgrößen und 48 x 48. Um ordnungsgemäß in Windows Explorer angezeigt werden soll, ICO-Dateien müssen gespeichert, die Tiefen der 24-Bit- und 8-Bit-Farbe für jede Größe auswählen werden.  
  
-   **XAML:** Entwurfsoberflächen und Windows-Adorner. XAML-Symbole sind vektorbasiertes Bild-Dateien, die skalieren, drehen, Archivierung und Transparenz zu unterstützen. Sie sind zurzeit nicht in Visual Studio häufig, jedoch werden immer populärer aufgrund ihrer Flexibilität.  
  
-   **SVG**  
  
-   **24-Bit-BMP:** für die Visual Studio-Befehlsleiste. Ein Bildformat der RGB-Farben "true" ist 24-Bit-BMP ein Symbol-Konvention, die eine Ebene der Transparenz erstellt mithilfe der Magenta (R = 255, G = 0, B = 255) als farbenschlüssel für eine Ebene Hit Transparenz. In einem 24-Bit-BMP werden alle Magenta Flächen mit die Hintergrundfarbe angezeigt.  
  
-   **24-Bit-GIF:** für die Visual Studio-Befehlsleiste. Ein "true"-Color RGB-Bildformat, das Transparenz unterstützt. GIF-Dateien werden häufig in Assistenten Bildmaterial und GIF-Animationen verwendet.  
  
### <a name="icon-construction"></a>Symbol für Erstellung  
 Die kleinste Größe der Symbole in Visual Studio ist 16 x 16. Das größte ist gemeinsam verwenden 32 x 32. Bedenken Sie nicht auf den gesamten Rahmen von 16 x 16, 24 x 24 oder 32 x 32 auffüllen, wenn Sie ein Symbol zu entwerfen. Symbol für lesbar, einheitliche Konstruktion ist wesentlich für Benutzer. Entsprechen Sie die folgenden Punkte beim Erstellen von Symbolen.  
  
- Symbole sollten klar verständlich und konsistent sein.  
  
- Es ist besser, die Status-Benachrichtigung-Elemente als einzelne Symbole zu verwenden und nicht auf die sie über ein Symbol Basiselement stack. In bestimmten Kontexten möglicherweise die Benutzeroberfläche das Status-Element mit einem Basiselement kombiniert werden.  
  
- Projektsymbole sind in der Regel die ICO-Dateien, die verschiedenen Größen enthalten. Nur die 16 x 16, 24 x 24 und 32 x 32-Symbole werden aktualisiert. Die meisten 16 x 16 und 24 x 24-Symbole werden dieselben Elemente enthalten. Die 32 x 32 Symbole enthalten weitere Informationen sowie die Sprache Projekttyp, falls zutreffend.  
  
- Für 32 x 32-Symbole haben die grundlegenden Elemente in der Regel eine 2-Pixel-Linienstärke. Eine 1 oder 2-Pixel-Linienstärke kann Details Elemente verwendet werden. Verwenden Sie Ihrem Urteilsvermögen, um zu bestimmen, die besser geeignet ist.  
  
- Verfügen Sie über mindestens einen 1-Pixel-der Abstand zwischen Elementen für 16 x 16 und 24 x 24 Symbole. Verwenden Sie für 32 x 32-Symbole 2-Pixel-Abstand zwischen Elementen sowie zwischen dem Modifizierer und das Basiselement.  
  
  ![Element Abstand für Symbole die Größe 16 x 16, 24 x 24 und 32 x 32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Elementabstand für Symbole die Größe 16 x 16, 24 x 24 und 32 x 32
  
#### <a name="color-and-accessibility"></a>Farbe und Barrierefreiheit  
 Visual Studio-Compliance-Richtlinien erfordern, dass alle Symbole in das Produkt den Anforderungen zur Barrierefreiheit für Farbe und Kontrast übergeben. Dies erfolgt über das Symbol Inversion und beim Entwerfen, sollten Sie bedenken, dass sie programmgesteuert innerhalb des Produkts umgekehrt werden soll.  
  
 Weitere Informationen zur Verwendung von Farbe in Visual Studio-Symbolen finden Sie unter [mithilfe von Farbe in Bildern](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="BKMK_UsingColorInImages"></a> Mithilfe von Farbe in Bildern  
  
### <a name="overview"></a>Übersicht  
 Symbole in Visual Studio sind in erster Linie monochrome. Farbe ist reserviert, um spezifische Informationen zu vermitteln und niemals für die Dekoration. Farbe wird verwendet:  
  
-   Um eine Aktion anzugeben.  
  
-   Benachrichtigung des Benutzers auf eine Benachrichtigung zum status  
  
-   Festlegen von Sprache-Zuordnung  
  
-   Um Elemente in IntelliSense zu unterscheiden.  
  
### <a name="accessibility"></a>Zugriff  
 Visual Studio-Compliance-Richtlinien erfordern, dass alle Symbole in der Product-Durchlauf der Anforderungen zur Barrierefreiheit für Farbe und Kontrast überprüft. Farben in der visuellen Sprache Palette getestet wurden und die folgenden Voraussetzungen erfüllen.  
  
#### <a name="color-inversion-for-dark-themes"></a>Farbumkehrung für dunkle Designs  
 Um Symbole, die mit der richtigen Kontrastverhältnis im dunklen Design von Visual Studio angezeigt werden können, ist eine Umkehrung programmgesteuert angewendet. Die Farben in dieser Anleitung wurden teilweise ausgewählt, damit sie ordnungsgemäß umkehren. Beschränken Ihre Verwendung von Farben zu dieser Palette, oder Sie erhalten zu unvorhersehbaren Ergebnissen auf, wenn die Umkehrung angewendet wird.  
  
 ![Beispiele von Symbolen, die deren Farben umgekehrt wurden](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Beispiele von Symbolen, die deren Farben umgekehrt wurden
  
### <a name="base-palette"></a>Basispalette  
 Alle standard-Symbole enthalten drei grundlegende Farben. Symbole enthalten keine Farbverläufe oder Schlagschatten, die mit einem oder zwei Ausnahmen für 3D-Tool-Symbole.  
  
|Verwendung|name|Wert (Design "hell")|Farbmuster|Beispiel|  
|-----------|----------|---------------------------|------------|-------------|  
|Hintergrund/dunklen|VS BG|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Beispiel für basispalette](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|  
|Vordergrund-/Licht|VS FG|F0EFF1 / 240,239,241|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Gliederung|Visual Studio heraus|F6F6F6 / 246,246,246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Zusätzlich zu den Grundfarben kann jedes Symbol eine zusätzliche Farbe aus der erweiterten Palette enthalten.  
  
### <a name="extended-palette"></a>Erweiterte palette  
  
#### <a name="action-modifiers"></a>Aktionsmodifizierer  
 Die vier Farben unten zeigen die Aktionen, die erforderliche Aktionsmodifizierer:  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Positiv|Grün für Visual Studio-Aktion|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Negativ|Rot für Visual Studio-Aktion|A1260D / 161,38,13|![Swatch A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Neutral|Visual Studio Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|/ Neu erstellen|Visual Studio Aktion Orange|C27D1A / 194,156,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Beispiele  
 Grün wird verwendet, für positive Aktionsmodifizierer wie "Hinzufügen", "Ausführen", "Wiedergabe" und "Überprüfen".  
  
|||||  
|-|-|-|-|  
|![Run icon](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Run|![Execute query icon](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />Abfrage ausführen|![Symbol für alle Schritte wiedergeben](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />Alle Schritte wiedergeben|![Steuerelementsymbol "hinzufügen"](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />Steuerelement hinzufügen|  
  
 Rot wird für negative Aktionsmodifizierer wie ","Stop,"Delete" verwendet "Abbrechen" und "Schließen".  
  
|||||  
|-|-|-|-|  
|![Delete relationship icon](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />Beziehung löschen|![Spaltensymbol "löschen"](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />Spalte löschen|![Stop-Abfragesymbol](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />Abfrage beenden|![Symbol "Verbindung offline"](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />Offline-Verbindung|  
  
 Blau wird auf neutral Aktion angewendet, dargestellt als Pfeile, wie ","Weiter","Zurück", öffnen Sie" Modifizierer am häufigsten "Import" und "Exportieren".  
  
|||||  
|-|-|-|-|  
|![Wechseln Sie zu dem Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />Wechseln Sie zum Feld|![Überprüfen Sie in einem Batch verarbeitet&#45;im Symbol](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />Im Batch Einchecken|![Symbol "Adresse-Editor"](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />Adress-Editor|![Symbol "Zuordnung-Editor"](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />Zuordnungs-Editor|  
  
 Dunkle "Gold" wird in erster Linie für den "Neu"-Modifizierer verwendet.  
  
|||||  
|-|-|-|-|  
|![Symbol "Neues Projekt"](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />Neues Projekt|![Erstellen Sie neue graphsymbol](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />Erstellen eines neuen Diagramms|![Symbol "neu Unit Test"](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />Neuen Komponententests|![Neue Liste Symbol "Element"](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />Neues Listenelement|  
  
#### <a name="special-cases"></a>Sonderfälle  
 In besonderen Fällen möglicherweise ein farbigen Aktion Modifizierer unabhängig als eigenständige Symbol verwendet werden. Die Farbe für das Symbol gibt die Aktionen, denen das Symbol zugeordnet ist. Diese Verwendung ist beschränkt auf eine kleine Teilmenge von Symbolen, einschließlich:  
  
||||||  
|-|-|-|-|-|  
|![Run icon](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Run|![Symbol "Beenden"](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Anhalten|![Symbol "löschen"](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />Löschen|![Symbol "Speichern"](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />Speichern|![Navigate back icon](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />Rückwärts navigieren|  
  
### <a name="code-hierarchy-palette"></a>Befehlspalette der Code-Hierarchie  
  
#### <a name="folder"></a>Ordner  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|Beispiel|  
|-----------|----------|--------------------------|------------|-------------|  
|Ordner|Ordner|DCB67A / 220,182,122|![Swatch DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Symbol "Ordner Farbe"](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio-Sprachen  
 Jede der allgemeinen Sprachen oder Plattformen in Visual Studio verfügbaren verfügt über zugeordnete Farbe. Diese Farben werden verwendet, auf das Symbol "Basis" oder auf der Language-Modifizierer, die in der Ecke der zusammengesetzten Symbole angezeigt werden.  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML-WPF-Blau|0095D 7 / 0,149,215|![Swatch 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP-Lila|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS Grün (VS Aktion Grün)|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|CSS-Rot|BD1E2D / 189,30,45|![Swatch BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS Lila|672878 / 103,40,120|![Swatch 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS Orange|F16421 / 241,100,33|![Muster F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB Blau (Visual Studio-Aktion-Blau)|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|TS Orange|E04C06 / 224,76,6|![Swatch E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|PY Grün|879636 / 135,150,54|![Swatch 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Beispiele für Symbole mit Language-Modifizierer  
  
|||||||  
|-|-|-|-|-|-|  
|![Visual Basic-Symbol](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![C&#35; icon](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C&#43;&#43; icon](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![F&#35; icon](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![Symbol "JavaScript"](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Python icon](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|  
|![HTML icon](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF icon](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP-Symbol](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Symbol "CSS"](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript icon](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 IntelliSense-Symbole verwenden, eine exklusive Farbpalette. Diese Farben verwendet, um Benutzer schnell zwischen den verschiedenen Elementen in der Liste der IntelliSense-Popupfenster unterscheiden.  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Event-Klasse|Visual Studio Aktion Orange|C27D1A / 194,125,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Erweiterungsmethode "," Methode ","-Modul, Delegat|Visual Studio Aktion Lila|652D 90 / 101,45,144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Feld "," Enum-Element ","-Makro "," Struktur "," Wert Union-Typ, Operator, Schnittstelle|Visual Studio Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Object|Grün für Visual Studio-Aktion|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Konstanten, die Typdefinition Ausnahme, Enum-Element, Map, Map-Element, Namespace, Vorlage|Hintergrund (VS BG)|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Beispiele für die IntelliSense-Symbole  
  
||||||  
|-|-|-|-|-|  
|![Symbol für IntelliSense-Klasse](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />Klasse|![Symbol für IntelliSense privates Ereignis](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />Private-Ereignis|![Symbol für IntelliSense-Delegat](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />delegate|![Symbol "Friend" der IntelliSense-Methode](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Methode Friend|![Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />Feld|  
|![IntelliSense geschützt Enum-Symbol "Element"](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />Geschützte Enumeration-Element|![Symbol für IntelliSense-Objekt](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Object|![Symbol für IntelliSense-Vorlage](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />Vorlage|![Symbol "Verknüpfung" der IntelliSense-Ausnahme](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />Ausnahme-Kontextmenü||  
  
### <a name="notifications"></a>Benachrichtigungen  
 Benachrichtigungen in Visual Studio werden verwendet, um Status anzugeben. Die Benachrichtigung Palette verwendet die folgenden vier Farben angezeigt werden, sowie Schwarz oder weiß Foreground-Optionen, so definieren Sie Benachrichtigungen mit den folgenden Statusebenen an.  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Status: neutral|Benachrichtigung Blau (Visual Studio-Blau)|1BA1E2 / 27,161,226|![Swatch 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Status: positiv|Benachrichtigung Grün (VS Grün)|339933 / 51,153,51|![Swatch 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Status: negative|Benachrichtigung Red (Rot Visual Studio)|E51400 / 229,20,0|![Swatch E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Status: Warnung|Benachrichtigung, Gelb (VS Orange)|FFCC00 / 255,204,0|![Muster FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Füllfarbe|Benachrichtigung Schwarz (Schwarz)|000000 / 0,0,0|![Swatch &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Füllfarbe|Benachrichtigung Whitepaper (Whitepaper)|FFFFFF / 255,255,255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Beispiele für die Symbole für Benachrichtigungen  
  
|||||  
|-|-|-|-|  
|![Symbol "Warnung"](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />Warnung|![Symbol "Warnung"](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Warnung|![Symbol "abgeschlossen"](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />Abgeschlossen|![Symbol "Beenden"](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Anhalten|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 Im Allgemeinen besteht aus Visual Studio Online-Funktionen in einem Browser gehostet. Die Farbe in unterschiedlichen Umgebungen variieren, aber das Format bleibt unverändert.  
  
|Gruppieren|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Hintergrund|TFSO BG|656565/ 101, 101, 101|![Swatch 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Gliederung|TFSO OUT|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Swatch 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Darauf zeigen (Hover)|F12 Blue_Hover|2279BF / 34,121,191|![Swatch 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Deaktiviert|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Muster ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Zeigen Sie Hintergrund|Zeigen Sie bg|D9EBF7 / 217,235,247|![Swatch D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Searchboxpressedbackgroundkey|Gedrückten bg|B2D7F0 / 178,215,240|![Swatch B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Gliederung|VISUAL STUDIO HERAUS|F6F6F6 / 246,246,246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Information|Information|00BCF2 / 0,188,242|![Swatch 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Warnung|Warnung|F28300 / 242,131,0|![Swatch F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Fehler / negativ|Error_Negative|E81123 / 232,17,35|![Swatch E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Starten / Positive|Start_Positive|009E49 / 0,158,73|![Swatch 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Break-Typ|Break-Typ|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Ereignis markieren|Ereignis markieren|A51F00 / 165,31,0|![Muster A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Benutzermarkierung|Benutzermarkierung|F16220 / 241,98,32|![Muster F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Beispiele für Visual Studio Online-Symbole  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Symbol "Team" TFS Online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />Online-Team|![Symbol für TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />Information|![Symbol für TFS-Verlauf](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />Versionsgeschichte|![Symbol für TFS-Branch](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Verzweigung|  
  
|Napa||||  
|----------|-|-|-|  
|![Symbol für Napa-Inhalt](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />Content|![Symbol für Napa Office Mail](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />Office-e-Mails|![Napa SharePoint icon](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Symbol für Napa-Aufgabe Bereich](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />Aufgabenbereich|  
  
|Monaco||||  
|------------|-|-|-|  
|![Symbol für Monaco-Dateien](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />Dateien|![Symbol für Monaco Git](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Symbol für Monaco-suchen](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />Suchen|![Symbol für Monaco-Text](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />Text|  
  
|F12|||  
|---------|-|-|  
|![Symbol für F12-pretty-Code](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />Pretty-Code|![Symbol für F12-Warnung](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Warnung|![Symbol für F12-Emulation](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />Emulieren|