---
title: "XML-Schemata (Dialogfeld) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XML-Schemata (Dialogfeld)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Dialogfeld **XML\-Schemas** wird verwendet, um festzulegen, welche Schemas der XML\-Schemadefinitionssprache \(XML schema definition language, XSD\) einem XML\-Dokument zugeordnet werden sollen.Es kann ein Schema aus dem Schemacache ausgewählt oder ein Schema angegeben werden, das sich nicht im Cache befindet.Ausgewählte Schemas werden als Teil eines Schemasatzes behandelt.Das Schemaset wird für IntelliSense und zur Überprüfung von XML\-Dokumenten verwendet.  
  
 Sie können auf das Dialogfeld **XML\-Schemas** zugreifen, indem Sie im Eigenschaftenfenster des Dokuments auf die Schaltfläche **Schemas** klicken oder im Menü **XML** die Option **Schemas** wählen.  
  
## UIElement-Liste  
 **Verwendung**  
 Wählen Sie aus, wie das XML\-Schema verwendet werden soll.  
  
-   **Automatisch**.Dieses Schema wird vom aktuellen Dokument nicht verwendet, ist jedoch für eine automatische Zuordnung verfügbar.Wenn im XML\-Dokument ein Namespace deklariert wird, der dem `targetNamespace` dieses Schemas entspricht, wird das Schema automatisch zugeordnet und dem Schemaset hinzugefügt.  
  
-   **Dieses Schema verwenden**.Dieses Schema wird vom aktuellen Dokument verwendet.Entweder wurde die Verwendung dieses Schemas durch Klicken auf diese Spalte explizit durch den Benutzer festgelegt, oder das Schema wurde auf Grundlage eines übereinstimmenden `targetNamespace` automatisch zugeordnet.  
  
-   **Ausgewählte Schemas nicht verwenden**.Dieses Schema wird vom aktuellen Dokument nicht verwendet. Dies gilt auch, wenn ein mit dem Schema übereinstimmender `targetNamespace` vorhanden ist.Diese Einstellung ist nützlich zum Lösen von Konflikten, wenn sich mehrere Versionen desselben Schemas im Schemacache oder der Projektmappe befinden.  
  
 **Zielnamespace**  
 Zeigt den dem XML\-Schema zugeordneten Zielnamespace an.  
  
 **Dateiname**  
 Zeigt den Dateinamen des XML\-Schemas an.  
  
 **Hinzufügen**  
 Öffnet das Dialogfeld **XSD\-Schema öffnen**, in dem Sie dem Schemaset zusätzliche Schemas hinzufügen können.Wenn Sie dem Schemaset ein Schema hinzufügen, wird der Wert der Spalte **Verwendung** auf **Dieses Schema verwenden** festgelegt.  
  
 **Entfernen**  
 Entfernt das ausgewählte Schema aus dem Schemaset.Dies entfernt das Schema aus dem Schemacache im Speicher, jedoch nicht aus dem Dateisystem.  
  
## Siehe auch  
 [Komponenten des XML\-Editors](../xml-tools/xml-editor-components.md)   
 [Gewusst wie: Auswählen der zu verwendenden XML\-Schemas](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Schemacache](../xml-tools/schema-cache.md)