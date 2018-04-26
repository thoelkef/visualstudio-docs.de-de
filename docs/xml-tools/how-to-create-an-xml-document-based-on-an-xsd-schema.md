---
title: 'Gewusst wie: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11ec095bd3228eb2291f77bf9fadceb0b74d8a37
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Gewusst wie: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas

Die **Beispiel-XML generieren** Feature generiert eine Beispiel-XML-Datei auf Grundlage der XML-Schema (XSD).

 Diese Option kann für die folgenden Szenarien verwendet werden :

-   Um die Verwendung verschiedener Konstrukte im Schema zu verstehen.

-   Um zu bestätigen, dass das Schema wie beabsichtigt ausgeführt wird.

Die **Beispiel-XML generieren** Feature ist nur für globale Elemente verfügbar und erfordert ein gültiges XML-Schemaset.

Diese Funktion generiert i. d. R. gültige XML-Dokumente. Wenn das Schema jedoch eines der folgenden Elemente enthält, ist das Beispiel möglicherweise nicht gültig:

-   Die folgenden Identitätseinschränkungen: `xs:key`, `xs:keyref` und `xs:unique`

-   `xs:pattern`-Facets

-   Enumerationen des `xs:QName`-Typs

-   `xs:ENTITY`-, `xs:ENTITIES`- und `xs:NOTATION`-Typen

Beachten Sie außerdem, dass `xs:base64Binary`-Inhalt nur dann generiert wird, wenn Enumerationen im Schema für diesen Typ vorkommen.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>So generieren Sie ein XML-Instanzdokument auf Grundlage der XSD-Datei

1.  Führen Sie die Schritte in [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  In der [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md), mit der rechten Maustaste die `PurchaseOrder` globale Element. Wählen Sie **Beispiel-XML generieren**.

     Die Datei "PurchaseOrder.xml" wird mit dem folgenden Beispiel-XML-Inhalt generiert und im XML-Editor geöffnet:

    ```xml
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

- [Arbeiten mit XML-Daten](../xml-tools/working-with-xml-data.md)