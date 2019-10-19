---
title: Verwenden von XML-Ausschnitten
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 163fcddb8553da39b035e649155e04c3da4b430e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601794"
---
# <a name="how-to-use-xml-snippets"></a>Gewusst wie: Verwenden von XML-Ausschnitten

Sie können XML-Ausschnitte aufrufen, indem Sie die folgenden beiden Befehle im Kontextmenü des XML-Editors verwenden. Der Befehl **Ausschnitt einfügen** fügt den XML-Code Ausschnitt an der Cursorposition ein. Der Befehl **Umschließen mit** umschließt den XML-Code Ausschnitt um den markierten Text. Jeder XML-Ausschnitt verfügt über definierte Ausschnitttypen. Die Ausschnitt Typen bestimmen, ob der Ausschnitt mit dem Befehl **Ausschnitt einfügen** , dem Befehl **Umschließen mit** oder beidem verfügbar ist.

Nachdem dem Editor der XML-Ausschnitt hinzugefügt wurde, werden alle editierbaren Felder in den Ausschnitten in gelber Farbe hervorgehoben, und der Cursor wird auf dem ersten editierbaren Feld platziert.

## <a name="insert-snippet"></a>Ausschnitt einfügen

In den folgenden Prozeduren wird beschrieben, wie Sie auf den Befehl **Ausschnitt einfügen** zugreifen.

> [!NOTE]
> Der Befehl **Ausschnitt einfügen** ist auch über die Tastenkombination (**STRG** +**K**, dann **STRG** +**X**) verfügbar.

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>So fügen Sie Ausschnitte über das Kontextmenü ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Klicken Sie mit der rechten Maustaste, und wählen Sie **Ausschnitt einfügen**aus.

   Es wird eine Liste der verfügbaren XML-Ausschnitte angezeigt.

3. Wählen Sie mit der Maus einen Ausschnitt aus der Liste aus, oder geben Sie den Namen des Ausschnitts ein, und drücken Sie die **Tab** -Taste oder die **Eingabe**Taste.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>So fügen Sie Ausschnitte über das IntelliSense-Menü ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Zeigen Sie im Menü **Bearbeiten** auf **IntelliSense**, und wählen Sie **Ausschnitt einfügen**aus.

   Es wird eine Liste der verfügbaren XML-Ausschnitte angezeigt.

3. Wählen Sie mit der Maus einen Ausschnitt aus der Liste aus, oder geben Sie den Namen des Ausschnitts ein, und drücken Sie die **Tab** -Taste oder die **Eingabe**Taste.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>So fügen Sie Ausschnitte durch die IntelliSense-Liste "Wort vervollständigen" ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Beginnen Sie mit dem Eingeben des XML-Ausschnitts, der der Datei hinzugefügt werden soll. Wenn die automatische Vervollständigung aktiviert ist, wird die Wort vervollständigen-Liste von IntelliSense angezeigt. Wenn Sie nicht angezeigt wird, drücken Sie **STRG** +**LEERTASTE** , um Sie zu aktivieren.

3. Wählen Sie den XML-Ausschnitt aus der Wort vervollständigen-Liste aus.

4. Drücken Sie **Tab**, **Tab** , um den XML-Ausschnitt aufzurufen.

> [!NOTE]
> Möglicherweise können XML-Ausschnitte in einigen Fällen nicht aufgerufen werden. Wenn Sie z. B. versuchen, ein `xs:complexType`-Element innerhalb eines `xs:element`-Knotens einzufügen, generiert der Editor keinen XML-Ausschnitt. Wenn ein `xs:complexType`-Element innerhalb eines `xs:element`-Knotens verwendet wird, sind die erforderlichen Attribute oder Unterelemente nicht vorhanden, sodass der Editor über keine Daten zum Einfügen verfügt.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>So fügen Sie Ausschnitte mithilfe von Abkürzungsnamen ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Geben Sie im Editorbereich `<` ein.

3. Drücken Sie **ESC** , um die Liste IntelliSense Complete Word zu schließen.

4. Geben Sie den Verknüpfungs Namen des Ausschnitts ein, und drücken Sie die **Tab** -Taste, um den XML-Ausschnitt aufzurufen.

## <a name="surround-with"></a>Umgeben mit

In den folgenden Verfahren wird beschrieben, wie Sie auf den Befehl **Umschließen mit** zugreifen.

> [!NOTE]
> Der Befehl **Umschließen mit** ist auch über die Tastenkombination (**STRG** +**K**, dann **STRG** +**S**) verfügbar.

### <a name="to-use-surround-with-from-the-context-menu"></a>So verwenden Sie "umgeben mit" über das Kontextmenü

1. Wählen Sie den Text aus, der im XML-Editor umschließt werden soll

2. Klicken Sie mit der rechten Maustaste, und wählen Sie **umgeben mit**

   Eine Liste der verfügbaren Umgeben mit-XML-Ausschnitte wird angezeigt.

3. Wählen Sie mit der Maus einen Ausschnitt aus der Liste aus, oder geben Sie den Namen des Ausschnitts ein, und drücken Sie die **Tab** -Taste oder die **Eingabe**Taste.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>So verwenden Sie "umschließen mit" über das IntelliSense-Menü

1. Wählen Sie den Text aus, der im XML-Editor umschließt werden soll

2. Zeigen Sie im Menü **Bearbeiten** auf **IntelliSense**, und wählen Sie dann **Umschließen mit**aus.

   Eine Liste der verfügbaren Umgeben mit-XML-Ausschnitte wird angezeigt.

3. Wählen Sie mit der Maus einen Ausschnitt aus der Liste aus, oder geben Sie den Namen des Ausschnitts ein, und drücken Sie die **Tab** -Taste oder die **Eingabe**Taste.

## <a name="use-xml-snippets"></a>Verwenden von XML-Ausschnitten

Wenn Sie einen XML-Ausschnitt ausgewählt haben, wird der Text des Codeausschnitts automatisch an der Cursorposition eingefügt. Alle editierbaren Felder im Ausschnitt sind hervorgehoben, und das erste editierbare Feld wird automatisch markiert. Das aktuell markierte Feld ist geschachtelt.

Wenn ein Feld markiert ist, können Sie einen neuen Wert in das Feld eingeben. Durch Drücken der **Tab** -Taste durch die bearbeitbaren Felder des Code Ausschnitts durch Drücken der **UMSCHALT** +**Registerkarte** werden Sie in umgekehrter Reihenfolge durchlaufen Durch Klicken auf ein Feld wird der Cursor in diesem Feld platziert. Mit einem Doppelklick auf ein Feld wird dieses markiert. Wenn ein Feld hervorgehoben ist, kann eine QuickInfo angezeigt werden, die eine Beschreibung des Felds liefert.

Nur die erste Instanz des jeweiligen Feldes ist editierbar. Wenn dieses Feld hervorgehoben ist, sind die anderen Instanzen des Feldes mit einem Rahmen versehen. Wenn Sie den Wert eines editierbaren Feldes ändern, wird das Feld an allen Stellen im Ausschnitt geändert, an denen es verwendet wird.

Durch Drücken der **Eingabe** Taste oder **ESC** wird die Feldbearbeitung abgebrochen, und der Editor wird normal zurückgegeben.

Die Standardfarben für bearbeitbare Code Ausschnitt Felder können geändert werden, indem Sie im Bereich **Schriftarten und Farben** des Dialog Felds **Optionen** die Einstellung für das **Code Ausschnitt Feld** ändern. Weitere Informationen finden Sie unter Gewusst [wie: Ändern von Schriftarten und Farben im Editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Siehe auch

- [XML-Ausschnitte](../xml-tools/xml-snippets.md)
- [Gewusst wie: Generieren eines XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Gewusst wie: Erstellen von XML-Ausschnitten](../xml-tools/how-to-create-xml-snippets.md)