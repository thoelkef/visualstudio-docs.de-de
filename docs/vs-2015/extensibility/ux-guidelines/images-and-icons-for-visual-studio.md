---
title: Bilder und Symbole
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 843829c56fcbd2f5c558d7c4a8b14a660a431eac
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301326"
---
# <a name="images-and-icons-for-visual-studio"></a>Bilder und Symbole für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Bildverwendung in Visual Studio
 Bevor Sie Grafiken erstellen, sollten Sie die verwendung der mehr als 1.000 Bilder in der [Visual Studio-Bildbibliothek](https://www.microsoft.com/download/details.aspx?id=35825)verwenden.

### <a name="types-of-images"></a>Arten von Bildern

- **Symbole**. Kleine Bilder, die in Befehlen, Hierarchien, Vorlagen usw. angezeigt werden. Die in Visual Studio verwendete Standardsymbolgröße ist ein 16x16 PNG. Vom Image-Service erzeugten Symbole generieren automatisch das XAML-Format für HDPI-Unterstützung.

     **HINWEIS:** Während Bilder im Menüsystem verwendet werden, sollten Sie nicht für jeden Befehl ein Symbol erstellen. In [den Menüs und Befehlen für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) erfahren Sie, ob Ihr Befehl ein Symbol erhalten soll.

- **Miniaturansichten.** Bilder, die im Vorschaubereich eines Dialogfelds verwendet werden, z. B. im Dialogfeld Neues Projekt.

- **Dialogbilder.** Bilder, die in Dialogfeldern oder Assistenten angezeigt werden, entweder als beschreibende Grafiken oder Nachrichtenindikatoren. Verwenden Sie selten und nur bei Bedarf, um ein schwieriges Konzept zu veranschaulichen oder die Aufmerksamkeit des Benutzers zu gewinnen (Warnung, Warnung).

- **Animierte Bilder.** Wird in Fortschrittsindikatoren, Statusleisten und Vorgangsdialogen verwendet.

- **Cursor.** Wird verwendet, um anzugeben, ob ein Vorgang mit der Maus zulässig ist, wo ein Objekt gelöscht werden kann usw.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Icon-Design

### <a name="overview"></a>Übersicht
 Visual Studio verwendet Symbole im modernen Stil, die eine saubere Geometrie und eine 50/50-Balance von positiv/negativ (hell/dunkel) aufweisen und direkte, verständliche Metaphern verwenden. Entscheidende Icon-Designpunkte drehen sich um Klarheit, Vereinfachung und Kontext.

- **Klarheit:** Konzentrieren Sie sich auf die Kernmetapher, die einer Ikone ihre Bedeutung und Individualität verleiht.

- **Vereinfachung:** Reduzieren Sie das Symbol auf seine Kernbedeutung – bringen Sie das Thema mit nur den notwendigen Elementen und ohne Schnickschnack rüber.

- **Kontext:** Berücksichtigen Sie alle Aspekte der Rolle einer Ikone während der Konzeptentwicklung, was bei der Entscheidung, welche Elemente die Kernmetapher der Ikone darstellen, von entscheidender Bedeutung ist.

  Bei Symbolen gibt es eine Reihe von Designpunkten zu vermeiden:

- Verwenden Sie keine Symbole, die UI-Elemente bedeuten, es sei denn, dies ist angemessen. Wählen Sie einen abstrakteren oder symbolischeren Ansatz, wenn das UI-Element weder allgemein, offensichtlich noch eindeutig ist.

- Verwenden Sie keine allgemeinen Elemente wie Dokumente, Ordner, Pfeile und die Lupe. Verwenden Sie solche Elemente nur, wenn dies für die Bedeutung des Symbols wesentlich ist. Beispielsweise sollte die nach rechts gerichtete Lupe nur Such- und Suchvorgänge anzeigen.

- Obwohl einige ältere Icon-Elemente die Verwendung von Perspektive beibehalten, erstellen Sie keine neuen Symbole mit Perspektive, es sei denn, das Element ist ohne sie nicht klar.

- Verpacken Sie nicht zu viele Informationen in ein Symbol. Ein einfaches Bild, das leicht als erkennbares Symbol erkannt oder erlernt werden kann, ist viel nützlicher als ein zu komplexes Bild. Ein Symbol kann nicht die ganze Geschichte erzählen.

### <a name="icon-creation"></a>Icon-Erstellung

#### <a name="concept-development"></a>Konzeptentwicklung
 Visual Studio verfügt über eine Vielzahl von Symboltypen. Berücksichtigen Sie den Symboltyp während der Entwicklung sorgfältig. Verwenden Sie keine unklaren oder ungewöhnlichen UI-Objekte für Ihre Symbolelemente. Entscheiden Sie sich in diesen Fällen für das Symbolische, z. B. mit dem SmartTag-Symbol. Beachten Sie, dass die Bedeutung des abstrakten Tags auf der linken Seite offensichtlicher ist als die vage, UI-basierte Version auf der rechten Seite:

|||
|-|-|
|**Korrekte Verwendung symbolischer Bilder**|**Falsche Verwendung von symbolischen Bildern**|
|![Symbol für richtiges Smarttag](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404-01_SmartTagCorrect")|![Symbol für falsches Smarttag](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Es gibt Fälle, in denen standardmäßige, leicht erkennbare UI-Elemente gut für Symbole geeignet sind. Fenster hinzufügen ist ein solches Beispiel:

|||
|-|-|
|**Korrigieren des UI-Elements in einem Symbol**|**Falsches UI-Element in einem Symbol**|
|![Richtiges Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404-03_AddWindowCorrect")|![Falsches Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Verwenden Sie ein Dokument nicht als Basiselement, es sei denn, es ist für die Bedeutung des Symbols unerlässlich. Ohne das Dokumentelement auf Dokument hinzufügen (unten) geht die Bedeutung verloren, während beim Aktualisieren das Dokumentelement nicht erforderlich ist, um die Bedeutung zu kommunizieren.

|||
|-|-|
|**Korrekte Verwendung des Dokumentsymbols**|**Falsche Verwendung des Dokumentsymbols**|
|![Richtiges Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Falsches Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Das Konzept "Show" sollte durch das Symbol dargestellt werden, das am besten veranschaulicht, was angezeigt wird, z. B. im Beispiel Alle Dateien anzeigen. Eine Linsenmetapher kann verwendet werden, um bei Bedarf das Konzept "Ansicht" anzugeben, z. B. im Beispiel Ressourcenansicht.

|||
|-|-|
|**"Show"**|**"Ansicht"**|
|![Symbol "Anzeigen"](../../extensibility/ux-guidelines/media/0404-07-show.png "0404-07_Show")|![Symbol "Ansicht"](../../extensibility/ux-guidelines/media/0404-08-view.png "0404-08_View")|

 Das nach rechts gerichtete Lupensymbol sollte nur Suchen, Suchen und Durchsuchen darstellen. Die nach links gerichtete Variante mit dem Plus- oder Minuszeichen sollte nur Vergrößern/Verkleinern darstellen.

|||
|-|-|
|**"Suchen"**|**"Zoom"**|
|![Suchsymbol](../../extensibility/ux-guidelines/media/0404-09-search.png "0404-09_Search")|![Symbol "Zoom"](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404-10_Zoom")|

 Verwenden Sie in Baumansichten nicht sowohl das Ordnersymbol als auch einen Modifikator. Wenn verfügbar, verwenden Sie nur den Modifikator.

|||
|-|-|
|**Korrekte Baumansichtssymbole**|**Falsche Baumansichtssymbole**|
|![Korrektes Baumansichtssymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404-11_TreeViewCorrect1") Symbol für die ![korrekte Strukturansicht &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Falsches Baumansichtssymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![Falsches Baumansichtssymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Stildetails

#### <a name="layout"></a>Layout
 Stapelelemente, wie für Standard 16x16-Symbole gezeigt:

 ![Layoutstack für 16x16-Symbole](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404-15_LayoutStack")

 **Layoutstack für 16x16-Symbole**

 Statusbenachrichtigungselemente werden besser als eigenständige Symbole verwendet. Es gibt jedoch Kontexte, in denen eine Benachrichtigung auf dem Basiselement gestapelt werden soll, z. B. mit dem Symbol "Task Complete":

 ![Eigenständige Benachrichtigungen in Visual Studio](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")

 **Eigenständige Benachrichtigungssymbole**

 ![Symbol für abgeschlossene Aufgabe](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404-17_TaskComplete")

 **Task Complete-Symbol**

 Projektsymbole sind in der Regel .ico-Dateien, die mehrere Größen enthalten. Die meisten 16x16-Symbole enthalten dieselben Elemente. Die 32x32-Versionen enthalten weitere Details, einschließlich des projekttyps, falls zutreffend.

 ![Projektsymbole in Visual Studio](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")

 **VB Windows Control Library Projektsymbole, 16 x 16 und 32 x 32**

 Zentrieren Sie ein Symbol innerhalb des Pixelrahmens. Wenn dies nicht möglich ist, richten Sie das Symbol nach oben und/oder rechts des Rahmens aus.

 ![Innerhalb des Pixelframes zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404-19_IconCentered")

 **Innerhalb des Pixelframes zentriertes Symbol**

 ![Am Pixelframe oben rechts ausgerichtetes Symbol](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404-20_IconTopRight")

 **Symbol, das oben rechts im Rahmen ausgerichtet ist**

 ![Am Pixelframe oben rechts ausgerichtetes und zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404-21_IconTopAlign")

 **Symbol zentriert und am oberen Rand des Rahmens ausgerichtet**

 Um eine optimale Ausrichtung und Balance zu erreichen, vermeiden Sie es, das Basiselement des Symbols mit Aktionsglyphen zu behindern. Platzieren Sie die Glyphe in der Nähe der oberen linken Seite des Basiselements. Berücksichtigen Sie beim Hinzufügen eines zusätzlichen Elements die Ausrichtung und den Saldo des Symbols.

|||
|-|-|
|**Korrekte Ausrichtung und Balance**|**Falsche Ausrichtung und Balance**|
|![Richtige Symbolverteilung und -ausrichtung](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Falsche Symbolverteilung und -ausrichtung](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Stellen Sie die Größenparität für Symbole sicher, die Elemente gemeinsam verwenden und in Sätzen verwendet werden. Beachten Sie, dass bei der falschen Kopplung Kreis und Pfeil überdimensioniert sind und nicht übereinstimmen.

|||
|-|-|
|**Korrekte Größenparität**|**Falsche Größenparität**|
|![Richtige Symbolgröße und -parität](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Falsche Symbolgröße und -parität](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Verwenden Sie konsistente Linien- und visuelle Gewichtungen. Bewerten Sie anhand eines Vergleichs, wie das Symbol, das Sie erstellen, mit anderen Symbolen verglichen wird. Verwenden Sie niemals den gesamten 16x16 Rahmen, verwenden Sie 15x15 oder kleiner. Das negative Verhältnis zu -positiv (dunkel-licht) sollte 50/50 betragen.

|||
|-|-|
|**Korrektes Negativ-Positiv-Verhältnis**|**Falsches Negativ-Positiv-Verhältnis**|
|![Korrektes visuelles Gewicht für Symbole &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Korrektes visuelles Gewicht für Symbole &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Korrektes visuelles Gewicht für Symbole &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Falsche optische Gewichtung für Symbole](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Verwenden Sie einfache, vergleichbare Formen und komplementäre Winkel, um Ihre Elemente zu erstellen, ohne die Elementintegrität zu opfern. Verwenden Sie nach Möglichkeit 45° oder 90° Winkel.

 ![Richtige Symbolwinkel](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektive
 Halten Sie das Symbol klar und verständlich. Verwenden Sie Perspektive und eine Lichtquelle nur bei Bedarf. Obwohl die Verwendung von Perspektivelementen für Symbolelemente vermieden werden sollte, sind einige Elemente ohne sie nicht erkennbar. In solchen Fällen vermittelt eine stilisierte Perspektive die Klarheit des Elements.

 ![3&#45;-Punkte-Perspektive](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404-31_3PointPerspective")

 **3-Punkt-Perspektive**

 ![1&#45;-Punkte-Perspektive](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404-32_1PointPerspective")

 **1-Punkt-Perspektive**

 Die meisten Elemente sollten nach rechts gerichtet oder abgewinkelt sein.

 ![Symbole rechts angeschrägt](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404-33_AngledRight")

 Verwenden Sie Lichtquellen nur, wenn Sie einem Objekt die erforderliche Klarheit hinzufügen.

|||
|-|-|
|**Korrekte Lichtquelle**|**Falsche Lichtquelle**|
|![Richtige Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Falsche Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Verwenden Sie Umrisse nur, um die Lesbarkeit zu verbessern oder die Metapher besser zu kommunizieren. Die negativ-positive (dunkellichtige) Waage sollte 50/50 betragen.

|||
|-|-|
|**Korrekte Verwendung von Umrissen**|**Falsche Verwendung von Umrissen**|
|![Richtige Konturen](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404-36_OutlinesCorrect")|![Falsche Konturen](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Icon-Typen
 **Shell- und Befehlsleistensymbole** bestehen aus nicht mehr als drei der folgenden Elemente: einer Basis, einem Modifikator, einer Aktion oder einem Status.

 ![Shell- und Befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404-38_ShellIcons")

 **Beispiele für Shell- und Befehlsleistensymbole**

 **Symbolfenster-Befehlsleistensymbole** bestehen aus nicht mehr als drei der folgenden Elemente: einer Basis, einem Modifikator, einer Aktion oder einem Status.

 ![Toolfenster-/Befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")

 **Beispiele für Symbolsymbole für Die Befehlsleiste des Werkzeugfensters**

 **Baumansichts-Disambiguatorsymbole** bestehen aus nicht mehr als drei der folgenden Elemente: einer Basis, einem Modifikator, einer Aktion oder einem Status.

 ![Strukturansichtsymbole (Begriffserklärung)](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404-40_TreeViewIcons")

 **Beispiele für Baumansichts-Disambiguatorsymbole**

 **Statusbasierte Werttaxonomiesymbole** sind in den folgenden Zuständen vorhanden: aktiv, aktiv deaktiviert und inaktiv deaktiviert.

 ![Status&#45;-basierten Taxonomiewertsymbolen](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")

 **Beispiele für statusbasierte Werttaxonomiesymbole**

 **IntelliSense-Symbole** bestehen aus nicht mehr als drei der folgenden Elemente: einer Basis, einem Modifikator und einem Status.

 ![IntelliSense-Symbole](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404-42_IntelliSenseIcons")

 **Beispiele für IntelliSense-Symbole**

 **Kleine (16x16) Projektsymbole** sollten nicht mehr als zwei Elemente enthalten: eine Basis und ein Modifikator.

 ![16 x 16 Projektsymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404-43_16x16Project1") ![16 x 16 Projektsymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404-44_16x16Project2") ![16 x 16 Projekt-Projektsymbol &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404-45_16x16Project3")

 **Beispiele für kleine (16x16) Projektsymbole**

 **Große (32x32) Projektsymbole** bestehen aus nicht mehr als vier der folgenden Elemente: einer Basis, einem bis zwei Modifikatoren und einer Sprachüberlagerung.

 ![Projektsymbol, 32x32](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404-46_32x32Project")

 **Beispiele für große (32x32) Projektsymbole**

### <a name="production-details"></a>Produktionsdetails
 Alle neuen UI-Elemente sollten mit Windows Presentation Foundation (WPF) erstellt werden, und alle neuen Symbole für WPF sollten im 32-Bit-PNG-Format vorliegen. Das 24-Bit-PNG ist ein älteres Format, das keine Transparenz unterstützt und daher nicht für Symbole empfohlen wird.

 Speichern Sie die Auflösung bei 96 DPI.

#### <a name="file-types"></a>Dateitypen

- **32-Bit-PNG:** das bevorzugte Format für Icons. Ein verlustfreies Datenkomprimierungsdateiformat, das ein einzelnes Rasterbild (Pixel) speichern kann. 32-Bit-PNG-Dateien unterstützen Alpha-Kanal-Transparenz, Gamma-Korrektur und Interlacing.

- **32-Bit-BMP:** für Nicht-WPF-Steuerelemente. Auch XP oder High Color genannt, ist 32-Bit-BMP ein RGB/A-Bildformat, ein True-Color-Bild mit alphakanaliger Transparenz. Der Alphakanal ist eine in Adobe Photoshop festgelegte Transparenzebene, die dann in der Bitmap als zusätzlicher (vierter) Farbkanal gespeichert wird. Während der Artwork-Produktion wird allen 32-Bit-BMP-Dateien ein schwarzer Hintergrund hinzugefügt, um einen schnellen visuellen Hinweis auf die Farbtiefe zu geben. Dieser schwarze Hintergrund stellt den Bereich dar, der in der Benutzeroberfläche maskiert werden soll.

- **32-Bit-ICO:** für Projektsymbole und Element hinzufügen. Alle ICO-Dateien sind 32-Bit true Color mit Alpha-Kanal-Transparenz (RGB/A). Da ICO-Dateien mehrere Größen und Farbtiefen speichern können, befinden sich Vista-Symbole häufig in einem ICO-Format, das 16x16, 32x32, 48x48 und 256x256 Bildgrößen enthält. Um im Windows Explorer korrekt angezeigt zu werden, müssen ICO-Dateien für jede Bildgröße auf 24-Bit- und 8-Bit-Farbtiefen gespeichert werden.

- **XAML:** für Entwurfsoberflächen und Windows-Adorner. XAML-Symbole sind vektorbasierte Bilddateien, die Skalierung, Drehen, Ablegen und Transparenz unterstützen. Sie sind heute in Visual Studio nicht üblich, werden aber aufgrund ihrer Flexibilität immer beliebter.

- **SVG**

- **24-Bit-BMP:** für die Visual Studio-Befehlsleiste. Ein true-Color-RGB-Bildformat, 24-Bit-BMP ist eine Symbolkonvention, die eine Transparenzebene erstellt, indem Magenta (R=255, G=0, B=255) als Farbschlüssel für eine Knock-out-Transparenzebene verwendet wird. In einem 24-Bit-BMP werden alle Magenta-Oberflächen mit der Hintergrundfarbe angezeigt.

- **24-Bit-GIF:** für die Visual Studio-Befehlsleiste. Ein true-Color-RGB-Bildformat, das Transparenz unterstützt. GIF-Dateien werden häufig in Wizard-Grafiken und GIF-Animationen verwendet.

### <a name="icon-construction"></a>Icon-Konstruktion
 Die kleinste Symbolgröße in Visual Studio ist 16x16. Die größte gemeinsame Verwendung ist 32x32. Denken Sie daran, beim Entwerfen eines Symbols nicht den gesamten 16x16-, 24x24- oder 32x32-Rahmen zu füllen. Legible, einheitliche Icon-Konstruktion ist wichtig für die Benutzererkennung. Halten Sie beim Erstellen von Symbolen die folgenden Punkte ein.

- Symbole sollten klar, verständlich und konsistent sein.

- Es ist besser, die Statusbenachrichtigungselemente als einzelne Symbole zu verwenden und sie nicht über ein Symbolbasiselement zu stapeln. In bestimmten Kontexten erfordert die Benutzeroberfläche möglicherweise, dass das Statuselement mit einem Basiselement gekoppelt wird.

- Projektsymbole sind in der Regel .ico Dateien, die mehrere Größen enthalten. Nur die Symbole 16x16, 24x24 und 32x32 werden aktualisiert. Die meisten 16x16- und 24x24-Symbole enthalten dieselben Elemente. Die 32x32-Symbole enthalten weitere Details, einschließlich des Projektsprachentyps, falls zutreffend.

- Bei 32x32-Symbolen haben die Basiselemente in der Regel eine Linienstärke von 2 Pixeln. Für Detailelemente kann eine Linienstärke von 1 oder 2 Pixeln verwendet werden. Verwenden Sie Ihr bestes Urteil, um festzustellen, welche besser geeignet ist.

- Haben Sie mindestens einen Abstand von 1 Pixel zwischen Elementen für 16x16 und 24x24 Symbole. Verwenden Sie für 32x32-Symbole den Abstand von 2 Pixeln zwischen Elementen und zwischen dem Modifikator und dem Basiselement.

  ![Elementabstand für Symbole der Größen 16x16, 24x24 und 32x32](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404-47_ElementSpacing")

  **Elementabstand für Symbole der Größen 16x16, 24x24 und 32x32**

#### <a name="color-and-accessibility"></a>Farbe und Zugänglichkeit
 Visual Studio-Konformitätsrichtlinien schreiben vor, dass alle Symbole im Produkt die Barrierefreiheitsanforderungen für Farbe und Kontrast erfüllen. Dies wird durch die Icon-Inversion erreicht, und wenn Sie entwerfen, sollten Sie sich bewusst sein, dass sie programmgesteuert im Produkt invertiert werden.

 Weitere Informationen zur Verwendung von Farbe in Visual Studio-Symbolen finden Sie unter [Verwenden von Farbe in Bildern](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Verwenden von Farbe in Bildern

### <a name="overview"></a>Übersicht
 Symbole in Visual Studio sind in erster Linie monochromatisch. Farbe ist reserviert, um spezifische Informationen zu vermitteln und nie für die Dekoration. Farbe wird verwendet:

- , um eine Aktion anzuzeigen

- , um den Benutzer auf eine Statusbenachrichtigung aufmerksam zu machen

- zur Benennung der Sprachzugehörigkeit

- um Elemente innerhalb von IntelliSense zu unterscheiden

### <a name="accessibility"></a>Barrierefreiheit
 Visual Studio-Konformitätsrichtlinien schreiben vor, dass alle in das Produkt eingecheckten Symbole die Barrierefreiheitsanforderungen für Farbe und Kontrast erfüllen. Farben in der visuellen Sprachpalette wurden getestet und erfüllen diese Anforderungen.

#### <a name="color-inversion-for-dark-themes"></a>Farbumkehr für dunkle Themen
 Damit Symbole mit dem richtigen Kontrastverhältnis im Visual Studio-Dunkeldesign angezeigt werden, wird eine Inversion programmgesteuert angewendet. Die Farben in diesem Handbuch wurden teilweise so gewählt, dass sie korrekt umkehren. Beschränken Sie die Verwendung von Farbe auf diese Palette, oder Sie erhalten unvorhersehbare Ergebnisse, wenn die Inversion angewendet wird.

 ![Beispiele für Symbole, deren Farben umgekehrt wurden](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405-01_DarkThemeInversion")

 **Beispiele für Symbole, deren Farben invertiert wurden**

### <a name="base-palette"></a>Basispalette
 Alle Standardsymbole enthalten drei Grundfarben. Symbole enthalten keine Farbverläufe oder Schlagschatten, mit einer oder zwei Ausnahmen für 3D-Werkzeugsymbole.

|Verwendung|Name|Wert (Lichtdesign)|Swatch|Beispiel|
|-----------|----------|---------------------------|------------|-------------|
|Hintergrund/Dunkel|VS BG|424242 / 66,66,66|![Muster 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![Beispiel für Basispalette](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405-02_BasePaletteExample")|
|Vordergrund/Licht|VS FG|F0EFF1 / 240,239,241|![Muster F0EFF1](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||
|Outline|VS-Aus|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||

 Zusätzlich zu den Grundfarben kann jedes Symbol eine zusätzliche Farbe aus der erweiterten Palette enthalten.

### <a name="extended-palette"></a>Erweiterte Palette

#### <a name="action-modifiers"></a>Aktionsmodifikatoren
 Die folgenden vier Farben geben die Arten von Aktionen an, die von Aktionsmodifikatoren benötigt werden:

|Verwendung|Name|Wert (alle Themen)|Swatch|
|-----------|----------|--------------------------|------------|
|Positiv|VS Action Green|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Negativ|VS Aktion Rot|A1260D / 161,38,13|![Muster A1260D](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|
|Neutral|VS Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Erstellen/Neu|VS Aktion Orange|C27D1A / 194,156,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Beispiele
 Grün wird für positive Aktionsmodifikatoren wie "Hinzufügen", "Ausführen", "Wiedergabe" und "Validieren" verwendet.

|||||
|-|-|-|-|
|![Run-Symbol](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **Ausführen**|![Execute query icon](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405-04_ExecuteQuery") **Execute Query**|![Alle Schritte symbol](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405-05_PlayAllSteps") **Alle Schritte abspielen**|![Steuerelementsymbol hinzufügen](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405-06_AddControl") **Steuerelement hinzufügen**|

 Rot wird für negative Aktionsmodifikatoren wie "Löschen", "Stopp", "Abbrechen" und "Schließen" verwendet.

|||||
|-|-|-|-|
|![Beziehungssymbol löschen](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405-07_DeleteRelationship") **Beziehung löschen**|![Spaltensymbol Löschen](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405-08_DeleteColumn") **Spalte löschen**|![Stopp-Abfragesymbol](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405-09_StopQuery") **Stop Query**|![Verbindungs-Offline-Symbol](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405-10_ConnectionOffline") **Verbindung Offline**|

 Blau wird auf neutrale Aktionsmodifikatoren angewendet, die am häufigsten als Pfeile dargestellt werden, z. B. "Öffnen", "Weiter", "Vorherige", "Importieren" und "Exportieren".

|||||
|-|-|-|-|
|![Zum Feldsymbol](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405-11_GoToField") **Gehe zu Feld**|![Batched Check&#45;in Icon](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405-12_BatchedCheckIn") **Batched Check-In**|![Adresseditor-Symbol](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405-13_AddressEditor") **Adresseditor**|![Assoziationseditor Icon](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405-14_AssociationEditor") **Association Editor**|

 Dunkles Gold wird hauptsächlich für den Modifikator "Neu" verwendet.

|||||
|-|-|-|-|
|![Neues Projektsymbol](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405-15_NewProject") **Neues Projekt**|![Neues Diagrammsymbol erstellen](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405-16_CreateNewGraph") **Neues Diagramm erstellen**|![Neues Komponententestsymbol](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405-17_NewUnitTest") **Neuer Komponententest**|![Neues Listenelementsymbol](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405-18_NewListItem") **Neues Listenelement**|

#### <a name="special-cases"></a>Spezialfälle
 In besonderen Fällen kann ein farbiger Aktionsmodifikator unabhängig voneinander als eigenständiges Symbol verwendet werden. Die für das Symbol verwendete Farbe spiegelt die Aktionen wider, denen das Symbol zugeordnet ist. Diese Verwendung ist auf eine kleine Teilmenge von Symbolen beschränkt, einschließlich:

||||||
|-|-|-|-|-|
|![Run-Symbol](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **Ausführen**|![Stopp-Symbol](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405-19_Stop") **Stop**|![Symbol löschen](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405-20_Delete") **Löschen**|![Speichern des Symbols](../../extensibility/ux-guidelines/media/0405-21-save.png "0405-21_Save") **Speichern**|![Navigieren zurück Symbol](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405-22_NavigateBack") **Navigieren Zurück**|

### <a name="code-hierarchy-palette"></a>Codehierarchiepalette

#### <a name="folder"></a>Ordner

|Verwendung|Name|Wert (alle Themen)|Swatch|Beispiel|
|-----------|----------|--------------------------|------------|-------------|
|Ordner|Ordner|DCB67A / 220,182,122|![Muster DCB67A](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![Symbol "Ordnerfarbe"](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio-Sprachen
 Jede der in Visual Studio verfügbaren allgemeinen Sprachen oder Plattformen hat eine zugeordnete Farbe. Diese Farben werden auf dem Basissymbol oder auf Sprachmodifikatoren verwendet, die in der oberen rechten Ecke von zusammengesetzten Symbolen angezeigt werden.

|Verwendung|Name|Wert (alle Themen)|Swatch|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Blau|0095D7 / 0,149,215|![Muster 0095D7](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|
|C++|CPP Lila|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|C#|CS Grün (VS Action Green)|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|CSS|CSS Rot|BD1E2D / 189,30,45|![Muster BD1E2D](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|
|F#|FS Purple|672878 / 103,40,120|![Muster 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241,100,33|![Muster F16421](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|
|VB|VB Blau (VS Aktion Blau)|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06 / 224,76,6|![Muster E04C06](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|
|Python|PY Green|879636 / 135,150,54|![Muster 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Beispiele für Symbole mit Sprachmodifizierern

|||||||
|-|-|-|-|-|-|
|![Visual Basic-Symbol](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405-25_VB") **VB**|![C&#35;-Symbol](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405-26_CSharp") **C#**|![C&#43;&#43; Symbol](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405-27_CPlusPlus") **C++**|![F&#35;-Symbol](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405-28_FSharp") **F#**|![JavaScript-Symbol](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405-29_JavaScript") **JavaScript**|![Python-Symbol](../../extensibility/ux-guidelines/media/0405-30-python.png "0405-30_Python") **Python**|
|![HTML-Symbol](../../extensibility/ux-guidelines/media/0405-31-html.png "0405-31_HTML") **HTML**|![WPF-Symbol](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405-32_WPF") **WPF**|![ASP-Symbol](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405-33_ASP") **ASP**|![CSS-Symbol](../../extensibility/ux-guidelines/media/0405-34-css.png "0405-34_CSS") **CSS**|![TypeScript-Symbol](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405-35_TypeScript") **TypeScript**||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense-Symbole verwenden eine exklusive Farbpalette. Diese Farben werden verwendet, um Benutzern zu helfen, schnell zwischen den verschiedenen Elementen in der IntelliSense-Popupliste zu unterscheiden.

|Verwendung|Name|Wert (alle Themen)|Swatch|
|-----------|----------|--------------------------|------------|
|Klasse, Ereignis|VS Aktion Orange|C27D1A / 194,125,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|
|Erweiterungsmethode, Methode, Modul, Delegat|VS Action Purple|652D90 / 101,45,144|![Muster 652D90](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|
|Feld, Enumerieren, Makro, Struktur, Union-Werttyp, Operator, Schnittstelle|VS Aktion Blau|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Object|VS Action Green|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Konstante, Ausnahme, Enum-Element, Karte, Map-Element, Namespace, Vorlage, Typdefinition|Hintergrund (VS BG)|424242 / 66,66,66|![Muster 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Beispiele für IntelliSense-Symbole

||||||
|-|-|-|-|-|
|![IntelliSense-Klassensymbolklasse](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405-36_IntelliSenseClass") **Class**|![IntelliSense privates Ereignissymbol](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent") **Privates Ereignis Privates Ereignis**|![IntelliSense-Delegatsymbol](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405-38_IntelliSenseDelegate") **Delegate**|![IntelliSense-Methode Freund-Symbol](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") **Methode Freund**|![Feldsymbol](../../extensibility/ux-guidelines/media/0405-40-field.png "0405-40_Field") **FeldFeld**|
|![IntelliSense protected Enum item icon](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem") **Protected Enum Item**|![IntelliSense-Objektsymbol](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405-42_IntelliSenseObject") **Objekt**|Vorlage **für** ![intelliSense-Vorlagen](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![IntelliSense Ausnahmeverknüpfungssymbol](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut") **Ausnahmeverknüpfung**||

### <a name="notifications"></a>Benachrichtigungen
 Benachrichtigungen in Visual Studio werden verwendet, um den Status anzuzeigen. Die Benachrichtigungspalette verwendet die folgenden vier Farben sowie Optionen für die Ausfüllung des Vordergrunds in Schwarz oder Weiß, um Benachrichtigungen mit den folgenden Statusebenen zu definieren.

|Verwendung|Name|Wert (alle Themen)|Swatch|
|-----------|----------|--------------------------|------------|
|Status: neutral|Benachrichtigung Blau (VS Blau)|1BA1E2 / 27,161,226|![Muster 1BA1E2](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|
|Status: positiv|Benachrichtigung Grün (VS Grün)|339933 / 51,153,51|![Muster 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|
|Status: negativ|Benachrichtigung Rot (VS Rot)|E51400 / 229,20,0|![Muster E51400](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|
|Status: Warnung|Benachrichtigung Gelb (VS Orange)|FFCC00 / 255,204,0|![Muster FFCC00](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|
|Vordergrundfüllung|Benachrichtigung Schwarz (Schwarz)|000000 / 0,0,0|![Swatch &#35;000000](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|
|Vordergrundfüllung|Benachrichtigung Weiß (Weiß)|FFFF / 255,255,255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Beispiele für Benachrichtigungssymbole

|||||
|-|-|-|-|
|![Warnungssymbol](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405-45_Alert") **Warnung**|![Warnsymbol](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405-48_Warning") **Warnung**|![Vollständiges Symbol](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405-46_Complete") **Komplett**|![Stopp-Symbol](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405-47_Stop") **Stop**|

### <a name="visual-studio-online"></a>Visual Studio Online
 Im Allgemeinen besteht Visual Studio Online aus Features, die in einem Browser gehostet werden. Die Farbe variiert in verschiedenen Umgebungen, aber der Stil bleibt gleich.

|Group|Verwendung|Name|Wert (alle Themen)|Swatch|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Hintergrund|TFSO BG|656565/ 101, 101, 101|![Muster 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|
|TFS|Outline|TFSO OUT|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Napa|Hintergrund|White|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Monaco|Hintergrund|White|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Hintergrund|White|FFFFFF / 255, 255, 255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Muster 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|
|F12|Darauf zeigen (Hover)|F12 Blue_Hover|2279BF / 34,121,191|![Muster 2279BF](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|
|F12|Disabled|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Muster ABABAC](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|
|F12|Hover-Hintergrund|Hover bg|D9EBF7 / 217,235,247|![Muster D9EBF7](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|
|F12|Gedrückter Hintergrund|Gepresst ebg|B2D7F0 / 178,215,240|![Muster B2D7F0](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|
|F12|Outline|VS OUT|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|
|F12|Information|Information|00BCF2 / 0,188,242|![Muster 00BCF2](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|
|F12|Warnung|Warnung|F28300 / 242,131,0|![Muster F28300](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|
|F12|Fehler / Negativ|Error_Negative|E81123 / 232,17,35|![Muster E81123](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|
|F12|Start / Positiv|Start_Positive|009E49 / 0,158,73|![Muster 009E49](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|
|F12|Break-Typ|Break-Typ|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|F12|Ereignismarke|Ereignismarke|A51F00 / 165,31,0|![Muster A51F00](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|
|F12|Benutzermarke|Benutzermarke|F16220 / 241,98,32|![Muster F16220](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Beispiele für Visual Studio Online-Symbole

|TFS Online||||
|----------------|-|-|-|
|![TFS Online-Teamsymbol](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405-49_TFSOnlineTeam") **Online Team**|![TFS-Informationssymbol](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405-50_TFSInformation") **Informationen**|![TFS-Verlaufssymbol](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405-51_TFSHistory") **Geschichte Geschichte**|![TFS-Zweigsymbol](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405-52_TFSBranch") **Branch**|

|Napa||||
|----------|-|-|-|
|![Napa-Inhaltssymbol](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405-53_NapaContent") **Inhalt**|![Napa Office Mail-Symbol](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405-54_NapaOfficeMail") **Office Mail**|![Napa SharePoint-Symbol](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405-55_NapaSharePoint") **SharePoint**|![Napa-Aufgabenbereich-Symbol](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405-56_NapaTaskPane") **Aufgabenbereich**|

|Monaco||||
|------------|-|-|-|
|![Monaco Dateien Symbol](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405-57_MonacoFiles") **Dateien**|![Monaco Git-Ikone](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405-58_MonacoGit") **Git**|![Monaco Suchsymbol](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405-59_MonacoSearch") **Suche**|![Monaco Textsymbol](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405-60_MonacoText") **Text**|

|F12||||
|---------|-|-|-|
|![F12 hübsche Code-Symbol](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405-61_F12PrettyCode") **Pretty Code**|![F12 Warnsymbol](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405-62_F12Warning") **Warnung**|![F12 Emulieren des Symbols](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405-63_F12Emulate") **Emulieren**|
