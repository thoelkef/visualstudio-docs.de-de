---
title: Pseudovariablen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9ce72d69cb64b0421771324803a785546fa884f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693767"
---
# <a name="pseudovariables"></a>Pseudovariablen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pseudovariablen sind Begriffe, mit denen bestimmte Informationen in einem Variablenfenster oder im Dialogfeld **Schnellüberwachung** angezeigt werden. Eine Pseudovariable können Sie genauso wie eine normale Variable eingeben. Pseudovariablen sind jedoch keine Variablen und es gibt keine entsprechenden Variablennamen im Programm.  
  
## <a name="example"></a>Beispiel  
 Angenommen, Sie schreiben eine Anwendung in nativem Code, und Sie möchten die Anzahl zugeordneter Handles der Anwendung anzeigen. Im Fenster **Überwachen** können Sie in der Spalte **Name** die folgende Pseudovariable eingeben und zur Auswertung anschließend die EINGABETASTE drücken:  
  
```  
$handles  
```  
  
 Bei systemeigenem Code können Sie die in dieser Tabelle aufgeführten Pseudovariablen verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$err`|Es wird der letzten Fehlerwert angezeigt, der mit der Funktion "SetLastError" festgelegt wird. Der angezeigte Wert stellt das Ergebnis der Rückgabe der Funktion "GetLastError" dar.<br /><br /> Verwenden Sie `$err,hr`, um die dekodierte Form dieses Werts anzuzeigen. Wenn der letzte Fehler z. B. 3 wäre, würde `$err,hr``ERROR_PATH_NOT_FOUND : The system cannot find the path specified.` anzeigen.|  
|`$handles`|Zeigt die Anzahl von Handles an, die der Anwendung zugeordnet sind.|  
|`$vframe`|Zeigt die Adresse des aktuellen Stapelrahmens an.|  
|`$tid`|Zeigt die Thread-ID für den aktuellen Thread an.|  
|`$env`|Zeigt den Umgebungsblock im Zeichenfolgen-Viewer an.|  
|`$cmdline`|Zeigt die Befehlszeilenzeichenfolge an, mit der das Programm gestartet wurde.|  
|`$pid`|Zeigt die Prozess-ID an.|  
|`$` *Registername*<br /><br /> oder<br /><br /> `@` *Registername*|Zeigt den Inhalt des Registers *Registername* an.<br /><br /> Normalerweise geben Sie zum Anzeigen des Registerinhalts einfach den Registernamen ein. Nur beim Überladen eines Variablennamens durch einen Registernamen müssen Sie diese Syntax verwenden. Wenn der Registername im aktuellen Gültigkeitsbereich dem Variablennamen entspricht, interpretiert der Debugger den Namen als Variablenname. In diesem Fall sind `$`*Registername* bzw. `@`*Registername* praktisch.|  
|`$clk`|Zeigt die Zeit in Taktzyklen an.|  
|`$user`|Zeigt eine Struktur mit Kontoinformationen für das die Anwendung ausführende Konto an. Aus Sicherheitsgründen werden die Kennwortinformationen nicht angezeigt.|  
|`$exceptionstack`|Zeigt die Stapelüberwachung der aktuellen Windows-Runtime-Ausnahme an. `$ exceptionstack` funktioniert nur in Store-apps, die unter Windows 8.1 oder höher ausgeführt werden. `$ exceptionstack` wird nicht für C++- und SEH-Ausnahmen unterstützt.|  
|`$ReturnValue`|Zeigt den Rückgabewert einer .NET Framework-Methode an. Finden Sie unter [Überprüfen von Rückgabewerten der Methodenaufrufe](https://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 Die in dieser Tabelle angezeigten Pseudovariablen können Sie in C# und Visual Basic verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$exception`|Zeigt Informationen über die letzte Ausnahme an. Wenn keine Ausnahme aufgetreten ist, wird beim Auswerten von `$exception` eine Fehlermeldung angezeigt.<br /><br /> Bei deaktiviertem Ausnahmen-Assistenten wird in Visual C# dem Fenster **Lokal** bei Auftreten einer Ausnahme automatisch `$exception` hinzugefügt.|  
|`$user`|Zeigt eine Struktur mit Kontoinformationen für das die Anwendung ausführende Konto an. Aus Sicherheitsgründen werden die Kennwortinformationen nicht angezeigt.|  
  
 Die in dieser Tabelle angezeigten Pseudovariablen können Sie in Visual Basic verwenden:  
  
|Pseudovariable|Funktion|  
|--------------------|--------------|  
|`$delete` oder `$$delete`|Löscht eine implizite Variable, die im Fenster **Direkt** erstellt wurde. Die Syntax ist `$delete,` *Variable* oder`$delete,` *Variable*`.`|  
|`$objectids` oder `$listobjectids`|Zeigt alle aktiven Objekt-IDs als untergeordnete Elemente des angegebenen Ausdrucks an. Die Syntax ist `$objectid,` *Ausdruck* oder`$listobjectids,` *Ausdruck*`.`|  
|`$` *N* `#`|Zeigt das Objekt mit der Objekt-ID *N* an.|  
|`$dynamic`|Zeigt den besonderen Knoten **Dynamische Ansicht** für ein Objekt an, das `IDynamicMetaObjectProvider` implementiert. Schnittstelle Die Syntax lautet `$dynamic,` *Objekt*. Diese Funktion gilt nur für Code, der .NET Framework Version 4 verwendet. Finden Sie unter [dynamische Ansicht](https://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Siehe auch  
 [Fenster „Überwachen“ und „Schnellüberwachung“](../debugger/watch-and-quickwatch-windows.md)   
 [Variablenfenster](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
