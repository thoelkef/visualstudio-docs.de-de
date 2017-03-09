---
title: "VSInstr-Warnungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Instrumentierung, VSInstr-Tool"
  - "Leistungstools, VSInstr-Tool"
  - "VSInstr-Tool"
  - "Warnungen"
  - "Warnungen, VSInstr-Tool"
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSInstr-Warnungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der folgenden Tabelle werden die vom Tool VSInstr.exe ausgegebenen Warnungen aufgelistet.  Sie können die NOWARN\-Option zusammen mit den Warnnummern verwenden, um das Anzeigen einer Warnung zu unterdrücken.  
  
|Warnnummer|**Beschreibung**|  
|----------------|----------------------|  
|**VSP2000**|Interner Fehler.  Der Moduldateiname für diese ausführbare Datei kann nicht abgerufen werden.|  
|**VSP2001**|\<Assemblyname\> ist eine stark benannte Assembly.  Sie muss neu signiert werden, bevor sie ausgeführt werden kann.<br /><br /> Diese Warnung wird bei der Instrumentation einer signierten Assembly ausgegeben.  Sie können das Tool "sn.exe" verwenden, um die Binärdatei zu entfernen oder die Anforderung für starke Namen vorübergehend zu deaktivieren.  Weitere Informationen finden Sie unter [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).|  
|**VSP2002**|Die Funktion \<funcname\> im Dateidateinamen nicht \<gefunden\><br /><br /> Diese Warnung wird ausgegeben, wenn eine Funktion in der angegebenen Datei nicht gefunden wurde.|  
|**VSP2003**|Es wurden keine Quersprünge zur Funktion \<funcname\> in Datei \<filename\> gefunden.<br /><br /> Diese Warnung wird ausgegeben, wenn VSInstr keine Quersprünge aufheben kann.  Quersprünge werden zur Codeoptimierung verwendet.|  
|**VSP2004**|Funktion \<funcname\> wurde ausgeschlossen, indem der EXCLUDE\-Befehlszeilenschalter verwendet wurde, jedoch erforderlich war, da ein Quersprung enthielt.<br /><br /> Diese Warnung wird ausgegeben, wenn die Funktion mithilfe der EXCLUDE\-Option ausgeschlossen wurde, die Funktion während des Instrumentationsvorgangs jedoch erforderlich war.  Der Profiler schließt automatisch die erforderliche Funktion ein.|  
|**VSP2005**|Interner Instrumentations\-Fehler \<Fehlertext\><br /><br /> Diese Warnung wird ausgegeben, wenn die Instrumentation nicht ausgeführt werden kann.  Überprüfen Sie den Fehlertext, um herauszufinden, ob der Fehler korrigiert werden kann.|  
|**VSP2006**|Könnte PDB für \<Namen nicht gefunden\><br /><br /> Diese Warnung wird ausgegeben, wenn die PDB\-Datei im Suchpfad nicht vorhanden ist oder der Binärdatei nicht entspricht.|  
|**VSP2007**|\<Dateiname\> enthält keinen instrumentable Code.<br /><br /> Diese Warnung wird ausgegeben, wenn die Funktionen in der Binärdatei alle ausgeschlossen wurden oder die angegebene Datei nur Ressourcen enthält.|  
|**VSP2008**|Die Sicherheitsattribute, vom Namen \<abzurufen\>.  Fehlercode \<code\><br /><br /> Diese Warnung wird ausgegeben, wenn der Benutzer nicht über die READ\_DAC\-Berechtigung verfügt.  Während des Instrumentationsvorgangs versucht der Profiler, die ursprüngliche freigegebene Zugriffssteuerungsliste \(Discretionary Access Control List – DACL\) für die Binärdatei zu erhalten.  Da die ursprüngliche Binärdatei jedoch durch eine neue Binärdatei ersetzt wird, muss die DACL aus der ursprünglichen Binärdatei kopiert und für die neue Binärdatei übernommen werden.  Dieser Vorgang schlägt fehl, wenn der Benutzer nicht über READ\_DAC\-Zugriff auf die ursprüngliche Binärdatei verfügt.|  
|**VSP2009**|Die Sicherheitsattribute, auf \<Namen\>festzulegen.  Fehlercode \<fehlernummer\><br /><br /> Diese Warnung wird ausgegeben, wenn der Benutzer nicht über die WRITE\_DAC\-Berechtigung verfügt.  Während des Instrumentationsvorgangs versucht der Profiler, die ursprüngliche freigegebene Zugriffssteuerungsliste \(Discretionary Access Control List – DACL\) für die Binärdatei zu erhalten.  Da die ursprüngliche Binärdatei jedoch durch eine neue Binärdatei ersetzt wird, muss die DACL aus der ursprünglichen Binärdatei kopiert und für die neue Binärdatei übernommen werden.  Dieser Vorgang schlägt fehl, wenn der Benutzer nicht über WRITE\_DAC\-Zugriff auf die neue Binärdatei verfügt.|  
|**VSP2010**|Es sind keine Funktionen speziell für die Instrumentation aufgrund von \/INCLUDE\- oder \/EXCLUDE\-Optionen ausgewählt.|  
|**VSP2011**|Schließen Sie ein, und schließen Sie funcspec \<Namen\> übereinstimmt keine Funktionen aus|  
|**VSP2012**|Das Abbild enthält keinen Code, der für die Codeabdeckung instrumentiert werden kann.<br /><br /> Der folgende Codetyp wird vom Profiler nicht instrumentiert:<br /><br /> -   Statische CRT\-Funktionen<br />-   Verwaltete mit NonUserCodeAttribute attributierte Methoden<br />-   Verwaltete mit DebuggerHiddenAttribute attributierte Methoden<br />-   MASM\-Blöcke<br /><br /> Diese Warnung wird generiert, wenn nach dieser Filterung kein Code mehr übrig ist.|  
|**VSP2013**|Für die Instrumentation dieses Image ist es erforderlich, das Image als 32\-Bit\-Prozess auszuführen.  Die CLR\-Headerflags wurden hierfür aktualisiert.<br /><br /> Der Profiler ändert die Binärdatei, damit 64\-Bit\-Betriebssysteme den 32\-Bit\-Prozess im WOW64\-Emulator öffnen können.  Diese Vorgehensweise schlägt bei Bibliotheken \(DLLs\) u. U. fehl, wenn sie in einen vorhandenen 64\-Bit\-Prozess geladen werden.  Diese Warnung informiert den Benutzer über die Abhängigkeit.|  
|**VSP2014**|Das sich ergebende instrumentierte Abbild ist scheinbar ungültig und wird möglicherweise nicht ausgeführt.<br /><br /> Diese Meldung wird ausgegeben, wenn die fertige instrumentierte Assembly über einen ungültigen PE\-Header verfügt.|  
  
## Siehe auch  
 [VSInstr](../profiling/vsinstr.md)