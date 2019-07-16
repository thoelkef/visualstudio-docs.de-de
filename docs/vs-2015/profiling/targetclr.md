---
title: TargetCLR | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145620"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Option **TargetCLR** gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere CLR-Versionen geladen wurden.  
  
 In der Standardeinstellung verwenden die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools als Ziel die erste Version der CLR, die von der Anwendung geladen wird.  
  
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
