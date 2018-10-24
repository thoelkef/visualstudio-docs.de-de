---
title: 'Vorgehensweise: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbecacc0729c936489c05d3bb59260341a08d314
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884224"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Gewusst wie: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas
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



