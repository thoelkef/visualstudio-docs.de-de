---
title: VSInstr-Warnungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b178afb59558f5e684d704137039891aefbf0e3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683242"
---
# <a name="vsinstr-warnings"></a>VSInstr-Warnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgende Tabelle enthält die vom Tool VSInstr.exe ausgegebenen Warnungen. Sie können die NOWARN-Option zusammen mit den Warnungsnummern verwenden, um die Anzeige der Warnung zu unterdrücken.  
  
|Warnnummer|Beschreibung|  
|--------------------|-----------------|  
|**VSP2000**|Interner Fehler. Der Moduldateiname für diese ausführbare Datei kann nicht abgerufen werden.|  
|**VSP2001**|\<assembly name> ist eine Assembly mit starkem Namen. Sie muss neu signiert werden, bevor sie ausgeführt werden kann.<br /><br /> Diese Warnung tritt auf, wenn eine signierte Assembly instrumentiert wird. Sie können das Tool „sn.exe“ verwenden, um die Binärdatei neu zu signieren oder die Anforderung des starken Namens vorübergehend zu deaktivieren. Weitere Informationen finden Sie unter [Sn.exe (Strong Name-Tool)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).|  
|**VSP2002**|Die Funktion \<funcname> wurde in der Datei \<filename> nicht gefunden.<br /><br /> Diese Warnung tritt auf, wenn eine Funktion in der angegebenen Datei nicht gefunden werden kann.|  
|**VSP2003**|Es konnten keine Quersprünge zur Funktion \<funcname> in der Datei \<filename> gefunden werden.<br /><br /> Diese Warnung tritt auf, wenn VSInstr keine Quersprünge aufheben kann. Quersprünge werden für die Codeoptimierung verwendet.|  
|**VSP2004**|Die Funktion \<funcname> wurde mithilfe des Befehlszeilenschalters „/EXCLUDE“ ausgeschlossen, sie war jedoch erforderlich, da sie einen Quersprung enthielt.<br /><br /> Diese Warnung tritt auf, wenn die Funktion mithilfe der EXCLUDE-Option ausgeschlossen wurde, aber während des Instrumentierungsvorgangs erforderlich ist. Der Profiler schließt automatisch die erforderliche Funktion ein.|  
|**VSP2005**|Interner Instrumentierungsfehler: \<error text><br /><br /> Diese Warnung wird ausgegeben, wenn die Instrumentierung nicht ausgeführt werden kann. Überprüfen Sie den Fehlertext, um festzustellen, ob er korrigiert werden kann.|  
|**VSP2006**|PDB für \<name> konnte nicht gefunden werden.<br /><br /> Diese Warnung tritt auf, wenn die PDB-Datei im Suchpfad nicht vorhanden ist oder nicht der Binärdatei entspricht.|  
|**VSP2007**|\<filename> enthält keinen instrumentierbaren Code.<br /><br /> Diese Warnung wird ausgegeben, wenn alle Funktionen in der Binärdatei ausgeschlossen wurden, oder wenn die angegebene Datei nur Ressourcen enthält.|  
|**VSP2008**|Sicherheitsattribute können nicht aus \<name> abgerufen werden. Fehlercode \<code><br /><br /> Diese Warnung tritt auf, wenn der Benutzer nicht über READ_DAC-Berechtigung verfügt. Während des Instrumentierungsvorgangs versucht der Profiler, die ursprüngliche DACL für die Binärdatei zu erhalten. Da die ursprüngliche Binärdatei durch eine neue Binärdatei ersetzt wird, muss die DACL aus der ursprünglichen Binärdatei kopiert und auf die neue Binärdatei angewendet werden. Hierbei kann ein Fehler auftreten, wenn der Benutzer nicht über READ_DAC-Zugriff auf die ursprüngliche Binärdatei verfügt.|  
|**VSP2009**|Sicherheitsattribute für \<name> können nicht festgelegt werden. Fehlercode \<error number><br /><br /> Diese Warnung tritt auf, wenn der Benutzer nicht über WRITE_DAC-Berechtigung verfügt. Während des Instrumentierungsvorgangs versucht der Profiler, die ursprüngliche DACL für die Binärdatei zu erhalten. Da die ursprüngliche Binärdatei durch eine neue Binärdatei ersetzt wird, muss die DACL aus der ursprünglichen Binärdatei kopiert und auf die neue Binärdatei angewendet werden. Hierbei kann ein Fehler auftreten, wenn der Benutzer nicht über WRITE_DAC-Zugriff auf die neue Binärdatei verfügt.|  
|**VSP2010**|Es sind keine Funktionen speziell für die Instrumentation aufgrund von /INCLUDE- oder /EXCLUDE-Optionen ausgewählt.|  
|**VSP2011**|Funcspec \<name> zum Einschließen/Ausschließen stimmt mit keiner Funktion überein.|  
|**VSP2012**|Das Abbild enthält keinen Code, der für die Codeabdeckung instrumentiert werden kann.<br /><br /> Der Profiler instrumentiert folgende Art von Code nicht:<br /><br /> – Statische CRT-Funktionen<br />– Verwaltete Methoden, die mit dem NonUserCodeAttribute-Attribut versehen sind<br />– Verwaltete Methoden, die mit dem DebuggerHiddenAttribute-Attribut versehen sind<br />– MASM-Blöcke<br /><br /> Diese Warnung wird generiert, wenn nach dieser Filterung kein Code mehr vorhanden ist.|  
|**VSP2013**|Für die Instrumentation dieses Abbilds ist es erforderlich, das Abbild als 32-Bit-Prozess auszuführen. Die CLR-Headerflags wurden hierfür aktualisiert.<br /><br /> Der Profiler ändert die Binärdatei, sodass 64-Bit-Betriebssysteme den 32-Bit-Prozess im WOW64-Emulator öffnen können. Bei Bibliotheken (DLLs) kann hierbei ein Fehler auftreten, wenn sie in einen vorhandenen 64-Bit-Prozess geladen werden. Diese Warnung informiert den Benutzer über die Abhängigkeit.|  
|**VSP2014**|Das sich ergebende instrumentierte Abbild ist scheinbar ungültig und wird möglicherweise nicht ausgeführt.<br /><br /> Diese Meldung tritt auf, wenn die endgültige instrumentierte Assembly über einen ungültigen PE-Header verfügt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSInstr](../profiling/vsinstr.md)
