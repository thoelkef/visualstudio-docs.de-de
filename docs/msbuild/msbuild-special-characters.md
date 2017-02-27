---
title: "MSBuild Special Characters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "escape characters"
  - "escape"
  - "MSBuild Escape Characters"
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# MSBuild Special Characters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reserviert einige Zeichen zur besonderen Verwendung in bestimmten Kontexten.  Sie müssen diese Zeichen nur mit Escapezeichen versehen, wenn Sie sie im reservierten Kontext als Literal verwenden möchten.  So hat ein Sternchen \(\*\) nur für das `Include`\-Attribut und das `Exclude`\-Attribut einer Elementdefinition sowie in Aufrufen von `CreateItem` eine besondere Bedeutung.  Wenn ein Sternchen in diesen Kontexten als Sternchen angezeigt werden soll, müssen Sie es mit einem Escapezeichen versehen.  Geben Sie in jedem anderen Kontext das Sternchen dort ein, wo es angezeigt werden soll.  
  
 Um ein Sonderzeichen mit Escapezeichen zu versehen, verwenden Sie die Syntax %*xx*, wobei *xx* den Hexadezimalwert des ASCII\-Zeichens darstellt.  Weitere Informationen finden Sie unter [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## Sonderzeichen  
 In der folgenden Tabelle sind die Sonderzeichen von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aufgeführt:  
  
|**Zeichen**|**ASCII**|**Reservierte Verwendung**|  
|-----------------|---------------|--------------------------------|  
|%|%25|Verweis auf Metadaten|  
|$|%24|Verweis auf Eigenschaften|  
|@|%40|Verweis auf Elementlisten|  
|'|%27|Bedingungen und andere Ausdrücke|  
|;|%3B|Listentrennzeichen|  
|?|%3F|Platzhalterzeichen für Dateinamen im `Include`\-Attribut und im `Exclude`\-Attribut|  
|\*|%2A|Platzhalterzeichen für Dateinamen im `Include`\-Attribut und im `Exclude`\-Attribut|  
  
## Siehe auch  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md)   
 [Items](../msbuild/msbuild-items.md)