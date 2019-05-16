---
title: 'CA2107: Deny und PermitOnly überprüfen | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d6ba41720ff97ffe9a085774477b2a9ee6426dbe
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687389"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Verwendung von Deny und PermitOnly überprüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode enthält eine sicherheitsüberprüfung, die angibt, die Sicherheitsaktion PermitOnly "oder" ablehnen.

## <a name="rule-description"></a>Regelbeschreibung
 Die [verwenden der PermitOnly-Methode](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) und <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Sicherheitsaktionen verwendet werden sollte, nur von Kenntnissen der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Sicherheit. Code, in dem diese Sicherheitsaktionen verwendet werden, sollte einer Sicherheitsüberprüfung unterzogen werden.

 Verweigern ändert das Standardverhalten des Stackwalks, die als Reaktion auf eine sicherheitsforderung auftritt. Sie können Berechtigungen angeben, die für die Dauer der Deny-Methode, unabhängig von den tatsächlichen Berechtigungen der Aufrufer in der Aufrufliste nicht gewährt werden müssen. Wenn der Stackwalk erkennt eine Methode, die durch das Verweigern gesichert ist, und der Stackwalk schlägt, wenn die geforderte Berechtigung in der verweigerten Berechtigungen enthalten ist fehl. PermitOnly ändert auch das Standardverhalten des Stackwalks. Sie können Code nur die Berechtigungen an, die gewährt werden können, unabhängig von den Berechtigungen des Aufrufers. Wenn der Stackwalk erkennt eine Methode, die durch PermitOnly gesichert ist, und der Stackwalk schlägt, wenn die angeforderte Berechtigung nicht mit den Berechtigungen enthalten ist, die durch die PermitOnly angegeben werden fehl.

 Sicherheitsrisiken aufgrund ihrer begrenzten nutzen und ein leicht unterschiedliches Verhalten sollte der Code, der für diese Aktionen beruht sorgfältig bewertet werden. Nehmen wir einmal die folgende Situation:

- [Linkaufrufe](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) durch Deny oder PermitOnly nicht betroffen sind.

- Im Falle Deny oder PermitOnly im gleichen Stapelrahmen wie die Anforderung, bei dem der Stapeldurchlauf, haben die Sicherheitsaktionen keine Auswirkungen.

- Werte, die zum Erstellen der pfadbasierten Berechtigungen verwendet werden, können in der Regel auf unterschiedliche Weise angegeben werden. Verweigern des Zugriffs auf eine Form des Pfads wird Zugriff auf alle Formulare nicht verweigert werden. Wenn eine Dateifreigabe beispielsweise \\\Server\Share zugeordnet ist, auf einem Netzlaufwerk X:, zum Verweigern von Zugriff auf eine Datei auf der Freigabe, Sie müssen verweigert \\\Server\Share\File, X:\File und alle anderen Pfade, die auf die Datei zugreift.

- Ein <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> kann einen Stackwalk beendet, bevor Deny oder PermitOnly erreicht wird.

- Wenn Deny keine Auswirkung hat, beispielsweise kann Wenn ein Aufrufer eine Berechtigung verfügt, die durch das verweigern, blockiert ist der Aufrufer direkt auf die geschützte Ressource zugreifen unter Umgehung der. Wenn der Aufrufer nicht über die verweigerte Berechtigung verfügt, würde der Stackwalk ohne Deny fehlschlagen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Jede Verwendung dieser Aktionen Sicherheit bewirkt eine Verletzung. Um einen Verstoß zu beheben, verwenden Sie nicht diese Sicherheitsaktionen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, nur nach dem Durchführen einer sicherheitsüberprüfung.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einige Einschränkungen der verweigern.

 Die folgende Bibliothek enthält eine Klasse mit zwei Methoden, die mit Ausnahme von sicherheitsanforderungen identisch sind, die sie schützen.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung zeigt die Auswirkungen von Deny auf die geschützten Methoden aus der Bibliothek.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Anforderung: Verweigern des Aufrufers wirkt sich nicht bei Bedarf mit der bestätigten Berechtigung. ** 
 **LinkDemand: Verweigern des Aufrufers wirkt sich nicht auf LinkDemand mit der bestätigten Berechtigung. ** 
 **LinkDemand: Verweigern des Aufrufers wirkt sich nicht durch LinkDemand geschützten Code aus. ** 
 **LinkDemand: Dieser verweigern wirkt sich nicht durch LinkDemand geschützten Code aus.**
## <a name="see-also"></a>Siehe auch
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Sichern Sie die Richtlinien für das Codieren](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Überschreiben von Sicherheitsüberprüfungen](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [verwenden der PermitOnly-Methode](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
