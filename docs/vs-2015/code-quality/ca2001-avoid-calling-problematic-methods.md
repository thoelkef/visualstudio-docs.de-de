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
ms.openlocfilehash: 17f3c283f0a837873c5e01716ec2c412b1e67f16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667732"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Keine problematischen Methoden aufrufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.

## <a name="rule-description"></a>Regelbeschreibung
 Vermeiden Sie unnötige und potenziell gefährliche Methodenaufrufe.

 Ein Verstoß gegen diese Regel tritt auf, wenn ein Member eine der folgenden Methoden aufruft.

|Methode|Beschreibung|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC wird aufgerufen. Collect kann die Anwendungsleistung erheblich beeinträchtigen und ist nur selten erforderlich. Weitere Informationen finden Sie auf der MSDN-Website im Blogbeitrag von [Rico Mariani Performance tidbits](http://go.microsoft.com/fwlink/?LinkId=169256) .|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|"Thread. Suspend" und "Thread. Resume" wurden aufgrund des unvorhersehbaren Verhaltens als veraltet markiert.  Verwenden Sie andere Klassen im <xref:System.Threading>-Namespace, z. b. <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> und <xref:System.Threading.Semaphore>, um Threads zu synchronisieren oder Ressourcen zu schützen.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Die DangerousGetHandle-Methode stellt ein Sicherheitsrisiko dar, da Sie ein ungültiges Handle zurückgeben kann. Weitere Informationen zur sicheren Verwendung der Methode "DangerousGetHandle" finden Sie in den <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A>-und <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>-Methoden.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Diese Methoden können Assemblys von unerwarteten Speicherorten laden. Informationen zu den Methoden, die Assemblys laden, finden Sie Beispiels [Weise in den Blogbeiträgen zu den](http://go.microsoft.com/fwlink/?LinkId=164451) .NET CLR-Notizen von Suzanne Cook und im Blogbeitrag [LoadFile.](http://go.microsoft.com/fwlink/?LinkId=164450)|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (OLE32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (OLE32)|Zum Zeitpunkt, zu dem der Benutzercode mit der Ausführung in einem verwalteten Prozess beginnt, ist es zu spät, CoSetProxyBlanket zuverlässig aufzurufen. Der Common Language Runtime (CLR) führt Initialisierungs Aktionen aus, die möglicherweise verhindern, dass die Benutzer den P/Aufruf erfolgreich durchführt.<br /><br /> Wenn Sie CoSetProxyBlanket für eine verwaltete Anwendung aufrufen müssen, empfiehlt es sich, den Prozess mit einer ausführbaren Datei mit System eigenem CodeC++() zu starten, CoSetProxyBlanket im systemeigenen Code aufzurufen und anschließend die Anwendung mit verwaltetem Code in Verarbeitung zu starten. (Stellen Sie sicher, dass Sie eine Versionsnummer für die Laufzeit angeben.)|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen oder ersetzen Sie den-aufruhalte der gefährlichen oder problematischen Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie sollten Nachrichten von dieser Regel nur unterdrücken, wenn keine Alternativen zur problematischen Methode verfügbar sind.

## <a name="see-also"></a>Siehe auch
 [Zuverlässigkeitswarnungen](../code-quality/reliability-warnings.md)
