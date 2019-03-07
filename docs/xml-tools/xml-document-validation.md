---
title: Validierung von XML-Dokumenten in XML-editor
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d9953190220acf572ac04b18e9018c1d45a3b2c
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525747"
---
# <a name="xml-document-validation"></a>Validierung von XML-Dokumenten

Der XML-Editor überprüft XML 1.0-Syntax und führt auch die datenvalidierung während der Eingabe. Die Validierung wird vom Editor mithilfe einer DTD (Document Type Definition) oder eines Schemas vorgenommen. Durch rote wellenförmige Unterstreichungen werden Wohlgeformtheits-Fehler in XML 1.0 hervorgehoben. Blaue Wellenlinien weisen auf semantische Fehler in Abhängigkeit von der DTD- oder Schemavalidierung hin. Jedem Fehler ist ein Eintrag in der Fehlerliste zugeordnet. Sie können die Fehlermeldung auch anzeigen, indem Sie mit der Maus auf die Wellenlinie zeigen.

 Die bei der Validierung verwendeten Schemata werden durch Abgleichen des `targetNamespace` eines kompilierten Schemas mit der xmlns-Deklaration des Elements gefunden. Kompilierte Schemata werden von einem der folgenden Speicherorte geladen, die entsprechend ihrer Priorität aufgelistet sind:

-   Vom Dateinamen angegeben, der **Schemas** Feld des Dokuments **Eigenschaften** Fenster.

-   Aus einem Inlineschema oder einer DTD.

-   Aus einer externen DTD oder einem `xsd:schemaLocation`-Attribut und einem `xsd:noNamespaceSchemaLocation`-Attribut.

-   Ein Namespace-URI eines "x-schema"-XDR-Schemas.

Schemata können auch an den folgenden zusätzlichen Speicherorten gefunden werden, wenn das Schema einen nicht-leeren Zielnamespace aufweist:

-   Ein anderes Editor-Fenster, das das Schema enthält

-   In einem Schema in der aktuellen Projektmappe.

-   In einem Schema im Verzeichnis des Schemacache.

## <a name="xslt-files"></a>XSLT-Dateien
 Beim Bearbeiten einer XSLT-Datei, die *xslt.xsd* Datei im Schemacache für die Validierung verwendet wird. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Fehler aus dem XXLT-Compiler werden als rote wellenförmige Unterstreichungen angezeigt.

## <a name="xml-schema-xsd-files"></a>XML-Schemadateien (XSD)
 Beim Bearbeiten von XML-Schemadatei, die *xsdschema.xsd* Datei im Schemacache für die Validierung verwendet wird. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Alle Kompilierungsfehler werden als rote wellenförmige Unterstreichungen angezeigt.

## <a name="see-also"></a>Siehe auch

- [XML-editor](../xml-tools/xml-editor.md)