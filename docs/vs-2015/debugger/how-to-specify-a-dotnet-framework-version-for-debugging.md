---
title: 'Vorgehensweise: Geben Sie eine .NET Framework-Version für das Debuggen | Microsoft-Dokumentation'
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b3e5d7ebb1f61ffdbff98f49f83025115c80f64
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957413"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Vorgehensweise: Geben Sie eine .NET Framework-Version für das Debuggen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]-Debugger unterstützt das Debuggen sowohl älterer Versionen von Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] als auch der aktuellen Version. Wenn Sie eine Anwendung von Visual Studio aus starten, erkennt der Debugger stets die richtige Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] für die Anwendung, die Sie debuggen. Wenn die Anwendung bereits ausgeführt wird und Sie **Anfügen an**, der Debugger immer möglicherweise nicht zum Identifizieren von einer älteren Version von der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Dann erhalten Sie eine Fehlermeldung, die besagt,  
  
 Der Debugger ist bei der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version, die von der Anwendung verwendet werden soll, von falschen Voraussetzungen ausgegangen.  
  
 Für diesen seltenen Fall können Sie in einem Registrierungsschlüssel die Version festlegen, die vom Debugger verwendet werden soll.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>So geben Sie eine .NET Framework-Version für das Debuggen an  
  
1.  Durchsuchen Sie das Verzeichnis Windows\Microsoft.NET\Framework, um zu bestimmen, welche Versionen von .NET Framework auf dem Computer installiert sind. Die Versionsnummern haben folgendes Format:  
  
     `V1.1.4322`  
  
     Identifizieren Sie die richtige Versionsnummer, und notieren Sie sie.  
  
2.  Starten Sie den **Registrierungs-Editor** (regedit).  
  
3.  Öffnen Sie im **Registrierungs-Editor** den Ordner HKEY_LOCAL_MACHINE.  
  
4.  Navigieren Sie zu: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, und klicken Sie auf **Neuer Schlüssel**. Nennen Sie den neuen Schlüssel `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Suchen Sie unter {449EC4CC-30D2-4032-9256-EE18EB41B62B} in der Spalte **Name** den Schlüssel CLRVersionForDebugging.  
  
    1.  Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf {449EC4CC-30D2-4032-9256-EE18EB41B62B}, und klicken Sie dann auf **Neuer Zeichenfolgenwert**. Klicken Sie dann den neuen Zeichenfolgenwert, klicken Sie auf **umbenennen**, und geben `CLRVersionForDebugging`.  
  
6.  Doppelklicken Sie auf **CLRVersionForDebugging**.  
  
7.  Geben Sie im Feld **Zeichenfolge bearbeiten** die .NET Framework-Versionsnummer in das Feld **Wert** ein. Zum Beispiel: V1.1.4322  
  
8.  Klicken Sie auf **OK**.  
  
9. Schließen Sie den **Registrierungs-Editor**.  
  
     Wenn beim Starten des Debuggens weiterhin eine Fehlermeldung angezeigt wird, stellen Sie sicher, dass Sie in der Registrierung die richtige Versionsnummer eingegeben haben. Stellen Sie außerdem sicher, dass Sie eine Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verwenden, die von Visual Studio unterstützt wird. Der Debugger ist mit der aktuellen .NET Framework-Version und älteren Versionen kompatibel. Er ist jedoch möglicherweise nicht mit zukünftigen Versionen kompatibel.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
