---
title: 'CA2118: Überprüfen Sie SuppressUnmanagedCodeSecurityAttribute Verwendung von | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: 8d862f285efa3487c428aed2e5aed3a67c3baef6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Überprüfen der Verwendung von SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter Typ oder Member hat die <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> Attribut.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Ändert das Standardverhalten des Sicherheitssystems für Member, die nicht verwalteten Code mit COM-Interop oder Plattformaufrufe Aufruf ausführen. Im Allgemeinen führt das System eine [Daten und Modellierung](/dotnet/framework/data/index) Berechtigung für nicht verwalteten Code. Diese Anforderung erfolgt zur Laufzeit für jeden Aufruf des Elements, und alle Aufrufer in der Aufrufliste für die Berechtigung überprüft. Wenn das Attribut vorhanden ist, führt das System eine [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands) für die Berechtigung: die Berechtigungen des unmittelbaren Aufrufers überprüft werden, wenn der Aufrufer JIT-kompiliert wird.  
  
 Dieses Attribut wird hauptsächlich verwendet, um die Leistung zu erhöhen. Der Leistungszuwachs geht jedoch mit beträchtlichen Sicherheitsrisiken einher. Wenn Sie das Attribut auf öffentliche Member, die systemeigene Methoden aufrufen platzieren, ist der Aufrufer in der Aufrufliste (außer den unmittelbaren Aufrufer) Berechtigung zum Ausführen von nicht verwalteten Codes nicht verwalteten Code nicht erforderlich. Abhängig von des öffentlichen Members Aktionen und Behandlung der Eingabe könnte dies nicht vertrauenswürdige Aufrufern Zugriff-Funktionalität, die normalerweise nur für vertrauenswürdigen Code ermöglichen.  
  
 Die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] basiert auf sicherheitsüberprüfungen zu verhindern, dass Aufrufer den direkten Zugriff auf den aktuellen Prozess-Adressraum. Da dieses Attribut normalen Sicherheit umgangen werden, dürfen Codes eine ernsthafte Bedrohung aus, wenn es das Lesen und Schreiben in den Arbeitsspeicher des Prozesses verwendet werden kann. Beachten Sie, dass das Risiko, dass nicht auf Methoden beschränkt ist, die absichtlich Zugriff zum Verarbeiten von Arbeitsspeicher bereitstellen. Es ist auch in jedem Szenario, in denen bösartiger Code Zugriff mit welchen Mitteln, z. B. erreichen, indem Sie kann durch die überraschend, fehlerhafte oder ungültige Eingabe, vorhanden.  
  
 Die Standardsicherheitsrichtlinie nicht verwalteter Code auf eine Assembly gewährt Ihnen kein Recht, wenn er vom lokalen Computer ausgeführt wird, oder ein Mitglied einer der folgenden Gruppen ist:  
  
-   Mein Computer Internetzonen-Codegruppe  
  
-   Microsoft starker Namen Codegruppe  
  
-   ECMA Strong Name-Codegruppe  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Überprüfen Sie sorgfältig den Code, um sicherzustellen, dass dieses Attribut absolut notwendig ist. Wenn Sie mit verwaltetem codesicherheit nicht vertraut sind, oder die Sicherheitsaspekte bei der Verwendung dieses Attributs nicht verstehen, entfernen Sie es aus dem Code. Wenn das Attribut erforderlich ist, müssen Sie sicherstellen, dass Aufrufer den Code in böswilliger Absicht verwenden können. Wenn Code nicht über die Berechtigung zum Ausführen von nicht verwalteten Codes verfügt, wird dieses Attribut hat keine Auswirkungen und sollte entfernt werden.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Um eine Warnung dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, dass Ihr Code Aufrufer keinen Zugriff auf systemeigene Vorgänge oder Ressourcen, die einen destruktiven Weise verwendet werden können.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel verstößt gegen die Regel.  
  
 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel die `DoWork` Methode bietet einen öffentlich zugänglichen Codepfad für die Plattform-Aufruf-Methode `FormatHardDisk`.  
  
 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel, das die öffentliche Methode `DoDangerousThing` bewirkt eine Verletzung. Zum Auflösen des Verstoßes `DoDangerousThing` private gemacht werden sollen, und den Zugriff darauf über eine öffentliche Methode, die durch eine sicherheitsforderung gesichert sein sollte, da veranschaulicht die `DoWork` Methode.  
  
 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Schreiben von sicherem Richtlinien](/dotnet/standard/security/secure-coding-guidelines)   
 [Daten und Modellierung](/dotnet/framework/data/index)  
 [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)  
  