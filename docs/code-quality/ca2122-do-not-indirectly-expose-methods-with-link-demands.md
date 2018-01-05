---
title: 'CA2122: Machen Methoden mit Linkaufrufen nicht indirekt | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fc1d8c2ea663862e44b3092b0e2b8489eff3df6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen
|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter Member verfügt über eine [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands) und wird aufgerufen, indem Sie einen Member, der keine sicherheitsüberprüfungen ausführt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein Linkaufruf überprüft nur die Berechtigungen des unmittelbaren Aufrufers. Wenn ein Element `X` macht keine sicherheitsforderungen Aufrufer und Code geschützt durch einen Linkaufruf einen Aufrufer ohne die erforderliche Berechtigung verwenden, kann Aufrufe `X` auf den geschützten Member zuzugreifen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Fügen Sie ein Sicherheitstoken [Daten und Modellierung](/dotnet/framework/data/index) oder bei Bedarf auf den Member verknüpfen, sodass es nicht mehr ungesicherten Zugriff auf den Link Bedarf geschützte Member bereitstellt.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Um problemlos eine Warnung dieser Regel zu unterdrücken, müssen Sie sicherstellen, dass Ihr Code keine seine Aufrufer gewährt Zugriff auf Vorgänge oder Ressourcen, die einen destruktiven Weise verwendet werden können.  
  
## <a name="example"></a>Beispiel  
 Die folgenden Beispiele zeigen eine Bibliothek, die die Regel verletzt und eine Anwendung, die die Bibliothek aufzeigt. Die Beispielbibliothek bietet zwei Methoden, die zusammen die Regel verletzen. Die `EnvironmentSetting` Methode wird durch einen Linkaufruf für uneingeschränkten Zugriff auf Umgebungsvariablen gesichert. Die `DomainInformation` Methode ist keine sicherheitsforderungen Aufrufer vor `EnvironmentSetting`.  
  
 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Die folgende Anwendung ruft die unsicheren Bibliothekmembers.  
  
 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **Wert von unsichere Mitglied: "Seattle.corp.contoso.com"**   
## <a name="see-also"></a>Siehe auch  
 [Schreiben von sicherem Richtlinien](/dotnet/standard/security/secure-coding-guidelines)   
 [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)   
 [Daten und Modellierung](/dotnet/framework/data/index)