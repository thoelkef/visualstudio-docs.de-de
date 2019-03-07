---
title: 'Gewusst wie: Verwenden von XML-Ausschnitte'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4a56249c0a87b2516dc233818208f7c7c4b696e
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526216"
---
# <a name="how-to-use-xml-snippets"></a>Vorgehensweise: Verwenden von XML-Ausschnitten

Sie können XML-Ausschnitte aufrufen, indem Sie die folgenden zwei Befehle im Kontextmenü des XML-Editor verwenden. Die **Ausschnitt einfügen** Befehl wird den XML-Ausschnitt an der Cursorposition eingefügt. Die **Umschließen mit** Befehl dient als Wrapper für den XML-Ausschnitt für den ausgewählten Text. Jeder XML-Ausschnitt verfügt über definierte Ausschnitttypen. Die Ausschnitttypen bestimmen, ob der Ausschnitt mit verfügbar ist. die **Ausschnitt einfügen** Befehl aus, die **Umschließen mit** oder mit beiden Befehlen.

Nachdem dem Editor der XML-Ausschnitt hinzugefügt wurde, werden alle editierbaren Felder in den Ausschnitten in gelber Farbe hervorgehoben, und der Cursor wird auf dem ersten editierbaren Feld platziert.

## <a name="insert-snippet"></a>Ausschnitt einfügen

Die folgenden Verfahren wird beschrieben, wie Sie den Zugriff auf die **Ausschnitt einfügen** Befehl.

> [!NOTE]
> Die **Ausschnitt einfügen** Befehl steht auch über die Tastenkombination (**STRG**+**K**, klicken Sie dann **STRG** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>So fügen Sie Ausschnitte über das Kontextmenü ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Mit der rechten Maustaste, und wählen Sie **Ausschnitt einfügen**.

   Es wird eine Liste der verfügbaren XML-Ausschnitte angezeigt.

3. Wählen Sie einen Ausschnitt aus der Liste mit der Maus oder durch Eingabe des Namens der Codeausschnitt, und drücken **Registerkarte** oder **EINGABETASTE**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>So fügen Sie Ausschnitte über das IntelliSense-Menü ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Von der **bearbeiten** Startmenü **IntelliSense**, und wählen Sie dann **Ausschnitt einfügen**.

   Es wird eine Liste der verfügbaren XML-Ausschnitte angezeigt.

3. Wählen Sie einen Ausschnitt aus der Liste mit der Maus oder durch Eingabe des Namens der Codeausschnitt, und drücken **Registerkarte** oder **EINGABETASTE**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Zum Einfügen von Codeausschnitten in der Liste der IntelliSense-Wort vervollständigen

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Beginnen Sie mit dem Eingeben des XML-Ausschnitts, der der Datei hinzugefügt werden soll. Wenn die automatische Vervollständigung aktiviert ist, wird die Wort vervollständigen-Liste von IntelliSense angezeigt. Wenn es nicht angezeigt wird, drücken Sie die **STRG**+**Speicherplatz** aktivieren.

3. Wählen Sie den XML-Ausschnitt aus der Wort vervollständigen-Liste aus.

4. Drücken Sie **Registerkarte**, **Registerkarte** um den XML-Ausschnitt aufzurufen.

> [!NOTE]
> Möglicherweise können XML-Ausschnitte in einigen Fällen nicht aufgerufen werden. Wenn Sie z. B. versuchen, ein `xs:complexType`-Element innerhalb eines `xs:element`-Knotens einzufügen, generiert der Editor keinen XML-Ausschnitt. Wenn ein `xs:complexType`-Element innerhalb eines `xs:element`-Knotens verwendet wird, sind die erforderlichen Attribute oder Unterelemente nicht vorhanden, sodass der Editor über keine Daten zum Einfügen verfügt.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>So fügen Sie Ausschnitte mithilfe von Abkürzungsnamen ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Geben Sie im Editorbereich `<` ein.

3. Drücken Sie **Esc** , schließen Sie die IntelliSense-Liste Wort vervollständigen.

4. Geben Sie den Namen der Verknüpfung der Codeausschnitt, und drücken Sie **Registerkarte** um den XML-Ausschnitt aufzurufen.

## <a name="surround-with"></a>Umgeben mit

Die folgenden Verfahren wird beschrieben, wie Sie den Zugriff auf die **Umschließen mit** Befehl.

> [!NOTE]
> Die **Umschließen mit** Befehl steht auch über die Tastenkombination (**STRG**+**K**, klicken Sie dann **STRG** + **S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Umschließen mit aus dem Kontextmenü verwenden

1. Wählen Sie den Text an, in der XML-Editor umgeben.

2. Mit der rechten Maustaste, und wählen Sie **Umschließen mit**.

   Eine Liste der verfügbaren Umgeben mit-XML-Ausschnitte wird angezeigt.

3. Wählen Sie einen Ausschnitt aus der Liste mit der Maus oder durch Eingabe des Namens der Codeausschnitt, und drücken **Registerkarte** oder **EINGABETASTE**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Umschließen mit der IntelliSense-Menü verwenden

1. Wählen Sie den Text an, in der XML-Editor umgeben.

2. Von der **bearbeiten** Startmenü **IntelliSense**, und wählen Sie dann **Umschließen mit**.

   Eine Liste der verfügbaren Umgeben mit-XML-Ausschnitte wird angezeigt.

3. Wählen Sie einen Ausschnitt aus der Liste mit der Maus oder durch Eingabe des Namens der Codeausschnitt, und drücken **Registerkarte** oder **EINGABETASTE**.

## <a name="use-xml-snippets"></a>Verwenden von XML-Ausschnitten

Wenn Sie einen XML-Ausschnitt ausgewählt haben, wird der Text des Codeausschnitts automatisch an der Cursorposition eingefügt. Alle editierbaren Felder im Ausschnitt sind hervorgehoben, und das erste editierbare Feld wird automatisch markiert. Das aktuell markierte Feld ist geschachtelt.

Wenn ein Feld markiert ist, können Sie einen neuen Wert in das Feld eingeben. Drücken Sie **Registerkarte** durchläuft den editierbaren Felder des Ausschnitts; drücken **UMSCHALT**+**Registerkarte** navigieren Sie in umgekehrter Reihenfolge. Durch Klicken auf ein Feld wird der Cursor in diesem Feld platziert. Mit einem Doppelklick auf ein Feld wird dieses markiert. Wenn ein Feld hervorgehoben ist, kann eine QuickInfo angezeigt werden, die eine Beschreibung des Felds liefert.

Nur die erste Instanz des jeweiligen Feldes ist editierbar. Wenn dieses Feld hervorgehoben ist, sind die anderen Instanzen des Feldes mit einem Rahmen versehen. Wenn Sie den Wert eines editierbaren Feldes ändern, wird das Feld an allen Stellen im Ausschnitt geändert, an denen es verwendet wird.

Drücken Sie **EINGABETASTE** oder **Esc** feldbearbeitung beendet, und den Editor zurück in den normalen.

Die Standardfarben für editierbare können geändert werden, indem die **Codeausschnittfeld** festlegen in der **Schriftarten und Farben** im Bereich der **Optionen** Dialogfeld. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern der im Editor in Visual Studio 2017 verwendeten Schriftarten und Farben](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Siehe auch

- [XML-Ausschnitte](../xml-tools/xml-snippets.md)
- [Vorgehensweise: Generieren eines XML-Ausschnitts aus einem XML-schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Vorgehensweise: Erstellen von XML-Ausschnitten](../xml-tools/how-to-create-xml-snippets.md)