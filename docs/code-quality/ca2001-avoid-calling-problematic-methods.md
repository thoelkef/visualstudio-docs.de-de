---
title: "CA2001: Keine problematischen Methoden aufrufen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2001"
  - "AvoidCallingProblematicMethods"
helpviewer_keywords: 
  - "CA2001"
  - "AvoidCallingProblematicMethods"
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2001: Keine problematischen Methoden aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|CheckId|CA2001|  
|Kategorie \(Category\)|Microsoft.Reliability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.  
  
## Regelbeschreibung  
 Vermeiden Sie überflüssige und möglicherweise gefährliche Methodenaufrufe.  
  
 Eine Verletzung dieser Regel tritt auf, wenn ein Member eine der folgenden Methoden aufruft.  
  
|Methode|**Beschreibung**|  
|-------------|----------------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Der Aufruf von GC.Collect kann die Anwendungsleistung bedeutend beeinträchtigen und ist selten notwendig.  Weitere Informationen finden Sie im [Leistung Leckerbissen Rico Marianis](http://go.microsoft.com/fwlink/?LinkId=169256) Blogeintrag auf MSDN.|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|"Thread.Suspend" und "Thread.Resume" sind wegen ihres unvorhersehbaren Verhaltens nun veraltet.  Verwenden Sie andere Klassen im <xref:System.Threading>\-Namespace, z. B. <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex%2C>, <xref:System.Threading.Mutex> und <xref:System.Threading.Semaphore>, um Threads zu synchronisieren oder Ressourcen zu schützen.|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Die DangerousGetHandle\-Methode stellt ein Sicherheitsrisiko dar, da es ein Handle zurückgeben kann, das nicht gültig ist.  Weitere Informationen zum sicheren Verwenden der DangerousGetHandle\-Methode finden Sie in der <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A>\-Methode und in der <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>\-Methode.|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Diese Methoden können Assemblys von unerwarteten Speicherorten laden.  Ein Beispiel finden Sie unter Hinweisblogbeiträge .NET CLR Suzanne\-Kochs [LoadFile für LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) und [Auswählen eines Bindungskontextes](http://go.microsoft.com/fwlink/?LinkId=164451) auf der MSDN\-Website zu Informationen über Methoden, die Assemblys laden.|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) \(Ole32\)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) \(Ole32\)|Sobald die Ausführung des Benutzercodes in einem verwalteten Prozess gestartet wird, ist es zu spät, CoSetProxyBlanket zuverlässig aufzurufen.  Die Common Language Runtime \(CLR\) führt Initialisierungsaktionen aus, die möglicherweise verhindern, dass ein P\/Invoke von Benutzern erfolgreich ist.<br /><br /> Wenn CoSetProxyBlanket jedoch für eine verwaltete Anwendung aufgerufen werden muss, wird empfohlen, den Prozess unter Verwendung von systemeigenem, ausführbarem Code \(C\+\+\) zu starten, CoSetProxyBlanket im systemeigenen Code aufzurufen und anschließend die Anwendung mit verwaltetem Code im Prozess auszuführen. \(Achten Sie darauf, eine Versionsnummer für die Laufzeit anzugeben.\)|  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen oder ersetzen Sie den Aufruf der gefährlichen oder problematischen Methode.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie Meldungen von dieser Regel nur, wenn keine Alternativen zu der problematischen Methode vorhanden sind.  
  
## Siehe auch  
 [Zuverlässigkeitswarnungen](../code-quality/reliability-warnings.md)