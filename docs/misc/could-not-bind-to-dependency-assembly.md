---
title: "Could not bind to dependency &#39;assembly&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cantbinddependency"
ms.assetid: 0f76190d-d57e-4e0e-bec4-532aec978d08
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not bind to dependency &#39;assembly&#39;
Einer der Projektverweise enthält einen Assemblyverweis \(eine Abhängigkeit\), der gefunden wurde, jedoch keine gültige Assembly ist.  Die Erstellung des Projekts wird durch den Fehler nicht beeinträchtigt.  Ein Laufzeitfehler kann jedoch auftreten.  
  
 Diese Situation setzt voraus, dass folgende drei Bedingungen zutreffen:  
  
-   Es gibt mehr als eine Datei mit demselben Namen auf der Festplatte.  
  
-   Eine der Dateien ist keine Assembly, aber die andere ist eine Assembly.  
  
-   Der Verweispfad durchsucht zuerst das Verzeichnis, das die Datei enthält, die keine Assembly ist.  
  
 **So beheben Sie diesen Fehler**  
  
-   Ändern Sie die Reihenfolge, in der das Projekt die Verzeichnisse nach Verweisen durchsucht.  Weitere Informationen finden Sie unter [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/de-de/8e549b39-7256-456a-8fd7-089b23facf9c).  
  
## Siehe auch  
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)   
 [Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweise hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/de-de/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)