---
title: "Gewusst wie: Aufheben der Registrierung von VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Beispielanwendungen [Visual Studio SDK], deinstallieren"
  - "Setup, VSPackages"
ms.assetid: b51522f0-c033-4d93-b928-2171a953032b
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Gewusst wie: Aufheben der Registrierung von VSPackages
Beim Erstellen von VSPackages werden diese standardmäßig für die experimentelle Registrierungsstruktur registriert. Die experimentelle Struktur kann mit VSPackages gefüllt werden, die Sie nach deren Untersuchung nicht zu behalten beabsichtigen.  
  
 Setzen Sie einfach die Struktur mithilfe des CreateExpInstance\-Tools und der Option „\/Reset“ zurück, um alle Pakete zu löschen, die in der experimentellen Struktur registriert sind. Weitere Informationen finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
## Aufheben der Registrierung einzelner VSPackages  
  
#### So heben Sie die Registrierung eines nicht verwalteten VSPackages auf  
  
1.  Klicken Sie auf **Start** und auf **Ausführen**, geben Sie `regsvr32 /u` *pathToVSPackage.dll* ein, und klicken Sie dann auf „OK“.  
  
 Da nicht verwaltete VSPackages Selbstregistrierungscodes enthalten, können Sie das Dienstprogramm „regsvr32“ zum Registrieren sowie zum Aufheben der Registrierung verwenden.  
  
#### So heben Sie die Registrierung eines verwalteten VSPackages auf  
  
1.  Klicken Sie auf **Start** und **Ausführen**, geben Sie dann *Visual Studio SDK\-Installationspfad*`\EnvSDK\tools\bin\x86\regpkg /unregister` *pathToVSPackage.dll* ein, und klicken Sie anschließend auf „OK“.  
  
 Das RegPkg\-Tool liest die Registrierungsattribute, die in einem verwalteten VSPackage eingebettet werden können. Der **\/unregister**\-Schalter weist RegPkg entsprechend an, die Informationen aus der Registrierung zu entfernen.  
  
## Siehe auch  
 [Visual Studio Integration Samples](http://msdn.microsoft.com/de-de/b5dbf078-3af2-4fed-a1ea-171e4ee73a43)