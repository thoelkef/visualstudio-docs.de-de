---
title: Pseudovariables | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b6856517a680809ccc802c02dc880b6349eadc5
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535958"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudo Variablen im Visual Studio-Debugger
Pseudovariablen sind Begriffe, mit denen bestimmte Informationen in einem Variablenfenster oder im Dialogfeld **Schnellüberwachung** angezeigt werden. Eine Pseudovariable können Sie genauso wie eine normale Variable eingeben. Pseudovariablen sind jedoch keine Variablen und es gibt keine entsprechenden Variablennamen im Programm.

## <a name="example"></a>Beispiel
 Angenommen, Sie schreiben eine Anwendung in nativem Code, und Sie möchten die Anzahl zugeordneter Handles der Anwendung anzeigen. Im Fenster **Überwachen** können Sie in der Spalte **Name** die folgende Pseudovariable eingeben und zur Auswertung anschließend die EINGABETASTE drücken:

`$handles`

 In nativem Code können Sie die in der folgenden Tabelle gezeigten Pseudo Variablen verwenden:

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
|`$exceptionstack`|Zeigt die Stapelüberwachung der aktuellen Windows-Runtime-Ausnahme an. `$ exceptionstack` funktioniert nur in UWP-apps. `$ exceptionstack` wird für C++ -und SEH-Ausnahmen nicht unterstützt.|
|`$returnvalue`|Zeigt den Rückgabewert einer .NET-Methode an.|

 In C# können Sie die in der folgenden Tabelle aufgeführten Pseudo Variablen verwenden:

|Pseudovariable|Funktion|
|--------------------|--------------|
|`$exception`|Zeigt Informationen über die letzte Ausnahme an. Wenn keine Ausnahme aufgetreten ist, wird beim Auswerten von `$exception` eine Fehlermeldung angezeigt.<br /><br /> Wenn der Ausnahmen-Assistent deaktiviert ist, wird `$exception` automatisch dem lokal **Fenster hinzu** gefügt, wenn eine Ausnahme auftritt.|
|`$user`|Zeigt eine Struktur mit Kontoinformationen für das die Anwendung ausführende Konto an. Aus Sicherheitsgründen werden die Kennwortinformationen nicht angezeigt.|
|`$returnvalue`|Zeigt den Rückgabewert einer .NET-Methode an.|

 Die in dieser Tabelle angezeigten Pseudovariablen können Sie in Visual Basic verwenden:

|Pseudovariable|Funktion|
|--------------------|--------------|
|`$exception`|Zeigt Informationen über die letzte Ausnahme an. Wenn keine Ausnahme aufgetreten ist, wird beim Auswerten von `$exception` eine Fehlermeldung angezeigt.|
|`$delete` oder `$$delete`|Löscht eine implizite Variable, die im Fenster **Direkt** erstellt wurde. Die Syntax ist `$delete,` *Variable* oder `$delete,` *Variable* `.`|
|`$objectids` oder `$listobjectids`|Zeigt alle aktiven Objekt-IDs als untergeordnete Elemente des angegebenen Ausdrucks an. Die Syntax ist `$objectid,` *Ausdruck* oder `$listobjectids,` *Ausdruck* `.`|
|`$` *N* `#`|Zeigt das Objekt mit der Objekt-ID *N* an.|
|`$dynamic`|Zeigt den besonderen Knoten **Dynamische Ansicht** für ein Objekt an, das `IDynamicMetaObjectProvider` implementiert. Schnittstelle Die Syntax lautet `$dynamic,` *Objekt*. Diese Funktion gilt nur für Code, der .NET Framework Version 4 oder höher verwendet.|

## <a name="see-also"></a>Siehe auch
- [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)
- [Variablenfenster](../debugger/debugger-windows.md)
