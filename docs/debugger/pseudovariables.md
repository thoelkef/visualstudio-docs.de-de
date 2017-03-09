---
title: "Pseudovariablen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Pseudovariablen"
  - "Pseudovariablen"
  - "Überwachungsfenster, Pseudovariablen"
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pseudovariablen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pseudovariablen sind Begriffe, mit denen bestimmte Informationen in einem Variablenfenster oder im Dialogfeld **Schnellüberwachung** angezeigt werden.  Eine Pseudovariable können Sie genauso wie eine normale Variable eingeben.  Pseudovariablen sind jedoch keine Variablen und es gibt keine entsprechenden Variablennamen im Programm.  
  
## Beispiel  
 Angenommen, Sie schreiben eine Anwendung in systemeigenem Code, und Sie möchten die Anzahl zugeordneter Handles der Anwendung anzeigen.  Im Fenster **Überwachen** können Sie in der Spalte **Name** die folgende Pseudovariable eingeben und zur Auswertung anschließend die EINGABETASTE drücken:  
  
```  
$handles  
```  
  
 Bei systemeigenem Code können Sie die in dieser Tabelle aufgeführten Pseudovariablen verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$err`|Es wird der letzten Fehlerwert angezeigt, der mit der Funktion "SetLastError" festgelegt wird.  Der angezeigte Wert stellt das Ergebnis der Rückgabe der Funktion "GetLastError" dar.<br /><br /> Verwenden Sie `$err,hr`, um die dekodierte Form dieses Werts anzuzeigen.  Wenn der letzte Fehler z. B. 3 wäre, würde `$err,hr` `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.` anzeigen.|  
|`$handles`|Zeigt die Anzahl von Handles an, die der Anwendung zugeordnet sind.|  
|`$vframe`|Zeigt die Adresse des aktuellen Stapelrahmens an.|  
|`$tid`|Zeigt die Thread\-ID für den aktuellen Thread an.|  
|`$env`|Zeigt den Umgebungsblock im Zeichenfolgen\-Viewer an.|  
|`$cmdline`|Zeigt die Befehlszeilenzeichenfolge an, mit der das Programm gestartet wurde.|  
|`$pid`|Zeigt die Prozess\-ID an.|  
|`$` *Registername*<br /><br /> oder<br /><br /> `@` *Registername*|Zeigt den Inhalt des Registers *Registername* an.<br /><br /> Normalerweise geben Sie zum Anzeigen des Registerinhalts einfach den Registernamen ein.  Nur beim Überladen eines Variablennamens durch einen Registernamen müssen Sie diese Syntax verwenden.  Wenn der Registername im aktuellen Gültigkeitsbereich dem Variablennamen entspricht, interpretiert der Debugger den Namen als Variablenname.  In diesem Fall sind `$`*Registername* bzw. `@`*Registername* praktisch.|  
|`$clk`|Zeigt die Zeit in Taktzyklen an.|  
|`$user`|Zeigt eine Struktur mit Kontoinformationen für das die Anwendung ausführende Konto an.  Aus Sicherheitsgründen werden die Kennwortinformationen nicht angezeigt.|  
|`$exceptionstack`|Zeigt die Stapelüberwachung der aktuellen Windows\-Runtime\-Ausnahme an.  `$ exceptionstack` funktioniert nur in Store\-Apps, die unter Windows 8.1 oder höher ausgeführt werden.  `$ exceptionstack` wird nicht für C\+\+\- und SEH\-Ausnahmen unterstützt.|  
|`$ReturnValue`|Zeigt den Rückgabewert einer .NET Framework\-Methode an.  Siehe [Überprüfen von Rückgabewerten der Methodenaufrufe](../Topic/Examine%20return%20values%20of%20method%20calls.md).|  
  
 Die in dieser Tabelle angezeigten Pseudovariablen können Sie in C\# und Visual Basic verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$exception`|Zeigt Informationen über die letzte Ausnahme an.  Wenn keine Ausnahme aufgetreten ist, wird beim Auswerten von `$exception` eine Fehlermeldung angezeigt.<br /><br /> In Visual C\# wird bei deaktiviertem Ausnahmen\-Assistenten dem Fenster **Lokal** bei Auftreten einer Ausnahme automatisch `$exception` hinzugefügt.|  
|`$user`|Zeigt eine Struktur mit Kontoinformationen für das die Anwendung ausführende Konto an.  Aus Sicherheitsgründen werden die Kennwortinformationen nicht angezeigt.|  
  
 Die in dieser Tabelle angezeigten Pseudovariablen können Sie in Visual Basic verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$delete` oder `$$delete`|Löscht eine implizite Variable, die im Fenster **Direkt** erstellt wurde.  Die Syntax lautet `$delete,` *Variable* oder `$delete,` *Variable*`.`|  
|`$objectids` oder `$listobjectids`|Zeigt alle aktiven Objekt\-IDs als untergeordnete Elemente des angegebenen Ausdrucks an.  Die Syntax lautet `$objectid,` *Ausdruck* oder `$listobjectids,` *Ausdruck*`.`|  
|`$` *N* `#`|Zeigt das Objekt mit der Objekt\-ID *N* an.|  
|`$dynamic`|Zeigt den besonderen Knoten **Dynamische Ansicht** für ein Objekt an, das `IDynamicMetaObjectProvider` implementiert.  Schnittstelle  Die Syntax lautet `$dynamic,` *Objekt*.  Diese Funktion gilt nur für Code, der .NET Framework Version 4 verwendet.  Siehe [Dynamische Ansicht](../Topic/Dynamic%20View.md).|  
  
## Siehe auch  
 [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)   
 [Variablenfenster](../Topic/Variable%20Windows.md)