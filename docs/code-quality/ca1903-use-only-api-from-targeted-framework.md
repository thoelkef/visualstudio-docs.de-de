---
title: 'CA1903: Nur API aus Zielframework verwenden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d20496fae54b0fdf2b0f0d17de0590c325bab0ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Nur API aus Zielframework verwenden
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Kategorie|Microsoft.Portability|  
|Unterbrechende Änderung|Unterbrechend – Wenn Sie mit der Signatur eines extern sichtbaren Members oder Typs ausgelöst.<br /><br /> Nicht unterbrechend – Wenn im Text einer Methode ausgelöst.|  
  
## <a name="cause"></a>Ursache  
 Ein Member oder Typ verwendet ein Member oder Typ, der in einem Servicepack eingeführt wurde, nicht in das Zielframework des Projekts enthalten ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Neue Elemente und Typen wurden in .NET Framework 2.0 Service Pack 1 und 2, .NET Framework 3.0 Servicepack 1 und 2 und .NET Framework 3.5 Servicepack 1 enthalten. Projekte, die den Hauptversionen von .NET Framework als Ziel dauert unbeabsichtigt Abhängigkeiten auf diesen neuen APIs. Um diese Abhängigkeit zu verhindern, wird diese Regel ausgelöst, nach Verwendung eines beliebigen neue Elemente und Typen, die nicht standardmäßig mit Zielframework des Projekts enthalten sind.  
  
 **Zielframework und Service Pack-Abhängigkeiten**  
  
|||  
|-|-|  
|Wenn ist Zielframework|Wird ausgelöst, auf die Verwendungen der Elemente, die in eingeführt|  
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|Nicht zutreffend|  
  
 Um das Zielframework des Projekts ändern möchten, finden Sie unter [für eine bestimmte .NET Framework-Version](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um die Abhängigkeit auf das Servicepack zu entfernen, entfernen Sie alle Verwendungen des neuen Member oder Typ aus. Ist dies eine absichtliche Abhängigkeit, die Warnung unterdrücken, oder diese Regel deaktivieren.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, wenn dies nicht absichtliche Abhängigkeit des angegebenen Servicepacks war. In diesem Fall möglicherweise nicht Ihrer Anwendung zur Ausführung auf Systemen ohne dieses Servicepack installiert. Unterdrückt die Warnung aus, oder diese Regel deaktivieren, wenn dies eine absichtliche Abhängigkeit wurde.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Klasse, die den Datentyp "DateTimeOffset" verwendet, die nur in .NET 2.0 Service Pack 1 verfügbar ist. Dieses Beispiel erfordert, dass .NET Framework 2.0 in der Dropdownliste Zielframework in den Projekteigenschaften ausgewählt wurde.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel werden der zuvor beschriebenen Verstoß durch Ersetzen der Verwendungen des Typs "DateTimeOffset" mit dem Typ "DateTime" korrigiert.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [Portabilitätswarnungen](../code-quality/portability-warnings.md)   
 [Festlegen einer bestimmten .NET-Framework-Version](../ide/targeting-a-specific-dotnet-framework-version.md)