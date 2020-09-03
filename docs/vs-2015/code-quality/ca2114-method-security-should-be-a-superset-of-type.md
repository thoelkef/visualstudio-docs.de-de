---
title: 'CA2114: die Methoden Sicherheit muss eine übergeordnete Gruppe vom Typ "|" sein. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7879d8b2aa9eb4ece1ce07f89681b6c0b0f5f31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534705"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Methodensicherheit sollte Superset des Typs sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ verfügt über deklarative Sicherheit, und eine seiner Methoden verfügt über deklarative Sicherheit für dieselbe Sicherheitsaktion, und die Sicherheitsaktion ist keine Verknüpfungs-oder [Vererbungs Anforderungen](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9), und die vom-Typ geprüften Berechtigungen [sind keine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) Teilmenge der Berechtigungen, die von der-Methode geprüft werden.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine Methode sollte nicht sowohl eine deklarative Sicherheit auf Methoden Ebene als auch auf Typebene für dieselbe Aktion aufweisen. Die beiden Überprüfungen werden nicht kombiniert. nur die Anforderung auf Methoden Ebene wird angewendet. Wenn z. b. ein Typ `X` die-Berechtigung erfordert und eine der Methoden die-Berechtigung erfordert `Y` , muss der Code nicht über `X` die Berechtigung zum Ausführen der Methode verfügen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie den Code, um sicherzustellen, dass beide Aktionen erforderlich sind. Wenn beide Aktionen erforderlich sind, stellen Sie sicher, dass die Aktion auf Methoden Ebene die auf der Typebene angegebene Sicherheit einschließt. Wenn der Typ beispielsweise die-Berechtigung erfordert `X` und seine-Methode auch die-Berechtigung anfordern muss `Y` , sollte die `X` -Methode und explizit aufrufen `Y` .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die-Methode nicht die vom-Typ angegebene Sicherheit erfordert. Dies ist jedoch kein normales Szenario und deutet möglicherweise auf eine sorgfältige Entwurfs Überprüfung hin.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden Umgebungs Berechtigungen verwendet, um die Gefahren bei Verstößen gegen diese Regel zu veranschaulichen. In diesem Beispiel erstellt der Anwendungscode eine Instanz des gesicherten Typs, bevor die Berechtigung verweigert wird, die für den Typ erforderlich ist. In einem realen Bedrohungsszenario benötigt die Anwendung eine andere Möglichkeit zum Abrufen einer Instanz des Objekts.

 Im folgenden Beispiel fordert die Bibliothek Schreibberechtigungen für einen Typ und eine Leseberechtigung für eine Methode an.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Beispiel
 Der folgende Anwendungscode veranschaulicht das Sicherheitsrisiko der Bibliothek, indem die-Methode aufgerufen wird, obwohl Sie die Sicherheitsanforderung auf Typebene nicht erfüllt.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **[Alle Berechtigungen] persönliche Informationen: 6/16/1964 12:00:00 Uhr** 
 **[Keine Schreib Berechtigung (vom Typ gefordert)] persönliche Informationen: 6/16/1964 12:00:00 Uhr** 
 **[Keine Leseberechtigung (von der Methode gefordert)] konnte nicht auf persönliche Informationen zugreifen:** Fehler bei der Anforderung.
## <a name="see-also"></a>Weitere Informationen
 [Sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Vererbungs Anforderungen](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) Verknüpfungs [Anforderungen](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
