---
title: "MSBuild Best Practices | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "best practices, MSBuild"
  - "MSBuild, best practices"
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# MSBuild Best Practices
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es werden die folgenden bewährten Methoden zum Schreiben von MSBuild\-Skripts empfohlen:  
  
-   Standardwerte für Eigenschaften werden am besten mit dem `Condition`\-Attribut verarbeitet und nicht durch Deklarieren einer Eigenschaft, deren Standardwert in der Befehlszeile überschrieben werden kann.  Verwenden Sie beispielsweise  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Vermeiden Sie beim Auswählen von Elementen den Einsatz von Platzhaltern.  Geben Sie stattdessen Dateien explizit an.  Dies erleichtert das Auffinden von Fehlern, die beim Hinzufügen oder Löschen von Dateien auftreten können.  
  
## Siehe auch  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md)