---
title: TargetCLR | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf48109107e6e2ef0c4f2d5d4c8f72a8f8fc0443
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973654"
---
# <a name="targetclr"></a>TargetCLR
Die Option **TargetCLR** gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere CLR-Versionen geladen wurden.  
  
 In der Standardeinstellung verwenden die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools als Ziel die erste Version der CLR, die von der Anwendung geladen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parameter  
 `ClrVersion`  
 Die Versionsnummer der CLR. Verwenden Sie das Versionsformat **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die Option **TargetCLR** kann nur mit den Optionen **Launch** (Start) oder **Attach** (Anfügen) verwendet werden.  
  
 **Starten:** `AppName`  
 Startet die angegebene Anwendung und die Profilerstellung.  
  
 **Attach:** `PID`  
 Beginnt mit der Profilerstellung des angegebenen Prozesses.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die TargetCLR-Option verwendet, um sicherzustellen, dass das Profil der CLR-Version 4.0.11003 erstellt wird.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```