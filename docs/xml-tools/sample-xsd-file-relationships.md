---
title: 'XSD-Beispieldatei: Beziehungen'
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: 60126510-b7dd-4cb4-92d3-9883590b92f2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d5342bece15fff25ba970270456aed96c5dc7f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601756"
---
# <a name="sample-xsd-file-relationships"></a>XSD-Beispieldatei: Beziehungen

Die folgende XSD-Datei wird in verschiedenen Beispielen in der Dokumentation zum XSD-Schema-Designer verwendet. Bei dieser Datei handelt es sich um ein Bestellungsschema mit Anmerkungen und Dokumentation.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="pet" type="PetType"/>

  <xs:attributeGroup name="NameAgeAttributes">
    <xs:attribute name="age" type="xs:integer" use="required"/>
    <xs:attribute name="name" type="xs:string" use="required"/>
  </xs:attributeGroup>

  <xs:complexType name="PetType">
    <xs:attributeGroup ref="NameAgeAttributes"/>
  </xs:complexType>

  <xs:element name="cat" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

  <xs:element name="dog" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

</xs:schema>
```

> [!NOTE]
> Die in den Beispielen genannten Unternehmen, Organisationen, Produkte, Domänennamen, E-Mail-Adressen, Logos, Personen, Orte und Ereignisse sind frei erfunden. Jede Ähnlichkeit mit bestehenden Unternehmen, Organisationen, Produkten, Domänen, E-Mail-Adressen, Logos, Personen, Orten oder Ereignissen ist rein zufällig.