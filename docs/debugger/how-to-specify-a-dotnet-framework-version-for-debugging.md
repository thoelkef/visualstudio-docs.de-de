---
title: "Gewusst wie: Angeben einer .NET&#160;Framework-Version f&#252;r das Debuggen | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".NET Framework, Festlegen der Version für das Debuggen"
  - "Debuggen [Visual Studio], Angeben der .NET Framework-Version"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Angeben einer .NET&#160;Framework-Version f&#252;r das Debuggen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]\-Debugger unterstützt das Debuggen sowohl älterer Versionen von Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] als auch der aktuellen Version.  Wenn Sie eine Anwendung von Visual Studio aus starten, erkennt der Debugger stets die richtige Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] für die Anwendung, die Sie debuggen.  Wenn die Anwendung bereits ausgeführt wird und Sie **Anfügen an** verwenden, kann der Debugger möglicherweise nicht immer eine frühere Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] erkennen.  Dann erhalten Sie eine Fehlermeldung, die besagt,  
  
 Der Debugger ist bei der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Version, die von der Anwendung verwendet werden soll, von falschen Voraussetzungen ausgegangen.  
  
 Für diesen seltenen Fall können Sie in einem Registrierungsschlüssel die Version festlegen, die vom Debugger verwendet werden soll.  
  
### So geben Sie eine .NET Framework\-Version für das Debuggen an  
  
1.  Durchsuchen Sie das Verzeichnis Windows\\Microsoft.NET\\Framework, um zu bestimmen, welche Versionen von .NET Framework auf dem Computer installiert sind.  Die Versionsnummern haben folgendes Format:  
  
     `V1.1.4322`  
  
     Identifizieren Sie die richtige Versionsnummer, und notieren Sie sie.  
  
2.  Starten Sie den **Registrierungs\-Editor** \(regedit\).  
  
3.  Öffnen Sie im **Registrierungs\-Editor** den Ordner HKEY\_LOCAL\_MACHINE.  
  
4.  Navigieren Sie zu HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}.  
  
     Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\8.0\\AD7Metrics\\Engine, und klicken Sie auf **Neuer Schlüssel**.  Geben Sie dem neuen Schlüssel den Namen `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Suchen Sie unter {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} in der Spalte **Name** den Schlüssel CLRVersionForDebugging.  
  
    1.  Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}, und klicken Sie auf **Neuer Zeichenfolgenwert**.  Klicken Sie dann mit der rechten Maustaste auf den neuen Zeichenfolgenwert, klicken Sie auf **Umbenennen**, und geben Sie `CLRVersionForDebugging` ein.  
  
6.  Doppelklicken Sie auf **CLRVersionForDebugging**.  
  
7.  Geben Sie im Feld **Zeichenfolge bearbeiten** die .NET Framework\-Versionsnummer in das Feld **Wert** ein.  Beispiel: V1.1.4322  
  
8.  Klicken Sie auf **OK**.  
  
9. Schließen Sie den **Registrierungs\-Editor**.  
  
     Wenn beim Starten des Debuggens weiterhin eine Fehlermeldung angezeigt wird, stellen Sie sicher, dass Sie in der Registrierung die richtige Versionsnummer eingegeben haben.  Stellen Sie außerdem sicher, dass Sie eine Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwenden, die von Visual Studio unterstützt wird.  Der Debugger ist mit der aktuellen .NET Framework\-Version und älteren Versionen kompatibel. Er ist jedoch möglicherweise nicht mit zukünftigen Versionen kompatibel.  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)