---
title: TargetCLR | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1af1c4ac4220b387614653c8791d907fea8f264e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="targetclr"></a>TargetCLR
Die Option **TargetCLR** gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere CLR-Versionen geladen wurden.  
  
 In der Standardeinstellung verwenden die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools als Ziel die erste Version der CLR, die von der Anwendung geladen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```