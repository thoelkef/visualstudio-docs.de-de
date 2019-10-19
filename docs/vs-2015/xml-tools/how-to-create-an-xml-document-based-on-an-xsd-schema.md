---
title: 'Gewusst wie: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e48c48d6711a1eb21157122d13790e22688855
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670950"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Gewusst wie: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Funktion **Beispiel-XML generieren** generiert eine XML-Beispieldatei, die auf der XML-Schema Datei (XSD) basiert.

 Diese Option kann für die folgenden Szenarien verwendet werden :

- Um die Verwendung verschiedener Konstrukte im Schema zu verstehen.

- Um zu bestätigen, dass das Schema wie beabsichtigt ausgeführt wird.

  Die Funktion **Beispiel-XML generieren** ist nur für globale Elemente verfügbar und erfordert ein gültiges XML-Schemaset.

  Diese Funktion generiert i. d. R. gültige XML-Dokumente. Wenn das Schema jedoch eines der folgenden Elemente enthält, ist das Beispiel möglicherweise nicht gültig:

- Die folgenden Identitätseinschränkungen: `xs:key`, `xs:keyref` und `xs:unique`

- `xs:pattern`-Facets

- Enumerationen des `xs:QName`-Typs

- `xs:ENTITY`-, `xs:ENTITIES`- und `xs:NOTATION`-Typen

  Beachten Sie außerdem, dass `xs:base64Binary`-Inhalt nur dann generiert wird, wenn Enumerationen im Schema für diesen Typ vorkommen.

### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>So generieren Sie ein XML-Instanzdokument auf Grundlage der XSD-Datei

1. Befolgen Sie die Schritte unter Gewusst [wie: Erstellen und Bearbeiten einer XSD-Schema Datei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Klicken Sie im [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)mit der rechten Maustaste auf das `PurchaseOrder` globale Element. Wählen Sie **Beispiel-XML generieren**aus.

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
