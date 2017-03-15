---
title: "CA2132: Standardkonstruktoren m&#252;ssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2132"
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2132: Standardkonstruktoren m&#252;ssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
> [!NOTE]
>  Diese Warnung wird nur für Code übernommen, in dem die CoreCLR ausgeführt wird \(die Version der CLR, die speziell für Silverlight\-Webanwendungen verwendet wird\).  
  
## Ursache  
 Das Transparenzattribut des Standardkonstruktors einer abgeleiteten Klasse ist nicht so wichtig wie die Transparenz der Basisklasse.  
  
## Regelbeschreibung  
 Typen und Member, die über das <xref:System.Security.SecurityCriticalAttribute> verfügen, können nicht vom Silverlight\-Anwendungscode verwendet werden.  Sicherheitsrelevante Typen und Member können nur von vertrauenswürdigem Code in der .NET Framework for Silverlight\-Klassenbibliothek verwendet werden.  Da eine öffentliche oder geschützte Konstruktion in einer abgeleiteten Klasse mindestens die gleiche Transparenz aufweisen muss wie die zugehörige Basisklasse, können Klassen in einer Anwendung nicht von Klassen abgeleitet werden, die als SecurityCritical markiert sind.  
  
 Bei CoreCLR\-Plattformcode muss der abgeleitete Typ den Standardkonstruktorvererbungsregeln gehorchen, wenn ein Basistyp über einen öffentlichen oder geschützten nicht transparenten Standardkonstruktor verfügt.  Der abgeleitete Typ muss auch über einen Standardkonstruktor verfügen, und dieser Konstruktor muss mindestens wichtiger Standardkonstruktor des Basistyps sein.  
  
## Behandeln von Verstößen  
 Um die Verletzung zu korrigieren, entfernen Sie den Typ, oder nehmen Sie keine Ableitung vom nicht sicherheitstransparenten Typen vor.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Verstöße gegen diese Regel durch Anwendungscode führen dazu, dass CoreCLR das Laden des Typs mit einem <xref:System.TypeLoadException>\-Objekt verweigert.  
  
### Code  
 [!code-cs[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### Kommentare