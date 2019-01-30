---
title: Mark | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 952d5c726090aabbc4fe550f64696bcce7a3f784
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940075"
---
# <a name="mark"></a>Mark
Über die *VSPerfCmd.exe*-Option **Mark** (Markieren) werden die angegeben Informationen in die Profilerstellungs-Datendatei eingefügt. Die Option „Mark“ kann in einem separaten VSPerfReport-Bericht oder in der Mark-Berichtsansicht der Benutzeroberfläche für die Profilerstellung aufgeführt werden. **Mark** kann verwendet werden, um Start- und Endpunkte in Berichten sowie Filter für die Ansicht anzugeben.  
  
 Die Option **Mark** (Markieren) muss als einzige Option in der Befehlszeile angegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parameter  
 `MarkID`  
 Eine benutzerdefinierte Ganzzahl, die als Mark-ID in den Ansichten des Profilers und des Berichts aufgeführt ist. `MarkID` muss nicht eindeutig sein.  
  
 `MarkName`  
 (Optional) Eine benutzerdefinierte Zeichenfolge, die als der Markierungsname in den Ansichten des Profilers und des Berichts aufgeführt ist. Wenn `MarkName` nicht angegeben ist, ist das Feld für den Markierungsnamen in der Markierungsauflistung leer. Setzen Sie Zeichenfolgen, die Leerräume und Schrägstriche enthalten, in Anführungszeichen.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird ein Mark mit der ID „123“ und dem Markierungsnamen „TestMark“ eingefügt.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)