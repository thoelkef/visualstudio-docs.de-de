---
title: WaitStart | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a409a4fe4ffe843df536e3c9e17a3a5a3b6560db
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322499"
---
# <a name="waitstart"></a>WaitStart
Die Option „WaitStart“ hat zur Folge, dass der Start-Unterbefehl für *VSPerfCmd.exe* nur einen Wert zurückgibt, wenn der Profiler initialisiert wurde oder die angegebene Anzahl von Sekunden überschritten wurde. Standardmäßig gibt der Startbefehl sofort einen Wert zurück. Wenn der Unterbefehl für den Start einen Wert zurückgibt, ohne einen Profiler zu initialisieren, wird ein Fehler zurückgegeben. Wenn die Zeit nicht in Sekunden vorgegeben ist, wird der Startbefehl auf unbestimmte Zeit ausgesetzt.

 Die Option „WaitStart“ ist nützlich für Batchdateien, um sicherzustellen, dass der Profiler initialisiert wurde.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parameter
 `Seconds`: die Wartezeit in Sekunden, bis der Unterbefehl für den Start einen Wert zurückgibt.

## <a name="required-options"></a>Erforderliche Optionen
 Die Option „WaitStart“ kann nur mit dem Unterbefehl für den Start verwendet werden.

 **Ausgabe:** `filename` gibt den Ausgabedateinamen an.

## <a name="remarks"></a>Anmerkungen

## <a name="example"></a>Beispiel
 In diesem Beispiel für eine Batchdatei wartet der Startbefehl fünf Sekunden darauf, dass der Profiler initialisiert wird.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
