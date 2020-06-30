---
title: 'CA2001: vermeiden Sie das Aufrufen von problematischen Methoden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba64c27cde5f335f32cca362417078a5c9ed13e3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538579"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Keine problematischen Methoden aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Category|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.

## <a name="rule-description"></a>Beschreibung der Regel
 Vermeiden Sie unnötige und potenziell gefährliche Methodenaufrufe.

 Ein Verstoß gegen diese Regel tritt auf, wenn ein Member eine der folgenden Methoden aufruft.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC wird aufgerufen. Collect kann die Anwendungsleistung erheblich beeinträchtigen und ist nur selten erforderlich. Weitere Informationen finden Sie auf der MSDN-Website im Blogbeitrag von [Rico Mariani Performance tidbits](https://docs.microsoft.com/archive/blogs/ricom/when-to-call-gc-collect) .|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|"Thread. Suspend" und "Thread. Resume" wurden aufgrund des unvorhersehbaren Verhaltens als veraltet markiert.  Verwenden Sie andere Klassen im <xref:System.Threading> -Namespace, z <xref:System.Threading.Monitor> . b., <xref:System.Threading.Mutex> und, <xref:System.Threading.Semaphore> um Threads zu synchronisieren oder Ressourcen zu schützen.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Die DangerousGetHandle-Methode stellt ein Sicherheitsrisiko dar, da Sie ein ungültiges Handle zurückgeben kann. <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> Weitere Informationen zur sicheren Verwendung der Methode "DangerousGetHandle" finden Sie in den Methoden und.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Diese Methoden können Assemblys von unerwarteten Speicherorten laden. Informationen zu den Methoden, die Assemblys laden, finden Sie Beispiels [Weise in den Blogbeiträgen zu den](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context) .NET CLR-Notizen von Suzanne Cook und im Blogbeitrag [LoadFile.](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom)|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (OLE32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (OLE32)|Zum Zeitpunkt, zu dem der Benutzercode mit der Ausführung in einem verwalteten Prozess beginnt, ist es zu spät, CoSetProxyBlanket zuverlässig aufzurufen. Der Common Language Runtime (CLR) führt Initialisierungs Aktionen aus, die möglicherweise verhindern, dass die Benutzer den P/Aufruf erfolgreich durchführt.<br /><br /> Wenn Sie CoSetProxyBlanket für eine verwaltete Anwendung aufrufen müssen, empfiehlt es sich, den Prozess zu starten, indem Sie eine ausführbare Datei mit System eigenem Code (C++) verwenden, CoSetProxyBlanket im systemeigenen Code aufrufen und dann die Anwendung mit verwaltetem Code in Verarbeitung starten. (Stellen Sie sicher, dass Sie eine Versionsnummer für die Laufzeit angeben.)|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen oder ersetzen Sie den-aufruhalte der gefährlichen oder problematischen Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie sollten Nachrichten von dieser Regel nur unterdrücken, wenn keine Alternativen zur problematischen Methode verfügbar sind.

## <a name="see-also"></a>Weitere Informationen
 [Zuverlässigkeits Warnungen](../code-quality/reliability-warnings.md)
