---
title: "CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren | Microsoft Docs"
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
  - "CA1824"
  - "MarkAssembliesWithNeutralResourcesLanguage"
helpviewer_keywords: 
  - "MarkAssembliesWithNeutralResourcesLanguage"
  - "CA1824"
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Assembly enthält eine **ResX**\-basierte Ressource, ohne dass <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> auf die Assembly angewendet wurde.  
  
## Regelbeschreibung  
 Mit dem **NeutralResourcesLanguage**\-Attribut wird dem **ResourceManager** die Sprache mitgeteilt, in der die Ressourcen der neutralen Kultur für eine Assembly angezeigt wurden.  Wenn Ressourcen in derselben Kultur gesucht werden, in der sich die Sprache der neutralen Ressourcen befindet, verwendet der **ResourceManager** automatisch die Ressourcen in der Hauptassembly,  anstatt nach einer Satellitenassembly mit der aktuellen Benutzeroberflächenkultur für den aktuellen Thread zu suchen.  Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern.  
  
## Korrigieren von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Assembly das Attribut hinzu und geben dabei die Sprache für die Ressourcen der neutralen Kultur an.  
  
## Festlegen der Sprache  
  
#### So legen Sie die Sprache für die Ressource der neutralen Kultur fest  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Wählen Sie in der linken Navigationsleiste **Anwendung** aus, und klicken Sie dann auf **Assemblyinformationen**.  
  
3.  Wählen Sie im Dialogfeld **Assemblyinformationen** die Sprache aus der Dropdownliste **Neutrale Sprache** aus.  
  
4.  Klicken Sie auf **OK**.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden.  Allerdings könnte die Startleistung abfallen.