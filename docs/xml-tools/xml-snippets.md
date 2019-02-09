---
title: XML-Ausschnitte
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76701499c9304551c2bc6213b3eebbbc2421e4c2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953749"
---
# <a name="xml-snippets"></a>XML-Ausschnitte

Der XML-Editor bietet ein Feature namens *XML-Ausschnitte*, können Sie schneller XML-Dateien zu erstellen. Sie können XML-Ausschnitte wiederverwenden, indem Sie diese in die Dateien einfügen. XML-Dateien können auch auf der Grundlage eines XSD-Schemas (XML Schema Definition Language) erstellt werden.

## <a name="reusable-xml-snippets"></a>Wiederverwendbare XML-Ausschnitte

Der XML-Editor enthält viele Ausschnitte, die einige häufig auszuführende Aufgaben beinhalten. Dadurch wird Ihnen das Erstellen von XML-Dateien erleichtert. Wenn Sie z. B. ein XML-Schema unter Verwendung der Ausschnitte "complexType Sequence-Element" und "simpleType-Element" erstellt haben, wird der folgende XML-Text in die Datei eingefügt. Entsprechend Ihren Anforderungen ändern Sie den `name`-Wert.

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

 Es gibt zwei Möglichkeiten zum Einfügen von Ausschnitten. Die **Ausschnitt einfügen** Befehl wird den XML-Ausschnitt an der Cursorposition eingefügt. Die **Umschließen mit** Befehl dient als Wrapper für den XML-Ausschnitt für den ausgewählten Text. Beide Befehle sind entweder verfügbar, aus der **IntelliSense** Untermenü unter der **bearbeiten** im Menü oder im Kontextmenü des Editors.

 Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von XML-Ausschnitte](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Schema generierte XML-Ausschnitte
 Der XML-Editor verfügt über die Funktion, XML-Ausschnitte aus einem XML-Schema zu generieren. Mithilfe dieser Funktion können Sie ein Element mit XML-Elementen auffüllen, die aus den Schemainformationen für dieses Element generiert werden.

 Weitere Informationen finden Sie unter [Vorgehensweise: Generieren ein XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Erstellen neuer XML-Ausschnitte
 Zusätzlich zu den Codeausschnitten, die in enthaltenen [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio wird standardmäßig auch erstellen und verwenden Sie eigene XML-Ausschnitte können.

 Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von XML-Ausschnitten](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)