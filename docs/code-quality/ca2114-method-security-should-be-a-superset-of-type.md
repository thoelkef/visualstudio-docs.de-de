---
title: 'CA2114: Methodensicherheit sollte Superset des Typs werden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac633134b5b8037eb9e45131128b0ee0cf2887ab
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Methodensicherheit sollte Superset des Typs sein
|||  
|-|-|  
|TypeName|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typ verfügt, deklarativen Sicherheit und einer der Methoden für die gleiche Sicherheitsaktion deklarativen Sicherheit hat die Sicherheitsaktion ist nicht [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands), und die Berechtigungen vom Typ überprüft nicht sind eine Teilmenge der Berechtigungen durch die Methode überprüft.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine Methode sollte nicht sowohl auf einer Methodenebene als auch Typebene deklarative Sicherheit für die gleiche Aktion aufweisen. Zwei Überprüfungen sind nicht kombiniert werden. nur die Methodenebene Anforderung angewendet wird. Wenn Berechtigungen anfordert, ein Typ ermöglicht z. B. `X`, und eine seiner Methoden fordert die Berechtigung `Y`, Code verfügt nicht über die Berechtigung verfügen über `X` zur Ausführung der Methode.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Überprüfen Sie den Code um sicherzustellen, dass beide Aktionen erforderlich sind. Wenn beide Aktionen erforderlich sind, stellen Sie sicher, dass die Aktion Methodenebene die Sicherheit auf Typebene angegeben enthält. Wenn Ihr Typ Berechtigung erfordert z. B. `X`, und die Methode muss auch die Berechtigung anfordern `Y`, die Methode sollte explizit anfordern `X` und `Y`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn die Methode nicht die Sicherheit, die vom angegebenen Typ erfordert. Dies ist allerdings keinem normalen Szenario und Hinweisen zur Überprüfung eine sorgfältige Planung erforderlich.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Umgebungsberechtigungen die Gefahren Verstoß gegen diese Regel veranschaulicht. In diesem Beispiel erstellt der Anwendungscode eine Instanz des gesicherten Typs vor dem Verweigern der Berechtigung, die durch den Typ erforderlich. In einem Bedrohungsszenario mit realen müsste die Anwendung eine weitere Möglichkeit zum Abrufen einer Instanz des Objekts.  
  
 Im folgenden Beispiel fordert die Bibliothek eine Schreibberechtigung für einen Typ und read-Berechtigung für eine Methode.  
  
 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Der folgende Code veranschaulicht die Sicherheitslücke der Bibliothek durch Aufrufen der Methode, obwohl sie die Sicherheit auf Nachrichtenebene Typ-Anforderung nicht erfüllt.  
  
 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **[Alle Berechtigungen] Persönliche Informationen: 6/16/1964 12:00:00 Uhr**  
**[Keine Schreibberechtigung (von Typ gefordert)] Persönliche Informationen: 6/16/1964 12:00:00 Uhr**  
**[Keine Leseberechtigung (von Methode gefordert)] Persönliche Informationen konnte nicht zugegriffen werden: Fehler bei der Anforderung.**   
## <a name="see-also"></a>Siehe auch  
 [Schreiben von sicherem Richtlinien](/dotnet/standard/security/secure-coding-guidelines)   
 [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)   
 [Daten und Modellierung](/dotnet/framework/data/index)