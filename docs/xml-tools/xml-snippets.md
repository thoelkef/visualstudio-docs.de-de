---
title: "XML-Ausschnitte | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XML-Ausschnitte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der XML\-Editor bietet ein als *XML\-Ausschnitte* bezeichnetes Feature, mit dem Sie schneller XML\-Dateien erstellen können.Sie können XML\-Ausschnitte wiederverwenden, indem Sie diese in die Dateien einfügen.XML\-Dateien können auch auf der Grundlage eines XSD\-Schemas \(XML Schema Definition Language\) erstellt werden.  
  
## Wiederverwendbare XML\-Ausschnitte  
 Der XML\-Editor enthält viele Ausschnitte, die einige häufig auszuführende Aufgaben beinhalten.Dadurch wird Ihnen das Erstellen von XML\-Dateien erleichtert.Wenn Sie z. B. ein XML\-Schema unter Verwendung der Ausschnitte "complexType Sequence\-Element" und "simpleType\-Element" erstellt haben, wird der folgende XML\-Text in die Datei eingefügt.Entsprechend Ihren Anforderungen ändern Sie den `name`\-Wert.  
  
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
  
 Es gibt zwei Möglichkeiten zum Einfügen von Ausschnitten.Mit dem Befehl **Ausschnitt einfügen** wird der XML\-Ausschnitt an der Cursorposition eingefügt.Der Befehl **Umgeben mit** veranlasst, dass der XML\-Ausschnitt als Wrapper für den ausgewählten Text fungiert.Beide Befehle sind entweder im Menü **Bearbeiten**, Untermenü **IntelliSense**, oder im Kontextmenü des Editors verfügbar.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von XML\-Ausschnitten](../xml-tools/how-to-use-xml-snippets.md).  
  
## Schemagenerierte XML\-Ausschnitte  
 Der XML\-Editor verfügt über die Funktion, XML\-Ausschnitte aus einem XML\-Schema zu generieren.Mithilfe dieses Features können Sie ein Element mit XML\-Elementen auffüllen, die aus den Schemainformationen für dieses Element generiert werden.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Generieren eines XML\-Ausschnitts aus einem XML\-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## Erstellen neuer XML\-Ausschnitte  
 Zusätzlich zu den standardmäßig in [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]\-Visual Studio enthaltenen Ausschnitten können Sie eigene XML\-Ausschnitte erstellen und verwenden.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von XML\-Ausschnitten](../xml-tools/how-to-create-xml-snippets.md).  
  
## Siehe auch  
 [XML\-Editor](../xml-tools/xml-editor.md)