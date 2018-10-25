---
title: 'Vorgehensweise: angeben eine .NET Framework-Version für das Debuggen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 79bbe6e6feefa8e7ccab04fe5bae5c2ec7c214ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902957"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Gewusst wie: Angeben einer .NET Framework-Version für das Debuggen
Der [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]-Debugger unterstützt das Debuggen sowohl älterer Versionen von Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] als auch der aktuellen Version. Wenn Sie eine Anwendung aus Visual Studio starten, kann der Debugger immer die richtige Version von erkennen die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] für die Anwendung, die Sie debuggen. Wenn die Anwendung bereits ausgeführt wird und Sie **Anfügen an**, der Debugger immer möglicherweise nicht zum Identifizieren von einer älteren Version von der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Dann erhalten Sie eine Fehlermeldung, die besagt,  
  
 Der Debugger ist bei der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Version, die von der Anwendung verwendet werden soll, von falschen Voraussetzungen ausgegangen.  
  
 Für diesen seltenen Fall können Sie in einem Registrierungsschlüssel die Version festlegen, die vom Debugger verwendet werden soll.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>So geben Sie eine .NET Framework-Version für das Debuggen an  
  
1. Durchsuchen Sie das Verzeichnis Windows\Microsoft.NET\Framework, um zu bestimmen, welche Versionen von .NET Framework auf dem Computer installiert sind. Die Versionsnummern haben folgendes Format:  
  
    `V1.1.4322`  
  
    Identifizieren Sie die richtige Versionsnummer, und notieren Sie sie.  
  
2. Starten Sie den **Registrierungs-Editor** (Regedit).  
  
3. In der **Registrierungs-Editor**, öffnen Sie den Ordner HKEY_LOCAL_MACHINE.  
  
4. Navigieren Sie zu: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
    Wenn der Schlüssel nicht vorhanden ist, mit der rechten Maustaste HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, und klicken Sie auf **neuer Schlüssel**. Nennen Sie den neuen Schlüssel `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. Suchen Sie nach dem Navigieren unter {449EC4CC-30D2-4032-9256-EE18EB41B62B}, in der **Namen** Spalte und den Schlüssel CLRVersionForDebugging.  
  
   1.  Wenn der Schlüssel nicht vorhanden ist, mit der rechten Maustaste unter {449EC4CC-30D2-4032-9256-EE18EB41B62B}, und klicken Sie auf **neuer Zeichenfolgenwert**. Klicken Sie dann den neuen Zeichenfolgenwert, klicken Sie auf **umbenennen**, und geben `CLRVersionForDebugging`.  
  
6. Doppelklicken Sie auf **CLRVersionForDebugging**.  
  
7. In der **Zeichenfolge bearbeiten** geben die .NET Framework-Versionsnummer in der **Wert** Feld. Beispiel: V1.1.4322  
  
8. Klicken Sie auf **OK**.  
  
9. Schließen der **Registrierungs-Editor**.  
  
     Wenn beim Starten des Debuggens weiterhin eine Fehlermeldung angezeigt wird, stellen Sie sicher, dass Sie in der Registrierung die richtige Versionsnummer eingegeben haben. Stellen Sie außerdem sicher, dass Sie eine Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwenden, die von Visual Studio unterstützt wird. Der Debugger ist mit der aktuellen .NET Framework-Version und älteren Versionen kompatibel. Er ist jedoch möglicherweise nicht mit zukünftigen Versionen kompatibel.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)