---
title: 'CA2107: Überprüfen Sie Deny und nur die Verwendung zulassen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f273ea5f58babf7a0c04f6b0758732d43aab7db
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547770"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Verwendung von Deny und PermitOnly überprüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode enthält eine Sicherheitsüberprüfung, die die PermitOnly-oder Deny-Sicherheitsaktion angibt.

## <a name="rule-description"></a>Beschreibung der Regel
 Der, der [die PermitOnly-Methode](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) und die <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Sicherheitsaktionen verwendet, sollte nur von denjenigen verwendet werden, die über erweiterte Kenntnisse der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Sicherheit verfügen. Code, in dem diese Sicherheitsaktionen verwendet werden, sollte einer Sicherheitsüberprüfung unterzogen werden.

 Deny ändert das Standardverhalten des Stackwalk, der als Reaktion auf eine Sicherheitsanforderung auftritt. Sie können Berechtigungen angeben, die für die Dauer der verweigerten Methode nicht erteilt werden dürfen, unabhängig von den tatsächlichen Berechtigungen der Aufrufer in der Aufruf Listen. Wenn der Stackwalk eine Methode erkennt, die durch Deny geschützt ist, und wenn die angeforderte Berechtigung in den verweigerten Berechtigungen enthalten ist, schlägt der Stapel Durchlauf fehl. PermitOnly ändert auch das Standardverhalten des Stackwalk. Es ermöglicht es Code, nur die Berechtigungen anzugeben, die unabhängig von den Berechtigungen der Aufrufer erteilt werden können. Wenn der Stackwalk eine Methode erkennt, die von PermitOnly geschützt ist, und wenn die angeforderte Berechtigung nicht in den Berechtigungen enthalten ist, die von PermitOnly angegeben werden, schlägt der Stapel Durchlauf fehl.

 Code, der sich auf diese Aktionen stützt, sollte aufgrund der eingeschränkten Nützlichkeit und des feinen Verhaltens sorgfältig auf Sicherheitsrisiken geprüft werden. Beachten Sie Folgendes:

- [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) Aufrufe werden von Deny oder PermitOnly nicht beeinträchtigt.

- Wenn Deny oder PermitOnly im gleichen Stapel Rahmen wie die Anforderung auftritt, die den Stapel Durchlauf verursacht, haben die Sicherheitsaktionen keine Auswirkung.

- Werte, die zum Erstellen von Pfad basierten Berechtigungen verwendet werden, können in der Regel auf verschiedene Weise angegeben werden. Durch das Verweigern des Zugriffs auf eine Form des Pfads wird nicht der Zugriff auf alle Formulare verweigert. Wenn z. b. eine Dateifreigabe \\ \server\freigabe einem Netzwerklaufwerk X: zugeordnet ist, müssen Sie zum Verweigern des Zugriffs auf eine Datei auf der Freigabe " \\ \server\share\file", "x:\file" und jedem anderen Pfad, der auf die Datei zugreift, verweigern.

- Ein <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> kann einen Stapel Durchlauf beenden, bevor Deny oder PermitOnly erreicht wird.

- Wenn ein Deny einen Effekt hat, d. h., wenn ein Aufrufer über eine Berechtigung verfügt, die durch den Deny blockiert ist, kann der Aufrufer direkt auf die geschützte Ressource zugreifen und dabei den Deny umgehen. Wenn der Aufrufer nicht über die verweigerte Berechtigung verfügt, würde der Stapel Durchlauf auch ohne Deny fehlschlagen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Jede Verwendung dieser Sicherheitsaktionen führt zu einer Verletzung. Verwenden Sie diese Sicherheitsaktionen nicht, um einen Verstoß zu beheben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung aus dieser Regel erst, nachdem Sie eine Sicherheitsüberprüfung durchgeführt haben.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden einige Einschränkungen von Deny veranschaulicht.

 Die folgende Bibliothek enthält eine-Klasse mit zwei Methoden, die mit Ausnahme der Sicherheitsanforderungen, die Sie schützen, identisch sind.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung veranschaulicht die Auswirkungen von Deny auf gesicherte Methoden aus der Bibliothek.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Demand: die DENY-Anweisung des Aufrufers hat keine Auswirkung auf den Bedarf mit der bestätigten Berechtigung.** 
 **LinkDemand: die DENY-Anweisung des Aufrufers hat keine Auswirkung auf LinkDemand mit der bestätigten Berechtigung.** 
 **LinkDemand: das Deny des Aufrufers hat keine Auswirkung auf den Code, der von LinkDemand geschützt wird.** 
 **LinkDemand: dieses Deny hat keine Auswirkung auf den Code, der von LinkDemand geschützt wird.**
## <a name="see-also"></a>Weitere Informationen
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) Überschreiben von [Sicherheitsüberprüfungen](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [mithilfe der PermitOnly-Methode](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
