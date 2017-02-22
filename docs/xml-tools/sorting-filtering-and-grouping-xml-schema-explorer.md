---
title: "Sortieren, Filtern und Gruppieren (XML-Schema-Explorer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Sortieren, Filtern und Gruppieren (XML-Schema-Explorer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema werden die Optionen beschrieben, die im Menü mit den **Filter\-, Sortierungs\- und Gruppierungsoptionen** auf der Symbolleiste des XML\-Schema\-Explorers verfügbar sind.  
  
## Filteroptionen  
 Die folgenden Filteroptionen sind verfügbar.Standardmäßig sind die Optionen **Namespaces anzeigen** und **Schemadateien anzeigen** aktiviert.  
  
-   **Namespaces anzeigen**  
  
-   **Schemadateien anzeigen**  
  
-   **Compositors anzeigen \(sequence\/choice\/all\)**  
  
## Sortierungsoptionen  
 Die folgenden Sortierungsoptionen sind verfügbar.Die Standardeinstellung ist **Nach Typ sortieren**.Die "Sortieren nach"\-Optionen gelten nicht für Dateien und Namespaces.  
  
-   **Nach Typ sortieren**  
  
-   **Nach Namen sortieren**  
  
-   **Nach Dokumentreihenfolge sortieren**  
  
### Nach Typ sortieren  
 Wenn die Option **Nach Typ sortieren** aktiviert ist, werden globale Knoten in der folgenden Reihenfolge sortiert.Knoten sind innerhalb jeder Gruppe alphabetisch sortiert.  
  
1.  `import`\-Knoten  
  
2.  `include`\-Knoten  
  
3.  `redefine`\-Knoten  
  
4.  `attribute`\-Knoten  
  
5.  `attributeGroup`\-Knoten  
  
6.  `complexType`\-Knoten  
  
7.  `simpleType`\-Knoten  
  
8.  `element`\-Knoten  
  
9. `group`\-Knoten  
  
### Nach Namen sortieren  
 Wenn die Option **Nach Namen sortieren** aktiviert ist, werden globale Knoten in der folgenden Reihenfolge sortiert:  
  
1.  `import`\-Knoten \(in alphabetischer Reihenfolge der Namespaces\)  
  
2.  `include`\-Knoten \(in alphabetischer Reihenfolge der `schemaLocation`\-Attribute\)  
  
3.  `redefine`\-Knoten \(in alphabetischer Reihenfolge der `schemaLocation`\-Attribute\)  
  
4.  Andere globale Knoten in alphabetischer Reihenfolge  
  
### Nach Dokumentreihenfolge sortieren  
 Die Option **Nach Dokumentreihenfolge sortieren** ist verfügbar, wenn die Option **Schemadateien anzeigen** aktiviert ist.Wenn **Nach Dokumentreihenfolge sortieren** aktiviert ist, werden globale Knoten in der Reihenfolge angezeigt, in der sie in der Schemadatei vorkommen.  
  
## Speichern von Sortierungs\-\/Filteroptionen  
 Die Sortierungs\-, Filter\- und Gruppierungsoptionen werden in der Registrierung für jeden Benutzer gespeichert, unabhängig davon, welche Projektmappe oder welche Dateien beim Ändern der Einstellungen geöffnet waren.