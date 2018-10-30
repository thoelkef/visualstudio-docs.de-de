---
title: 'CA2114: Methodensicherheit sollte Superset des Typs sein | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5bdb7d5eb43958a892320fad244625f09fcd7592
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878283"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Methodensicherheit sollte Superset des Typs sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ verfügt über die deklarative Sicherheit und eine seiner Methoden die deklarative Sicherheit für die gleiche Aktion für die Sicherheit hat und die Sicherheitsaktion nicht [Verknüpfungsaufrufe](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) oder [Vererbungsanforderungen](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9), und die Berechtigungen überprüft, von dem Typ sind keine Teilmenge der Berechtigungen von der Methode überprüft.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Methode sollte nicht sowohl eine Methode auf und Typebene deklarative Sicherheit für die gleiche Aktion aufweisen. Die zwei Überprüfungen sind nicht kombiniert werden; Es wird nur auf die Anforderung auf Methodenebene angewendet. Angenommen, ein Berechtigung anfordert `X`, und eine seiner Methoden fordert die Berechtigung `Y`, Code verfügt nicht über die Berechtigung verfügen über `X` zum Ausführen der Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie Ihren Code, um sicherzustellen, dass beide Aktionen erforderlich sind. Wenn beide Aktionen erforderlich sind, stellen Sie sicher, dass die Aktion auf Methodenebene, die Sicherheit auf Typebene angegeben enthält. Wenn Ihr Typ Berechtigung erfordert z. B. `X`, und die Methode muss auch die Berechtigung anfordern `Y`, die Methode sollte explizit anfordern `X` und `Y`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn die Methode nicht die Sicherheit, die vom angegebenen Typ erforderlich ist. Dies ist jedoch keinem normalen Szenario und möglicherweise die Notwendigkeit von Entwurf sorgfältig zu überprüfen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Umgebungsberechtigungen die Gefahren des Verstoßes gegen diese Regel veranschaulicht. In diesem Beispiel erstellt der Anwendungscode eine Instanz des gesicherten Typs vor dem Verweigern der Berechtigung, die durch den Typ erforderlich. In einem Bedrohungsszenario mit echten benötigt die Anwendung eine andere Möglichkeit, eine Instanz des Objekts abzurufen.

 Im folgenden Beispiel fordert die Bibliothek Schreibberechtigungen für einen Typ und read-Berechtigung für eine Methode.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Beispiel
 Der folgende Code veranschaulicht die Sicherheitsrisiken für die Bibliothek durch Aufrufen der Methode, obwohl sie die Sicherheit auf Zeilenebene Typ Anforderungen nicht erfüllt.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **[Alle Berechtigungen] Persönliche Informationen: 6/16/1964 12:00:00 Uhr**
 **[keine Schreibberechtigung (nach Typ gefordert)] persönliche Informationen: 6/16/1964 12:00:00 Uhr**
 **[read keine Berechtigung () von Methode gefordert)] konnte nicht zugegriffen werden persönliche Informationen: Fehler bei der Anforderung.**
## <a name="see-also"></a>Siehe auch
 [Sichern Sie die Richtlinien für das Codieren](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Vererbungsanforderungen](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [Linkaufrufe](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten und Modellierung](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



