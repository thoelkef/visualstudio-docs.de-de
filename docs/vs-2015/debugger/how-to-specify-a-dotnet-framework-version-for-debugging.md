---
title: 'Vorgehensweise: angeben eine .NET Framework-Version für das Debuggen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a07975591525f9109fecfbfb5aaa27642fc9562
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512724"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Gewusst wie: Angeben einer .NET Framework-Version für das Debuggen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Angeben einer .NET Framework-Version für Debuggen](https://docs.microsoft.com/visualstudio/debugger/how-to-specify-a-dotnet-framework-version-for-debugging).  
  
Der [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]-Debugger unterstützt das Debuggen sowohl älterer Versionen von Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] als auch der aktuellen Version. Wenn Sie eine Anwendung aus Visual Studio starten, kann der Debugger immer die richtige Version von erkennen die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] für die Anwendung, die Sie debuggen. Wenn die Anwendung bereits ausgeführt wird und Sie **Anfügen an**, der Debugger immer möglicherweise nicht zum Identifizieren von einer älteren Version von der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Dann erhalten Sie eine Fehlermeldung, die besagt,  
  
 Der Debugger ist bei der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version, die von der Anwendung verwendet werden soll, von falschen Voraussetzungen ausgegangen.  
  
 Für diesen seltenen Fall können Sie in einem Registrierungsschlüssel die Version festlegen, die vom Debugger verwendet werden soll.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>So geben Sie eine .NET Framework-Version für das Debuggen an  
  
1.  Durchsuchen Sie das Verzeichnis Windows\Microsoft.NET\Framework, um zu bestimmen, welche Versionen von .NET Framework auf dem Computer installiert sind. Die Versionsnummern haben folgendes Format:  
  
     `V1.1.4322`  
  
     Identifizieren Sie die richtige Versionsnummer, und notieren Sie sie.  
  
2.  Starten Sie den **Registrierungs-Editor** (Regedit).  
  
3.  In der **Registrierungs-Editor**, öffnen Sie den Ordner HKEY_LOCAL_MACHINE.  
  
4.  Navigieren Sie zu: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Wenn der Schlüssel nicht vorhanden ist, mit der rechten Maustaste HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, und klicken Sie auf **neuer Schlüssel**. Nennen Sie den neuen Schlüssel `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Suchen Sie nach dem Navigieren unter {449EC4CC-30D2-4032-9256-EE18EB41B62B}, in der **Namen** Spalte und den Schlüssel CLRVersionForDebugging.  
  
    1.  Wenn der Schlüssel nicht vorhanden ist, mit der rechten Maustaste unter {449EC4CC-30D2-4032-9256-EE18EB41B62B}, und klicken Sie auf **neuer Zeichenfolgenwert**. Klicken Sie dann den neuen Zeichenfolgenwert, klicken Sie auf **umbenennen**, und geben `CLRVersionForDebugging`.  
  
6.  Doppelklicken Sie auf **CLRVersionForDebugging**.  
  
7.  In der **Zeichenfolge bearbeiten** geben die .NET Framework-Versionsnummer in der **Wert** Feld. Beispiel: V1.1.4322  
  
8.  Klicken Sie auf **OK**.  
  
9. Schließen der **Registrierungs-Editor**.  
  
     Wenn beim Starten des Debuggens weiterhin eine Fehlermeldung angezeigt wird, stellen Sie sicher, dass Sie in der Registrierung die richtige Versionsnummer eingegeben haben. Stellen Sie außerdem sicher, dass Sie eine Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verwenden, die von Visual Studio unterstützt wird. Der Debugger ist mit der aktuellen .NET Framework-Version und älteren Versionen kompatibel. Er ist jedoch möglicherweise nicht mit zukünftigen Versionen kompatibel.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)



