---
title: XML-Ausschnitte
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f2bcdd0c28d7b4b99c92d3346b32ed34aa92a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592320"
---
# <a name="xml-snippets"></a>XML-Ausschnitte

Der XML-Editor bietet eine Funktion mit dem Namen *XML-Ausschnitte*, mit der Sie XML-Dateien schneller erstellen können. Sie können XML-Ausschnitte wiederverwenden, indem Sie diese in die Dateien einfügen. Sie können auch XML-Daten auf Grundlage eines XSD-Schemas (XML Schema Definition Language) generieren.

## <a name="reusable-xml-snippets"></a>Verwendbare XML-Ausschnitte

Der XML-Editor enthält viele Code Ausschnitte, die einige allgemeine Aufgaben abdecken. Dadurch wird Ihnen das Erstellen von XML-Dateien erleichtert. Wenn Sie z. b. ein XML-Schema erstellen, wird durch die Verwendung der Code Ausschnitte "Complex Type Sequence Element" und "Simple Type Element" der folgende XML-Text in die Datei eingefügt. Entsprechend Ihren Anforderungen ändern Sie den `name`-Wert.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

Es gibt zwei Möglichkeiten zum Einfügen von Ausschnitten. Der Befehl **Ausschnitt einfügen** fügt den XML-Code Ausschnitt an der Cursorposition ein. Der Befehl **Umschließen mit** umschließt den XML-Code Ausschnitt um den markierten Text. Beide Befehle sind entweder über das **IntelliSense** -Untermenü im Menü " **Bearbeiten** " oder über das Kontextmenü im Editor verfügbar.

Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von XML-Ausschnitten](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Schema generierte XML-Ausschnitte

Der XML-Editor ist auch in der Lage, einen XML-Ausschnitt aus einem XML-Schema zu generieren. Mithilfe dieses Features können Sie ein Element mit XML-Elementen auffüllen, die aus den Schemainformationen für dieses Element generiert werden. Weitere Informationen finden Sie unter Gewusst [wie: Generieren eines XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Erstellen neuer XML-Ausschnitte

Zusätzlich zu den Code Ausschnitten, die in Visual Studio standardmäßig enthalten sind, können Sie auch eigene XML-Ausschnitte erstellen und verwenden. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von XML-Ausschnitten](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Siehe auch

- [Code Ausschnitte in Visual Studio](../ide/code-snippets.md)
- [XML-Editor](../xml-tools/xml-editor.md)
