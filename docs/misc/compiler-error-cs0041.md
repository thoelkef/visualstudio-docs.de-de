---
title: "Compilerfehler CS0041 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0041"
ms.assetid: 80dbfe00-8cdb-4275-9574-8a215c7139d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0041
Der vollqualifizierte Name für "Typ" ist zu lang für Debuginformationen. Führen Sie die Kompilierung ohne die \/debug\-Option durch.  
  
 Dieser Fehler kann auftreten, wenn die [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)\-Compileroption verwendet wird. Wenn dieser Fehler auftritt, versuchen Sie, die PDB\-Dateien im Verzeichnis "bin" zu löschen und neu zu kompilieren. Wenn dieser Fehler weiterhin auftritt, müssen Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] möglicherweise reparieren oder neu installieren.