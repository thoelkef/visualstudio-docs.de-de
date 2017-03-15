---
title: "Bilder und Symbole f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Bilder und Symbole f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="a-namebkmkimageuseinvisualstudioa-image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Image-Verwendung in Visual Studio  
 Vor dem Erstellen von Grafiken, Betracht Verwendung von mehr als 1.000 Bildern in den [Visual Studio-Bildbibliothek](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Typen von Bildern  
  
-   **Symbole**. Kleine Bilder, die in Befehle, Hierarchien, Vorlagen usw. angezeigt werden. Die in Visual Studio verwendet Standardsymbolgröße ist eine 16 x 16-PNG-DATEI. Symbole, die automatisch von der Image-Dienst erzeugten generieren, das XAML-Format für die Unterstützung von ANZEIGEN.  
  
     **HINWEIS:** während Bilder im Menüsystem verwendet werden, sollten Sie ein Symbol für jeden Befehl nicht erstellen. Wenden Sie sich an [Menüs und Befehlen für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) um festzustellen, ob der Befehl ein Symbol abgerufen werden soll.  
  
-   **Miniaturansichten.** Bilder im Vorschaubereich eines Dialogfelds, z. B. das Dialogfeld "Neues Projekt" verwendet.  
  
-   **Dialogfeld Bilder.** Bilder, die im Assistenten als beschreibende Grafiken oder Nachricht Indikatoren oder Dialogfelder angezeigt werden. Verwenden Sie selten und nur bei Bedarf ein schwieriges Konzept veranschaulichen oder die Aufmerksamkeit des Benutzers (Warnung) zu erhalten.  
  
-   **Animierte Bilder.** Statusanzeigen, Statusleisten und Vorgang Dialogfelder verwendet.  
  
-   **Cursor.** Verwendet, um anzugeben, ob ein Vorgang mit der Maus, wobei ein Objekt gelöscht werden kann usw. zulässig ist.  
  
##  <a name="a-namebkmkicondesigna-icon-design"></a><a name="BKMK_IconDesign"></a> Symbol entwerfen  
  
### <a name="overview"></a>Übersicht  
 Visual Studio verwendet moderne Symbole, die von clean Geometrie und 50/50 Saldo positiv/negativ (Hell/Dunkel) haben, und direkte, verständliche Metaphern verwenden. Symbol "wichtig" Entwurf Punkte im Mittelpunkt Klarheit, Vereinfachung und Kontext.  
  
-   **Klarheit:** konzentrieren, die Core-Metapher, die ein Symbol den Sinn und wahren bietet.  
  
-   **Vereinfachung:** reduzieren Sie das Symbol auf die zentrale Bedeutung – das Design über erhalten Sie nur die erforderlichen Elemente und schnörkellos.  
  
-   **Kontext:** sollten Sie alle Aspekte der Rolle ein Symbol während der Entwicklung Konzept bei der Entscheidung, welche Elemente auf das Symbol Core Metapher bilden von entscheidender Bedeutung ist.  
  
 Mit Symbolen gibt es eine Reihe von Punkten Entwurf, um zu vermeiden:  
  
-   Verwenden Sie keine Symbole, die Elemente der Benutzeroberfläche außer bei Bedarf angeben. Wählen Sie einen weitere abstrakte oder symbolischen Ansatz, wenn das Element der Benutzeroberfläche weder allgemeine, offensichtlich noch eindeutig ist.  
  
-   Nicht zu viele gemeinsame Elemente wie Dokumente, Ordner, Pfeile und die Lupe aus. Verwenden Sie diese Elemente nur, wenn für das Symbol Bedeutung. Z. B. sollte die Lupe nach rechts zeigenden angeben nur suchen, durchsuchen und finden.  
  
-   Obwohl einige ältere Symbolelementen die Verwendung der Perspektive beibehalten, erstellen Sie keine neue Symbole mit Perspektive, wenn das Element verfügt nicht über die Klarheit, ohne ihn.  
  
-   Unterzubringen Sie nicht zu viele Informationen in ein Symbol. Ein einfaches Bild, das leicht erkannt oder als ein Symbol erkannt werden kann, ist viel nützlicher als eine übermäßig komplexe Bild. Ein Symbol kann nicht die ganze Geschichte zu erzählen.  
  
### <a name="icon-creation"></a>Symbol für Erstellung  
  
#### <a name="concept-development"></a>Konzept-Entwicklung  
 Visual Studio ist eine Vielzahl von Symboltypen in die Benutzeroberfläche. Während der Entwicklung der Symbolart sorgfältig prüfen. Verwenden Sie für Ihre Symbolelementen unklar oder ungewöhnlich, dass UI-Objekte. Entscheiden Sie sich für die symbolische in diesen Fällen, wie z. B. mit dem Smarttag-Symbol. Beachten Sie, dass die Bedeutung des abstrakten Tags auf der linken Seite als die vage und UI-basierte Version auf der rechten Seite ist:  
  
|||  
|-|-|  
|**Richtige Verwendung von symbolischen Bilder**|**Falsche Verwendung von symbolischen Bilder**|  
|![Symbol für richtiges Smarttag](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Symbol für falsches Smarttag](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|  
  
 Es gibt Fälle, die Standard, leicht zu erkennende Benutzeroberflächenelemente für Symbole gut funktionieren. Fügen Sie im Fenster ein Beispiel ist:  
  
|||  
|-|-|  
|**Richtige UI-Element in einem Symbol**|**Falsche Element der Benutzeroberfläche in einem Symbol**|  
|![Richtiges Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Falsches Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|  
  
 Verwenden Sie ein Dokument nicht als Basiselement auf das Symbol von Bedeutung ist. Ohne das Dokument ist Element im Dokument hinzufügen (siehe unten) die Bedeutung verloren gehen, während mit Aktualisierung das Dokumentelement nicht erforderlich, kommunizieren die Bedeutung ist.  
  
|||  
|-|-|  
|**Richtige Verwendung von Dokumentsymbol**|**Falsche Verwendung von Dokumentsymbol**|  
|![Richtiges Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Falsches Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|  
  
 Das Konzept der "Show" muss durch das Symbol dargestellt werden, die am besten veranschaulicht, was angezeigt wird, z. B. wie bei im Beispiel alle Dateien anzeigen. Eine Metapher Linse kann verwendet werden, das Konzept der "Ansicht", falls erforderlich, z. B. mit dem Beispiel Ressourcenansicht an.  
  
|||  
|-|-|  
|**"Anzeigen"**|**"Ansicht"**|  
|![Symbol "Anzeigen"](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Symbol "Ansicht"](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|  
  
 Der nach rechts vergrößern können nur darstellen suchen soll, suchen und durchsuchen. Nach links zeigenden Variante mit dem Pluszeichen (+) oder Minuszeichen sollte darstellen nur vergrößern / verkleinern.  
  
|||  
|-|-|  
|**"Suchen"**|**"Zoom"**|  
|![Symbol "Suche"](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Symbol "Zoom"](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|  
  
 Verwenden Sie in der Struktur nicht das Ordnersymbol und Modifizierer. Sofern verfügbar, verwenden Sie nur den Modifizierer.  
  
|||  
|-|-|  
|**Symbole der richtigen Struktur anzeigen**|**Symbole für falsche Struktur anzeigen**|  
|![Richtiges strukturansichtsymbol &#40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![Richtiges strukturansichtsymbol &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Falsches strukturansichtsymbol &#40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![Falsches strukturansichtsymbol &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Stildetails  
  
#### <a name="layout"></a>Layout  
 Stapeln von Elementen wie für standard 16 x 16-Symbole dargestellt:  
  
 ![Layoutstack für 16x16-Symbole](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")  
  
 **Layoutstack für 16 x 16-Symbole**  
  
 Status Notification Elemente sind besser als eigenständige Symbole verwendet. Kontexte sind vorhanden, jedoch in denen eine Benachrichtigung bei base-Elements, z. B. mit dem Symbol für Task abgeschlossen gestapelt werden sollten:  
  
 ![Eigenständige Benachrichtigungen in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")  
  
 **Eigenständige Benachrichtigungssymbole**  
  
 ![Symbol für abgeschlossene Aufgabe](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")  
  
 **Symbol für abgeschlossene Aufgabe**  
  
 Symbole sind in der Regel ICO-Dateien, die verschiedenen Größen enthalten. Die meisten 16 x 16-Symbole werden dieselben Elemente enthalten. Die 32 x 32-Versionen sind weitere Details, darunter den Projekttyp, falls zutreffend.  
  
 ![Projektsymbole in Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")  
  
 **VB Windows-Steuerelementbibliothek-Projekt Symbole, 16 x 16 und 32 x 32**  
  
 Zentrieren Sie ein Symbol in deren Rahmen Pixel. Wenn dies nicht möglich ist, richten Sie das Symbol am Anfang und/oder rechts von dem Frame.  
  
 ![Innerhalb des Pixelframes zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")  
  
 **Innerhalb des pixelframes zentriertes Symbol**  
  
 ![Am Pixelframe oben rechts ausgerichtetes Symbol](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")  
  
 **Symbol oben ausgerichtet rechts von dem Frame**  
  
 ![Am Pixelframe oben rechts ausgerichtetes und zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")  
  
 **Und zentriertes Symbol am Anfang der frame**  
  
 Um ideale Ausrichtung und einen Lastenausgleich zu erreichen, vermeiden Sie das Symbol Basiselement mit Glyphs Action sitzt. Platzieren Sie das Symbol im oberen Bereich des Basiselements links an. Wenn Sie ein weiteres Element hinzufügen möchten, sollten Sie die Ausrichtung und den Saldo des Symbols.  
  
|||  
|-|-|  
|**Richtige Ausrichtung und Lastenausgleich**|**Falsche Ausrichtung und Lastenausgleich**|  
|![Richtige Symbolverteilung und -ausrichtung](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Falsche Symbolverteilung und -ausrichtung](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|  
  
 Stellen Sie sicher Parität der Größe von Symbolen, die Elemente und in Gruppen verwendet werden. Beachten Sie, dass in der falschen Paarung den Kreis und Pfeil groß sind, und stimmen nicht überein.  
  
|||  
|-|-|  
|**Richtige Größe Parität**|**Falsche Größe Parität**|  
|![Richtige Symbolgröße und -parität](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Falsche Symbolgröße und -parität](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|  
  
 Verwenden Sie konsistente Linien- und visual Gewichtungen. Bewerten Sie, wie das Symbol, das Sie erstellen, mit anderen Symbole verglichen, in einem Seite-an-Seite-Vergleich. Verwenden Sie den gesamten 16 x 16-Rahmen verwenden nie 15 x 15 oder kleiner. Das Verhältnis der negativ, positiv (dunkel-hell) sollte 50/50.  
  
|||  
|-|-|  
|**Richtig negativ, positiv-Verhältnis**|**Falsch negativ, positiv-Verhältnis**|  
|![Korrigieren Sie optische Gewichtung für Symbole &#40; 1 & #41.](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Korrigieren Sie optische Gewichtung für Symbole &#40; 2 & #41.](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Korrigieren Sie optische Gewichtung für Symbole &#40; 3 & #41.](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Falsche optische Gewichtung für Symbole](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|  
  
 Verwenden Sie einfach und vergleichbare Formen und Komplementärfarbe Winkel um die Elemente zu erstellen, ohne Einbußen bei der Element-Integrität. Verwenden Sie nach Möglichkeit 45 Grad oder 90 Grad-Winkel.  
  
 ![Richtige Symbolwinkel](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Perspektive  
 Lassen Sie das Symbol klar und verständlich. Verwenden Sie die Perspektive und einer Lichtquelle nur bei Bedarf. Obwohl mit Perspektive auf Symbolelementen vermieden werden sollten, sind einige Elemente ohne nicht erkannt. In solchen Fällen kommuniziert Standpunkt stilisierte Klarheit des Elements.  
  
 ![3 &#45; Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")  
  
 **3-Punkt-Perspektive**  
  
 ![1 &#45; Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")  
  
 **1-Punkt-Perspektive**  
  
 Die meisten Elemente sollten treffen oder schräg nach rechts.  
  
 ![Symbole rechts angeschrägt](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")  
  
 Verwenden Sie Lichtquellen nur, wenn ein Objekt erforderlichen Klarheit hinzugefügt.  
  
|||  
|-|-|  
|**Richtige Lichtquelle**|**Falsche Lichtquelle**|  
|![Richtige Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Falsche Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|  
  
 Verwenden Sie beschrieben werden, nur um die Lesbarkeit zu verbessern oder um das Prinzip besser zu kommunizieren. Der Negative positiv (dunkel hell) Saldo sollte 50/50.  
  
|||  
|-|-|  
|**Richtige Verwendung von Konturen**|**Falsche Verwendung von Konturen**|  
|![Richtige Konturen](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Falsche Konturen](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Symbol für Typen  
 **Shell- und Befehlsleiste** Symbolen bestehen aus nicht mehr als drei der folgenden Elemente: eine Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Shell- und Befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")  
  
 **Beispiele für Shell- und befehlsleistensymbole**  
  
 **Tool-Fenster Befehlsleiste** Symbolen bestehen aus nicht mehr als drei der folgenden Elemente: eine Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Toolfenster-/Befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")  
  
 **Beispiele für Symbole der Tool-Fenster Befehlsleiste**  
  
 **Struktur anzeigen Begriffsklärung** Symbolen bestehen aus nicht mehr als drei der folgenden Elemente: eine Basis, einen Modifizierer, eine Aktion oder ein Status.  
  
 ![Strukturansichtsymbole (Begriffserklärung)](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")  
  
 **Beispiele für die Struktur anzeigen Begriffsklärung Symbole**  
  
 **Zustandsbasierte Wert Taxonomie** Symbole enthalten sind, in der folgenden Zustände: aktiv, deaktiviert aktiv und inaktiv deaktiviert.  
  
 ![Status &#45; je Taxonomie Symbole](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")  
  
 **Beispiele für Symbole für statusbasierte Taxonomie**  
  
 **IntelliSense** Symbolen bestehen aus nicht mehr als drei der folgenden Elemente: eine Basis ein Modifizierer und einen Status.  
  
 ![IntelliSense-Symbole](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")  
  
 **Beispiele für IntelliSense-Symbole**  
  
 **Kleine (16 x 16)-Projekt** Symbole sollten nicht mehr als zwei Elemente verfügen: eine Basis und ein Modifizierer.  
  
 ![Symbol für 16 x 16-Projekt &#40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![Symbol für 16 x 16-Projekt &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![Symbol für 16 x 16-Projekt &#40; 3 &#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")  
  
 **Beispiele für kleine (16 x 16)-Projektsymbole**  
  
 **Großes (32 x 32) Projekt** Symbolen bestehen aus nicht mehr als vier der folgenden Elemente: eine Basis, ein bis zwei Modifizierer und eine Sprache überlagern.  
  
 ![Projektsymbol, 32x32](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")  
  
 **Beispiele für große Projektsymbole (32 x 32)**  
  
### <a name="production-details"></a>Produktionsdetails  
 Alle neuen Elemente der Benutzeroberfläche mit Windows Presentation Foundation (WPF) erstellt werden soll, und alle neuen Symbole für WPF sollte im 32-Bit-PNG-Format sein. Die 24-Bit-PNG-DATEI ist ein legacy-Format, die Transparenz wird nicht unterstützt und sollte daher nicht für Symbole.  
  
 Speichern Sie die Auflösung von 96 dpi.  
  
#### <a name="file-types"></a>Dateitypen  
  
-   **32-Bit-PNG:** das bevorzugte Format für Symbole. Eine verlustfreie Komprimierung Datendateiformat, die ein einzelnes Raster (Pixel)-Bild speichern können. 32-Bit-PNG-Dateien unterstützen Alphakanaltransparenz, Gammakorrektur und Zeilensprungverfahren.  
  
-   **32-Bit-BMP:** für nicht-WPF-Steuerelemente. Auch als XP oder Highcolor ist 32-Bit-BMP RGB/ein Bildformat, eine True-Color-Image mit einer Alphakanaltransparenz. Der alpha-Kanal ist eine Ebene der Transparenz in Adobe Photoshop, der anschließend innerhalb der Bitmap als eine zusätzliche (4) gespeichert ist festgelegt Farbkanal. Schwarzer Hintergrund wird während der Produktion von Bildmaterial für alle 32-Bit-BMP-Dateien ermöglichen einen schnelle visuellen Hinweis auf die Farbtiefe hinzugefügt. Diese schwarze Hintergrund stellt den Bereich, in der Benutzeroberfläche maskiert werden.  
  
-   **32-Bit-ICO:** für Symbole und Element hinzufügen. Alle ICO-Dateien sind 32-Bit-true Color mit Alphakanaltransparenz (RGB/A). Da ICO-Dateien mehrere Größe und Farbe Tiefen speichern können, haben häufig eine ICO-Format mit 16 x 16, 32 x 32, 48 x 48 und 256 x 256 Bildgrößen Vista-Symbolen. Um in Windows-Explorer korrekt angezeigt wird, ICO-Dateien müssen gespeichert, 24-Bit- und 8-Bit-Farbe Tiefen für jede Bildgröße unterbrochen werden.  
  
-   **XAML:** für Entwurfsoberflächen und Windows-Adorner. XAML-Symbole sind vektorbasiertes Bild-Dateien, die skalieren, drehen, ablegen und Transparenz zu unterstützen. Sie gelten nicht in Visual Studio heute aber werden immer populärer aufgrund ihrer Flexibilität.  
  
-   **SVG**  
  
-   **24-Bit-BMP:** für die Visual Studio-Befehlsleiste. Ein True Color RGB-Bildformat 24-Bit-BMP ist ein Symbol-Konvention, die eine Ebene der Transparenz erstellt mithilfe von Magenta (R = 255, G = 0, B = 255) als Schlüssel für die Transparenzebene Hit Farbe. In einem 24-Bit-BMP werden alle Magenta Flächen mit der Hintergrundfarbe angezeigt.  
  
-   **24-Bit-GIF:** für die Visual Studio-Befehlsleiste. Ein True Color RGB-Bildformat, das Transparenz unterstützt. GIF-Dateien werden häufig in Assistenten Bildmaterial und GIF-Animationen verwendet.  
  
### <a name="icon-construction"></a>Symbol-Konstruktion  
 Die kleinste Größe der Symbole in Visual Studio ist 16 x 16. Das größte ist gemeinsam mit 32 x 32. Bedenken Sie nicht auf den gesamten 16 x 16, 24 x 24 und 32 x 32 Rahmen beim Entwerfen ein Symbol gefüllt. Lesbar, einheitliche Symbol Konstruktion ist wichtig für Benutzer. Befolgen Sie folgende Punkte, wenn Sie Symbole erstellen.  
  
-   Symbole sollte klar, verständlich und konsistent sein.  
  
-   Es ist besser, die Status-Benachrichtigung-Elemente als einzelne Symbole verwendet und nicht auf die sie über ein Symbol Basiselement Stapeln. In bestimmten Kontexten möglicherweise die Benutzeroberfläche der Status-Element mit einem base-Element kombiniert werden.  
  
-   Symbole sind normalerweise ICO-Dateien, die verschiedenen Größen enthalten. Nur die 16 x 16, 24 x 24 und 32 x 32-Symbole werden aktualisiert. Die meisten 16 x 16 und 24 x 24 Symbole werden dieselben Elemente enthalten. Die 32 x 32-Symbole enthalten weitere Details, darunter die Sprache Projekttyp, falls zutreffend.  
  
-   Für 32 x 32-Symbole besitzen die Basiselementen im Allgemeinen eine Linienstärke von 2 Pixel. Eine Linienstärke 1 oder 2 Pixel kann für Detailelemente verwendet werden. Verwenden Sie Ihr Urteilsvermögen, um zu bestimmen, die besser geeignet ist.  
  
-   Müssen Sie mindestens einen 1-Pixel-Abstand zwischen Elementen für 16 x 16 und 24 x 24 Symbole. Verwenden Sie für 32 x 32-Symbole 2 Pixel Abstand zwischen Elementen sowie zwischen den Modifizierer und Basiselement.  
  
 ![Elementabstand für Symbole der Größen 16x16, 24x24 und 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")  
  
 **Elementabstand für Symbole Größe 16 x 16, 24 x 24 und 32 x 32**  
  
#### <a name="color-and-accessibility"></a>Farbe und Eingabehilfen  
 Visual Studio-Compliance-Richtlinien erfordern, dass alle Symbole in das Produkt erforderlichen Eingabehilfen für die Farbe und Kontrast übergeben. Dies wird durch das Symbol Inversion, und beim Entwerfen, sollten Sie bedenken, dass sie programmgesteuert im Produkt umgekehrt werden.  
  
 Weitere Informationen zum Verwenden von Farbe in Visual Studio-Symbolen finden Sie unter [mit Farbe in Bildern](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="a-namebkmkusingcolorinimagesa-using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Verwenden von Farbe in Bildern  
  
### <a name="overview"></a>Übersicht  
 Symbole in Visual Studio sind in erster Linie einfarbig. Farbe ist reserviert, um bestimmte Informationen zu vermitteln und nie zur Gestaltung. Farbe wird verwendet:  
  
-   Um eine Aktion anzugeben.  
  
-   Benachrichtigung des Benutzers auf eine Benachrichtigung zum status  
  
-   Language-Zugehörigkeit festlegen  
  
-   Um Elemente in IntelliSense zu unterscheiden.  
  
### <a name="accessibility"></a>Barrierefreiheit  
 Visual Studio-Compliance-Richtlinien erfordern, dass alle Symbole in der Bahn Produkt erforderlichen Eingabehilfen für die Farbe und Kontrast aktiviert. Farben in der Palette visuellen Sprache getestet wurden und diese Anforderungen zu erfüllen.  
  
#### <a name="color-inversion-for-dark-themes"></a>Farbumkehrung für dunkle Designs  
 Um Symbole, die mit der richtigen Kontrastverhältnis im Visual Studio dunkle Design angezeigt zu machen, wird eine Umkehrung programmgesteuert angewendet. Die Farben in dieser Anleitung wurden teilweise ausgewählt, damit sie ordnungsgemäß umkehren. Die Verwendung von Farben zu dieser Palette einschränken oder erhalten Sie zu unvorhersehbaren Ergebnissen, wenn die Umkehrung angewendet wird.  
  
 ![Beispiele für Symbole, deren Farben umgekehrt wurden](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")  
  
 **Beispiele von Symbolen, die deren Farben umgekehrt wurden**  
  
### <a name="base-palette"></a>Basispalette  
 Alle Standardsymbole enthalten drei Grundfarben. Symbole enthalten keine Farbverläufe oder Schlagschatten, die mit einem oder zwei Ausnahmen für 3D-Symbole.  
  
|Verwendung|Name|Wert (Design "hell")|Farbmuster|Beispiel|  
|-----------|----------|---------------------------|------------|-------------|  
|Hintergrund oder dunkle|VS-BG|424242 / 66,66,66|![Muster 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Beispiel für Basispalette](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|  
|Vordergrund-/Licht|VS FG|F0EFF1 / 240,239,241|![Muster F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Gliederung|Visual STUDIO heraus|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Zusätzlich zu den Grundfarben kann jedes Symbol einer zusätzliche Farbe aus der Palette der erweiterten enthalten.  
  
### <a name="extended-palette"></a>Erweiterte palette  
  
#### <a name="action-modifiers"></a>Aktionsmodifizierer  
 Die folgenden vier Farben zeigen die Aktionsmodifizierer erforderlichen Aktionen:  
  
|Verwendung|Name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Positiv|VS Aktion Grün|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Negativ|VS Aktion Rot|A1260D / 161,38,13|![Muster A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Neutral|VS Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|/ Neu erstellen|VS Aktion Orange|C27D1A / 194,156,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Beispiele  
 Grün dient für positive Aktionsmodifizierer wie z. B. "Add", "Ausführen", "Wiedergabe" und "Validate".  
  
|||||  
|-|-|-|-|  
|![Symbol "ausführen"](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun") **Ausführen**|![Symbol "Abfrage ausführen"](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery") **Abfrage ausführen**|![Symbol für alle Schritte wiedergeben](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps") **alle Schritte wiedergeben**|![Symbol "Steuerelement hinzufügen"](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl") **-Steuerelement hinzufügen**|  
  
 Rot dient für negative Aktionsmodifizierer wie z. B. "Löschen" "Beenden", "Abbrechen" und "Schließen".  
  
|||||  
|-|-|-|-|  
|![Beziehung löschen](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship") **Beziehung löschen**|![Spalte löschen](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn") **Spalte löschen**|![Symbol "Abfrage beenden"](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery") **Abfrage beenden**|![Symbol "Verbindung offline"](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline") **Verbindung Offline**|  
  
 Blau neutrale Aktion gilt für Modifizierer am häufigsten 'Importieren' als Pfeile, wie z. B. ","Weiter","Zurück"Öffnen" und "Exportieren".  
  
|||||  
|-|-|-|-|  
|![Klicken Sie auf das Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField") **zum Feld**|![In einem Batch verarbeitet &#45; überprüfen im Symbol](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn") **Batch Einchecken**|![Symbol "Adress-Editor"](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor") **Adress-Editor**|![Symbol "Zuordnungs-Editor"](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor") **Zuordnungs-Editor**|  
  
 Dunkle Gold wird hauptsächlich für den Modifizierer "Neu".  
  
|||||  
|-|-|-|-|  
|![Neues Projektsymbol](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject") **Neues Projekt**|![Erstellen neuer Symbol "Diagramm"](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph") **Neues Diagramm erstellen**|![Symbol "neue Unit Test"](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest") **neue Komponententest**|![Symbol für neue Liste](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem") **neues Listenelement**|  
  
#### <a name="special-cases"></a>Sonderfälle  
 In besonderen Fällen kann ein farbige Aktion-Modifizierer unabhängig als eigenständige-Symbol verwendet werden. Die Farbe für das Symbol zeigt die Aktionen, denen das Symbol zugeordnet ist. Die Verwendung ist nur eine kleine Teilmenge von Symbolen, einschließlich:  
  
||||||  
|-|-|-|-|-|  
|![Symbol "ausführen"](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun") **Ausführen**|![Symbol "Anhalten"](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop") **Beenden**|![Symbol "löschen"](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete") **Löschen**|![Symbol "Speichern"](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save") **Speichern**|![Symbol für navigieren](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack") **zurück navigieren**|  
  
### <a name="code-hierarchy-palette"></a>Code-Hierarchie-palette  
  
#### <a name="folder"></a>Ordner  
  
|Verwendung|Name|Wert (alle Designs)|Farbmuster|Beispiel|  
|-----------|----------|--------------------------|------------|-------------|  
|Ordner|Ordner|DCB67A / 220,182,122|![Muster DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Symbol "Ordnerfarbe"](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio-Sprachen  
 Jede allgemeine Sprachen oder Plattformen in Visual Studio verfügbaren verfügt über eine entsprechende Farbe. Diese Farben werden verwendet, auf das Basis-Symbol oder Language-Modifizierer, die in der oberen rechten Ecke der zusammengesetzten Symbole angezeigt werden.  
  
|Verwendung|Name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML WPF Blau|0095D 7 / 0,149,215|![Muster 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP Violett|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|A#|CS-Grün (VS Aktion Grün)|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|CSS-Rot|BD1E2D / 189,30,45|![Muster BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS Violett|672878 / 103,40,120|![Muster 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS-Orange|F16421 / 241,100,33|![Muster F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB Blau (VS Aktion Blau)|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|Terminaldienste-Orange|E04C06 / 224,76,6|![Muster E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|PY Grün|879636 / 135,150,54|![Muster 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Beispiele von Symbolen mit Language-Modifizierer  
  
|||||||  
|-|-|-|-|-|-|  
|![Visual Basic-Symbol](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB") **VB**|![C &#35; Symbol für](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp") **c#**|![C &#43; &#43; Symbol für](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus") **C++**|![F &#35; Symbol für](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp") **f#**|![Symbol "JavaScript"](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript") **JavaScript**|![Python-Symbol](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python") **Python**|  
|![Symbol "HTML"](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML") **HTML**|![Symbol für WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF") **WPF**|![ASP-Symbol](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP") **ASP**|![CSS-Symbol](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS") **CSS**|![TypeScript-Symbol](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript") **TypeScript**||  
  
#### <a name="intellisense"></a>IntelliSense  
 IntelliSense-Symbole verwenden eine exklusive Farbpalette. Diese Farben werden verwendet, um Benutzer schnell zwischen den verschiedenen Elementen in der IntelliSense-Popup-Liste unterscheiden können.  
  
|Verwendung|Name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Event-Klasse|VS Aktion Orange|C27D1A / 194,125,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Erweiterungsmethode Delegaten Modul-Methode|VS Aktion Violett|652D 90 / 101,45,144|![Muster 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Feld, Enum-Element, Makros, Struktur, Union Werttyp Operator-Schnittstelle|VS Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Objekt|VS Aktion Grün|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Konstante, Typdefinition Ausnahme, Enum-Element, Zuordnung, Zuordnungselement, Namespace, Vorlage|Hintergrund (VS BG)|424242 / 66,66,66|![Muster 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Beispiele für IntelliSense-Symbole  
  
||||||  
|-|-|-|-|-|  
|![Symbol für IntelliSense-Klasse](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass") **Klasse**|![Symbol für IntelliSense-privates Ereignis](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent") **Private-Ereignis**|![Symbol für IntelliSense-Delegat](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate") **Delegieren**|![Friend-Symbol für IntelliSense-Methode](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") **Friend-Methode**|![Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field") **Feld**|  
|![IntelliSense geschützt Enum Symbol](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem") **geschützt Enum-Element**|![Symbol für IntelliSense-Objekt](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject") **Objekt**|![Symbol für IntelliSense-Vorlage](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate") **Vorlage**|![Symbol für IntelliSense-ausnahmeverknüpfung](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut") **Ausnahme-Kontextmenü**||  
  
### <a name="notifications"></a>Benachrichtigungen  
 Benachrichtigungen in Visual Studio werden verwendet, um den Status anzuzeigen. Die Benachrichtigung Palette verwendet die folgenden vier Farben als auch Schwarz oder weiß Foreground-Optionen, um Benachrichtigungen mit den folgenden Statusebenen zu definieren.  
  
|Verwendung|Name|Wert (alle Designs)|Farbmuster|  
|-----------|----------|--------------------------|------------|  
|Status: neutral|Benachrichtigung Blau (VS-Blau)|1BA1E2 / 27,161,226|![Muster 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Status: positive|Benachrichtigung Grün (VS Grün)|339933 / 51,153,51|![Muster 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Status: negativ|Benachrichtigung Rot (VS Rot)|E51400 / 229,20,0|![Muster E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Status: Warnung|Benachrichtigung Gelb (VS Orange)|FFCC00 / 255,204,0|![Muster FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Füllfarbe|Benachrichtigung Black (Schwarz)|000000 / 0,0,0|![Muster &#35; 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Füllfarbe|Benachrichtigung weiß (weiß)|FFFFFF / 255,255,255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Beispiele für Benachrichtigungssymbole  
  
|||||  
|-|-|-|-|  
|![Symbol "Warnung"](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert") **Warnung**|![Symbol "Warnung"](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning") **Warnung**|![Symbol "abgeschlossen"](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete") **abschließen**|![Symbol "Anhalten"](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop") **Beenden**|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 Im Allgemeinen besteht aus Visual Studio Online-Funktionen in einem Browser gehostet. Die Farbe ändert sich in unterschiedlichen Umgebungen, die Formatvorlage bleibt jedoch gleich.  
  
|Gruppieren|Verwendung|Name|Wert (alle Designs)|Farbmuster|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Hintergrund|TFSO BG|656565/ 101, 101, 101|![Muster 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Gliederung|TFSO|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Hintergrund|Weiß|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Muster 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Darauf zeigen (Hover)|F12 Blue_Hover|2279BF / 34,121,191|![Muster 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Deaktiviert|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Muster ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Hover-Hintergrund|Zeigen Sie bg|D9EBF7 / 217,235,247|![Muster D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Gedrückten Hintergrund|Gedrückten bg|B2D7F0 / 178,215,240|![Muster B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Gliederung|VISUAL STUDIO HERAUS|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Informationen|Information|00BCF2 / 0,188,242|![Muster 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Warnung|Warnung|F28300 / 242,131,0|![Muster F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Fehler / Negative|Error_Negative|E81123 / 232,17,35|![Muster E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Starten / Positive|Start_Positive|009E49 / 0,158,73|![Muster 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Break-Typ|Break-Typ|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Ereignis markieren|Ereignis markieren|A51F00 / 165,31,0|![Muster A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Benutzermarkierung|Benutzermarkierung|F16220 / 241,98,32|![Muster F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Beispiele für Visual Studio Online-Symbole  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Symbol für TFS Online Team](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam") **Online-Team**|![Symbol für TFS-Informationen](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation") **Informationen**|![Symbol für TFS-Verlauf](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory") **Verlauf**|![Symbol für TFS-Verzweigung](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch") **Verzweigung**|  
  
|Napa||||  
|----------|-|-|-|  
|![Symbol für Napa-Inhalt](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent") **Inhalt**|![E-Mail-Symbol für Napa-Office](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail") **Office E-Mail**|![Symbol für Napa SharePoint](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint") **SharePoint**|![Symbol für Napa-Aufgabenbereich](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane") **Aufgabenbereich**|  
  
|Monaco||||  
|------------|-|-|-|  
|![Symbol für Monaco-Dateien](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles") **Dateien**|![Symbol für Monaco Git](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit") **Git**|![Symbol für Monaco-suchen](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch") **Suchen**|![Symbol für Monaco-Text](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText") **Text**|  
  
|F12||||  
|---------|-|-|-|  
|![Symbol für F12-pretty-Code](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode") **ziemlich Code**|![Symbol für F12-Warnung](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning") **Warnung**|![Symbol für F12-Emulation](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate") **Emulate**|