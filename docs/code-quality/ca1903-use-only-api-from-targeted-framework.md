---
title: "CA1903: Nur API aus Zielframework verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# CA1903: Nur API aus Zielframework verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Kategorie \(Category\)|Microsoft.Portability|  
|Unterbrechende Änderung|Unterbrechend – Bei Auslösung gegen die Signatur eines extern sichtbaren Members oder Typs.<br /><br /> Nicht unterbrechend – Bei Auslösung im Text einer Methode.|  
  
## Ursache  
 Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist.  
  
## Regelbeschreibung  
 In .NET Framework 2.0 Service Pack 1 und 2, .NET Framework 3.0 Service Pack 1 und 2 sowie .NET Framework 3.5 Service Pack 1 wurden neue Member und Typen aufgenommen.  Projekte, die auf die Hauptversionen von .NET Framework abzielen, können unabsichtlich Abhängigkeiten von diesen neuen APIs zeigen.  Um derartige Abhängigkeiten zu vermeiden, wird diese Regel bei Verwendung aller neuen Member und Typen ausgelöst, die nicht standardmäßig im Zielframework des Projekts enthalten waren.  
  
 **Zielframework und Service Pack\-Abhängigkeiten**  
  
|||  
|-|-|  
|Verwendetes Zielframework|Auslösung bei Verwendung von Membern aus|  
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|Nicht zutreffend|  
  
 Weitere Informationen zum Ändern des Zielframeworks eines Projekts finden Sie unter [Festlegen einer bestimmten .NET\-Framework\-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## Behandeln von Verstößen  
 Um die Abhängigkeit vom Service Pack zu entfernen, entfernen Sie alle Verwendungen des neuen Members oder Typs.  Wenn es sich um eine absichtliche Abhängigkeit handelt, können Sie die Warnung unterdrücken oder diese Regel deaktivieren.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie die durch diese Regel ausgelöste Warnung nicht, wenn dies keine absichtliche Abhängigkeit von dem jeweiligen Service Pack ist.  In diesem Fall kann die Anwendung in Systemen, in denen dieses Service Pack nicht installiert ist, möglicherweise nicht mehr ausgeführt werden.  Bei einer absichtlichen Abhängigkeit können Sie die Warnung unterdrücken oder diese Regel deaktivieren.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Klasse gezeigt, die den Typ DateTimeOffset verwendet, der nur in .NET 2.0 Service Pack 1 verfügbar ist.  Dieses Beispiel erfordert, dass .NET Framework 2.0 in der Dropdownliste Zielframework in den Projekteigenschaften ausgewählt wurde.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird der vorherige Verstoß behoben, indem der Typ DateTimeOffset durch den Typ DateTime ersetzt wird.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## Siehe auch  
 [Portabilitätswarnungen](../code-quality/portability-warnings.md)   
 [Festlegen einer bestimmten .NET\-Framework\-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md)