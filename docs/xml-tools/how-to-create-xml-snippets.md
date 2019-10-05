---
title: 'Vorgehensweise: Erstellen von XML-Ausschnitten'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d5ba351c20328829c05168d846fb7bffad7c11d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926509"
---
# <a name="how-to-create-xml-snippets"></a>Vorgehensweise: Erstellen von XML-Ausschnitten

Der XML-Editor kann zum Erstellen neuer XML-Ausschnitte verwendet werden. Der Editor enthält einen XML-Ausschnitt mit dem Namen "Snippet". Dies ist ein vorformulierter Ausschnitt zum Erstellen neuer XML-Ausschnitte.

## <a name="to-create-a-new-xml-snippet"></a>So erstellen Sie einen neuen XML-Ausschnitt

Um einen neuen XML-Code Ausschnitt zu erstellen, erstellen Sie eine neue XML-Datei, und verwenden Sie das Feature " **Ausschnitt einfügen** ".

1. Klicken Sie im Menü **Datei** auf **neu** , und klicken Sie dann auf **Datei**.

2. Klicken Sie auf **XML-Datei** und dann auf **Öffnen**.

3. Klicken Sie mit der rechten Maustaste in den Bereich Editor, und wählen Sie **Ausschnitt einfügen**aus.

4. Wählen Sie in der Liste **Ausschnitt** aus, und drücken **Sie die Eingabe**Taste.

5. Nehmen Sie die gewünschten Änderungen an dem neuen Ausschnitt vor.

6. Wählen Sie im Menü **Datei** die Option **xmlfile. XML speichern**aus.

     Das Dialogfeld **Datei speichern** unter wird angezeigt.

7. Geben Sie den Namen für den neuen Code Ausschnitt ein, und wählen Sie im Dropdown Fenster **Dateityp** die Option **Ausschnitt Dateien** aus.

8. Verwenden Sie die Dropdown Liste **Speichern in** , um den Datei Speicherort in den Ordner *My Documents\Visual Studio 2005 \ Code snippeer \ xml\my XML Snippets* zu ändern, und klicken Sie dann auf **Save**.

## <a name="snippet-description"></a>Ausschnitt Beschreibung

In diesem Abschnitt werden einige Schlüsselelemente im vorformulierten Ausschnitt beschrieben. Weitere Informationen zu Schema Elementen, die von den XML-Ausschnitten verwendet werden, finden Sie unter [Schema Referenz für Code Ausschnitte](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType-Element

Vom Editor werden zwei Ausschnitttypen unterstützt:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

Der `Expansion` -Typ bestimmt, ob der Ausschnitt angezeigt wird, wenn Sie den Befehl **Ausschnitt einfügen** aufrufen. Der `SurroundsWith` -Typ bestimmt, ob der Ausschnitt angezeigt wird, wenn Sie den Befehl "umschließen **mit** " aufrufen.

### <a name="code-element"></a>Codeelement

Das `Code`-Element definiert den XML-Text, der beim Aufrufen des Ausschnitts eingefügt wird.

> [!NOTE]
> Der XML-Ausschnitttext muss in einem `<![CDATA[...]]>`-Abschnitt eingeschlossen werden.

Es folgt das `Code`-Element, das von einem vorformulierten Ausschnitt erstellt wurde.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

Das `Code`-Element enthält drei Variablen.

- $name$ ist eine benutzerdefinierte Variable. Sie erstellt ein `name`-Element mit einem editierbaren Wert, dessen Standardwert "name" ist. Benutzerdefinierte Variablen werden mithilfe des `Literal`-Elements definiert.

- $selected$ ist eine vordefinierte Variable. Sie stellt den Text dar, der im XML-Editor vor dem Aufrufen des Code Ausschnitts ausgewählt wurde. Die Positionierung dieser Variablen bestimmt, an welcher Position der ausgewählte Text im Codeausschnitt angezeigt wird, der die Auswahl umgibt.

- $end$ ist eine vordefinierte Variable. Wenn der Benutzer die **Eingabe** Taste drückt, um die Bearbeitung der Code Ausschnitt Felder abzuschließen, bestimmt diese Variable, wohin die Einfügemarke (^) verschoben wird.

  Das obige `Code`-Element fügt den folgenden XML-Text ein:

```xml
<test>
  <name>name</name>
</test>
```

Der Wert des name-Elements wird als editierbarer Bereich gekennzeichnet.

### <a name="literal-element"></a>Literalelement

Mithilfe des `Literal`-Elements wird der Ersetzungstext angegeben, der nach dem Einfügen in die Datei angepasst werden kann. Literalzeichenfolgen, numerische Werte und einige Variablennamen können beispielsweise als Literale deklariert werden. Sie können in einem XML-Ausschnitt beliebig viele Literale definieren, und Sie können darauf mehrfach aus dem Ausschnitt verweisen. Es folgt ein Beispiel für ein `Literal`-Element, das eine $name$-Variable definiert, deren Standardwert "name" ist.

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Literale können auch auf Funktionen verweisen. Der XML-Editor enthält eine Funktion mit dem Namen **LookupPrefix**. Die **LookupPrefix** -Funktion sucht den angegebenen Namespace-URI von dem Speicherort im XML-Dokument, von dem aus dieser Ausschnitt aufgerufen wird, und gibt das Namespace Präfix zurück, das für diesen Namespace definiert ist, sofern vorhanden, und enthält den Doppelpunkt (:) in diesem Namen. Im folgenden finden Sie ein Beispiel für `Literal` ein-Element, das die **LookupPrefix** -Funktion verwendet.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

Die $prefix$-Variable kann anschließend an beliebiger Stelle im XML-Ausschnitt verwendet werden.

## <a name="see-also"></a>Siehe auch

- [XML-Ausschnitte](../xml-tools/xml-snippets.md)
- [Vorgehensweise: XML-Ausschnitte verwenden](../xml-tools/how-to-use-xml-snippets.md)
- [Vorgehensweise: Generieren eines XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)