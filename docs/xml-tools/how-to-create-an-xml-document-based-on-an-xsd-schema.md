---
title: 'Vorgehensweise: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 424b325b244499a18077cc1df0ff9164c41763d2
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815460"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Vorgehensweise: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas

Die Funktion **Beispiel-XML generieren** generiert auf Grundlage der XML-Schemadatei (XSD) eine Beispiel-XML-Datei.

Diese Option kann für die folgenden Szenarien verwendet werden :

- Um die Verwendung verschiedener Konstrukte im Schema zu verstehen.

- Um zu bestätigen, dass das Schema wie beabsichtigt ausgeführt wird.

Die Funktion **Beispiel-XML generieren** ist nur für globale Elemente verfügbar und benötigt ein gültiges XML-Schemaset.

Diese Funktion generiert i. d. R. gültige XML-Dokumente. Wenn das Schema jedoch eines der folgenden Elemente enthält, ist das Beispiel möglicherweise nicht gültig:

- Die folgenden Identitätseinschränkungen: `xs:key`, `xs:keyref` und `xs:unique`

- `xs:pattern`-Facets.

- Enumerationen des `xs:QName`-Typs

- `xs:ENTITY`-, `xs:ENTITIES`- und `xs:NOTATION`-Typen.

Beachten Sie außerdem, dass `xs:base64Binary`-Inhalt nur dann generiert wird, wenn Enumerationen im Schema für diesen Typ vorkommen.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>So generieren Sie ein XML-Instanzdokument auf Grundlage der XSD-Datei

1. Führen Sie die unter [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md) aufgeführten Schritte durch.

2. Klicken Sie im [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md) mit der rechten Maustaste auf das globale `PurchaseOrder`-Element. Wählen Sie **Beispiel-XML generieren** aus.

     Die Datei „PurchaseOrder.*xml*“ wird mit dem folgenden Beispiel-XML-Inhalt generiert und im XML-Editor geöffnet:

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
