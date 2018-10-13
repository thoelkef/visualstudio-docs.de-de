---
title: Bilder und Symbole für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a818bf9b1975692c220b2be82b2fed7ca97fad13
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255748"
---
# <a name="images-and-icons-for-visual-studio"></a>Bilder und Symbole für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_ImageUseInVisualStudio"></a> Image-Verwendung in Visual Studio  
 Berücksichtigen Sie vor dem Erstellen von Grafiken, Erstellung Verwendung von mehr als 1.000 Bildern in der [Visual Studio-Bildbibliothek](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Typen von Bildern  
  
-   **Symbole**. Kleine Bilder, die in Befehlen, Hierarchien, Vorlagen und So weiter angezeigt werden. Die Standardgröße-Symbol in Visual Studio verwendet, ist eine 16 x 16-PNG-Datei. Symbole, die der Image-Dienst automatisch erzeugten generieren, das XAML-Format für die HDPI-Unterstützung.  
  
     **Hinweis:** während Images im Menüsystem verwendet werden, sollten Sie ein Symbol für jeden Befehl nicht erstellen. Wenden Sie sich an [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) um festzustellen, ob der Befehl auf ein Symbol erhalten soll.  
  
-   **Miniaturansichten.** Bilder, die in den Vorschaubereich des ein Dialogfeld an, wie das Dialogfeld "Neues Projekt" verwendet werden.  
  
-   **Dialogfeld-Images.** Bilder, die in Dialogfeldern oder Assistenten, die als beschreibender Grafiken oder Nachricht Indikatoren angezeigt werden. Verwenden Sie nur selten und nur bei Bedarf ein schwieriges Konzept veranschaulichen oder erhalten die Aufmerksamkeit des Benutzers (Warnung).  
  
-   **Animierte Bilder.** Statusanzeigen, Statusleisten und Dialogfelder des Vorgangs verwendet.  
  
-   **Cursor.** Wird verwendet, um anzugeben, ob ein Vorgang zulässig ist, mit der Maus, in dem ein Objekt gelöscht werden kann und so weiter.  
  
##  <a name="BKMK_IconDesign"></a> Symbol entwerfen  
  
### <a name="overview"></a>Übersicht  
 Visual Studio verwendet moderne Symbole bereinigen Geometrie und eine 50/50 Balance zwischen positiv/negativ (hellen/dunklen), und direktere, verständliche Metaphern verwenden. Symbol für wichtige Design Punkte stehen im Mittelpunkt Klarheit, Vereinfachung und den Kontextinformationen.  
  
-   **Klarheit:** die Core-Metapher, die ein Symbol den Sinn und wahren erhalten konzentrieren.  
  
-   **Vereinfachung:** reduzieren Sie das Symbol auf seine Bedeutung Core – mit nur die erforderlichen Elemente und schnörkellos können Sie das Design auf.  
  
-   **Kontext:** sollten Sie alle Aspekte der Symbole Rolle während der Entwicklung Konzept der entscheidend ist, bei der Entscheidung, welche Elemente auf das Symbol "Core Metapher bilden.  
  
 Mit Symbolen gibt es diverse Punkte beim Entwerfen, zu vermeiden:  
  
-   Verwenden Sie keine Symbole, die UI-Elemente, außer bei Bedarf angeben. Wählen Sie einen eher abstrakte oder symbolischen Ansatz, wenn das Benutzeroberflächenelement weder allgemeine, offensichtlich noch eindeutig ist.  
  
-   Nicht zu viele gemeinsame Elemente wie Dokumenten, Ordner, Pfeile und das Lupensymbol aus. Verwenden Sie solche Elemente nur dann, wenn für das Symbol "Bedeutung. Beispielsweise sollte das Lupensymbol nach rechts zeigenden angeben nur suchen, durchsuchen und ermitteln.  
  
-   Obwohl einige Symbol für veraltet-Elemente, die Verwendung der Sicht beizubehalten, erstellen Sie keine neue Symbole mit Perspektive, wenn das Element verfügt nicht über die Klarheit, ohne ihn.  
  
-   Nicht, die für Desktopmonitore zu viele Informationen in ein Symbol. Ein einfaches Image, das leicht erkannt und als erkennbar Symbol gelernt werden kann, ist viel nützlicher als ein Bild zu komplex. Ein Symbol kann nicht die ganze Geschichte zu erzählen.  
  
### <a name="icon-creation"></a>Symbol für Erstellung  
  
#### <a name="concept-development"></a>Concept-Entwicklung  
 Visual Studio bietet eine Vielzahl von Symboltypen in der Benutzeroberfläche aus. Überlegen Sie während der Entwicklung der Symboltyp. Verwenden Sie nicht unklar oder ungewöhnlich, dass UI-Objekte für die Symbol-Elemente. Sich für die symbolische in diesen Fällen, z. B. entscheiden Sie, mit dem Smart Tag-Symbol. Beachten Sie, dass die Bedeutung des abstrakten Tags auf der linken Seite noch deutlicher als die vage und UI-basierten Version auf der rechten Seite ist:  
  
|||  
|-|-|  
|**Richtige Verwendung von symbolischen Bilder**|**Falsche Verwendung von symbolischen Bilder**|  
|![Richtige Smarttag-Symbol](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404-01_SmartTagCorrect")|![Symbol für falsches Smarttag](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404-02_SmartTagIncorrect")|  
  
 Es gibt Fälle, in denen standard, leicht zu erkennende UI-Elemente für Symbole gut funktionieren. Fügen Sie, dass das Fenster ein solches Beispiel hinzu:  
  
|||  
|-|-|  
|**Richtige UI-Element in einem Symbol**|**Falsche UI-Element in einem Symbol**|  
|![Richtige Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404-03_AddWindowCorrect")|![Falsche Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404-04_AddWindowIncorrect")|  
  
 Verwenden Sie nicht, wird ein Dokument als Basiselement festgelegt, es sei denn, es wichtig, auf das Symbol "Bedeutung ist. Ohne das Dokument ist ein Element auf Dokument hinzufügen (siehe unten) die Bedeutung verloren geht, während der Aktualisierung das Dokumentelement nicht erforderlich, für die Kommunikation von Bedeutung ist.  
  
|||  
|-|-|  
|**Richtige Verwendung von Dokumentsymbol**|**Falsche Verwendung der Dokument-Symbol**|  
|![Richtige Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Falsches Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404-06_DocumentIconIncorrect")|  
  
 Das Konzept der "anzeigen" muss durch das Symbol dargestellt werden, die am besten geeignet ist, was angezeigt wird, z. B. wie bei den im Beispiel alle Dateien anzeigen. Eine Metapher Fokus kann verwendet werden, an das Konzept der "View", falls erforderlich, z. B. mit dem Beispiel für die Ressourcenansicht nutzen zu können.  
  
|||  
|-|-|  
|**"Anzeigen"**|**"View"**|  
|![Symbol "anzeigen"](../../extensibility/ux-guidelines/media/0404-07-show.png "0404-07_Show")|![Symbol für die](../../extensibility/ux-guidelines/media/0404-08-view.png "0404-08_View")|  
  
 Die nach rechts zeigenden vergrößern klicken stellen nur suchen soll, suchen und durchsuchen. Die Variante nach links, mit dem Pluszeichen (+) oder Minuszeichen (-) sollten darstellen nur vergrößern / verkleinern.  
  
|||  
|-|-|  
|**"Search"**|**"Zoom"**|  
|![Symbol "Suche"](../../extensibility/ux-guidelines/media/0404-09-search.png "0404-09_Search")|![Symbol "Zoom"](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404-10_Zoom")|  
  
 Verwenden Sie in der Struktur nicht sowohl auf das Symbol "Ordner" als auch auf einen Modifizierer. Sofern verfügbar, verwenden Sie nur den Modifizierer.  
  
|||  
|-|-|  
|**Symbole der richtigen Struktur anzeigen**|**Symbole für falsche Struktur anzeigen**|  
|![Richtiges strukturansichtsymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![richtiges strukturansichtsymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Falsches strukturansichtsymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![falsches strukturansichtsymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404-14_ TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Style-details  
  
#### <a name="layout"></a>Layout  
 Stapeln von Elementen wie für standard 16 x 16-Symbole dargestellt:  
  
 ![Layoutstack für 16 x 16-Symbole](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404-15_LayoutStack")  
  
 **Layoutstack für 16 x 16-Symbole**  
  
 Status-Benachrichtigung-Elemente sind besser als eigenständige Symbole verwendet. Kontexte sind vorhanden, jedoch in denen eine Benachrichtigung des Basiselements, z. B. mit dem Task abgeschlossen Symbol gestapelt werden sollten:  
  
 ![Eigenständige Benachrichtigungen in Visual Studio](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")  
  
 **Eigenständige-Benachrichtigungssymbole**  
  
 ![Symbol für abgeschlossene Aufgabe](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404-17_TaskComplete")  
  
 **Symbol für abgeschlossene Aufgabe**  
  
 Projektsymbole sind in der Regel die ICO-Dateien, die mehrere Größen enthalten. Die meisten 16 x 16-Symbole werden dieselben Elemente enthalten. Weitere Informationen sowie den Projekttyp ggf. über die 32 x 32-Versionen verfügen.  
  
 ![Symbole in Visual Studio Project](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")  
  
 **Windows-Steuerelementbibliothek-Projekt VB-Symbole, 16 x 16 und 32 x 32**  
  
 Ein Symbol in der pixelframes im Mittelpunkt. Wenn dies nicht möglich ist, richten Sie das Symbol an den Anfang bzw. rechts des Frames.  
  
 ![Innerhalb des pixelframes zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404-19_IconCentered")  
  
 **Innerhalb des pixelframes zentriertes Symbol**  
  
 ![Symbol "ausgerichtet, die obere rechte Ecke des pixelframes](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404-20_IconTopRight")  
  
 **Symbol oben ausgerichtet rechts von dem Frame**  
  
 ![Ausgerichtetes und zentriertes Symbol pixelframe oben ausgerichtet](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404-21_IconTopAlign")  
  
 **Ausgerichtetes und zentriertes Symbol Ausrichtung am oberen Rand des Frames**  
  
 Um die ideale Ausrichtung und Balance zu erzielen, vermeiden Sie sitzt das Symbol "-Basiselement mit Aktion aus. Ort des Symbols im oberen Bereich des grundlegenden Elements links. Wenn Sie ein weiteres Element hinzufügen möchten, sollten Sie die Ausrichtung und den Saldo des Symbols.  
  
|||  
|-|-|  
|**Richtige Ausrichtung und Lastenausgleich**|**Falsche Ausrichtung und Lastenausgleich**|  
|![Korrigieren Sie symbolverteilung und-Ausrichtung](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Falsche symbolverteilung und-Ausrichtung](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|  
  
 Stellen Sie sicher Größe Parität für Symbole, die Elemente in Gruppen verwendet werden. Beachten Sie, dass in die falschen Kopplung der Kreis und Pfeil groß sind, und stimmen nicht überein.  
  
|||  
|-|-|  
|**Richtige Größe Parität**|**Falsche Größe Parität**|  
|![Korrigieren Sie Symbolgröße und-Parität](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Falsche Symbolgröße und-Parität](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404-25_SizeParityIncorrect")|  
  
 Verwenden Sie konsistente Zeile und visuelle Gewichtung. Werten Sie das Symbol, das Sie erstellen mit anderen Symbolen wie verglichen werden soll, mithilfe eines Vergleichs von Seite-an-Seite. Verwenden Sie niemals den gesamten Rahmen von 16 x 16, verwenden Sie 15 x 15 oder kleiner. Das Verhältnis der negativ, positiv (dunkel-hell) sollte 50/50.  
  
|||  
|-|-|  
|**Richtig negativ, positiv Verhältnis**|**Falsch negativ, positiv Verhältnis**|  
|![Korrigieren Sie optische Gewichtung für Symbole &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Korrigieren Sie optische Gewichtung für Symbole &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Korrigieren Sie optische Gewichtung für Symbole &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Falsche optische Gewichtung für Symbole](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404-29_VisualWeightIncorrect")|  
  
 Verwenden Sie einfache, vergleichbarer Formen und Komplementärfarbe Winkel, um Ihre Elemente zu erstellen, ohne Einbußen bei der Integrität des Elements. Verwenden Sie nach Möglichkeit 45° oder um 90°-Winkel.  
  
 ![Korrigieren Sie symbolwinkel](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404-30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Perspektive  
 Lassen Sie das Symbol, klar und verständlich. Verwenden Sie die Perspektive und einer Lichtquelle nur bei Bedarf. Obwohl Perspektive auf das Symbol für Elemente verwenden vermieden werden sollte, sind einige Elemente nicht erkennbar, ohne ihn. In solchen Fällen kommuniziert Standpunkt stilisierte Gründen der Übersichtlichkeit des Elements ab.  
  
 ![3&#45;Perspektive zeigen](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404-31_3PointPerspective")  
  
 **3-Punkt-Perspektive**  
  
 ![1&#45;Perspektive zeigen](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404-32_1PointPerspective")  
  
 **1-Punkt-Perspektive**  
  
 Die meisten Elemente sollten konfrontiert oder schräg nach rechts.  
  
 ![Symbole rechts angeschrägt](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404-33_AngledRight")  
  
 Verwenden Sie Lichtquellen, nur beim Hinzufügen der erforderlichen Klarheit auf ein Objekt.  
  
|||  
|-|-|  
|**Richtige Lichtquelle**|**Falsche Lichtquelle**|  
|![Korrigieren von Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Falsche Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|  
  
 Verwenden Sie sind nur für die Lesbarkeit zu verbessern oder die Metapher Verbesserung der Kommunikation. Das Verhältnis der Negative positiv (Hell-Dunkel) sollte 50/50.  
  
|||  
|-|-|  
|**Richtige Verwendung von Konturen**|**Falsche Verwendung von Konturen**|  
|![Korrigieren von Konturen](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404-36_OutlinesCorrect")|![Falsche Konturen](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404-37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Symbol "-Typen  
 **Shell- und Befehlsleiste** Symbole bestehen aus nicht mehr als drei der folgenden Elemente: eine einzige Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Shell- und befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404-38_ShellIcons")  
  
 **Beispiele von Shell- und befehlsleistensymbole**  
  
 **Symbolleiste für Fenster-Befehl** Symbole bestehen aus nicht mehr als drei der folgenden Elemente: eine einzige Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Fenster/befehlsleistensymbole Tool](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")  
  
 **Beispiele für die Tool-Fenster/befehlsleistensymbole**  
  
 **Struktur anzeigen Disambiguator** Symbole bestehen aus nicht mehr als drei der folgenden Elemente: eine einzige Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Struktur anzeigen Disambiguator Symbole](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404-40_TreeViewIcons")  
  
 **Beispiele für die Struktur anzeigen Disambiguator-Symbole**  
  
 **Zustandsbasierte Wert Taxonomie** Symbole enthalten sind, in der folgenden Zustände: aktiv, deaktiviert aktive und inaktive deaktiviert.  
  
 ![Status&#45;Symbole für Taxonomie basierte](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")  
  
 **Beispiele für die Symbole für statusbasierte Taxonomie**  
  
 **IntelliSense** Symbole bestehen aus nicht mehr als drei der folgenden Elemente: eine einzige Basis, einen Modifizierer und einen Status.  
  
 ![IntelliSense-Symbole](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404-42_IntelliSenseIcons")  
  
 **Beispiele für die IntelliSense-Symbole**  
  
 **Kleine (16 x 16)-Projekt** Symbole sollten nicht mehr als zwei Elemente verfügen: eine einzige Basis und einen Modifizierer.  
  
 ![Projektsymbol, 16 x 16 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404-43_16x16Project1") ![Projektsymbol, 16 x 16 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404-44_16x16Project2") ![Projektsymbol, 16 x 16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404-45_16x16Project3")  
  
 **Beispiele für kleine (16 x 16)-Projektsymbole**  
  
 **Groß (32 x 32)-Projekt** Symbole nicht mehr als vier aus den folgenden Elementen bestehen: eine einzige Basis, ein bis zwei Modifizierer und eine Sprache, die Überlagerung.  
  
 ![32 x 32 Projektsymbole](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404-46_32x32Project")  
  
 **Beispiele für große (32 x 32) Projektsymbole**  
  
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
  
-   Symbole sollten klar verständlich und konsistent sein.  
  
-   Es ist besser, die Status-Benachrichtigung-Elemente als einzelne Symbole zu verwenden und nicht auf die sie über ein Symbol Basiselement stack. In bestimmten Kontexten möglicherweise die Benutzeroberfläche das Status-Element mit einem Basiselement kombiniert werden.  
  
-   Projektsymbole sind in der Regel die ICO-Dateien, die verschiedenen Größen enthalten. Nur die 16 x 16, 24 x 24 und 32 x 32-Symbole werden aktualisiert. Die meisten 16 x 16 und 24 x 24-Symbole werden dieselben Elemente enthalten. Die 32 x 32 Symbole enthalten weitere Informationen sowie die Sprache Projekttyp, falls zutreffend.  
  
-   Für 32 x 32-Symbole haben die grundlegenden Elemente in der Regel eine 2-Pixel-Linienstärke. Eine 1 oder 2-Pixel-Linienstärke kann Details Elemente verwendet werden. Verwenden Sie Ihrem Urteilsvermögen, um zu bestimmen, die besser geeignet ist.  
  
-   Verfügen Sie über mindestens einen 1-Pixel-der Abstand zwischen Elementen für 16 x 16 und 24 x 24 Symbole. Verwenden Sie für 32 x 32-Symbole 2-Pixel-Abstand zwischen Elementen sowie zwischen dem Modifizierer und das Basiselement.  
  
 ![Elementabstand für 16 x 16, 24 x 24 und 32 x 32 Symbole](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404-47_ElementSpacing")  
  
 **Elementabstand für Symbole die Größe 16 x 16, 24 x 24 und 32 x 32**  
  
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
  
 ![Beispiele für Symbole, deren Farben umgekehrt wurden haben](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405-01_DarkThemeInversion")  
  
 **Beispiele von Symbolen, die deren Farben umgekehrt wurden**  
  
### <a name="base-palette"></a>Basispalette  
 Alle standard-Symbole enthalten drei grundlegende Farben. Symbole enthalten keine Farbverläufe oder Schlagschatten, die mit einem oder zwei Ausnahmen für 3D-Tool-Symbole.  
  
|Verwendung|name|Wert (Design "hell")|Farbmuster|Beispiel|  
|-----------|----------|---------------------------|------------|-------------|  
|Hintergrund/dunklen|VISUAL STUDIO BG|424242 / 66,66,66|![Farbmuster 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![Beispiel für basispalette](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405-02_BasePaletteExample")|  
|Vordergrund-/Licht|VISUAL STUDIO FG|F0EFF1 / 240,239,241|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||  
|Gliederung|Visual Studio heraus|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||  
  
 Zusätzlich zu den Grundfarben kann jedes Symbol eine zusätzliche Farbe aus der erweiterten Palette enthalten.  
  
### <a name="extended-palette"></a>Erweiterte palette  
  
#### <a name="action-modifiers"></a>Aktionsmodifizierer  
 Die vier Farben unten zeigen die Aktionen, die erforderliche Aktionsmodifizierer:  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Positiv|Grün für Visual Studio-Aktion|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|  
|Negativ|Rot für Visual Studio-Aktion|A1260D / 161,38,13|![Muster A1260D](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|  
|Neutral|Visual Studio Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|  
|/ Neu erstellen|Visual Studio Aktion Orange|C27D1A / 194,156,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Beispiele  
 Grün wird verwendet, für positive Aktionsmodifizierer wie z. B. "Hinzufügen", "Ausführen", "Wiedergabe" und "Überprüfen".  
  
|||||  
|-|-|-|-|  
|![Symbol "ausführen"](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **ausführen**|![Symbol für Execute Query](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405-04_ExecuteQuery") **Abfrage ausführen**|![Symbol für alle Schritte wiedergeben](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405-05_PlayAllSteps") **alle Schritte wiedergeben**|![Symbol zum Hinzufügen von Steuerelement](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405-06_AddControl") **-Steuerelement hinzufügen**|  
  
 Red dient für negative Aktionsmodifizierer wie z. B. "Löschen" "Stop", "" Abbrechen"," und "Schließen".  
  
|||||  
|-|-|-|-|  
|![Löschen von Symbol "Beziehung"](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405-07_DeleteRelationship") **Beziehung löschen**|![Spaltensymbol "löschen"](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405-08_DeleteColumn") **Spalte löschen**|![Stop-Abfragesymbol](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405-09_StopQuery") **Abfrage beenden**|![Symbol "Verbindung offline"](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405-10_ConnectionOffline") **Verbindung Offline**|  
  
 Blau wird auf neutral Aktion angewendet, dargestellt als Pfeile, z. B. ","Weiter","Zurück", öffnen Sie" Modifizierer am häufigsten "Import" und "Exportieren".  
  
|||||  
|-|-|-|-|  
|![Wechseln Sie zu dem Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405-11_GoToField") **wechseln Sie zum Feld**|![Überprüfen Sie in einem Batch verarbeitet&#45;im Symbol](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405-12_BatchedCheckIn") **im Batchmodus Check-In**|![Symbol "Adresse-Editor"](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405-13_AddressEditor") **Adress-Editor**|![Symbol "Zuordnung-Editor"](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405-14_AssociationEditor") **Zuordnungs-Editor**|  
  
 Dunkle "Gold" wird in erster Linie für den "Neu"-Modifizierer verwendet.  
  
|||||  
|-|-|-|-|  
|![Symbol "Neues Projekt"](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405-15_NewProject") **neues Projekt**|![Erstellen neuer Symbol "Diagramm"](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405-16_CreateNewGraph") **neues Diagramm erstellen**|![Symbol "neu Unit Test"](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405-17_NewUnitTest") **neue Komponententests**|![Neue Liste Symbol "Element"](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405-18_NewListItem") **neuen Listenelements**|  
  
#### <a name="special-cases"></a>Sonderfälle  
 In besonderen Fällen möglicherweise ein farbigen Aktion Modifizierer unabhängig als eigenständige Symbol verwendet werden. Die Farbe für das Symbol gibt die Aktionen, denen das Symbol zugeordnet ist. Diese Verwendung ist beschränkt auf eine kleine Teilmenge von Symbolen, einschließlich:  
  
||||||  
|-|-|-|-|-|  
|![Symbol "ausführen"](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **ausführen**|![Symbol "Beenden"](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405-19_Stop") **beenden**|![Symbol "löschen"](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405-20_Delete") **löschen**|![Symbol "Speichern"](../../extensibility/ux-guidelines/media/0405-21-save.png "0405-21_Save") **speichern**|![Symbol für Rückwärtssuche Navigate](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405-22_NavigateBack") **zurück navigieren**|  
  
### <a name="code-hierarchy-palette"></a>Befehlspalette der Code-Hierarchie  
  
#### <a name="folder"></a>Ordner  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|Beispiel|  
|-----------|----------|--------------------------|------------|-------------|  
|Ordner|Ordner|DCB67A / 220,182,122|![Muster DCB67A](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![Symbol "Ordner Farbe"](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405-23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio-Sprachen  
 Jede der allgemeinen Sprachen oder Plattformen in Visual Studio verfügbaren verfügt über zugeordnete Farbe. Diese Farben werden verwendet, auf das Symbol "Basis" oder auf der Language-Modifizierer, die in der Ecke der zusammengesetzten Symbole angezeigt werden.  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML-WPF-Blau|0095D 7 / 0,149,215|![Muster 0095d7](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|  
|C++|CPP-Lila|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|  
|C#|CS Grün (VS Aktion Grün)|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|  
|CSS|CSS-Rot|BD1E2D / 189,30,45|![Muster BD1E2D](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|  
|F#|FS Lila|672878 / 103,40,120|![Farbmuster 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|  
|JavaScript|JS-Orange|F16421 / 241,100,33|![Muster F16421](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|  
|VB|VB Blau (Visual Studio-Aktion-Blau)|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|  
|TypeScript|Terminaldienste-Orange|E04C06 / 224,76,6|![Muster E04C06](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|  
|Python|PY Grün|879636 / 135,150,54|![Farbmuster 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Beispiele für Symbole mit Language-Modifizierer  
  
|||||||  
|-|-|-|-|-|-|  
|![Visual Basic-Symbol](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405-25_VB") **VB**|![C&#35; Symbol](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405-26_CSharp") **c#**|![C&#43; &#43; Symbol](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405-27_CPlusPlus") **C++**|![F&#35; Symbol](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405-28_FSharp") **f#**|![Symbol "JavaScript"](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405-29_JavaScript") **JavaScript**|![Symbol "Python"](../../extensibility/ux-guidelines/media/0405-30-python.png "0405-30_Python") **Python**|  
|![Symbol "HTML"](../../extensibility/ux-guidelines/media/0405-31-html.png "0405-31_HTML") **HTML**|![Symbol "WPF"](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405-32_WPF") **WPF**|![ASP-Symbol](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405-33_ASP") **ASP**|![Symbol "CSS"](../../extensibility/ux-guidelines/media/0405-34-css.png "0405-34_CSS") **CSS**|![TypeScript-Symbol](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405-35_TypeScript") **TypeScript**||  
  
#### <a name="intellisense"></a>IntelliSense  
 IntelliSense-Symbole verwenden, eine exklusive Farbpalette. Diese Farben verwendet, um Benutzer schnell zwischen den verschiedenen Elementen in der Liste der IntelliSense-Popupfenster unterscheiden.  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Event-Klasse|Visual Studio Aktion Orange|C27D1A / 194,125,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|  
|Erweiterungsmethode "," Methode ","-Modul, Delegat|Visual Studio Aktion Lila|652D 90 / 101,45,144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|  
|Feld "," Enum-Element ","-Makro "," Struktur "," Wert Union-Typ, Operator, Schnittstelle|Visual Studio Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|  
|Object|Grün für Visual Studio-Aktion|388A34 / 56,138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|  
|Konstanten, die Typdefinition Ausnahme, Enum-Element, Map, Map-Element, Namespace, Vorlage|Hintergrund (VS BG)|424242 / 66,66,66|![Farbmuster 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Beispiele für die IntelliSense-Symbole  
  
||||||  
|-|-|-|-|-|  
|![Symbol für IntelliSense-Klasse](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405-36_IntelliSenseClass") **Klasse**|![Symbol für IntelliSense privates Ereignis](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent") **Private-Ereignis**|![Symbol für IntelliSense-Delegat](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405-38_IntelliSenseDelegate") **delegieren**|![Symbol "Friend" der IntelliSense-Methode](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") **Methode Friend**|![Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-40-field.png "0405-40_Field") **Feld**|  
|![IntelliSense geschützt Enum-Symbol "Element"](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem") **geschützt Enum-Element**|![Symbol für IntelliSense-Objekt](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405-42_IntelliSenseObject") **Objekt**|![Symbol für IntelliSense-Vorlage](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405-43_IntelliSenseTemplate") **Vorlage**|![Symbol "Verknüpfung" der IntelliSense-Ausnahme](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut") **Ausnahme-Kontextmenü**||  
  
### <a name="notifications"></a>Benachrichtigungen  
 Benachrichtigungen in Visual Studio werden verwendet, um Status anzugeben. Die Benachrichtigung Palette verwendet die folgenden vier Farben angezeigt werden, sowie Schwarz oder weiß Foreground-Optionen, so definieren Sie Benachrichtigungen mit den folgenden Statusebenen an.  
  
|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Status: neutral|Benachrichtigung Blau (Visual Studio-Blau)|1BA1E2 / 27,161,226|![Swatch 1BA1E2](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|  
|Status: positiv|Benachrichtigung Grün (VS Grün)|339933 / 51,153,51|![Farbmuster 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|  
|Status: negativ|Benachrichtigung Red (Rot Visual Studio)|E51400 / 229,20,0|![Muster E51400](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|  
|Status: Warnung|Benachrichtigung, Gelb (VS Orange)|FFCC00 / 255,204,0|![Muster FFCC00](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|  
|Füllfarbe|Benachrichtigung Schwarz (Schwarz)|000000 / 0,0,0|![Farbmuster &#35;000000](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|  
|Füllfarbe|Benachrichtigung Whitepaper (Whitepaper)|FFFFFF / 255,255,255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Beispiele für die Symbole für Benachrichtigungen  
  
|||||  
|-|-|-|-|  
|![Symbol "Warnung"](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405-45_Alert") **Warnung**|![Symbol "Warnung"](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405-48_Warning") **Warnung**|![Symbol "abgeschlossen"](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405-46_Complete") **abschließen**|![Symbol "Beenden"](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405-47_Stop") **beenden**|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 Im Allgemeinen besteht aus Visual Studio Online-Funktionen in einem Browser gehostet. Die Farbe in unterschiedlichen Umgebungen variieren, aber das Format bleibt unverändert.  
  
|Gruppieren|Verwendung|name|Wert (alle Designs)|Farbmuster|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Hintergrund|TFSO BG|656565/ 101, 101, 101|![Farbmuster 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|  
|TFS|Gliederung|TFSO OUT|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
|Napa|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
|Monaco|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
|F12|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|  
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Farbmuster 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|  
|F12|Darauf zeigen (Hover)|F12 Blue_Hover|2279BF / 34,121,191|![Swatch 2279BF](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|  
|F12|Deaktiviert|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Muster ABABAC](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|  
|F12|Zeigen Sie Hintergrund|Zeigen Sie bg|D9EBF7 / 217,235,247|![Muster D9EBF7](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|  
|F12|Searchboxpressedbackgroundkey|Gedrückten bg|B2D7F0 / 178,215,240|![Swatch B2D7F0](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|  
|F12|Gliederung|VISUAL STUDIO HERAUS|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|  
|F12|Information|Information|00BCF2 / 0,188,242|![Muster 00BCF2](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|  
|F12|Warnung|Warnung|F28300 / 242,131,0|![Muster F28300](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|  
|F12|Fehler / negativ|Error_Negative|E81123 / 232,17,35|![Muster E81123](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|  
|F12|Starten / Positive|Start_Positive|009E49 / 0,158,73|![Swatch 009E49](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|  
|F12|Break-Typ|Break-Typ|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|  
|F12|Ereignis markieren|Ereignis markieren|A51F00 / 165,31,0|![Muster A51F00](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|  
|F12|Benutzermarkierung|Benutzermarkierung|F16220 / 241,98,32|![Muster F16220](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Beispiele für Visual Studio Online-Symbole  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Symbol "Team" TFS Online](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405-49_TFSOnlineTeam") **Online-Team**|![Symbol für TFS](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405-50_TFSInformation") **Informationen**|![Symbol für TFS-Verlauf](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405-51_TFSHistory") **Verlauf**|![Symbol für TFS-Branch](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405-52_TFSBranch") **Branch**|  
  
|Napa||||  
|----------|-|-|-|  
|![Symbol für Napa-Inhalt](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405-53_NapaContent") **Inhalt**|![Symbol für Napa Office Mail](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405-54_NapaOfficeMail") **Office-e-Mails**|![Symbol für Napa SharePoint](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405-55_NapaSharePoint") **SharePoint**|![Symbol für Napa-Aufgabe Bereich](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405-56_NapaTaskPane") **Aufgabenbereich**|  
  
|Monaco||||  
|------------|-|-|-|  
|![Symbol für Monaco-Dateien](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405-57_MonacoFiles") **Dateien**|![Symbol für Monaco Git](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405-58_MonacoGit") **Git**|![Symbol für Monaco-suchen](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405-59_MonacoSearch") **suchen**|![Symbol für Monaco-Text](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405-60_MonacoText") **Text**|  
  
|F12||||  
|---------|-|-|-|  
|![Symbol für F12-pretty-Code](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405-61_F12PrettyCode") **ziemlich Code**|![Symbol für F12-Warnung](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405-62_F12Warning") **Warnung**|![Symbol für F12-Emulation](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405-63_F12Emulate") **Emulate**|

