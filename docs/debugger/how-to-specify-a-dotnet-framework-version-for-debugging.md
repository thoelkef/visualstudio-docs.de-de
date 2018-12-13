---
title: Geben Sie eine .NET Framework-Version für das Debuggen | Microsoft-Dokumentation
ms.custom: seodec18
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
ms.openlocfilehash: 86289c9a93a0bb9e0f7756443d79f4a1a6dd38a6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056007"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>Vorgehensweise: Geben Sie eine .NET Framework-Version für das Debuggen (C#, Visual Basic F#)

Visual Studio-Debugger unterstützt das Debuggen von älteren Versionen von Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sowie die aktuelle Version. Wenn Sie eine Anwendung von Visual Studio aus starten, erkennt der Debugger stets die richtige Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] für die Anwendung, die Sie debuggen. Allerdings ist die Anwendung bereits ausgeführt wird und Sie Debuggen mit **Anfügen an**, der Debugger immer möglicherweise nicht zum Identifizieren von einer älteren Version von der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Dann erhalten Sie eine Fehlermeldung, die besagt,  

``` cmd 
The debugger has made an incorrect assumption about the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version your application is going to use.  
```

In den seltenen Fällen, in denen dieser Fehler tritt auf, können Sie einen Registrierungsschlüssel an, dass zum Debugger, welche Version verwendet festlegen.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>So geben Sie eine .NET Framework-Version für das Debuggen an  
  
1. Durchsuchen Sie das Verzeichnis Windows\Microsoft.NET\Framework, um zu bestimmen, welche Versionen von .NET Framework auf dem Computer installiert sind. Die Versionsnummern haben folgendes Format:  
  
    `V1.1.4322`  
  
    Identifizieren Sie die richtige Versionsnummer, und notieren Sie sie.  
  
2. Starten Sie den **Registrierungs-Editor** (regedit).  
  
3. Öffnen Sie im **Registrierungs-Editor** den Ordner HKEY_LOCAL_MACHINE.  
  
4. Navigate to (Navigieren zu). HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
    Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, und klicken Sie auf **Neuer Schlüssel**. Nennen Sie den neuen Schlüssel `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. Suchen Sie unter {449EC4CC-30D2-4032-9256-EE18EB41B62B} in der Spalte **Name** den Schlüssel CLRVersionForDebugging.  
  
   1.  Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf {449EC4CC-30D2-4032-9256-EE18EB41B62B}, und klicken Sie dann auf **Neuer Zeichenfolgenwert**. Klicken Sie dann den neuen Zeichenfolgenwert, klicken Sie auf **umbenennen**, und geben `CLRVersionForDebugging`.  
  
6. Doppelklicken Sie auf **CLRVersionForDebugging**.  
  
7. Geben Sie im Feld **Zeichenfolge bearbeiten** die .NET Framework-Versionsnummer in das Feld **Wert** ein. Beispiel: V1.1.4322  
  
8. Klicken Sie auf **OK**.  
  
9. Schließen Sie den **Registrierungs-Editor**.  
  
     Wenn beim Starten des Debuggens weiterhin eine Fehlermeldung angezeigt wird, stellen Sie sicher, dass Sie in der Registrierung die richtige Versionsnummer eingegeben haben. Stellen Sie außerdem sicher, dass Sie eine Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwenden, die von Visual Studio unterstützt wird. Der Debugger ist mit der aktuellen .NET Framework-Version und älteren Versionen kompatibel. Er ist jedoch möglicherweise nicht mit zukünftigen Versionen kompatibel.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)