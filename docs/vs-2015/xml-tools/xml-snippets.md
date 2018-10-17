---
title: XML-Ausschnitten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf1ebeb70931e2e12f056ecfbaa45a6833e031df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183962"
---
# <a name="xml-snippets"></a>XML-Ausschnitte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Der XML-Editor bietet ein Feature namens *XML-Ausschnitte*, können Sie schneller XML-Dateien zu erstellen. Sie können XML-Ausschnitte wiederverwenden, indem Sie diese in die Dateien einfügen. XML-Dateien können auch auf der Grundlage eines XSD-Schemas (XML Schema Definition Language) erstellt werden.  
  
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
  
 Es gibt zwei Möglichkeiten zum Einfügen von Ausschnitten. Die **Ausschnitt einfügen** Befehl wird den XML-Ausschnitt an der Cursorposition eingefügt. Die **Umschließen mit** Befehl dient als Wrapper für den XML-Ausschnitt für den ausgewählten Text. Beide Befehle sind entweder verfügbar, aus der **IntelliSense** Untermenü unter der **bearbeiten** im Menü oder im Kontextmenü des Editors.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von XML-Ausschnitte](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Schemagenerierte XML-Ausschnitte  
 Der XML-Editor verfügt über die Funktion, XML-Ausschnitte aus einem XML-Schema zu generieren. Mithilfe dieser Funktion können Sie ein Element mit XML-Elementen auffüllen, die aus den Schemainformationen für dieses Element generiert werden.  
  
 Weitere Informationen finden Sie unter [wie: Generieren eines XML-Codeausschnitt aus einer XML-Schemas](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Erstellen neuer XML-Ausschnitte  
 Zusätzlich zu den Codeausschnitten, die in enthaltenen [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio wird standardmäßig auch erstellen und verwenden Sie eigene XML-Ausschnitte können.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von XML-Ausschnitte](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)



