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
ms.openlocfilehash: 43305d7b9353bd34e98a3dcfd31205cb9159a2f3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659918"
---
# <a name="how-to-create-xml-snippets"></a>Vorgehensweise: Erstellen von XML-Ausschnitten

Der XML-Editor kann verwendet werden, zum Erstellen neuer XML-Ausschnitte. Der Editor enthält einen XML-Ausschnitt mit dem Namen "Snippet". Dies ist ein vorformulierter Ausschnitt zum Erstellen neuer XML-Ausschnitte.

## <a name="to-create-a-new-xml-snippet"></a>So erstellen Sie einen neuen XML-Ausschnitt

 Erstellen Sie einen neuen XML-Code Codeausschnitt erstellen Sie eine neue XML-Datei, und Verwenden der **Ausschnitt einfügen** Feature.

1.  Auf der **Datei** Menü klicken Sie auf **neu** , und klicken Sie dann auf **Datei**.

2.  Klicken Sie auf **XML-Datei** , und klicken Sie dann auf **öffnen**.

3.  Mit der rechten Maustaste im Editor-Bereich, und wählen Sie **Ausschnitt einfügen**.

4.  Wählen Sie **Codeausschnitt** aus der Liste und drücken Sie **EINGABETASTE**.

5.  Nehmen Sie die gewünschten Änderungen an dem neuen Ausschnitt vor.

6.  Von der **Datei** Menü die Option **XMLFile.xml speichern**.

     Die **Datei speichern unter** Dialogfeld wird angezeigt.

7.  Geben Sie den Namen für den neuen Ausschnitt aus, und wählen Sie **Codeausschnittsdateien** aus der **Dateityp** Dropdownfenster.

8.  Verwenden der **speichern in** Dropdown-Liste so ändern Sie den Speicherort der *Eigene Dateien\Visual Studio 2005\Codeausschnitte \XML\My XML Snippets* Ordner, und drücken Sie dann die **speichern**.

## <a name="snippet-description"></a>Ausschnittbeschreibung

 In diesem Abschnitt werden einige Schlüsselelemente im vorformulierten Ausschnitt beschrieben. Weitere Informationen zu Schema-Elemente, die von der XML-Ausschnitten verwendet, finden Sie unter [Code Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType-Element

 Vom Editor werden zwei Ausschnitttypen unterstützt:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

 Die `Expansion` -Typ bestimmt, ob der Ausschnitt angezeigt, beim Aufrufen wird der **Ausschnitt einfügen** Befehl. Die `SurroundsWith` -Typ bestimmt, ob der Ausschnitt angezeigt, beim Aufrufen wird der **umgeben mit** Befehl.

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

- $selected$ ist eine vordefinierte Variable. Es stellt den Text, der in der XML-Editor vor dem Aufrufen des Ausschnitts ausgewählt wurde. Die Positionierung dieser Variablen bestimmt, an welcher Position der ausgewählte Text im Codeausschnitt angezeigt wird, der die Auswahl umgibt.

- $end$ ist eine vordefinierte Variable. Wenn der Benutzer drückt **EINGABETASTE** zur Bearbeitung der Codeausschnittfelder abgeschlossen haben, dieser Variablen wird festgelegt, in dem das Caretzeichen (^) in verschoben wird.

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

 Literale können auch auf Funktionen verweisen. Der XML-Editor enthält eine Funktion namens **LookupPrefix**. Die **LookupPrefix** -Funktion sucht den angegebenen Namespace-URI, von der Position in der XML-Dokument, dass dieser Ausschnitt aus aufgerufen wird, und gibt das Namespacepräfix, das für diesen Namespace definiert ist, sofern vorhanden, und fügt den Doppelpunkt (:) In diesem Namen. Folgendes ist ein Beispiel für eine `Literal` -Element, das verwendet die **LookupPrefix** Funktion.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

 Die $prefix$-Variable kann anschließend an beliebiger Stelle im XML-Ausschnitt verwendet werden.

## <a name="see-also"></a>Siehe auch

- [XML-Ausschnitte](../xml-tools/xml-snippets.md)
- [Vorgehensweise: Verwenden von XML-Ausschnitten](../xml-tools/how-to-use-xml-snippets.md)
- [Vorgehensweise: Generieren eines XML-Ausschnitts aus einem XML-schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)