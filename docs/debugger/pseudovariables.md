---
title: Pseudovariablen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b92b070641e4eed47b0094e1611f78cd799e6952
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudovariablen in Visual Studio-debugger
Pseudovariablen sind Begriffe, die bestimmte Informationen in einem Variablenfenster angezeigt oder **Schnellüberwachung** (Dialogfeld). Eine Pseudovariable können Sie genauso wie eine normale Variable eingeben. Pseudovariablen sind jedoch keine Variablen und es gibt keine entsprechenden Variablennamen im Programm.  
  
## <a name="example"></a>Beispiel  
 Angenommen, Sie schreiben eine Anwendung in nativem Code, und Sie möchten die Anzahl zugeordneter Handles der Anwendung anzeigen. In der **Überwachen** können Sie die in die folgende Pseudovariable eingeben der **Namen** Spalte, und drücken Sie zur Auswertung:  
  
```  
$handles  
```  
  
 Bei nativem Code können Sie die in dieser Tabelle aufgeführten Pseudovariablen verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$err`|Es wird der letzten Fehlerwert angezeigt, der mit der Funktion "SetLastError" festgelegt wird. Der angezeigte Wert stellt das Ergebnis der Rückgabe der Funktion "GetLastError" dar.<br /><br /> Verwenden Sie `$err,hr`, um die dekodierte Form dieses Werts anzuzeigen. Wenn der letzte Fehler z. B. 3 wäre, würde `$err,hr``ERROR_PATH_NOT_FOUND : The system cannot find the path specified.` anzeigen.|  
|`$handles`|Zeigt die Anzahl von Handles an, die der Anwendung zugeordnet sind.|  
|`$vframe`|Zeigt die Adresse des aktuellen Stapelrahmens an.|  
|`$tid`|Zeigt die Thread-ID für den aktuellen Thread an.|  
|`$env`|Zeigt den Umgebungsblock im Zeichenfolgen-Viewer an.|  
|`$cmdline`|Zeigt die Befehlszeilenzeichenfolge an, mit der das Programm gestartet wurde.|  
|`$pid`|Zeigt die Prozess-ID an.|  
|`$`*Registername*<br /><br /> oder<br /><br /> `@`*Registername*|Zeigt den Inhalt des Registers *Registername*.<br /><br /> Normalerweise geben Sie zum Anzeigen des Registerinhalts einfach den Registernamen ein. Nur beim Überladen eines Variablennamens durch einen Registernamen müssen Sie diese Syntax verwenden. Wenn der Registername im aktuellen Gültigkeitsbereich dem Variablennamen entspricht, interpretiert der Debugger den Namen als Variablenname. Wird, wenn `$` *Registername* oder `@` *Registername* erweist sich als nützlich.|  
|`$clk`|Zeigt die Zeit in Taktzyklen an.|  
|`$user`|Zeigt eine Struktur mit Kontoinformationen für das die Anwendung ausführende Konto an. Aus Sicherheitsgründen werden die Kennwortinformationen nicht angezeigt.|  
|`$exceptionstack`|Zeigt die Stapelüberwachung der aktuellen Windows-Runtime-Ausnahme an. `$ exceptionstack`funktioniert nur in UWP und Windows 8.1-apps oder höher. `$ exceptionstack` wird nicht für C++- und SEH-Ausnahmen unterstützt.|  
|`$ReturnValue`|Zeigt den Rückgabewert einer .NET Framework-Methode an.|  
  
 Die in dieser Tabelle angezeigten Pseudovariablen können Sie in C# und Visual Basic verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$exception`|Zeigt Informationen über die letzte Ausnahme an. Wenn keine Ausnahme aufgetreten ist, wird beim Auswerten von `$exception` eine Fehlermeldung angezeigt.<br /><br /> In Visual c# wird bei deaktiviertem Ausnahmen-Assistent `$exception` wird automatisch hinzugefügt, die **"lokal"** Fenster, wenn eine Ausnahme auftritt.|  
|`$user`|Zeigt eine Struktur mit Kontoinformationen für das die Anwendung ausführende Konto an. Aus Sicherheitsgründen werden die Kennwortinformationen nicht angezeigt.|  
  
 Die in dieser Tabelle angezeigten Pseudovariablen können Sie in Visual Basic verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$delete` oder `$$delete`|Löscht eine implizite Variable, die in erstellt haben, wurde die **Direktfenster** Fenster. Die Syntax lautet `$delete,` *Variable* oder`$delete,` *Variable*`.`|  
|`$objectids` oder `$listobjectids`|Zeigt alle aktiven Objekt-IDs als untergeordnete Elemente des angegebenen Ausdrucks an. Die Syntax lautet `$objectid,` *Ausdruck* oder`$listobjectids,` *Ausdruck*`.`|  
|`$`*N*`#`|Zeigt das Objekt mit Objekt-ID gleich *N*.|  
|`$dynamic`|Zeigt den besonderen **dynamische Ansicht** Knoten für ein Objekt, implementiert die `IDynamicMetaObjectProvider`. Schnittstelle Die Syntax lautet `$dynamic,` *Objekt*. Diese Funktion gilt nur für Code, der .NET Framework Version 4 verwendet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen "und" Schnellüberwachung Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Variablenfenster](../debugger/debugger-windows.md)