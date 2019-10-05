---
title: 'CA2118: Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b64551ec81de6a1eae7831af9f3382a2cd4c3b0e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232633"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen.

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein öffentlicher oder geschützter Typ oder Member verfügt über <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> das-Attribut.

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>ändert das Standardverhalten des Sicherheitssystems für Member, die nicht verwalteten Code mit COM-Interop oder Platt Form Aufruf ausführen. Im Allgemeinen erstellt das System eine [Daten und Modellierung](/dotnet/framework/data/index) für nicht verwalteten Code. Diese Anforderung tritt zur Laufzeit für jeden Aufruf des Members auf und überprüft jeden Aufrufer in der Aufruf Listen-Berechtigung. Wenn das-Attribut vorhanden ist, führt das System einen [Link](/dotnet/framework/misc/link-demands) für die Berechtigung aus: die Berechtigungen des unmittelbaren Aufrufers werden bei der JIT-Kompilierung des Aufrufers geprüft.

Dieses Attribut wird hauptsächlich verwendet, um die Leistung zu erhöhen. Der Leistungszuwachs geht jedoch mit beträchtlichen Sicherheitsrisiken einher. Wenn Sie das-Attribut in öffentlichen Membern platzieren, die Native Methoden aufzurufen, benötigen die Aufrufer in der Aufruf Listen-Datei (mit Ausnahme des unmittelbaren Aufrufers) keine Berechtigung für nicht verwalteten Code, um nicht verwalteten Code auszuführen. Abhängig von den Aktionen des öffentlichen Members und der Eingabe Behandlung können nicht vertrauenswürdige Aufrufer auf Funktionen zugreifen, die normalerweise auf vertrauenswürdigen Code beschränkt sind.

.NET basiert auf Sicherheitsüberprüfungen, um zu verhindern, dass Aufrufer direkt auf den Adressraum des aktuellen Prozesses zugreifen können. Da dieses Attribut die normale Sicherheit umgeht, stellt der Code eine ernsthafte Bedrohung dar, wenn er verwendet werden kann, um den Arbeitsspeicher des Prozesses zu lesen oder zu schreiben. Beachten Sie, dass das Risiko nicht auf Methoden beschränkt ist, die absichtlich Zugriff auf den Prozess Speicher bereitstellen. Es ist auch in jedem Szenario vorhanden, in dem bösartiger Code auf beliebige Weise Zugriff erhalten kann, z. b. durch die Bereitstellung von überraschenden, falsch formatierten oder ungültigen Eingaben.

Die Standard Sicherheitsrichtlinie gewährt einer Assembly keine Berechtigung für den nicht verwalteten Code, es sei denn, Sie wird auf dem lokalen Computer ausgeführt oder ist Mitglied einer der folgenden Gruppen:

- Arbeitsplatz Zonen-Code Gruppe

- Microsoft-Code Gruppe mit starkem Namen

- ECMA-Code Gruppe mit starkem Namen

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Überprüfen Sie sorgfältig den Code, um sicherzustellen, dass dieses Attribut unbedingt erforderlich ist. Wenn Sie mit der Sicherheit von verwaltetem Code nicht vertraut sind oder die Auswirkungen der Verwendung dieses Attributs auf die Sicherheit nicht verstehen, entfernen Sie Sie aus dem Code. Wenn das Attribut erforderlich ist, müssen Sie sicherstellen, dass der Code von Aufrufern nicht bösartig verwendet werden kann. Wenn der Code nicht über die Berechtigung zum Ausführen von nicht verwaltetem Code verfügt, hat dieses Attribut keine Auswirkung und sollte entfernt werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Um eine Warnung aus dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, dass der Code den Aufrufern keinen Zugriff auf systemeigene Vorgänge oder Ressourcen bereitstellt, die auf zerstörerische Weise verwendet werden können.

## <a name="example-1"></a>Beispiel 1

Im folgenden Beispiel wird gegen die Regel verstoßen.

[!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>Beispiel 2

Im folgenden Beispiel stellt die `DoWork` -Methode einen öffentlich zugänglichen Codepfad zur Platt Form Aufruf Methode `FormatHardDisk`bereit.

[!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>Beispiel 3

Im folgenden Beispiel verursacht die öffentliche Methode `DoDangerousThing` eine Verletzung. Um die Verletzung aufzulösen, `DoDangerousThing` sollte als privat festgestellt werden, und der Zugriff darauf sollte über eine öffentliche Methode erfolgen, die durch eine Sicherheitsanforderung gesichert ist `DoWork` , wie in der-Methode veranschaulicht.

[!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Daten und Modellierung](/dotnet/framework/data/index)
- [Link Aufrufe](/dotnet/framework/misc/link-demands)