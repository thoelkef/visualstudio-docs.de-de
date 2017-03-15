---
title: "Gewusst wie: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Gewusst wie: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Funktion **Beispiel\-XML generieren** generiert auf Grundlage der XML\-Schemadatei \(XSD\) eine Beispiel\-XML\-Datei.  
  
 Diese Option kann für die folgenden Szenarien verwendet werden :  
  
-   Um die Verwendung verschiedener Konstrukte im Schema zu verstehen.  
  
-   Um sicherzustellen, dass das Schema wie beabsichtigt ausgeführt wird.  
  
 Das Feature **Beispiel\-XML generieren** ist nur für globale Elemente verfügbar und benötigt ein gültiges XML\-Schemaset.  
  
 Dieses Feature generiert i. d. R. gültige XML\-Dokumente.Wenn das Schema jedoch eines der folgenden Elemente enthält, ist das Beispiel möglicherweise nicht gültig:  
  
-   Die folgenden Identitätseinschränkungen: `xs:key`, `xs:keyref` und `xs:unique`  
  
-   `xs:pattern`\-Facets  
  
-   Enumerationen des `xs:QName`\-Typs  
  
-   `xs:ENTITY`\-, `xs:ENTITIES`\- und `xs:NOTATION`\-Typen  
  
 Beachten Sie außerdem, dass `xs:base64Binary`\-Inhalt nur dann generiert wird, wenn Enumerationen im Schema für diesen Typ vorkommen.  
  
### So generieren Sie ein XML\-Instanzdokument auf Grundlage der XSD\-Datei  
  
1.  Führen Sie die in [Gewusst wie: Erstellen und Bearbeiten einer XSD\-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md) beschriebenen Schritte aus.  
  
2.  Klicken Sie im [XML\-Schema\-Explorer](../xml-tools/xml-schema-explorer.md) mit der rechten Maustaste auf das globale `PurchaseOrder`\-Element.Wählen Sie **Beispiel\-XML generieren** aus.  
  
     Die Datei "PurchaseOrder.xml" wird mit dem folgenden Beispiel\-XML\-Inhalt generiert und im XML\-Editor geöffnet:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">  
      <ShipTo country="US">  
        <name>name1</name>  
        <street>street1</street>  
        <city>city1</city>  
        <state>state1</state>  
        <zip>1</zip>  
      </ShipTo>  
      <ShipTo country="US">  
        <name>name2</name>  
        <street>street2</street>  
        <city>city2</city>  
        <state>state2</state>  
        <zip>-79228162514264337593543950335</zip>  
      </ShipTo>  
      <BillTo country="US">  
        <name>name1</name>  
        <street>street1</street>  
        <city>city1</city>  
        <state>state1</state>  
        <zip>1</zip>  
      </BillTo>  
    </PurchaseOrder>  
    ```  
  
## Siehe auch  
 [Arbeiten mit XML\-Daten](../xml-tools/working-with-xml-data.md)