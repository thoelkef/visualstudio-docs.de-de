---
title: TargetCLR | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fffcab1d841840c15957e8dae0ff0f87b20de28d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771600"
---
# <a name="targetclr"></a>TargetCLR
Die Option **TargetCLR** gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere CLR-Versionen geladen wurden.

 In der Standardeinstellung verwenden die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools als Ziel die erste Version der CLR, die von der Anwendung geladen wird.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parameter
 `ClrVersion`: die Versionsnummer der CLR. Verwenden Sie das Versionsformat **vN.N.NNNNN**.

## <a name="required-options"></a>Erforderliche Optionen
 Die Option **TargetCLR** kann nur mit den Optionen **Launch** (Start) oder **Attach** (Anfügen) verwendet werden.

 **Launch:** `AppName` startet die angegebene Anwendung und die Profilerstellung.

 **Attach:** `PID` beginnt mit der Profilerstellung des angegebenen Prozesses.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die TargetCLR-Option verwendet, um sicherzustellen, dass das Profil der CLR-Version 4.0.11003 erstellt wird.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
