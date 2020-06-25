---
title: XAML-Code-Editor
description: Tour durch den XAML-Code-Editor in Visual Studio
ms.date: 06/16/2020
ms.topic: overview
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6421fd0139b04262ac5f1e835f010c1372c034ee
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329176"
---
# <a name="xaml-code-editor"></a>XAML-Code-Editor

Der XAML-Code-Editor in der [Visual Studio-IDE](../get-started/visual-studio-ide.md) enthält alle Tools, die Sie zum Erstellen von WPF-und UWP-Apps für die Windows-Plattform und [xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/)benötigen. In diesem Artikel werden sowohl die Rolle, die der Code-Editor bei der Entwicklung von XAML-basierten apps spielt, als auch die Features beschrieben, die für den XAML-Code-Editor in Visual Studio 2019 eindeutig sind.

Betrachten wir zunächst die IDE (integrierte Entwicklungsumgebung) mit einem geöffneten WPF-Projekt. Die folgende Abbildung zeigt einige der wichtigsten IDE-Tools, die Sie zusammen mit dem XAML-Code-Editor verwenden.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="Die Visual Studio 2019-IDE mit einem geöffneten WPF-Projekt in XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

Von der unteren linken Seite des Bilds im Uhrzeigersinn sind die wichtigsten IDE-Tools wie folgt:

- Das Fenster **[XAML-Code-Editor](#xaml-code-editor-ui)** &mdash; der Betreff dieses Artikels, &mdash; in dem Sie Ihren Code erstellen und bearbeiten.
- Das **[XAML-Designer](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** Fenster, in dem Sie die Benutzeroberfläche entwerfen.
- Das andockbare Fenster der **[Toolbox](../ide/reference/toolbox.md)** , in dem Sie der Benutzeroberfläche Steuerelemente hinzufügen können.
- Die Schaltfläche **[Debuggen](../debugger/debugger-feature-tour.md)** , auf der Sie den Code ausführen und Debuggen. <br>(Sie können den Code auch in Echtzeit bearbeiten, während Sie mit dem [XAML-Hot-Neuladen](xaml-hot-reload.md)Debuggen.)
- Das **[Projektmappen-Explorer](../ide/solutions-and-projects-in-visual-studio.md)** Fenster, in dem Sie Ihre Dateien, Projekte und Projektmappen verwalten.
- Das **[Eigenschaften](../ide/reference/properties-window.md)** Fenster, in dem Sie die Art und Weise ändern, wie die Benutzeroberfläche aussieht und wie die UI-Steuerelemente funktioniert.

Um den Vorgang fortzusetzen, erfahren Sie mehr über den XAML-Code-Editor.

## <a name="xaml-code-editor-ui"></a>Benutzeroberfläche des XAML-Code-Editors

Während das Code-Editor-Fenster für XAML-apps einige Benutzeroberflächen Elemente (Benutzeroberflächen Elemente) gemeinsam nutzen, die auch in unserer Standard-IDE angezeigt werden, enthält es auch einige einzigartige Features, die die Entwicklung von XAML-apps vereinfachen.

Hier sehen Sie das Fenster "XAML-Code-Editor".

![Das Fenster "XAML-Code-Editor" in Visual Studio](media/xaml-code-editor-window.png "Screenshot des Fensters "XAML-Code-Editor" in Visual Studio 2019")

Sehen wir uns nun die Funktionen der einzelnen Benutzeroberflächen Elemente im Code-Editor an.

### <a name="first-row"></a>Erste Zeile

In der ersten Zeile oben im XAML-Code Fenster gibt es links eine Registerkarte **Entwurf** , eine Schaltfläche zum **austauschen** von Bereichen, eine **XAML** -Registerkarte und eine **Aufklapp-XAML** -Schaltfläche.

![Die erste der beiden oberen Zeilen im XAML-Code-Editor-Fenster in Visual Studio, wobei die linke Seite der ersten Zeile hervorgehoben ist.](media/xaml-code-editor-top-row-left.png "Screenshot der ersten der beiden oberen Zeilen im XAML-Code-Editor-Fenster in Visual Studio 2019, in dem die Benutzeroberflächen Elemente auf der linken Seite hervorgehoben sind")

So funktioniert es:

- Auf der Registerkarte **Entwurf** wird der Fokus vom XAML-Code-Editor auf den XAML-Designer geändert.
- Die Schaltfläche Bereiche **austauschen** kehrt den Speicherort des XAML-Designer und den XAML-Code-Editor in der IDE um.
- Die Registerkarte " **XAML** " ändert den Fokus wieder in den XAML-Code-Editor.
- Die Schaltfläche **Pop out XAML** erstellt ein separates XAML-Code-Editor-Fenster, das sich außerhalb der IDE befindet.

Wenn Sie auf der rechten Seite fortfahren, gibt es eine **vertikale Trenn** Schaltfläche, eine **horizontale Trenn** **Schaltfläche und die Schaltfläche** Bereiche reduzieren.

![Die erste der beiden oberen Zeilen im XAML-Code-Editor-Fenster in Visual Studio, wobei die Rechte Seite der ersten Zeile hervorgehoben ist.](media/xaml-code-editor-top-row-right.png "Screenshot der ersten der beiden oberen Zeilen des Fensters "XAML-Code-Editor" in Visual Studio 2019, in dem Benutzeroberflächen Elemente auf der rechten Seite hervorgehoben sind")

So funktioniert es:

- Die **vertikale Trenn** Schaltfläche ändert den Speicherort der XAML-Designer und den XAML-Code-Editor in der IDE von der horizontalen Ausrichtung in eine vertikale Ausrichtung.
- Die **horizontale Trenn** Schaltfläche ändert den Speicherort der XAML-Designer und den XAML-Code-Editor in der IDE von einer vertikalen Ausrichtung in eine horizontale Ausrichtung.
- Mithilfe **der Schaltfläche** Bereich reduzieren können Sie die Elemente im unteren Bereich reduzieren, unabhängig davon, ob es sich um den Code-Editor oder den Designer handelt. (Um den unteren Bereich wiederherzustellen, wählen Sie die gleiche Schaltfläche erneut aus, die nun **die Schaltfläche** Erweiterungsbereich heißt.)

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Zweite Zeile

In der zweiten Zeile oben im XAML-Code Fenster gibt es zwei Dropdown Listen für Fenster. Wenn Sie jedoch die QuickInfo für diese Elemente der Benutzeroberfläche anzeigen, werden Sie als "Element: Window" und als "Member: Window" bezeichnet.

![Die zweite der beiden oberen Zeilen des XAML-Code-Editor Fensters in Visual Studio, in dem die Dropdown Listen der Fenster sichtbar sind.](media/xaml-code-editor-top-row-windows.png "Screenshot der zweiten der beiden oberen Zeilen des Fensters "XAML-Code-Editor" in Visual Studio 2019, in dem beide Dropdown Listen für Fenster sichtbar sind")

Die Dropdown Listen für das Fenster weisen verschiedene Funktionen auf, wie im folgenden dargestellt:

- Das-Element im linken **Fenster** Bereich unterstützt Sie beim Anzeigen und navigieren zu gleich geordneten oder übergeordneten Elementen.

  Insbesondere wird eine Gliederungs Ansicht angezeigt, in der die Tagstruktur des Codes angezeigt wird. Wenn Sie aus der Liste auswählen, wird der Fokus im Code-Editor in der Codezeile angezeigt, die das ausgewählte Element enthält.

    ![Das Element: Dropdown Liste des Fensters in Visual Studio](media/xaml-element-window-dropdown.png "Screenshot des Elements: Dropdown Liste "Fenster" in Visual Studio 2019")

- Das Element "Element **:** " auf der rechten Seite unterstützt Sie beim Anzeigen und navigieren zu Attributen oder untergeordneten Elementen.

    Insbesondere wird eine Liste der Eigenschaften im Code angezeigt. Wenn Sie aus der Liste auswählen, wird der Fokus im Code-Editor in der Codezeile angezeigt, die die ausgewählte Eigenschaft enthält.

    ![Die Dropdown Liste "Member: Window" in Visual Studio](media/xaml-member-window-dropdown.png "Screenshot der Dropdown Liste "Member: Window" in Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Mittlerer Bereich, Code-Editor

Der mittlere Bereich ist der "Code"-Teil des XAML-Code-Editors. Sie enthält die meisten Features, die Sie im [IDE-Code-Editor](../get-started/tutorial-editor.md)finden. Wir befassen uns mit einigen der universellen IDE-Features, die Ihnen bei der Entwicklung Ihres XAML-Codes helfen können. Außerdem werden die Features "Unique-to-XAML" in der IDE hervorgehoben.

![Der XAML-Code-Editor, nur mittlerer Bereich in Visual Studio](media/xaml-code-editor-middle.png "Screenshot des XAML-Code-Editors, nur mittlerer Bereich in Visual Studio 2019")

#### <a name="quick-actions"></a>Schnelle Aktionen

Mithilfe von [schnellen Aktionen](../ide/quick-actions.md) können Sie Code mit einer einzelnen Aktion umgestalten, generieren oder anderweitig ändern.

Beispielsweise können Sie mithilfe von schnellen Aktionen unnötige using-Direktiven aus dem c#-Code auf der Registerkarte **MainWindow.XAML.cs** **Entfernen** .

Gehen Sie dabei folgendermaßen vor:

1. Zeigen Sie auf eine using-Anweisung, wählen Sie das Glühbirnen Symbol aus, und wählen Sie dann unnötige using-Direktiven **Entfernen** aus der Dropdown Liste aus.

    ![Die Option "unnötige using-Direktiven entfernen" des IDE-Editors aus dem Menü "schnelle Aktionen"](media/xaml-code-editor-remove-usings.png "Screenshot der Option "unnötige using-Direktiven entfernen" des IDE-Editors im Menü "schnelle Aktionen"")

1. Wählen Sie aus, ob alle Vorkommen im **Dokument**, im Projekt oder in der **Projekt**Mappe behoben werden **sollen.**
1. Zeigen Sie das Dialogfeld **Vorschau** an, und wählen Sie dann **anwenden**aus.

Sie können auch über die Menüleiste auf dieses Feature zugreifen. Wählen Sie hierzu **Bearbeiten**  >  **IntelliSense**entfernen aus,  >  **und Sortieren**Sie using-Direktiven.

Weitere Informationen zu Benutzeroberflächen Einstellungen finden Sie auf der Seite zum [Sortieren](../ide/reference/sort-usings.md) von using-Direktiven. Weitere Informationen zu IntelliSense finden Sie auf der Seite [IntelliSense in Visual Studio](../ide/using-intellisense.md) . Weitere Informationen zu einigen der typischen Möglichkeiten, wie Entwickler schnelle Aktionen verwenden, finden Sie auf der Seite [Allgemeine schnell Aktionen](../ide/common-quick-actions.md) .

#### <a name="change-tracking"></a>Änderungsnachverfolgung

Durch die Farbe am linken Rand können Sie die Änderungen verfolgen, die Sie an einer Datei vorgenommen haben. Im folgenden wird erläutert, wie sich die Farben auf die von Ihnen ausgeführten Aktionen beziehen:

- Änderungen, die Sie seit dem Öffnen der Datei vorgenommen, jedoch nicht gespeichert haben, werden durch eine **gelbe** Leiste am linken Rand gekennzeichnet (auch als Auswahl Rand bezeichnet).

    ![Code-Editor mit gelber Leiste bearbeiten](media/code-editor-edit-yellow.png "Screenshot des Code-Editors mit einer Änderung, die im Auswahl Rand mit einer gelben Leiste markiert ist.")

- Nachdem Sie die Änderungen gespeichert haben (aber vor dem Schließen der Datei), wird die Leiste **grün**.

    ![Code-Editor mit grüner Leiste bearbeiten](media/code-editor-edit-green.png "Screenshot des Code-Editors mit einer Änderung, die im Auswahl Rand mit einem grünen Balken gekennzeichnet ist.")

Um diese Funktion zu deaktivieren und zu aktivieren, ändern Sie die Option **Änderungen nachverfolgen** in den Einstellungen des **Text-Editors** **(Extras**  >  **Optionen**  >  **Text-Editor**).

Weitere Informationen zur Änderungs Nachverfolgung &mdash; , um die Wellenlinien (auch als "Wellenlinien" bezeichnet) zu enthalten, die unter Code Zeichenfolgen angezeigt werden, finden Sie im &mdash; Abschnitt " **[Editor Features](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** " der [Features der Visual Studio-Code-Editor](../ide/writing-code-in-the-code-and-text-editor.md) -Seite.

#### <a name="right-click-context-menu"></a>Kontextmenü mit der rechten Maustaste klicken

Wenn Sie den Code im XAML-Code-Editor bearbeiten, können Sie über das Kontextmenü mit der rechten Maustaste auf Sie zugreifen. Die meisten dieser Features sind universell in der Visual Studio-IDE verfügbar, während einige für die Verwendung eines Code-Editors zusammen mit einem Entwurfs Fenster spezifisch sind.

![Mit der rechten Maustaste auf das Kontextmenü des XAML-Code-Editors in Visual Studio](media/xaml-code-editor-right-click-menu.png "Screenshot des Kontextmenüs des XAML-Code-Editors in Visual Studio 2019")

Die einzelnen Features und Ihre Vorteile sind:

- **Code anzeigen** : öffnet das Code Fenster der Programmiersprache, das in der Regel neben der Standardansicht angezeigt wird, die das Entwurfs Fenster und den XAML-Code-Editor enthält.
- **Ansicht-Designer** : öffnet die Standardansicht, die das Entwurfs Fenster und den XAML-Code-Editor enthält. (Wenn Sie sich bereits in der Standardansicht befinden, hat dies keine Auswirkungen.)
- **Schnell Aktionen und refactoren** : umfaktoren, generieren oder anderweitig ändern von Code mit einer einzelnen Aktion. Wenn Sie auf Code zeigen, sehen Sie ein Glühbirnen Symbol, wenn eine schnelle Aktion oder Umgestaltung verfügbar ist. <br>Siehe auch: [schnelle Aktionen](../ide/quick-actions.md) und [Umgestalten von Code](../ide/refactoring-in-visual-studio.md).
- **Umbenennen...** : Benennt nur Namespaces um. Wenn Sie keinen Namespace zum Umbenennen haben, erhalten Sie eine Fehlermeldung mit dem Hinweis, dass nur Namespace Präfixe umbenannt werden können.
- **Namespaces entfernen und Sortieren** : entfernt nicht verwendete Namespaces und sortiert dann die verbleibenden Namespaces.
- **Definition** einsehen: zeigt eine Vorschau der Definition eines Typs an, ohne die aktuelle Position im Editor zu belassen. <br>Siehe auch: Einsehen der [Definition](../ide/go-to-and-peek-definition.md#peek-definition) und [anzeigen und Bearbeiten von Code mithilfe der Peek-Definition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Gehe zu Definition** : navigiert zur Quelle eines Typs oder Members und öffnet das Ergebnis auf einer neuen Registerkarte. <br>Siehe auch: [Gehe zu Definition](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Umschließen mit...** -Verwenden Sie umschließende Code Ausschnitte, die um einen ausgewählten Codeblock erweitert werden. <br>Siehe auch: [Erweiterungs Ausschnitte und umschließende Code Ausschnitte](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Ausschnitt einfügen** : Fügt einen Code Ausschnitt an der Cursorposition ein.
- **Ausschneiden** -selbsterklärend
- Selbsterklärende **Kopie**
- **Einfügen** -selbsterklärend
- **Gliederung: erweitern** und reduzieren von Code Abschnitten. <br>Siehe auch: [Gliederung.](../ide/outlining.md)
- **Quell** Code Verwaltung: Anzeigen des Verlaufs von Code Beiträgen in ein Open Source-Repository.

### <a name="middle-pane-scroll-bar"></a>Mittlerer Bereich, Scrollleiste

Die Scrollleiste kann mehr als einen Bildlauf durch den Code ausführen. Sie können es auch verwenden, um einen anderen Code-Editor-Bereich zu öffnen. Außerdem können Sie die Bild Lauf Leiste verwenden, um den Code effizienter zu gestalten, indem Sie Anmerkungen hinzufügen oder andere Anzeigemodi verwenden.

#### <a name="split-the-code-window"></a>Teilen des Code Fensters

In der Bild Lauf Leiste des Code-Editors befindet sich oben rechts eine **Trenn** Schaltfläche. Wenn Sie diese Option auswählen, können Sie einen anderen Code-Editor-Bereich öffnen. Dies ist nützlich, da Sie unabhängig voneinander betrieben werden, sodass Sie Sie verwenden können, um an verschiedenen Speicherorten an Code zu arbeiten.

![Der XAML-Code-Editor, nur mittlerer Bereich in Visual Studio](media/code-editor-split-window-button.png "Screenshot des XAML-Code-Editors, nur mittlerer Bereich in Visual Studio 2019")

Weitere Informationen zum Aufteilen eines Editor Fensters finden Sie auf der Seite zum [Verwalten von Editor-Fenstern](../ide/how-to-manage-editor-windows.md) .

#### <a name="use-annotations-or-map-mode"></a>Verwenden von Anmerkungen oder eines Zuordnungs Modus

Sie können auch ändern, wie die Scrollleiste aussieht und welche zusätzlichen Features Sie enthält. Beispielsweise können viele Personen *Anmerkungen* in der Bild Lauf Leiste einschließen, die visuelle Hinweise wie Codeänderungen, Breakpoints, Lesezeichen, Fehler und Position der Einfügemarke bereitstellen.

Andere Benutzer schätzen die Verwendung des Zuordnungs *Modus*, in dem auf der Bild Lauf Leiste Codezeilen in Miniatur angezeigt werden. Entwickler, die über viel Code in einer Datei verfügen, werden möglicherweise feststellen, dass der Zuordnungs Modus für Codezeilen effektiver ist als die Standard Scrollleiste.

Weitere Informationen zum Ändern der Standardeinstellungen der Bild Lauf Leiste finden Sie auf der Seite Bild Lauf [Leiste anpassen](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) .

## <a name="xaml-specific-features"></a>XAML-spezifische Funktionen

Die meisten der folgenden Features sind universell in der Visual Studio-IDE verfügbar. es gibt jedoch einige Dimensionen, die die Codierung für XAML-Entwickler vereinfachen.

### <a name="xaml-code-snippets"></a>XAML-Code Ausschnitte

Code Ausschnitte sind kleine Blöcke von wiederverwendbarem Code, die Sie in eine Codedatei einfügen können, indem Sie mit der rechten Maustaste auf den Kontextmenü Befehl " **Ausschnitt einfügen** " oder eine Kombination aus Tastenkombinationen (**STRG** + **K**, **STRG** + **X**) klicken. Wir haben [IntelliSense](../ide/using-intellisense.md) verbessert, sodass XAML-Ausschnitte angezeigt werden, die sowohl für integrierte Code Ausschnitte als auch für alle benutzerdefinierten Code Ausschnitte funktionieren, die Sie manuell hinzufügen. Zu den Standard-XAML-Code Ausschnitten zählen `#region` , `Column definition` , `Row definition` , `Setter` und `Tag` .

![Der XAML-Code-Editor mit XAML-Code Ausschnitt Optionen in IntelliSense](media/xaml-code-snippets.png "Screenshot des XAML-Code-Editors mit XAML-Code Ausschnitt Optionen in IntelliSense")

Weitere Informationen finden Sie auf den Seiten [Code Ausschnitte](../ide/code-snippets.md) und [c#-Code Ausschnitte](../ide/visual-csharp-code-snippets.md) .

### <a name="xaml-region-support"></a>Unterstützung für XAML-#Region

Ab Visual Studio 2015 haben wir #Region-Unterstützung für XAML-Entwickler in WPF und UWP und vor kurzem auch in [xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/)zur Verfügung gestellt. In Visual Studio 2019 nehmen wir weiterhin inkrementelle Verbesserungen an #Region-Unterstützung vor. Beispielsweise werden in [Version 16,4](/visualstudio/releases/2019/release-notes-v16.4/) und höher #Region Optionen angezeigt, wenn Sie mit der typinstallation beginnen `<!` .

![Der XAML-Code-Editor mit #Region Optionen, die in IntelliSense angezeigt werden.](media/code-editor-xaml-region.png "Screenshot des XAML-Code-Editors mit #Region Optionen, die in IntelliSense angezeigt werden")

Sie können Regionen verwenden, wenn Sie Abschnitte des Codes gruppieren möchten, die Sie auch erweitern oder reduzieren möchten.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Weitere Informationen zu Regionen finden Sie auf der Seite [#Region (c#-Referenz)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) . Weitere Informationen zum Erweitern und reduzieren von Code Abschnitten finden Sie [auf der Seite](../ide/outlining.md) Gliederung.

### <a name="xaml-comments"></a>XAML-Kommentare

Entwickler bevorzugen häufig das dokumentieren Ihres Codes mithilfe von Kommentaren. Sie können dem XAML-Code, der sich auf der Registerkarte **MainWindow. XAML** befindet, Kommentare wie folgt hinzufügen:

- Geben Sie `<!--` vor einem Kommentar ein, und fügen Sie dann `-->` nach dem Kommentar hinzu.
- Geben Sie ein, `<!` und wählen Sie dann `!--` aus der Liste der Optionen aus.

  ![Der XAML-Code-Editor mit der rechten Maustaste auf Kommentare hinzufügen Dialog](media/xaml-code-editor-comments.png "Screenshot des Rechtsklick-Kontextmenüs zum Hinzufügen von Kommentaren im XAML-Code-Editor")

- Wählen Sie den Code aus, den Sie mit einem Kommentar umschließen möchten, und wählen Sie dann auf der Symbolleiste in der IDE die Schaltfläche **Kommentar** aus. Um die Aktion umzukehren, klicken Sie auf die Schaltfläche aus **Kommentar entfernen** .

  ![Die Kommentar Schaltfläche und die Auskommentierung der Schaltfläche aus der IDE](media/comment-undo-comment-buttons.png "Screenshot der Kommentar Schaltfläche und der Schaltfläche "auskommentieren" in der IDE-Symbolleiste")

- Wählen Sie den Code aus, den Sie mit einem Kommentar umschließen möchten, und drücken Sie dann **STRG** + **K**, **STRG** + **C**. Zum Aufheben der Auskommentierung von ausgewähltem Code drücken Sie **STRG** + **K**, **STRG** + **U**.

Weitere Informationen zur Verwendung von Kommentaren im c#-Code auf der Registerkarte **MainWindow.XAML.cs** finden Sie auf der Seite [Dokumentations Kommentare](/dotnet/csharp/language-reference/language-specification/documentation-comments/) .

### <a name="xaml-lightbulbs"></a>XAML-Glühbirnen

Glühbirnen Symbole, die in Ihrem XAML-Code angezeigt werden, sind Teil der [schnellen Aktionen](../ide/quick-actions.md) , die Sie zum umgestalten, generieren oder anderweitig ändern von Code verwenden können.

Hier finden Sie einige Beispiele dafür, wie Sie Ihre XAML-Codierungs Funktionen nutzen können:

- **Entfernen Sie unnötige Namespaces**. Im XAML-Code-Editor werden unnötige Namespaces in abgeblendet Text angezeigt. Wenn Sie den Cursor über eine unnötige Verwendung bewegen, wird eine Glühbirne angezeigt. Wenn Sie in der Dropdown Liste die Option **unnötige Namespaces entfernen** auswählen, wird eine Vorschau angezeigt, die Sie entfernen können.

  ![Die Option "unnötige Namespaces entfernen" des XAML-Code-Editors aus der schnell Aktionen-Glühbirne](media/xaml-code-editor-dimmed-namespaces-preview.png "Screenshot der Option "unnötige Namespaces entfernen" des XAML-Code-Editors, die mithilfe der schnell Aktionen-Glühbirne angezeigt wird")

- **Benennen Sie den Namespace**um. Diese Funktion, die über das Kontextmenü verfügbar ist, nachdem Sie einen Namespace hervorgehoben haben, vereinfacht das gleich einmalige ändern mehrerer Instanzen einer Einstellung. Sie können auch auf diese Funktion zugreifen, indem Sie die Menü **Edit**Leiste verwenden,  >  **Refactor**  >  **Umbenennungen**bearbeiten oder **STRG** + **r**drücken und dann erneut **STRG** + **r** drücken.

  ![Die Option "Namespace umbenennen" im XAML-Code-Editor über das Kontextmenü (Rechtsklick)](media/code-editor-rename-namespace.png "Screenshot der Option "Namespace umbenennen" im XAML-Code-Editor, die über das Kontextmenü angezeigt wird.")

  Weitere Informationen finden Sie auf der Seite [Umbenennen eines Code Symbols](../ide/reference/rename.md) .

### <a name="conditional-xaml-for-uwp"></a>Bedingte XAML für UWP

Bedingtes XAML bietet eine Möglichkeit, die Methode [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) in XAML-Markup zu verwenden. Sie sind damit in der Lage, im Markup nur dann Eigenschaften festzulegen und Objekte zu initialisieren, wenn die entsprechende API vorhanden ist, ohne CodeBehind zu verwenden.

Weitere Informationen finden Sie auf der Seite [bedingte XAML](/windows/uwp/debug-test-perf/conditional-xaml/) und auf der Seite [mit den UWP-XAML-Steuerelementen auf der Desktop-App (XAML-Inseln)](/windows/apps/desktop/modernize/xaml-islands/) .

### <a name="xaml-structure-visualizer"></a>XAML-Struktur Schnellansicht

Die Funktion "Struktur Schnellansicht" im Code-Editor zeigt Struktur-Führungslinien, bei denen es sich um vertikal gestrichelte Linien handelt, die die übereinstimmenden geöffneten und geschlossenen Tagelemente in Ihrem Code angeben. Diese vertikalen Linien vereinfachen das Starten und beenden logischer Blöcke.

Weitere Informationen finden Sie auf der [Codepage Navigate](../ide/navigating-code.md) .

### <a name="intellicode-for-xaml"></a>Intellicode für XAML

Wenn Sie Ihrem Code ein XAML-Tag hinzufügen, beginnen Sie in der Regel mit einer öffnende spitze Klammer `<` . Wenn Sie diese Spitze Klammer eingeben, wird ein intellicode-Menü angezeigt, in dem mehrere der beliebtesten XAML-Tags aufgeführt sind. Wählen Sie die Option aus, die Sie dem Code schnell hinzufügen möchten.

Sie können die intellicode-Auswahl erkennen, da Sie oben in der Liste angezeigt werden und angezeigt werden.

![Die intellicode-Liste für den XAML-Text-Editor](media/xaml-intellicode-selection.png "Screenshot der intellicode-Liste für den XAML-Text-Editor")

Weitere Informationen finden Sie auf der Seite [Übersicht über intellicode](/visualstudio/intellicode/overview/) .

### <a name="settings"></a>Einstellungen

Weitere Informationen zu *allen* Einstellungen in der Visual Studio-IDE finden Sie auf der Seite [mit den Funktionen der Code-Editor](../ide/writing-code-in-the-code-and-text-editor.md) -Seite.

## <a name="xaml-optional-settings"></a>Optionale XAML-Einstellungen

Mit dem Dialogfeld [Optionen](../ide/reference/options-dialog-box-visual-studio.md) können Sie die Standardeinstellungen für den XAML-Code-Editor ändern. **Wählen Sie**Extras  >  **Optionen**  >  **Text-Editor**  >  **XAML**aus, um die Einstellungen anzuzeigen.

![Die Options Liste für den XAML-Text-Editor](media/xaml-tools-options.png "Screenshot der Options Liste für den XAML-Text-Editor")

> [!NOTE]
> Mithilfe von Tastenkombinationen können Sie auch auf das Dialogfeld Optionen zugreifen. Beispiel: Drücken Sie **STRG** + **Q** , um die IDE zu durchsuchen, geben Sie **Optionen**ein, und drücken Sie dann die **Eingabe**Taste. Drücken Sie als nächstes **STRG** + **E** , um das Dialogfeld Optionen zu durchsuchen, **Text-Editor**einzugeben, **Eingabe**Taste zu drücken, **XAML**einzugeben und dann die **Eingabe**Taste zu drücken.
>  
> Weitere Informationen zu Tastenkombinationen finden Sie auf der Seite mit den Verknüpfungs [Tipps für Visual Studio](../ide/productivity-shortcuts.md#code-editor) .

### <a name="universal-text-editor-options"></a>Universelle Text-Editor-Optionen

Im Dialogfeld [Optionen](../ide/reference/options-text-editor-xaml-formatting.md) für XAML sind die folgenden ersten drei Elemente für alle Programmiersprachen universell, die von der Visual Studio-IDE unterstützt werden. Weitere Informationen zu diesen Optionen und ihrer Verwendung finden Sie in den verknüpften Informationen in der folgenden Tabelle.

|name  |Weitere Informationen  |
|---------|---------|
|Allgemein  | [Dialogfeld "Optionen": Text-Editor > alle Sprachen](../ide/reference/options-text-editor-all-languages.md) |
|Bildlaufleisten | [Optionen, Text-Editor, Alle Sprachen, Scrollleisten](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Registerkarten  |  [Optionen, Text-Editor, Alle Sprachen, Registerkarten](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>XAML-spezifische Text-Editor-Optionen

In der folgenden Tabelle sind die Einstellungen im Dialogfeld [Optionen](../ide/reference/options-text-editor-xaml-formatting.md) aufgeführt, mit denen Sie die Bearbeitungsumgebung bei der Entwicklung von XAML-basierten apps verbessern können. Weitere Informationen zu diesen Optionen und ihrer Verwendung finden Sie in den verknüpften Informationen.

|name  |Weitere Informationen  |
|---------|---------|
|Formatierung | [Optionen, Text-Editor, XAML, Formatierung](../ide/reference/options-text-editor-xaml-formatting.md) |
|Sonstiges |  [Optionen, Text-Editor, XAML, Sonstiges](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> Die Einstellung für den **Namen der Ereignishandler-Methode Großbuchstaben** im Abschnitt **Verschiedenes** ist besonders nützlich für XAML-Entwickler. Diese Einstellung ist standardmäßig deaktiviert, da Sie neu ist, aber es wird empfohlen, dass Sie Sie *auf on* festlegen, um die korrekte Groß-/Kleinschreibung im Code zu unterstützen. *off*

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen dazu, wie Sie Ihren Code in Echtzeit bearbeiten, während Sie Ihre APP im Debugmodus ausführen, finden Sie auf der Seite zum aktiven [Laden von XAML](xaml-hot-reload.md) .

## <a name="see-also"></a>Siehe auch

- [Visual Studio Code-Editor-Funktionen](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML in UWP-Apps](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML in Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)
- [Xamarin-Mobile App Entwicklung (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 für Mac-IDE-Tour (Mac)](/visualstudio/mac/ide-tour/)
