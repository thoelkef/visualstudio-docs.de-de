---
title: "Security of Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, security"
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# Security of Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Überlegungen zur Sicherheit von Textvorlagen:  
  
-   Textvorlagen sind anfällig für das Einfügen von beliebigem Code.  
  
-   Wenn der vom Host zur Suche nach Direktivenprozessoren verwendete Mechanismus nicht sicher ist, kann ein böswilliger Direktivenprozessor ausgeführt werden.  
  
## Beliebiger Code  
 Wenn Sie eine Vorlage schreiben, können Sie innerhalb der \<\# \#\>\-Tags beliebigen Code einfügen.  Dadurch kann beliebiger Code innerhalb einer Textvorlage ausgeführt werden.  
  
 Verwenden Sie nur Vorlagen aus vertrauenswürdigen Quellen.  Weisen Sie die Endbenutzer der Anwendung darauf hin, dass Vorlagen, die nicht aus vertrauenswürdigen Quellen stammen, nicht ausgeführt werden dürfen.  
  
## Böswilliger Direktivenprozessor  
 Das Textvorlagenmodul interagiert mit einem Transformationshost und einem oder mehreren Direktivenprozessoren, um den Vorlagentext in eine Ausgabedatei zu transformieren.  Weitere Informationen finden Sie unter [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Wenn der vom Host zur Suche nach Direktivenprozessoren verwendete Mechanismus nicht sicher ist, besteht die Gefahr, dass ein böswilliger Direktivenprozessor ausgeführt wird.  Der böswillige Direktivenprozessor könnte Code bereitstellen, der bei der Ausführung der Vorlage im `FullTrust`\-Modus ausgeführt wird.  Wenn Sie einen benutzerdefinierten Textvorlagen\-Transformationshost erstellen, müssen Sie für das Modul einen sicheren Mechanismus zur Suche nach Direktivenprozessoren implementieren \(z. B. die Registrierung\).