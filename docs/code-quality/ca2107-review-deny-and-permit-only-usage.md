---
title: "CA2107: Überprüfung nur Verwendung von deny und | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edd0bd14a75dfd58ca043bfaa663e2cfb2660e75
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Verwendung von Deny und PermitOnly überprüfen
|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine Methode enthält eine sicherheitsüberprüfung, die angibt, die Sicherheitsaktion PermitOnly "oder" verweigern.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Sicherheitsaktion sollte verwendet werden, nur von Entwicklern mit sehr guten Kenntnissen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Sicherheit. Code, in dem diese Sicherheitsaktionen verwendet werden, sollte einer Sicherheitsüberprüfung unterzogen werden.  
  
 Verweigern ändert das Standardverhalten des den Stackwalk, der als Antwort auf eine sicherheitsforderung auftritt. Sie können Berechtigungen angeben, die für die Dauer der Deny-Methode, unabhängig von den tatsächlichen Berechtigungen der Aufrufer in der Aufrufliste nicht erteilt werden müssen. Wenn der Stackwalk erkennt eine Methode, die durch Verweigern gesichert ist, und der Stackwalk schlägt, wenn die geforderte Berechtigung in den verweigerten Berechtigungen enthalten ist fehl. Die PermitOnly ändert auch das Standardverhalten des Stackwalks. Es kann nur die Berechtigungen anzugeben, die gewährt werden können, unabhängig von den Berechtigungen des Aufrufers. Wenn der Stackwalk erkennt eine Methode, die durch PermitOnly gesichert ist und der Stackwalk schlägt, wenn die geforderte Berechtigung nicht mit den Berechtigungen enthalten ist, die durch die PermitOnly angegeben sind fehl.  
  
 Code, der für diese Aktionen nutzt sollten sorgfältig Sicherheitsrisiken aufgrund ihrer begrenzten Nützlichkeit und leicht unterschiedliches Verhalten bewertet werden. Nehmen wir einmal die folgende Situation:  
  
-   [Verknüpfen von Forderungen](/dotnet/framework/misc/link-demands) sind von Deny und PermitOnly nicht betroffen.  
  
-   Wenn Deny oder PermitOnly im gleichen Stapelrahmen wie die Anforderung ausgeführt wird, die bewirkt, den Stackwalk dass, haben die Sicherheitsaktionen keine Auswirkungen.  
  
-   Werte, die zum Erstellen von pfadbasierten Berechtigungen verwendet werden, können in der Regel auf verschiedene Weise angegeben werden. Verweigern des Zugriffs auf eine Form des Pfads wird nicht auf alle Formulare verweigern. Wenn eine Dateifreigabe beispielsweise \\\Server\Share einem Netzwerklaufwerk "x:", verweigert den Zugriff auf eine Datei auf der Freigabe zugeordnet ist Sie verweigern müssen \\\Server\Share\File, X:\File und jeder anderen Pfad, der auf die Datei zugreift.  
  
-   Ein <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> kann einen Stackwalk beendet, bevor Deny oder PermitOnly erreicht wird.  
  
-   Wenn Deny keine Auswirkung hat, nämlich kann Wenn ein Aufrufer eine Berechtigung verfügt, die durch das Verweigern blockiert ist der Aufrufer direkt auf die geschützte Ressource zugreifen unter Umgehung der DENY-Anweisung. Wenn der Aufrufer nicht über die verweigerte Berechtigung verfügt, schlägt der Stackwalk ohne die DENY-Anweisung fehl.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Alle Verwendungen von diese Sicherheitsaktionen bewirkt eine Verletzung. Um einen Verstoß zu beheben, verwenden Sie diese Sicherheitsaktionen nicht.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, nur nach der Durchführung einer sicherheitsüberprüfung.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einige Einschränkungen der DENY-Anweisung.  
  
 Die folgenden Bibliothek enthält eine Klasse mit zwei Methoden, die mit Ausnahme der sicherheitsforderungen identisch sind, die sie schützen.  
  
 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Die folgende Anwendung zeigt die Auswirkungen der DENY-Anweisung auf die sicheren Methoden aus der Bibliothek.  
  
 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **Bei Bedarf: Des Aufrufers Deny wirkt sich nicht bei Bedarf mit der erklärten Berechtigung.**  
**LinkDemand: Des Aufrufers Deny hat keine Auswirkungen auf LinkDemand mit der erklärten Berechtigung.**  
**LinkDemand: Des Aufrufers Deny wirkt sich nicht mit Code LinkDemand geschützt.**  
**LinkDemand: Dieser DENY-Anweisung hat keine Auswirkungen durch Code LinkDemand geschützt.**   
## <a name="see-also"></a>Siehe auch  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)   

