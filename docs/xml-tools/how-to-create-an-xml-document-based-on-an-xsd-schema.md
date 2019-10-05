---
title: 'Vorgehensweise: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7739f33bad62667fdc7be8704237ebdd3932739c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918567"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Vorgehensweise: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas

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

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>So generieren Sie ein XML-Instanzdokument auf Grundlage der XSD-Datei

1. Befolgen Sie die Schritte [unter Gewusst wie: Erstellen und bearbeiten Sie eine XSD-](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)Schema Datei.

2. Klicken Sie im [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)mit der `PurchaseOrder` rechten Maustaste auf das globale Element. Wählen Sie **Beispiel-XML generieren**aus.

     Wenn Sie diese Option auswählen, wird PurchaseOrder angegeben. die *XML* -Datei mit dem folgenden XML-Beispiel Inhalt wird generiert und im XML-Editor geöffnet:

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