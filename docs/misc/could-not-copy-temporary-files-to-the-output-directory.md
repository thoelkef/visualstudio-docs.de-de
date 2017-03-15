---
title: "Die tempor&#228;ren Dateien konnten nicht in das Ausgabeverzeichnis kopiert werden | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_copy_to_run_dir"
ms.assetid: b8b54984-74c9-4b9b-8164-d0d13c141055
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die tempor&#228;ren Dateien konnten nicht in das Ausgabeverzeichnis kopiert werden
Das Projektsystem konnte die temporären Dateien nicht in das Ausgabeverzeichnis kopieren. Compiler verwenden für ihre Buildausgabe immer Zwischenverzeichnisse, beispielsweise „obj\\`configname`“. Nach Abschluss des Buildprozesses kopiert das Projektsystem die Dateien aus dem Zwischenverzeichnis in das Projektausgabeverzeichnis.  
  
 Dieses Problem kann auftreten, wenn eine der zu kompilierenden Assemblys größer ist als 64 KB \(Kilobytes\) und mindestens eine der folgenden Bedingungen zutrifft:  
  
-   Die Projektmappe enthält Projekte, die in denselben Ausgabeordner kompiliert werden.  
  
-   Die „Lokale Kopie“\-Eigenschaft von einer der Assemblys oder einem der Projekte, auf die verwiesen wird, ist auf „False“ festgelegt.  
  
 **So beheben Sie diesen Fehler**  
  
-   Kompilieren Sie die Ausgaben für einzelne Projekte in unterschiedliche Ordner.  
  
-   Legen Sie die „Lokale Kopie“\-Eigenschaft der Assembly oder des Projekts, auf die bzw. das verwiesen wird, auf „True“ fest.  
  
-   Stellen Sie sicher, dass das Objektkatalogfenster nicht geöffnet ist.  
  
-   Vergewissern Sie sich, dass dasselbe Projekt \(oder dieselben Projekte\) nicht in einer anderen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] geöffnet ist \(sind\).  
  
## Siehe auch  
 [NIB: Gewusst wie: Festlegen der Eigenschaft „Lokale Kopie“ eines Verweises](http://msdn.microsoft.com/de-de/dfe2ba13-f27f-4356-a481-ea67d5acacbd)