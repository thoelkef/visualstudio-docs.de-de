---
title: 'CA2001: Keine problematischen Methoden aufrufen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc40f51fc0c5c3e2db428252d466760d9f297e23
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Keine problematischen Methoden aufrufen
|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.

## <a name="rule-description"></a>Regelbeschreibung
 Vermeiden Sie unnötige und potenziell gefährlichen Methodenaufrufe.

 Ein Verstoß gegen diese Regel tritt auf, wenn ein Mitglied einer der folgenden Methoden aufruft.

|Methode|Beschreibung|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Aufrufen von GC aus. Erfassen kann die Leistung der Anwendung deutlich beeinträchtigen und wird selten notwendig. Weitere Informationen finden Sie unter der [Rico Marianis Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) Blogeintrag auf MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend und Thread.Resume haben aufgrund ihrer zu unvorhersehbarem Verhalten als veraltet markiert.  Verwenden Sie andere Klassen in der <xref:System.Threading> Namespace, z. B. <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, <xref:System.Threading.Mutex>, und <xref:System.Threading.Semaphore> , Threads zu synchronisieren oder Ressourcen zu schützen.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Die DangerousGetHandle-Methode stellt ein Sicherheitsrisiko, da es ein Handle zurückgeben kann, der ungültig ist. Finden Sie unter der <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> und <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> Methoden für Weitere Informationen zur Verwendung die Methode DangerousGetHandle sicher.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Diese Methoden können Assemblys von unerwarteten Speicherorten geladen werden. Beispielsweise finden Sie unter Suzanne Cooks .NET CLR Notes-Blogbeiträge [LoadFile Vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) und [Choosing a Binding Context](http://go.microsoft.com/fwlink/?LinkId=164451) auf der MSDN-Website für Informationen zu Methoden, die Assemblys zu laden.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Die Startzeit des Benutzercodes in einem verwalteten Prozess ausführen, ist es zu spät, CoSetProxyBlanket zuverlässig aufzurufen. Die common Language Runtime (CLR) führt Initialisierungsaktionen aus, die adressiert, der die P/Invoke-Benutzer verhindern können.<br /><br /> Wenn Sie für eine verwaltete Anwendung CoSetProxyBlanket aufgerufen haben, wird empfohlen, dass Sie starten Sie den Prozess, mit der eine ausführbare systemeigener Code (C++), im systemeigenen Code CoSetProxyBlanket, und klicken Sie dann Ihre Anwendung mit verwaltetem Code im Prozess. (Achten Sie darauf eine Versionsnummer für die Common Language Runtime angeben.)|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie oder Ersetzen Sie den Aufruf an die gefährliche oder problematische Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Nur, wenn keine alternativen für die problematische Methode verfügbar sind, sollten Sie Nachrichten von dieser Regel unterdrücken.

## <a name="see-also"></a>Siehe auch
 [Zuverlässigkeitswarnungen](../code-quality/reliability-warnings.md)