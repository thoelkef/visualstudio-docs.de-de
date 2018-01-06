---
title: XML-Ausschnitte | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 88ccba516a0bce6e3413bf14d38d32baf68d8274
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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