---
title: WaitStart | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1737f13a5271b2c4012ff6ee957fa08b0b8b7799
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164545"
---
# <a name="waitstart"></a>WaitStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Option „WaitStart“ hat zur Folge, dass der Unterbefehl „VSPerfCmd.exe“ für den Start nur einen Wert zurückgibt, wenn der Profiler initialisiert wurde oder die angegebene Anzahl von Sekunden überschritten wurde. Standardmäßig gibt der Startbefehl sofort einen Wert zurück. Wenn der Unterbefehl für den Start einen Wert zurückgibt, ohne einen Profiler zu initialisieren, wird ein Fehler zurückgegeben. Wenn die Zeit nicht in Sekunden vorgegeben ist, wird der Startbefehl auf unbestimmte Zeit ausgesetzt.  
  
 Die Option „WaitStart“ ist nützlich für Batchdateien, um sicherzustellen, dass der Profiler initialisiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Seconds`  
 Die Zeit in Sekunden, die gewartet werden, bis der Unterbefehl für den Start einen Wert zurückgibt.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die Option „WaitStart“ kann nur mit dem Unterbefehl für den Start verwendet werden.  
  
 **Ausgabe:** `filename`  
 Gibt den Ausgabedateinamen an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel für eine Batchdatei wartet der Startbefehl fünf Sekunden darauf, dass der Profiler initialisiert wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```
