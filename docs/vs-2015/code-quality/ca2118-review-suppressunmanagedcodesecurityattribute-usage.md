---
title: 'CA2118: Überprüfen Sie SuppressUnmanagedCodeSecurityAttribute Verwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eb88a188c24e65bef6686b4a157c92fa63c5875f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589789"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Überprüfen der Verwendung von SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2118: Verwendung von Überprüfung SuppressUnmanagedCodeSecurityAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage).

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ oder Member ist der <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Ändert das Standardverhalten des Sicherheitssystems für Member, die nicht verwalteten Code mithilfe eines COM-Interop oder Plattformaufrufe ausführen. Im Allgemeinen führt das System eine [Daten und Modellierung](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) Berechtigung für nicht verwalteten Code. Diese Anforderung erfolgt zur Laufzeit für jeden Aufruf des Members, und alle Aufrufer in der Aufrufliste für die Berechtigung überprüft. Wenn das Attribut vorhanden ist, führt das System eine [Verknüpfungsaufrufe](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) für die Berechtigung: die Berechtigungen des unmittelbaren Aufrufers überprüft werden, wenn der Aufrufer JIT-kompiliert wird.

 Dieses Attribut wird hauptsächlich verwendet, um die Leistung zu erhöhen. Der Leistungszuwachs geht jedoch mit beträchtlichen Sicherheitsrisiken einher. Wenn Sie das-Attribut auf öffentliche Member, die native Methoden aufzurufen platzieren, ist der Aufrufer in der Aufrufliste (mit Ausnahme der direkte Aufrufer) nicht nicht verwalteten Code die Berechtigung zum Ausführen von nicht verwalteten Codes erforderlich. Abhängig von des öffentlichen Members Aktionen und Eingabeverarbeitung erlaubt es möglicherweise nicht vertrauenswürdige Aufrufern Access-Funktionalität, die normalerweise nur für vertrauenswürdigen Code.

 Die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sicherheitsüberprüfungen zu verhindern, dass Aufrufer am direkten Zugriff auf den aktuellen Prozess-Adressbereich verwendet. Da dieses Attribut Sicherheit umgangen werden, stellt Ihr Code eine ernsthafte Bedrohung, wenn sie zum Lesen oder Schreiben in den der Speicher des Prozesses verwendet werden kann. Beachten Sie, dass das Risiko nicht auf Methoden beschränkt ist, die absichtlich Zugriff zum Verarbeiten von Arbeitsspeicher bereitstellen. Es ist auch in jedem Szenario, in denen bösartiger Code den Zugriff mit welchen Mitteln, z. B. erreichen kann, indem die Eingabe von überraschend, falsch formatiert oder ungültig, vorhanden.

 Die Standardsicherheitsrichtlinie nicht verwaltetem Code auf eine Assembly gewährt Ihnen kein Recht, wenn sie auf dem lokalen Computer ausgeführt wird, oder ein Mitglied einer der folgenden Gruppen ist:

-   Meine Computer Internetzonen-Codegruppe

-   Codegruppe von Microsoft starker Name

-   ECMA Strong Name-Codegruppe

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie sorgfältig den Code, um sicherzustellen, dass dieses Attribut absolut notwendig ist. Wenn Sie nicht mit verwaltetem Code Security vertraut sind oder die Sicherheitsaspekte bei der Verwendung dieses Attributs nicht verstehen, aus dem Code entfernen. Wenn das Attribut erforderlich ist, müssen Sie sicherstellen, dass der Aufrufer können nicht für Code in böswilliger Absicht verwendet werden. Wenn Ihr Code keine Berechtigung zum nicht verwalteten Code ausführen, wird dieses Attribut hat keine Auswirkungen und sollte entfernt werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um problemlos eine Warnung dieser Regel zu unterdrücken, müssen Sie sicherstellen, dass Ihr Code keine Aufrufer den Zugriff auf systemeigene Vorgänge oder Ressourcen, die auf schädigende Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Das folgende Beispiel verstößt gegen die Regel.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel die `DoWork` Methode bietet einen öffentlich zugänglichen Codepfad für die Plattform-Methode aufrufen `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel, das die öffentliche Methode `DoDangerousThing` ein Verstoß. Zum Auflösen der Verletzung `DoDangerousThing` private gemacht werden sollen, und den Zugriff darauf muss über eine öffentliche Methode, die durch eine sicherheitsforderung geschützt, wie dargestellt die `DoWork` Methode.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Sichern Sie die Richtlinien für das Codieren](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Sicherheitsoptimierungen](http://msdn.microsoft.com/en-us/cf255069-d85d-4de3-914a-e4625215a7c0) [Daten und Modellierung](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [Linkaufrufe](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



