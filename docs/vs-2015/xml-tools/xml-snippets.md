---
title: XML-Ausschnitte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669364"
---
# <a name="xml-snippets"></a>XML-Ausschnitte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XML-Editor bietet eine Funktion mit dem Namen *XML-Ausschnitte*, mit der Sie XML-Dateien schneller erstellen können. Sie können XML-Ausschnitte wiederverwenden, indem Sie diese in die Dateien einfügen. XML-Dateien können auch auf der Grundlage eines XSD-Schemas (XML Schema Definition Language) erstellt werden.

## <a name="reusable-xml-snippets"></a>Wiederverwendbare XML-Ausschnitte
 Der XML-Editor enthält viele Ausschnitte, die einige häufig auszuführende Aufgaben beinhalten. Dadurch wird Ihnen das Erstellen von XML-Dateien erleichtert. Wenn Sie z. B. ein XML-Schema unter Verwendung der Ausschnitte "complexType Sequence-Element" und "simpleType-Element" erstellt haben, wird der folgende XML-Text in die Datei eingefügt. Entsprechend Ihren Anforderungen ändern Sie den `name`-Wert.

```
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

 Es gibt zwei Möglichkeiten zum Einfügen von Ausschnitten. Der Befehl **Ausschnitt einfügen** fügt den XML-Code Ausschnitt an der Cursorposition ein. Der Befehl **Umschließen mit** umschließt den XML-Code Ausschnitt um den markierten Text. Beide Befehle sind entweder über das **IntelliSense** -Untermenü im Menü " **Bearbeiten** " oder über das Kontextmenü des Editors verfügbar.

 Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von XML-Ausschnitten](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Schemagenerierte XML-Ausschnitte
 Der XML-Editor verfügt über die Funktion, XML-Ausschnitte aus einem XML-Schema zu generieren. Mithilfe dieses Features können Sie ein Element mit XML-Elementen auffüllen, die aus den Schemainformationen für dieses Element generiert werden.

 Weitere Informationen finden Sie unter Gewusst [wie: Generieren eines XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Erstellen neuer XML-Ausschnitte
 Zusätzlich zu den in [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio enthaltenen Code Ausschnitten können Sie auch eigene XML-Ausschnitte erstellen und verwenden.

 Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von XML-Ausschnitten](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Siehe auch
 [XML-Editor](../xml-tools/xml-editor.md)
