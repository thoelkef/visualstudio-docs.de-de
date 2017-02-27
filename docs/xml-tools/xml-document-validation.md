---
title: "Validierung von XML-Dokumenten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Validierung von XML-Dokumenten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der XML\-Editor überprüft die XML 1.0\-Syntax und validiert bereits beim Eingeben die Daten.Die Validierung wird vom Editor mithilfe einer DTD \(Document Type Definition\) oder eines Schemas vorgenommen.Durch rote wellenförmige Unterstreichungen werden Wohlgeformtheits\-Fehler in XML 1.0 hervorgehoben.Blaue Wellenlinien weisen auf semantische Fehler in Abhängigkeit von der DTD\- oder Schemavalidierung hin.Jedem Fehler ist ein Eintrag in der Fehlerliste zugeordnet.Sie können die Fehlermeldung auch anzeigen, indem Sie mit der Maus auf die Wellenlinie zeigen.  
  
 Die bei der Validierung verwendeten Schemata werden durch Abgleichen des `targetNamespace` eines kompilierten Schemas mit der xmlns\-Deklaration des Elements gefunden.Kompilierte Schemata werden von einem der folgenden Speicherorte geladen, die entsprechend ihrer Priorität aufgelistet sind:  
  
-   Von dem Dateinamen, der im Eigenschaftenfenster des Dokuments im **Schemata**\-Feld angegeben ist.  
  
-   Aus einem Inlineschema oder einer DTD.  
  
-   Aus einer externen DTD oder einem `xsd:schemaLocation`\-Attribut und einem `xsd:noNamespaceSchemaLocation`\-Attribut.  
  
-   Ein Namespace\-URI eines "x\-schema"\-XDR\-Schemas.  
  
 Schemas finden Sie auch an den folgenden zusätzlichen Orten, wenn der Zielnamespace des Schemas nicht leer ist:  
  
-   Ein anderes Editor\-Fenster, das das Schema enthält  
  
-   Ein Schema in der aktuellen Projektmappe  
  
-   Ein Schema im Verzeichnis des Schemacache  
  
## XSLT\-Dateien  
 Beim Bearbeiten einer XSLT\-Datei wird die im Schemacache befindliche Datei **xslt.xsd** für die Validierung verwendet.Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt.Fehler aus dem XXLT\-Compiler werden als rote wellenförmige Unterstreichungen angezeigt.  
  
## XSD\-Dateien \(XML Schema Language\)  
 Beim Bearbeiten einer XSD\-Datei wird die im Schemacache enthaltene Datei **xsdschema.xsd** für die Validierung verwendet.Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt.Alle Kompilierungsfehler werden als rote wellenförmige Unterstreichungen angezeigt.  
  
## Siehe auch  
 [XML\-Editor](../xml-tools/xml-editor.md)