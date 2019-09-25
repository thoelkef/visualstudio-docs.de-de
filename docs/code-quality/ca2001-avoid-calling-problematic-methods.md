---
title: 'CA2001: Keine problematischen Methoden aufrufen.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233190"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Keine problematischen Methoden aufrufen.

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.

## <a name="rule-description"></a>Regelbeschreibung

Vermeiden Sie unnötige und potenziell gefährliche Methodenaufrufe. Ein Verstoß gegen diese Regel tritt auf, wenn ein Member eine der folgenden Methoden aufruft:

|Methode|Beschreibung|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC wird aufgerufen. Collect kann die Anwendungsleistung erheblich beeinträchtigen und ist nur selten erforderlich. Weitere Informationen finden Sie auf MSDN im Blogbeitrag [von Rico Mariani Performance tidbits](http://go.microsoft.com/fwlink/?LinkId=169256) .|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|"Thread. Suspend" und "Thread. Resume" wurden aufgrund des unvorhersehbaren Verhaltens als veraltet markiert.  Verwenden Sie andere Klassen im <xref:System.Threading> -Namespace, <xref:System.Threading.Monitor>z. <xref:System.Threading.Mutex>b. <xref:System.Threading.Semaphore>, und, um Threads zu synchronisieren oder Ressourcen zu schützen.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Die DangerousGetHandle-Methode stellt ein Sicherheitsrisiko dar, da Sie ein ungültiges Handle zurückgeben kann. Weitere Informationen <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> zur sicheren <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> Verwendung der Methode "DangerousGetHandle" finden Sie in den Methoden und.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Diese Methoden können Assemblys von unerwarteten Speicherorten laden. Informationen hierzu finden Sie beispielsweise in den Blogbeiträgen [von Suzanne Cook im Blogbeitrag LoadFile im Vergleich zu LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) und [Auswählen eines Bindungs Kontexts](http://go.microsoft.com/fwlink/?LinkId=164451) für Informationen über Methoden, die Assemblys laden.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) Ole32<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) Ole32|Zum Zeitpunkt, zu dem der Benutzercode mit der Ausführung in einem verwalteten Prozess beginnt, ist es zu spät, CoSetProxyBlanket zuverlässig aufzurufen. Der Common Language Runtime (CLR) führt Initialisierungs Aktionen aus, die möglicherweise verhindern, dass die Benutzer den P/Aufruf erfolgreich durchführt.<br /><br /> Wenn Sie CoSetProxyBlanket für eine verwaltete Anwendung aufrufen müssen, empfiehlt es sich, den Prozess mit einer ausführbaren Datei mit System eigenem CodeC++() zu starten, CoSetProxyBlanket im systemeigenen Code aufzurufen und anschließend die Anwendung mit verwaltetem Code in Verarbeitung zu starten. (Stellen Sie sicher, dass Sie eine Versionsnummer für die Laufzeit angeben.)|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen oder ersetzen Sie den-aufruhalte der gefährlichen oder problematischen Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Sie sollten Nachrichten von dieser Regel nur unterdrücken, wenn keine Alternativen zur problematischen Methode verfügbar sind.

## <a name="see-also"></a>Siehe auch

- [Zuverlässigkeitswarnungen](../code-quality/reliability-warnings.md)