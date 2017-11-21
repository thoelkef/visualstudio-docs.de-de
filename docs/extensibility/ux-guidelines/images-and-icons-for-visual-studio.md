---
title: "Bilder und Symbole für Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7856f8fac7e986f3e5383fa91261de39fe815a28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="images-and-icons-for-visual-studio"></a>Bilder und Symbole für Visual Studio
##  <a name="BKMK_ImageUseInVisualStudio"></a>Image-Verwendung in Visual Studio  
 Berücksichtigen Sie vor dem Erstellen von Grafiken, festlegen, dass die Verwendung von mehr als 1.000 Bildern in der [Visual Studio-Bildbibliothek](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Typen von Bildern  
  
-   **Symbole**. Kleine Bilder, die in Befehle, Hierarchien, Vorlagen und So weiter angezeigt werden. Die Standardgröße-Symbol in Visual Studio verwendet ist ein 16 x 16-PNG. Symbole, die automatisch von der Image-Dienst erzeugten Generieren der XAML-Format für die HDPI-Unterstützung.  
  
     **Hinweis:** während Bilder im Menüsystem verwendet werden, sollten Sie ein Symbol für jeden Befehl nicht erstellen. Wenden Sie sich an [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) um festzustellen, ob der Befehl, ein Symbol abrufen soll.  
  
-   **Miniaturansichten.** Bilder, die in den Vorschaubereich eines Dialogfelds, z. B. das Dialogfeld "Neues Projekt" verwendet werden.  
  
-   **Dialogfeld-Images.** Bilder, die in Dialogfeldern oder Assistenten als beschreibender Grafiken oder Nachricht Indikatoren angezeigt werden. Verwenden Sie nur selten und nur bei Bedarf, um ein schwierig Konzept veranschaulichen oder gewinnen, die Aufmerksamkeit des Benutzers (Warnung).  
  
-   **Animierten Bildern.** Statusanzeigen, Statusleisten und Dialogfelder des Vorgangs verwendet.  
  
-   **Cursor.** Verwendet, um anzugeben, ob ein Vorgang mit der Maus, wobei ein Objekt kann gelöscht werden, usw. zulässig ist.  
  
##  <a name="BKMK_IconDesign"></a>Symbol entwerfen  
  
### <a name="overview"></a>Übersicht  
 Visual Studio verwendet modernes Symbole, die fehlerfreie Geometrie und 50/50 Saldo positiver und negativer (Hell/Dunkel) aufweisen und direkte und verständlich Metaphern verwenden. Symbol "wichtig" Entwurf Punkte im Mittelpunkt Klarheit Vereinfachung und Kontext.  
  
-   **Verdeutlichung:** darauf konzentrieren, die Core-Metapher, die ein Symbol, dessen Bedeutung und wahren bietet.  
  
-   **Vereinfachung:** reduzieren Sie das Symbol auf seiner Bedeutung Core - Designs über mit nur die erforderlichen Elemente und schnörkellos abrufen.  
  
-   **Kontext:** berücksichtigen Sie alle Aspekte der Rolle "ein Symbol" während der Entwicklung Konzept der entscheidend ist, bei der Entscheidung, welche Elemente auf das Symbol "Core Metapher bilden.  
  
 Mit Symbolen gibt es eine Anzahl von entwurfspunkte, um zu vermeiden:  
  
-   Verwenden Sie keine Symbole, die UI-Elemente, außer wenn dies angebracht anzugeben. Wählen Sie einen weiteren abstrakte oder symbolischen Ansatz aus, wenn das Element der Benutzeroberfläche weder allgemeine, offensichtlich noch eindeutig ist.  
  
-   Nicht zu viele gemeinsame Elemente wie Dokumente, Ordner, die Lupe dienenden Pfeile aus. Verwenden Sie solche Elemente angezeigt, wenn entscheidend dafür, dass das Symbol "Bedeutung. Beispielsweise herausstellt Lupe nach rechts weisend nur Suche, durchsuchen und finden.  
  
-   Zwar einige Symbol für veraltet-Elemente, die Verwendung der Perspektive verwalten, erstellen Sie nicht neuer Symbole mit Perspektive, sofern das Element Klarheit, ohne es fehlt.  
  
-   Unterzubringen Sie nicht zu viele Informationen in ein Symbol. Ein einfaches Abbild, das leicht erkannt oder als erkennbar Symbol gelernt werden kann eignet sich wesentlich mehr als eine übermäßig komplexe Bild. Ein Symbol kann nicht die gesamte Geschichte erzählen.  
  
### <a name="icon-creation"></a>Symbol "erstellen  
  
#### <a name="concept-development"></a>Konzept Entwicklung  
 Visual Studio ist eine Vielzahl von Symboltypen innerhalb der Benutzeroberfläche aus. Während der Entwicklung der Symbolart sorgfältig prüfen. Verwenden Sie für Ihre Symbolelementen unklar oder ungewöhnlich, dass UI-Objekte. Entscheiden Sie sich für die symbolische in diesen Fällen wie z. B. mit dem Smarttag-Symbol. Beachten Sie, dass die Bedeutung des abstrakte Tags auf der linken Seite als die vage und UI-basierten Version auf der rechten Seite leichter ersichtlich ist:  
  
|||  
|-|-|  
|**Richtige Verwendung von symbolischen Bilder**|**Falsche Verwendung von symbolischen Bilder**|  
|![Symbol für richtiges Smarttag](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404 01_SmartTagCorrect")|![Symbol für falsches Smarttag](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 02_SmartTagIncorrect")|  
  
 Es sind Instanzen, die in denen standardmäßigen, leicht erkennbare Benutzeroberflächenelemente gut für Symbole funktionieren. Das Hinzufügen eines Fensters ein solches Beispiel ist:  
  
|||  
|-|-|  
|**Richtige UI-Element in einem Symbol**|**Falsche Benutzeroberflächenautomatisierungs-Elements in ein Symbol**|  
|![Symbol für richtiges Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 03_AddWindowCorrect")|![Symbol für falsches Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 04_AddWindowIncorrect")|  
  
 Ein Dokument nicht als base-Elements verwendet werden, es sei denn, es entscheidend dafür, dass das Symbol "Bedeutung ist. Ohne das Dokument ist ein Element im Dokument hinzufügen (siehe unten) die Bedeutung verloren geht, während der Aktualisierungsvorgang Dokumentelement nicht erforderlich ist, kommunizieren die Bedeutung ist.  
  
|||  
|-|-|  
|**Richtige Verwendung von Dokumentsymbol**|**Falsche Verwendung von Dokumentsymbol**|  
|![Symbol für richtiges Dokument](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 05_DocumentIconCorrect")|![Falsches Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404 06_DocumentIconIncorrect")|  
  
 Das Konzept der "anzeigen" sollte durch das Symbol dargestellt werden, die am besten geeignet, was angezeigt wird, z. B. wie bei im Beispiel alle Dateien anzeigen. Eine Linse Metapher kann verwendet werden, um anzugeben, das Konzept der "View", falls erforderlich, z. B. mit der Ressource anzeigen eines Beispiels.  
  
|||  
|-|-|  
|**"Anzeigen"**|**"View"**|  
|![Symbol "anzeigen"](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 07_Show")|![Symbol "Ansicht"](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 08_View")|  
  
 Der nach rechts weisend vergrößern können darstellen nur durchsuchen soll, suchen und durchsuchen. Die Variante nach links weisend mit dem Pluszeichen (+) oder Minuszeichen (-) sollten darstellen nur vergrößern / verkleinern.  
  
|||  
|-|-|  
|**"Suchen"**|**"Zoom"**|  
|![Symbol "Suche"](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 09_Search")|![Symbol "Zoom"](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 10_Zoom")|  
  
 Verwenden Sie in den Strukturansichten das Symbol "Ordner" und einen Modifizierer. Wenn verfügbar ist, verwenden Sie nur den Modifizierer.  
  
|||  
|-|-|  
|**Symbole der richtigen Struktur anzeigen**|**Symbole für falsche Struktur anzeigen**|  
|![Richtiges strukturansichtsymbol &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![korrigieren strukturansichtsymbol &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![Falsches strukturansichtsymbol &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![falsches strukturansichtsymbol &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Stildetails  
  
#### <a name="layout"></a>Layout  
 Stack-Elemente, die für standard 16 x 16-Symbole angezeigt:  
  
 ![Layoutstack für 16 x 16-Symbole](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404 15_LayoutStack")<br />Layoutstack für 16x16-Symbole
  
 Benachrichtigung Statuselemente sind besser als eigenständige Symbole verwendet. Kontexte sind vorhanden, jedoch in denen eine Benachrichtigung auf das Basiselement z. B. mit dem Task abgeschlossen Symbol gestapelt werden sollten:  
  
 ![Eigenständige Benachrichtigungen in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404 16_StandaloneNotificationIcons")<br />Eigenständige Benachrichtigungssymbole
  
 ![Symbol für abgeschlossene Aufgabe](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 17_TaskComplete")<br />Symbol für abgeschlossene Aufgabe
  
 Projektsymbole sind in der Regel ICO-Dateien, die mehrere Größen enthalten. Die meisten 16 x 16-Symbole werden dieselben Elemente enthalten. Die 32 x 32-Versionen sind weitere Details, einschließlich der Projekttyp, wenn zutreffend.  
  
 ![Symbole in Visual Studio Project](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 18_IconProjectThreeSizes")<br />VB-Windows-Steuerelementbibliothek-Projekt Symbole, 16 x 16 und 32 x 32 
  
 Zentrieren Sie ein Symbol in deren Rahmen Pixel. Wenn dies nicht möglich ist, richten Sie das Symbol am Anfang und/oder rechts des Frames.  
  
 ![Innerhalb des pixelframes zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 19_IconCentered")<br />Innerhalb des Pixelframes zentriertes Symbol
  
 ![Symbol "ausgerichtet, die obere rechte Ecke des pixelframes](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 20_IconTopRight")<br />Symbol "oben ausgerichtet rechts des Frames
  
 ![Ausgerichtetes und zentriertes Symbol orientiert sich am pixelframe oben](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 21_IconTopAlign")<br />Und zentriertes Symbol am oberen Rand der frame
  
 Um optimale Ausrichtung und Lastenausgleich zu erzielen, vermeiden Sie sitzt das Symbol Basiselement mit Aktion Symbole aus. Setzen Sie das Symbol im oberen Bereich des grundlegenden Elements nach links. Wenn Sie ein weiteres Element hinzufügen möchten, sollten Sie die Ausrichtung und den Saldo des Symbols.  
  
|||  
|-|-|  
|**Richtige Ausrichtung und Lastenausgleich**|**Falsche Ausrichtung und Lastenausgleich**|  
|![Beheben Sie symbolverteilung und-Ausrichtung](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 22_AlignBalanceCorrect")|![Falsche symbolverteilung und-Ausrichtung](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 23_AlignBalanceIncorrect")|  
  
 Stellen Sie sicher Größe Parität für Symbole, die Elemente in Gruppen verwendet werden. Beachten Sie, dass in der falschen Paarung ergibt sich der Kreis und Pfeil groß sind, und stimmen nicht überein.  
  
|||  
|-|-|  
|**Richtige Größe Parität**|**Falsche Größe Parität**|  
|![Beheben Sie die Symbolgröße und-Parität](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 24_SizeParityCorrect")|![Falsche Symbolgröße und-Parität](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 25_SizeParityIncorrect")|  
  
 Verwenden Sie konsistente Linien- und visuelle Gewichtung. Werten Sie das Symbol ", das Sie erstellen mit anderen Symbole wie verglichen werden soll, mithilfe eines Seite-an-Seite-Vergleichs. Verwenden Sie niemals die gesamte 16 x 16-Frame, verwenden Sie 15 x 15 oder kleineren. Das Verhältnis des Negative-positiv (Dark-hell) sollte 50/50.  
  
|||  
|-|-|  
|**Richtig negativ-positivem-Verhältnis**|**Falsch Negative-positivem-Verhältnis**|  
|![Beheben Sie optische Gewichtung für Symbole &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 26_VisualWeightCorrect1")<br /><br /> ![Beheben Sie optische Gewichtung für Symbole &#40; 2 &#41; ] (../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 27_VisualWeightCorrect2")<br /><br /> ![Beheben Sie optische Gewichtung für Symbole &#40; 3 &#41; ] (../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 28_VisualWeightCorrect3")|![Falsche optische Gewichtung für Symbole](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 29_VisualWeightIncorrect")|  
  
 Verwenden Sie einfache, vergleichbare Formen und Komplementärfarbe Winkel, um Ihre Elemente erstellen möchten, ohne Einbußen bei der Element-Integrität. Verwenden Sie möglichst 45° oder 90-Grad-Winkel.  
  
 ![Beheben Sie symbolwinkel](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Perspektive  
 Lassen Sie das Symbol löschen und verständlich. Verwenden Sie die Sicht und eine Lichtquelle nur bei Bedarf. Obwohl mit Perspektive auf Symbolelementen vermieden werden sollte, sind einige Elemente nicht erkennbar, ohne ihn. In solchen Fällen kommuniziert eine gestalteten Perspektive Klarheit des Elements.  
  
 ![3-Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 31_3PointPerspective")<br />3-Punkt-Perspektive
  
 ![1-Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 32_1PointPerspective")<br />1-Punkt-Perspektive
  
 Die meisten Elemente zugängliche werden sollte oder rechts angeschrägt:  
  
 ![Symbole rechts angeschrägt](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 33_AngledRight")  
  
 Verwenden Sie Lichtquellen nur, wenn ein Objekt erforderlichen Klarheit hinzugefügt.  
  
|||  
|-|-|  
|**Richtige Lichtquelle**|**Falsche Lichtquelle**|  
|![Beheben Sie Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 34_LightSourcesCorrect")|![Falsche Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 35_LightSourcesIncorrect")|  
  
 Verwenden Sie beschrieben werden, nur für die Lesbarkeit zu verbessern oder die Metapher besser zu kommunizieren. Die Negative positiv (Dark-Light) Balance sollte 50/50.  
  
|||  
|-|-|  
|**Richtige Verwendung von Konturen**|**Falsche Verwendung von Konturen**|  
|![Beheben Sie Gliederungen](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 36_OutlinesCorrect")|![Falsche Konturen](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Symbol "-Typen  
 **Shell- und Befehlsleiste** Symbolen bestehen aus nicht mehr als drei der folgenden Elemente: eine Basis, einen Modifizierer, die eine Aktion oder einen Status.  
  
 ![Beispiele für Shell- und befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 38_ShellIcons")<br />Beispiele für Shell- und befehlsleistensymbole
  
 **Symbolleiste für Fenster-Befehl** Symbolen bestehen aus nicht mehr als drei der folgenden Elemente: eine Basis, einen Modifizierer, die eine Aktion oder einen Status.  
  
 ![Beispiele für Toolfenster Befehlsleisten Symbole](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 39_ToolWindowCommandBarIcons")<br />Beispiele für Tool Fenster/befehlsleistensymbole
  
 **Struktur anzeigen Disambiguator** Symbolen bestehen aus nicht mehr als drei der folgenden Elemente: eine Basis, einen Modifizierer, die eine Aktion oder einen Status.  
  
 ![Beispiele für die Struktur anzeigen Disambiguator Symbole](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 40_TreeViewIcons")<br />Beispiele für die Struktur anzeigen Disambiguator-Symbole
  
 **Zustandsbasierte Wert Taxonomie** Symbole vorhanden, in der folgenden Zustände: aktiv, deaktiviert aktiv und inaktiv deaktiviert.  
  
 ![Beispiele für die Symbole für statusbasierte Taxonomie](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404 41_StateBasedTaxonomy")<br />Beispiele für die Symbole für statusbasierte Taxonomie
  
 **IntelliSense** Symbolen bestehen aus nicht mehr als drei der folgenden Elemente: eine Basis, einen Modifizierer und einen Status.  
  
 ![Beispiele für IntelliSense-Symbole](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 42_IntelliSenseIcons")<br />Beispiele für IntelliSense-Symbole
  
 **Kleine (16 x 16)-Projekt** Symbole sollte nicht mehr als zwei Elemente verfügen: eine einzige Basis und einen Modifizierer.  
  
 ![Beispiele für kleine (16 x 16)-Projekt Symbole](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 43_16x16Project1") ![Projektsymbol, 16 x 16 &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 44_16x16Project2") ![Projektsymbol, 16 x 16 &#40; 3 &#41;] (../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 45_16x16Project3")<br />Beispiele für kleine (16 x 16)-Projektsymbole
  
 **Groß (32 x 32) Projekt** Symbolen bestehen aus nicht mehr als vier der folgenden Elemente: eine Basis, ein bis zwei Modifizierer und eine Sprache, die Überlagerung.  
  
 ![Beispiele für große (32 x 32)-Projekt Symbole](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 46_32x32Project")<br />Beispiele für große Projektsymbole (32 x 32)
  
### <a name="production-details"></a>Produktionsdetails  
 Alle neuen Elemente der Benutzeroberfläche mithilfe von Windows Presentation Foundation (WPF) erstellt werden sollen, und alle neuen Symbole für WPF muss im 32-Bit-PNG-Format. Das 24-Bit-PNG ist ein legacy-Format, die Transparenz nicht unterstützt und ist daher für die Symbole nicht empfohlen.  
  
 Speichern Sie die Lösung bei 96 DPI.  
  
#### <a name="file-types"></a>Dateitypen  
  
-   **32-Bit-PNG:** das bevorzugte Format für Symbole. Eine prioritätsbasierte Komprimierung Datendateiformat, die ein einzelnes Rasterbild (Pixel) gespeichert werden kann. 32-Bit-PNG-Dateien unterstützen Alpha-Kanal Transparenz, Gammakorrektur und Zeilensprung.  
  
-   **32-Bit-BMP:** für nicht-WPF-Steuerelemente. So genannte XP oder high Color, ist die 32-Bit-BMP ein RGB/A-Bildformat ein Bild "true" Farbe Zwischenfarbe einen Alpha-Kanal. Alpha-Kanal ist eine Ebene der Transparenz gekennzeichnet, die in Adobe Photoshop, die anschließend in die Bitmap als eine zusätzliche (vierte) gespeichert ist Farbe-Kanal. Schwarzer Hintergrund wird während der Grafik Produktion einsetzen, um alle 32-Bit-BMP-Dateien ermöglichen einen schnellen visuellen Hinweis auf die Farbtiefe hinzugefügt. Diese schwarze Hintergrund stellt den Bereich, in der Benutzeroberfläche maskiert werden.  
  
-   **32-Bit-ICO:** für Projektsymbole und Element hinzufügen. Alle ICO-Dateien sind "true" 32-Bit-Farbe Zwischenfarbe Alpha-Kanal (RGB/A). Da ICO-Dateien mehrere Größe und Farbe Tiefen gespeichert werden können, sind Vista Symbole häufig in einem mit 16 x 16, 32 x 32, 48 x 48 und 256 x 256 Bildgrößen ICO-Format. Um ordnungsgemäß in Windows-Explorer anzuzeigen, ICO-Dateien müssen gespeichert, 24-Bit- und 8-Bit-Farbe Tiefen für jede Bildgröße unterbrochen werden.  
  
-   **XAML:** für Entwurfsoberflächen und Windows-Adorner. Verwendung von XAML-Symbole werden vektorbasiertes Bild-Dateien, die Skalierung, drehen, ablegen und Transparenz unterstützen. Sie sind derzeit nicht in Visual Studio häufig, jedoch werden aufgrund ihrer Flexibilität gängigeren immer.  
  
-   **SVG**  
  
-   **24-Bit-BMP:** für Visual Studio-Befehlsleiste. Eine "true" Farbe RGB-Bildformat 24-Bit-BMP ist ein Symbol-Konvention, die eine Ebene der Transparenz erstellt, indem Sie Magenta (R = 255, G = 0, B = 255) als Schlüssel für eine Ebene Hit Transparenz Farbe. In einem 24-Bit-BMP werden alle Magenta Flächen mit der Hintergrundfarbe angezeigt.  
  
-   **24-Bit-GIF:** für Visual Studio-Befehlsleiste. Eine "true" Farbe RGB-Bildformat, die Transparenz unterstützt. GIF-Dateien werden häufig in Assistenten Grafiken und Animationen GIF verwendet.  
  
### <a name="icon-construction"></a>Symbol "-Konstruktion  
 Die kleinste Größe der Symbole in Visual Studio ist 16 x 16. Das größte ist gemeinsam verwenden 32 x 32. Bedenken Sie nicht auf den gesamten 16 x 16, 24 x 24 oder 32 x 32 Rahmen erstrecken beim Entwerfen ein Symbol. Symbol "lesbar, einheitliche" Konstruktion ist entscheidend dafür, dass Benutzer ausführen. Halten Sie folgende Punkte beim Erstellen von Symbolen.  
  
-   Symbole sollte klar, verständlich und konsistent sein.  
  
-   Es ist besser, die die Status-Benachrichtigung-Elemente als einzelne Symbole verwendet und nicht für sie zusätzlich zu einer Basis Icon-Element des Stapels. In bestimmten Kontexten möglicherweise die Benutzeroberfläche der Status-Element mit einem Basiselement kombiniert werden.  
  
-   Projektsymbole sind in der Regel ICO-Dateien, die einige Größen enthalten. Nur die 16 x 16, 24 x 24 und 32 x 32-Symbole werden aktualisiert. Die meisten Symbole der Größen 16 x 16 und 24 x 24 werden dieselben Elemente enthalten. Die 32 x 32-Symbole enthalten weitere Details, einschließlich der Sprache Projekttyp, wenn zutreffend.  
  
-   Für 32 x 32-Symbole haben die grundlegenden Elemente in der Regel eine 2-Pixel-Linienstärke. Eine Linienstärke 1 oder 2 Pixel kann für Detailelemente verwendet werden. Verwenden Sie bewährte Ihr eigenes Urteilsvermögen, um zu bestimmen, die besser geeignet ist.  
  
-   Verfügen Sie über mindestens einen 1 Pixel-Abstand zwischen Elementen für 16 x 16 und 24 x 24 Symbole. Verwenden Sie für 32 x 32-Symbole 2 Pixel Abstand zwischen Elementen sowie zwischen den Modifizierer und Basiselement.  
  
 ![Element Abstand für Symbole 16 x 16, 24 x 24 und 32 x 32 Größe](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 47_ElementSpacing")<br />Elementabstand für Symbole Größe 16 x 16, 24 x 24 und 32 x 32
  
#### <a name="color-and-accessibility"></a>Farbe und Barrierefreiheit  
 Visual Studio-Compliance-Richtlinien erfordern, dass alle Symbole in das Produkt die Anforderungen zur Barrierefreiheit für Farbe und Kontrast übergeben. Dies erfolgt über die Umkehrung Symbol, und beim Entwerfen, sollten Sie bedenken, dass sie programmgesteuert im Produkt umgekehrt werden.  
  
 Weitere Informationen zum Verwenden von Farben in Visual Studio-Symbolen finden Sie unter [über die Farbe in Bildern](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="BKMK_UsingColorInImages"></a>Über die Farbe in Bildern  
  
### <a name="overview"></a>Übersicht  
 Symbole in Visual Studio sind in erster Linie einfarbig. Farbe ist reserviert, um bestimmte Informationen zu vermitteln und nie für die Ergänzung. Farbe wird verwendet:  
  
-   Um eine Aktion anzugeben.  
  
-   um dem Benutzer eine Benachrichtigung zum Status zu informieren.  
  
-   Um Sprache Zugehörigkeit zu kennzeichnen.  
  
-   Um Elemente in IntelliSense zu unterscheiden.  
  
### <a name="accessibility"></a>Barrierefreiheit  
 Visual Studio-Compliance-Richtlinien erfordern, dass alle Symbole in der Product-Durchlauf der Anforderungen zur Barrierefreiheit für Farbe und Kontrast überprüft. Farben in der Palette visuellen Sprache getestet wurden und die folgenden Anforderungen erfüllen.  
  
#### <a name="color-inversion-for-dark-themes"></a>Farbumkehrung für dunkle Designs  
 Damit auch Symbole mit der richtigen Kontrast in der Visual Studio Design "dunkel" angezeigt werden, wird eine Umkehrung programmgesteuert angewendet. Die Farben in diesem Handbuch haben, damit sie ordnungsgemäß umkehren teilweise ausgewählt. Einschränken der Verwendung von Farben zu dieser Palette, oder Sie erhalten zu unvorhersehbaren Ergebnissen führt auf, wenn die Umkehrung angewendet wird.  
  
 ![Beispiele von Symbolen, die deren Farben umgekehrt wurden](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 01_DarkThemeInversion")<br />Beispiele von Symbolen, die deren Farben umgekehrt wurden
  
### <a name="base-palette"></a>Basispalette  
 Alle standard-Symbole enthalten drei grundlegende Farben. Symbolen enthalten keine Farbverläufe oder Schlagschatten mit ein oder zwei Ausnahmen für 3D-Tool-Symbole.  
  
|Verwendung|Name|Wert (Design "hell")|Farbfeld|Beispiel|  
|-----------|----------|---------------------------|------------|-------------|  
|Hintergrund/dunkel|VS-BG|424242 / 66,66,66|![Farbfeld 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Beispiel für basispalette](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 02_BasePaletteExample")|  
|Vordergrund-/leichte|VS FG|F0EFF1 / 240,239,241|![Muster F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Gliederung|VS Out|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Zusätzlich zu den Grundfarben kann jedes Symbol eine zusätzliche Farbe aus der Palette der erweiterten enthalten.  
  
### <a name="extended-palette"></a>Erweiterte palette  
  
#### <a name="action-modifiers"></a>Aktionsmodifizierer  
 Die folgenden vier Farben geben die Typen von Aktionen, die erforderliche Aktionsmodifizierer:  
  
|Verwendung|Name|Wert (alle Designs)|Farbfeld|  
|-----------|----------|--------------------------|------------|  
|Positiv|VS Aktion Grün|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Negativ|VS Aktion Rot|A1260D / 161,38,13|![Muster A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Neutral|VS Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|/ Neu erstellen|VS Aktion Orange|C27D1A / 194,156,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Beispiele  
 Grün dient für positive Aktionsmodifizierer wie "Hinzufügen", "Ausführen", "Play" und "Überprüfen".  
  
|||||  
|-|-|-|-|  
|![Symbol "ausführen"](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />Run|![Symbol "Abfrage" ausführen](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 04_ExecuteQuery")<br />Führen Sie Abfrage|![Symbol für alle Schritte wiedergeben](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 05_PlayAllSteps")<br />Alle Schritte wiedergeben|![Steuerelementsymbol "hinzufügen"](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 06_AddControl")<br />Fügen Sie Steuerelement hinzu|  
  
 Rot wird für negative Aktionsmodifizierer wie ","Beenden"Delete" verwendet "Abbrechen" und "Schließen".  
  
|||||  
|-|-|-|-|  
|![Symbol "Beziehung" Löschen](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 07_DeleteRelationship")<br />Beziehung löschen|![Symbol "Spalte" Löschen](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 08_DeleteColumn")<br />Spalte löschen|![Symbol "Abfrage" Stop](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 09_StopQuery")<br />Abfrage beenden|![Symbol "Verbindung offline"](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 10_ConnectionOffline")<br />Verbindung Offline|  
  
 Blau ist neutral Aktion angewendet, dargestellt als Pfeile, z. B. ","Weiter","Previous", öffnen Sie" am häufigsten Modifizierer "Importieren" und "Exportieren".  
  
|||||  
|-|-|-|-|  
|![Klicken Sie auf das Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 11_GoToField")<br />Gehe zu Feld|![In einem Batch verarbeitet Kontrollkästchen &#45; im Symbol](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 12_BatchedCheckIn")<br />Im Batch Einchecken|![Symbol "Adress-Editor"](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 13_AddressEditor")<br />Adress-Editor|![Symbol "Zuordnung-Editor"](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 14_AssociationEditor")<br />Zuordnungs-Editor|  
  
 Dunkel Gold dient in erster Linie für den Modifizierer "Neu".  
  
|||||  
|-|-|-|-|  
|![Symbol "Neues Projekt"](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 15_NewProject")<br />Neues Projekt|![Symbol "Neues Diagramm" erstellen](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 16_CreateNewGraph")<br />Erstellen eines neuen Diagramms|![Symbol "Neues Unit Test"](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 17_NewUnitTest")<br />Neuen Komponententests|![Symbol "Neues Element"](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 18_NewListItem")<br />Neues Listenelement|  
  
#### <a name="special-cases"></a>Sonderfälle  
 In besonderen Fällen möglicherweise ein farbigen Aktion Modifizierer unabhängig als eigenständige Symbol verwendet werden. Die Farbe für das Symbol "gibt die Aktionen, denen das Symbol zugeordnet ist. Diese Verwendung ist beschränkt auf eine kleine Teilmenge von Symbolen, einschließlich:  
  
||||||  
|-|-|-|-|-|  
|![Symbol "ausführen"](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />Run|![Symbol "Beenden"](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 19_Stop")<br />Stop|![Symbol "löschen"](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 20_Delete")<br />Löschen|![Symbol "Speichern"](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 21_Save")<br />Speichern|![Symbol "zurück" navigieren](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 22_NavigateBack")<br />Rückwärts navigieren|  
  
### <a name="code-hierarchy-palette"></a>Code-Hierarchie-palette  
  
#### <a name="folder"></a>Ordner  
  
|Verwendung|Name|Wert (alle Designs)|Farbfeld|Beispiel|  
|-----------|----------|--------------------------|------------|-------------|  
|Ordner|Ordner|DCB67A / 220,182,122|![Muster DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Symbol "ordnerfarbe" Ordner](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio-Sprachen  
 Jedes allgemeine Sprachen oder Plattformen in Visual Studio verfügbaren verfügt über eine zugeordnete Farbe. Diese Farben werden verwendet, auf das Symbol "Basis" oder auf Language-Modifizierer, die in der rechten oberen Ecke der zusammengesetzten Symbole angezeigt werden.  
  
|Verwendung|Name|Wert (alle Designs)|Farbfeld|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML WPF Blau|0095D 7 / 0,149,215|![Muster 0095d7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP Violett|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS-Grün (VS Aktion Grün)|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|CSS-Rot|BD1E2D / 189,30,45|![Muster BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS Violett|672878 / 103,40,120|![Farbfeld 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS-Orange|F16421 / 241,100,33|![Muster F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB Blau (VS Aktion Blau)|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|Terminaldienste-Orange|E04C06 / 224,76,6|![Muster E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|PY Grün|879636 / 135,150,54|![Farbfeld 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Beispiele von Symbolen mit Language-Modifizierer  
  
|||||||  
|-|-|-|-|-|-|  
|![Visual Basic-Symbol](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 25_VB")<br />VB|![C &#35; Symbol "](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 26_CSharp")<br />C#|![C# 43; &#43; Symbol "](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 27_CPlusPlus")<br />C++|![F &#35; Symbol "](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 28_FSharp")<br />F#|![Symbol "JavaScript"](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 29_JavaScript")<br />JavaScript|![Python-Symbol](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 30_Python")<br />Python|  
|![Symbol "HTML"](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 31_HTML")<br />HTML|![Symbol "WPF"](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 32_WPF")<br />WPF|![Symbol "ASP"](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 33_ASP")<br />ASP|![Symbol "CSS"](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 34_CSS")<br />CSS|![TypeScript-Symbol](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 35_TypeScript")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 IntelliSense-Symbole verwenden, eine exklusive Farbpalette. Diese Farben werden verwendet, damit Benutzer schnell zwischen den verschiedenen Elementen in der Liste der IntelliSense-Popup zu unterscheiden.  
  
|Verwendung|Name|Wert (alle Designs)|Farbfeld|  
|-----------|----------|--------------------------|------------|  
|Event-Klasse|VS Aktion Orange|C27D1A / 194,125,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Erweiterungsmethode, Delegaten Modul-Methode|VS Aktion Violett|652D 90 / 101,45,144|![Muster 652d90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Feld, Enum-Element, Makros, Struktur, Union Werttyp ist, Operator, Schnittstelle|VS Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Objekt|VS Aktion Grün|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Konstanten, Typdefinition Ausnahme, Enum-Element, Karten, Zuordnungselement, Namespace, Vorlage|Hintergrund (VS BG)|424242 / 66,66,66|![Farbfeld 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Beispiele für IntelliSense-Symbole  
  
||||||  
|-|-|-|-|-|  
|![Symbol "Klasse" IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 36_IntelliSenseClass")<br />Klasse|![Symbol für IntelliSense-privates Ereignis](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 37_IntelliSensePrivateEvent")<br />Privates Ereignis|![Symbol für IntelliSense-Delegat](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 38_IntelliSenseDelegate")<br />Delegate|![Symbol "Friend" der IntelliSense-Methode](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 39_IntelliSenseMethodFriend")<br />Methode "Friend"|![Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 40_Field")<br />Feld|  
|![IntelliSense geschützt Symbol "Enumeration"](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405 41_IntelliSenseProtectedEnumItem")<br />Geschützte Enum-Element|![Symbol für IntelliSense-Objekt](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 42_IntelliSenseObject")<br />Objekt|![Symbol für IntelliSense-Vorlage](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 43_IntelliSenseTemplate")<br />Vorlage|![Symbol "Verknüpfung" der IntelliSense-Ausnahme](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 44_IntelliSenseExceptionShortcut")<br />Ausnahme-Verknüpfung||  
  
### <a name="notifications"></a>Benachrichtigungen  
 Benachrichtigungen in Visual Studio werden verwendet, um Status anzugeben. Die Benachrichtigung Palette verwendet die folgenden vier Farben sowie Schwarz oder weiß Vordergrund AutoAusfüllen-Optionen, um Benachrichtigungen mit den folgenden Statusebenen definieren.  
  
|Verwendung|Name|Wert (alle Designs)|Farbfeld|  
|-----------|----------|--------------------------|------------|  
|Status: neutrale|Benachrichtigung Blau (VS-Blau)|1BA1E2 / 27,161,226|![Muster 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Status: positive|Benachrichtigung Grün (VS Grün)|339933 / 51,153,51|![Farbfeld 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Status: negativ|Benachrichtigung Rot (VS Rot)|E51400 / 229,20,0|![Muster E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Status: Warnung|Benachrichtigung, Gelb (VS Orange)|FFCC00 / 255,204,0|![Muster FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Füllfarbe|Benachrichtigung Schwarz (Schwarz)|000000 / 0,0,0|![Farbfeld &#35; 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Füllfarbe|Benachrichtigung weiß (weiß)|FFFFFF / 255,255,255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Beispiele für die Symbole für Benachrichtigungen  
  
|||||  
|-|-|-|-|  
|![Symbol "Warnung"](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 45_Alert")<br />Warnung|![Symbol "tabellenwarnung"](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 48_Warning")<br />Warnung|![Symbol für abgeschlossene](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 46_Complete")<br />Abgeschlossen|![Symbol "Beenden"](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 47_Stop")<br />Stop|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 Im Allgemeinen besteht aus Visual Studio Online-Funktionen in einem Browser gehostet. Die Farbe in verschiedenen Umgebungen variiert, der Stil bleibt jedoch gleich.  
  
|Gruppieren|Verwendung|Name|Wert (alle Designs)|Farbfeld|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Hintergrund|TFSO BG|656565/ 101, 101, 101|![Farbfeld 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Gliederung|TFSO OUT|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Farbfeld 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Darauf zeigen (Hover)|F12 Blue_Hover|2279BF / 34,121,191|![Muster 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Deaktiviert|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Muster ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Zeigen Sie im Hintergrund|Zeigen Sie bg|D9EBF7 / 217,235,247|![Muster D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Gedrückte Hintergrund|Gedrückte bg|B2D7F0 / 178,215,240|![Muster B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Gliederung|VS OUT|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Information|Information|00BCF2 / 0,188,242|![Muster 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Warnung|Warnung|F28300 / 242,131,0|![Muster F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Fehler / negativ|Error_Negative|E81123 / 232,17,35|![Muster E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Starten / Positive|Start_Positive|009E49 / 0,158,73|![Muster 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Break-Typ|Break-Typ|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Ereignis markieren|Ereignis markieren|A51F00 / 165,31,0|![Muster A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Benutzermarkierung|Benutzermarkierung|F16220 / 241,98,32|![Muster F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Beispiele für Visual Studio Online-Symbole  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Symbol für TFS Online-Team](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 49_TFSOnlineTeam")<br />Online-Team|![Symbol für TFS-Informationen](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405 50_TFSInformation")<br />Information|![Symbol für TFS-Verlauf](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 51_TFSHistory")<br />Versionsgeschichte|![Symbol für TFS-Verzweigung](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 52_TFSBranch")<br />Verzweigung|  
  
|Napa||||  
|----------|-|-|-|  
|![Symbol für Napa-Inhalt](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 53_NapaContent")<br />Inhalt|![Symbol für Napa Office Mail](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 54_NapaOfficeMail")<br />Office-Mail|![Symbol für Napa SharePoint](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 55_NapaSharePoint")<br />SharePoint|![Symbol für Napa-Aufgabenbereich](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 56_NapaTaskPane")<br />Aufgabenbereich|  
  
|Monaco||||  
|------------|-|-|-|  
|![Symbol für Monaco-Dateien](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 57_MonacoFiles")<br />Dateien|![Symbol für Monaco Git](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 58_MonacoGit")<br />Git|![Symbol "Suche" Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 59_MonacoSearch")<br />Suchen|![Symbol für Monaco-Text](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 60_MonacoText")<br />Text|  
  
|F12|||  
|---------|-|-|  
|![Symbol "F12-pretty-Code"](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 61_F12PrettyCode")<br />Pretty-Code|![Symbol für F12-Warnung](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 62_F12Warning")<br />Warnung|![Symbol für F12-Emulation](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 63_F12Emulate")<br />Emulieren|