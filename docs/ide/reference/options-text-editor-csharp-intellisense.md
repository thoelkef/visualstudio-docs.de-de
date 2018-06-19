---
title: Optionen, Text-Editor, C#, IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d8f6928dd09b971e2c5924d34058a1a0d5e28394
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947390"
---
# <a name="options-text-editor-c-intellisense"></a>Optionen, Text-Editor, C#, IntelliSense

Verwenden Sie die Optionsseite von **IntelliSense**, um Einstellungen zu ändern, die das Verhalten von IntelliSense für C# beeinflussen. Wenn Sie auf die Optionsseite zugreifen möchten, klicken Sie auf **Extras** > **Optionen** und anschließend auf **Text-Editor** > **C#** > **IntelliSense**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

Die Optionsseite **IntelliSense** enthält folgende Optionen:

## <a name="completion-lists"></a>Vervollständigungslisten

- Vervollständigungsliste nach Eingabe des ersten Zeichens anzeigen*

   Wenn diese Option aktiviert ist, zeigt IntelliSense automatisch die Vervollständigungsliste an, wenn Sie mit der Eingabe beginnen. Wenn diese Option nicht aktiviert ist, ist die IntelliSense-Vervollständigung trotzdem über das Menü **IntelliSense** oder durch Drücken von **STRG**+**LEERTASTE** verfügbar.

- Vervollständigungsliste nach Löschen eines Zeichens anzeigen

- Übereinstimmende Teile der Vervollständigungslistenelemente hervorheben

- Show completion list filters (Filter für die Vervollständigungsliste anzeigen)

- Show name suggestions (Namensvorschläge anzeigen)

### <a name="snippets-behavior"></a>Ausschnittverhalten

- Ausschnitte nie einschließen

   Wenn diese Option aktiviert ist, fügt IntelliSense keine Aliase für C#-Codeausschnitte zur Vervollständigungsliste hinzu.

- Ausschnitte immer einschließen

   Wenn diese Option aktiviert ist, fügt IntelliSense Aliase für C#-Codeausschnitte zur Vervollständigungsliste hinzu. Im Fall, dass das Codausschnitt-Alias mit dem Schlüsselwort, z.B. [class](/dotnet/csharp/language-reference/keywords/class) übereinstimmt, wird das Schlüsselwort durch die Verknüpfung ersetzt. Weitere Informationen finden Sie unter [Visual C#-Codeausschnitte](../../ide/visual-csharp-code-snippets.md).

- Ausschnitte einschließen, wenn ?-TAB nach einem Bezeichner eingegeben wird

   Wenn diese Option aktiviert ist, fügt IntelliSense Aliase für C#-Codeausschnitte zur Vervollständigungsliste hinzu, wenn **?**+**TAB-TASTE** nach einem Bezeichner gedrückt wird.

### <a name="enter-key-behavior"></a>Verhalten der EINGABETASTE

- Nie neue Zeile beim Drücken der EINGABETASTE einfügen

   Wenn diese Option aktiviert ist, wird nie automatisch eine neue Zeile hinzugefügt, nachdem ein Element in der Vervollständigungsliste ausgewählt und die **EINGABETASTE** gedrückt wird.

- Neue Zeile beim Drücken der EINGABETASTE nur nach einem vollständig eingegebenen Wort einfügen

   Gibt an, dass nach Eingabe aller Zeichen für einen Eintrag in die Vervollständigungsliste und Drücken der **EINGABETASTE** automatisch eine neue Zeile hinzugefügt wird und der Cursor zur neuen Zeile springt.

   Wenn Sie beispielsweise `else` eingeben und anschließend die **EINGABETASTE** drücken, erscheint Folgendes im Editor:

   `else`

   `|` (Cursorplatzierung)

   Wenn Sie allerdings nur `el` eingeben und anschließend die **EINGABETASTE** drücken, erscheint Folgendes im Editor:

   `else|` (Cursorplatzierung)

- Immer neue Zeile beim Drücken der EINGABETASTE einfügen

   Gibt an, dass nach Eingabe *aller* Zeichen für einen Eintrag in der Vervollständigungsliste und Drücken der **EINGABETASTE** automatisch eine neue Zeile erstellt wird und der Cursor zur neuen Zeile springt.

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
- [Verwenden von IntelliSense](../../ide/using-intellisense.md)