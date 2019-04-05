---
title: 'Vorgehensweise: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e857befa71095572661ff2c2e1a2ba074444f231
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961681"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Vorgehensweise: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Die **Beispiel-XML generieren** Funktion generiert eine XML-Beispieldatei, die basierend auf Ihrer XML-Schema (XSD)-Datei.  
  
 Diese Option kann für die folgenden Szenarien verwendet werden :  
  
- Um die Verwendung verschiedener Konstrukte im Schema zu verstehen.  
  
- Um zu bestätigen, dass das Schema wie beabsichtigt ausgeführt wird.  
  
  Die **Beispiel-XML generieren** Feature ist nur für globale Elemente verfügbar und erfordert ein gültiges XML-Schemaset.  
  
  Diese Funktion generiert i. d. R. gültige XML-Dokumente. Wenn das Schema jedoch eines der folgenden Elemente enthält, ist das Beispiel möglicherweise nicht gültig:  
  
- Die folgenden Identitätseinschränkungen: `xs:key`, `xs:keyref` und `xs:unique`  
  
- `xs:pattern`-Facets  
  
- Enumerationen des `xs:QName`-Typs  
  
- `xs:ENTITY`-, `xs:ENTITIES`- und `xs:NOTATION`-Typen  
  
  Beachten Sie außerdem, dass `xs:base64Binary`-Inhalt nur dann generiert wird, wenn Enumerationen im Schema für diesen Typ vorkommen.  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>So generieren Sie ein XML-Instanzdokument auf Grundlage der XSD-Datei  
  
1.  Führen Sie die Schritte in [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  In der [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md), mit der rechten Maustaste die `PurchaseOrder` globale Element. Wählen Sie **Beispiel-XML generieren**.  
  
     Die Datei "PurchaseOrder.xml" wird mit dem folgenden Beispiel-XML-Inhalt generiert und im XML-Editor geöffnet:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit XML-Daten](../xml-tools/working-with-xml-data.md)
