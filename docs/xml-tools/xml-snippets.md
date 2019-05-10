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
ms.openlocfilehash: 66736431b295f974bda1ca855d88cd5f5f868e7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807718"
---
# <a name="xml-snippets"></a>XML-Ausschnitte

Der XML-Editor bietet ein Feature namens *XML-Ausschnitte*, können Sie schneller XML-Dateien zu erstellen. Sie können XML-Ausschnitte wiederverwenden, indem Sie diese in die Dateien einfügen. Sie können auch XML-Daten, die basierend auf ein Schema von XML Schema Definition Language (XSD) generieren.

## <a name="reusable-xml-snippets"></a>Wiederverwendbare XML-Ausschnitte

Der XML-Editor enthält viele Ausschnitte, die einige häufig auszuführende Aufgaben beinhalten. Dadurch wird Ihnen das Erstellen von XML-Dateien erleichtert. Fügt z. B. Wenn Sie ein XML-Schema erstellt haben, verwenden die Ausschnitte "ComplexType Sequence-Element" und "SimpleType-Element" den folgenden XML-Text der Datei. Entsprechend Ihren Anforderungen ändern Sie den `name`-Wert.

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

Es gibt zwei Möglichkeiten zum Einfügen von Ausschnitten. Die **Ausschnitt einfügen** Befehl wird den XML-Ausschnitt an der Cursorposition eingefügt. Die **Umschließen mit** Befehl dient als Wrapper für den XML-Ausschnitt für den ausgewählten Text. Beide Befehle sind entweder verfügbar, aus der **IntelliSense** Untermenü unter der **bearbeiten** im Menü oder über das Kontextmenü im Editor.

Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von XML-Ausschnitte](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Schema generierte XML-Ausschnitte

Der XML-Editor kann auch zum Generieren eines XML-Ausschnitts aus einem XML-Schema. Mithilfe dieses Features können Sie ein Element mit XML-Elementen auffüllen, die aus den Schemainformationen für dieses Element generiert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Generieren ein XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Erstellen neuer XML-Ausschnitte

Zusätzlich zu die Codeausschnitte, die standardmäßig in Visual Studio enthalten sind, können Sie auch erstellen und verwenden Sie eigene XML-Ausschnitte. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von XML-Ausschnitten](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte in Visual Studio](../ide/code-snippets.md)
- [XML-editor](../xml-tools/xml-editor.md)