---
title: Args | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 036b13a7fea5d64e23e2b7d5ccbd8a7b17f91176
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608512"
---
# <a name="args"></a>Args
Die VSPerfCmd.exe-Option **Args** bestimmt eine Liste von Argumenten, die an die Zielanwendung des Unterbefehls **Starten** übergeben werden.

 **Args** kann nur dann verwendet werden, wenn **Starten** auch in der Befehlszeile angegeben ist. **Args** ist optional, wenn **Starten** angegeben ist.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parameter
 `Arguments`: eine Liste von Argumenten für die Zielanwendung des Befehls **Launch**.

## <a name="required-options"></a>Erforderliche Optionen
 **Launch:** `AppName` startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.

## <a name="example"></a>Beispiel
 Folgendes Beispiel verwendet die Option **Args**, um Argumente an TestApp.exe zu übergeben.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung von Diensten](../profiling/command-line-profiling-of-services.md)