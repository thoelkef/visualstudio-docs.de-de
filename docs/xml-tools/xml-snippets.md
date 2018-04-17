---
title: XML-Ausschnitte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47410a4f87d6e8afd1af6f41583261c101883562
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="xml-snippets"></a>XML-Ausschnitte
Der XML-Editor bietet eine Funktion *XML-Ausschnitte*, mit dem Sie schneller XML-Dateien erstellen. Sie können XML-Ausschnitte wiederverwenden, indem Sie diese in die Dateien einfügen. XML-Dateien können auch auf der Grundlage eines XSD-Schemas (XML Schema Definition Language) erstellt werden.  
  
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
  
 Es gibt zwei Möglichkeiten zum Einfügen von Ausschnitten. Die **Ausschnitt einfügen** Befehl fügt den XML-Ausschnitt an der Cursorposition eingefügt. Die **Umschließen mit** Befehl dient als Wrapper für die XML-Ausschnitt des markierten Texts. Beide Befehle sind entweder verfügbar aus den **IntelliSense** Untermenü unter der **bearbeiten** im Menü oder aus dem Editor-Kontextmenü.  
  
 Weitere Informationen finden Sie unter [wie: Verwenden von XML-Ausschnitte](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Schemagenerierte XML-Ausschnitte  
 Der XML-Editor verfügt über die Funktion, XML-Ausschnitte aus einem XML-Schema zu generieren. Mithilfe dieser Funktion können Sie ein Element mit XML-Elementen auffüllen, die aus den Schemainformationen für dieses Element generiert werden.  
  
 Weitere Informationen finden Sie unter [wie: Generieren eines XML-Ausschnitt aus einer XML-Schemas](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Erstellen neuer XML-Ausschnitte  
 Zusätzlich zu die Ausschnitte, die in enthaltenen [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio standardmäßig auch erstellen und eigene XML-Ausschnitte verwenden können.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von XML-Ausschnitte](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)