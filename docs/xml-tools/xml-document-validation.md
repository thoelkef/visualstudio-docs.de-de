---
title: XML-Dokument Validierung im XML-Editor
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13574a13aecf7edbc9627e7b8288689206f278c2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926699"
---
# <a name="xml-document-validation"></a>Validierung von XML-Dokumenten

Der XML-Editor überprüft die Syntax von XML 1,0 und führt während der Typvalidierung auch eine Datenüberprüfung durch. Die Validierung wird vom Editor mithilfe einer DTD (Document Type Definition) oder eines Schemas vorgenommen. Durch rote wellenförmige Unterstreichungen werden Wohlgeformtheits-Fehler in XML 1.0 hervorgehoben. Blaue Wellenlinien weisen auf semantische Fehler in Abhängigkeit von der DTD- oder Schemavalidierung hin. Jedem Fehler ist ein Eintrag in der Fehlerliste zugeordnet. Sie können die Fehlermeldung auch anzeigen, indem Sie mit der Maus auf die Wellenlinie zeigen.

Die bei der Validierung verwendeten Schemata werden durch Abgleichen des `targetNamespace` eines kompilierten Schemas mit der xmlns-Deklaration des Elements gefunden. Kompilierte Schemata werden von einem der folgenden Speicherorte geladen, die entsprechend ihrer Priorität aufgelistet sind:

- Aus dem Dateinamen, der im Feld **Schemas** des Fensters Dokument **Eigenschaften** angegeben ist.

- Aus einem Inlineschema oder einer DTD.

- Aus einer externen DTD oder einem `xsd:schemaLocation`-Attribut und einem `xsd:noNamespaceSchemaLocation`-Attribut.

- Ein Namespace-URI eines "x-schema"-XDR-Schemas.

Schemata können auch an den folgenden zusätzlichen Speicherorten gefunden werden, wenn das Schema einen nicht-leeren Zielnamespace aufweist:

- Ein anderes Editor-Fenster, das das Schema enthält

- In einem Schema in der aktuellen Projektmappe.

- In einem Schema im Verzeichnis des Schemacache.

## <a name="xslt-files"></a>XSLT-Dateien
Wenn Sie eine XSLT-Datei bearbeiten, wird die *XSLT. xsd* -Datei, die sich im Schema Cache befindet, für die Validierung verwendet. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Fehler aus dem XXLT-Compiler werden als rote wellenförmige Unterstreichungen angezeigt.

## <a name="xml-schema-xsd-files"></a>XML-Schema Dateien (XSD)
Beim Bearbeiten einer XML-Schema Datei wird die im Schema Cache befindliche *xsdschema. xsd* -Datei für die Validierung verwendet. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Alle Kompilierungsfehler werden als rote wellenförmige Unterstreichungen angezeigt.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)