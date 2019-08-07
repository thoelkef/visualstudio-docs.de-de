---
title: Quellcode-Editor
description: Verwendung des Quellcode-Editors in Visual Studio für Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: d1ea74b4893032252d04ebe5fe5e65ca1eedaeeb
ms.sourcegitcommit: 9fc8b144d4ed1c46aba87c0b7e1d24454e0eea9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68493232"
---
# <a name="source-editor"></a>Quellcode-Editor

Ein zuverlässiger Quellcode-Editor ist entscheidend für kurzen und effizienten Code. Visual Studio für Mac bietet einen anspruchsvollen Quellcode-Editor, der das Herzstück der IDE darstellt. Der Quellcode-Editor stellt Features bereit, die Sie möglicherweise erwarten und benötigen, um Ihre Arbeit mühelos durchzuführen: von den Grundlagen wie der Syntaxhervorhebung, über Codeausschnitte und der Codefaltung, bis hin zu den Vorteilen der Roslyn-Compilerintegration wie eine voll funktionale IntelliSense-Codevervollständigung.

Der Quellcode-Editor in Visual Studio für Mac funktioniert problemlos mit allen anderen Funktionen der IDE, z.B. dem Debuggen, der Umgestaltung und der Integration der Versionskontrolle.

In diesem Artikel werden die wichtigsten Funktionen des Quellcode-Editors eingeführt, und es wird erklärt, wie Sie Visual Studio für Mac so effektiv wie möglich verwenden können.

## <a name="the-source-editor-experience"></a>Benutzeroberfläche des Quellcode-Editors

Die Fähigkeit, den Code anzuzeigen und sich schnell darin bewegen zu können, ist wesentlich für den Entwicklungsworkflow. Wie Sie den Code anzeigen und verwalten, ist eine persönliche Entscheidung, die sich je nach Entwickler und Projekt unterscheidet.

Visual Studio für Mac bietet viele leistungsstarke Funktionen, mit denen die plattformübergreifende Entwicklung zugänglich und so übersichtlich wie möglich gestaltet wird. In den folgenden Abschnitten werden einige der Highlights beschrieben.

## <a name="code-folding"></a>Codefaltung

Die Codefaltung erleichtert das Verwalten großer Quellcodedateien, da Entwickler vollständige Codeabschnitte wie using-Direktiven, Codebausteine und -kommentare und #region-Anweisungen anzeigen oder ausblenden können. Codefaltung ist in Visual Studio für Mac standardmäßig deaktiviert.

Navigieren Sie zum Aktivieren der Codefaltung zu **Visual Studio > Einstellungen > Text-Editor > Allgemein > Codefaltung**:

![Optionen für die Codefaltung](media/source-neweditor-image1.png)

Dieses Menü enthält auch eine Option zum standardmäßigen Falten von #regions und Kommentaren, wobei ein benannter Hinweis anstelle von Code angezeigt wird.

Verwenden Sie zum Anzeigen oder Ausblenden von Abschnitten das Anzeigewidget neben der Zeilennummer:

![Ein- oder Ausblenden von Abschnitten im Code](media/source-neweditor-image2.png)

Sie können auch über die Menüelemente **Ansicht > Faltung > Toggle Fold (Faltung umschalten)/Toggle All Folds (Alle Faltungen umschalten)** zwischen dem Ein- und Ausblenden der Faltungen wechseln:

![Menüelement „Faltung“](media/source-editor-image19.png)

Dieses Menüelement kann auch zur Aktivierung oder Deaktivierung der Codefaltung verwendet werden.

## <a name="word-wrap"></a>Zeilenumbruch

Der Zeilenumbruch kann Ihnen beim Verwalten des Platzes helfen, wenn Sie an langen Codezeilen oder mit eingeschränktem Anzeigeraum arbeiten. Der Zeilenumbruch kann ebenso sicherstellen, dass Ihre Codeansicht den vollständigen Inhalt Ihrer Quelldatei enthält, auch wenn Sie Bereiche öffnen, die Ihre Ansicht verdecken oder die Breite Ihrer Quellanzeige minimieren. 

Der Zeilenumbruch ist in der Standardeinstellung deaktiviert, kann jedoch über die **Einstellungen** in Visual Studio für Mac aktiviert werden. 

Aktivieren Sie den Zeilenumbruch, indem Sie zu **Visual Studio > Einstellungen > Text-Editor > Neuer Editor > Zeilenumbruch** navigieren.

![Optionen für den Zeilenumbruch](media/source-neweditor-wordwrap1.png)

Wenn der Zeilenumbruch aktiviert ist, werden Zeilen, die die Breite der Ansicht Ihres Quellcode-Editors überschreiten, automatisch in die nächste Zeile innerhalb Ihrer Quelldatei umgebrochen. Sie können auch eine Option aktivieren, mit deren Hilfe eine sichtbare Glyphe neben umgebrochenen Zeilen angezeigt wird. Dadurch können Sie zwischen Zeilen unterscheiden, die automatisch umgebrochen wurden, und Zeilen, für die Sie den Zeilenumbruch manuell durchgeführt haben.

![Umgebrochener Text mit aktiviertem Zeilenumbruch](media/source-neweditor-wordwrap2.png)

## <a name="ruler"></a>Lineal

Das Spaltenlineal ist sehr hilfreich für die Bestimmung von Zeilenlängen, insbesondere dann, wenn ein Team Vorgaben für die Zeilenlänge hat. Das Spaltenlineal kann aktiviert oder deaktiviert werden, indem Sie zu **Visual Studio > Einstellungen > Text-Editor > Markes and Rulers (Markierungen und Lineale)** navigieren und **Show Column ruler** (Spaltenlineal anzeigen) wie in der folgenden Abbildung gezeigt aktivieren (bzw. deaktivieren):

![Dialogfeld „Preferences“ (Einstellungen) mit aktiviertem Kontrollkästchen „Show column ruler“ (Spaltenlineal anzeigen)](media/source-editor-image5.png)

 Dadurch wird im Quellcode-Editor eine vertikale, hellgraue Linie angezeigt.

## <a name="highlight-identifier-references"></a>Hervorheben von Bezeichnerverweisen

Wenn die Option „Hervorheben von Bezeichnerverweisen“ aktiviert ist, können Sie jedes Symbol im Quellcode auswählen, und der Quellcode-Editor stellt eine visuelle Anleitung zu allen anderen Verweisen in dieser Datei bereit. Wechseln Sie zum Aktivieren dieser Option zu **Visual Studio > Einstellungen > Text-Editor > Markers and Rulers** (Markierungen und Lineale), und wählen Sie _Highlight identifier references_ (Bezeichnerverweise hervorheben) wie in der folgenden Abbildung gezeigt aus:

![Dialogfeld „Preferences“ (Einstellungen) mit markiertem Kontrollkästchen „Highlight identifier references“ (Hervorheben von Bezeichnerverweisen)](media/source-editor-image6.png)

Die Farbe der Hervorhebung ist auch hilfreich, wenn angegeben werden soll, dass etwas zugewiesen oder darauf verwiesen wird. Wenn etwas zugewiesen wird, wird es in Rot hervorgehoben. Wenn darauf verwiesen wird, ist die Hervorhebung blau:

![Beispiel für die Markierungsfarbe](media/source-editor-image7.png)

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors (Visual Studio unter Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Gliederung (Visual Studio unter Windows)](/visualstudio/ide/outlining)
