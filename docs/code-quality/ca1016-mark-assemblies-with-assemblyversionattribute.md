---
title: "CA1016: Assemblys mit AssemblyVersionAttribute markieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016: Assemblys mit AssemblyVersionAttribute markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Die Assembly verfügt nicht über eine Versionsnummer.  
  
## Regelbeschreibung  
 Die Identität einer Assembly besteht aus den folgenden Informationen:  
  
-   Assemblyname  
  
-   Versionsnummer  
  
-   Kultur  
  
-   Öffentlicher Schlüssel \(für Assemblys mit starkem Namen\).  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwendet die Versionsnummer für die eindeutige Identifizierung einer Assembly und zum Binden an Datentypen in Assemblys mit starkem Namen.  Die Versionsnummer wird zusammen mit der Versions\- und Herausgeberrichtlinie verwendet.  Standardmäßig werden Anwendungen nur mit der Assemblyversion ausgeführt, mit der sie erstellt wurden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Assembly mithilfe des <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>\-Attributs eine Versionsnummer hinzu.  \(Siehe nachstehendes Beispiel.\)  
  
## Wann sollten Warnungen unterdrückt werden?  
 Bei Assemblys, die von Dritten oder in einer Produktionsumgebung verwendet werden, sollte keine Warnung dieser Regel unterdrückt werden.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Assembly, auf die das <xref:System.Reflection.AssemblyVersionAttribute>\-Attribut angewendet wurde.  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## Siehe auch  
 [Assemblyversionen](../Topic/Assembly%20Versioning.md)   
 [Gewusst wie: Erstellen einer Herausgeberrichtlinie](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)