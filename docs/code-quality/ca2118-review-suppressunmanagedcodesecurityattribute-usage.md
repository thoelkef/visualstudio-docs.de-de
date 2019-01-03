---
title: 'CA2118: Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 1bc65c6c27a22e39e48cb69dbe32108692d5ffea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860818"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ oder Member ist der <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Ändert das Standardverhalten des Sicherheitssystems für Member, die nicht verwalteten Code mithilfe eines COM-Interop oder Plattformaufrufe ausführen. Im Allgemeinen führt das System eine [Daten und Modellierung](/dotnet/framework/data/index) Berechtigung für nicht verwalteten Code. Diese Anforderung erfolgt zur Laufzeit für jeden Aufruf des Members, und alle Aufrufer in der Aufrufliste für die Berechtigung überprüft. Wenn das Attribut vorhanden ist, führt das System eine [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands) für die Berechtigung: die Berechtigungen des unmittelbaren Aufrufers überprüft werden, wenn der Aufrufer JIT-kompiliert wird.

 Dieses Attribut wird hauptsächlich verwendet, um die Leistung zu erhöhen. Der Leistungszuwachs geht jedoch mit beträchtlichen Sicherheitsrisiken einher. Wenn Sie das-Attribut auf öffentliche Member, die native Methoden aufzurufen platzieren, ist der Aufrufer in der Aufrufliste (mit Ausnahme der direkte Aufrufer) nicht nicht verwalteten Code die Berechtigung zum Ausführen von nicht verwalteten Codes erforderlich. Abhängig von des öffentlichen Members Aktionen und Eingabeverarbeitung erlaubt es möglicherweise nicht vertrauenswürdige Aufrufern Access-Funktionalität, die normalerweise nur für vertrauenswürdigen Code.

 .NET Framework basiert auf sicherheitsüberprüfungen zu verhindern, dass Aufrufer am direkten Zugriff auf den aktuellen Prozess-Adressbereich. Da dieses Attribut Sicherheit umgangen werden, stellt Ihr Code eine ernsthafte Bedrohung, wenn sie zum Lesen oder Schreiben in den der Speicher des Prozesses verwendet werden kann. Beachten Sie, dass das Risiko nicht auf Methoden beschränkt ist, die absichtlich Zugriff zum Verarbeiten von Arbeitsspeicher bereitstellen. Es ist auch in jedem Szenario, in denen bösartiger Code den Zugriff mit welchen Mitteln, z. B. erreichen kann, indem die Eingabe von überraschend, falsch formatiert oder ungültig, vorhanden.

 Die Standardsicherheitsrichtlinie nicht verwaltetem Code auf eine Assembly gewährt Ihnen kein Recht, wenn sie auf dem lokalen Computer ausgeführt wird, oder ein Mitglied einer der folgenden Gruppen ist:

- Meine Computer Internetzonen-Codegruppe

- Codegruppe von Microsoft starker Name

- ECMA Strong Name-Codegruppe

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie sorgfältig den Code, um sicherzustellen, dass dieses Attribut absolut notwendig ist. Wenn Sie nicht mit verwaltetem Code Security vertraut sind oder die Sicherheitsaspekte bei der Verwendung dieses Attributs nicht verstehen, aus dem Code entfernen. Wenn das Attribut erforderlich ist, müssen Sie sicherstellen, dass der Aufrufer können nicht für Code in böswilliger Absicht verwendet werden. Wenn Ihr Code keine Berechtigung zum nicht verwalteten Code ausführen, wird dieses Attribut hat keine Auswirkungen und sollte entfernt werden.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Um problemlos eine Warnung dieser Regel zu unterdrücken, müssen Sie sicherstellen, dass Ihr Code keine Aufrufer den Zugriff auf systemeigene Vorgänge oder Ressourcen, die auf schädigende Weise verwendet werden können.

## <a name="example-1"></a>Beispiel 1
 Das folgende Beispiel verstößt gegen die Regel.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>Beispiel 2
 Im folgenden Beispiel die `DoWork` Methode bietet einen öffentlich zugänglichen Codepfad für die Plattform-Methode aufrufen `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>Beispiel 3
 Im folgenden Beispiel, das die öffentliche Methode `DoDangerousThing` ein Verstoß. Zum Auflösen der Verletzung `DoDangerousThing` private gemacht werden sollen, und den Zugriff darauf muss über eine öffentliche Methode, die durch eine sicherheitsforderung geschützt, wie dargestellt die `DoWork` Methode.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Daten und Modellierung](/dotnet/framework/data/index)
- [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)