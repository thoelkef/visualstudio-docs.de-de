---
title: "Problembehandlung bei Ausnahmen: System.IO.FileLoadException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FileLoadException-Klasse"
ms.assetid: 6b4519e3-4d29-4031-8aec-c2735b4ee16d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IO.FileLoadException
Eine <xref:System.IO.FileLoadException>\-Ausnahme wird ausgelöst, wenn eine verwaltete Assembly gefunden wurde, die nicht geladen werden kann.  
  
## Tipps  
 **Stellen Sie sicher, dass die Datei eine gültige .NET Framework\-Assembly ist.**  
 Diese Ausnahme wird ausgelöst, wenn die Datei keine gültige .NET Framework\-Assembly ist. Weitere Informationen finden Sie unter <xref:System.Reflection.Assembly>.  
  
 **Überprüfen Sie, ob eine Assembly oder ein Modul nicht zweimal mit zwei unterschiedlichen Beweisen geladen wurde.**  
 Den Beweis bilden die Informationen, die der Sicherheitsrichtlinie als Eingaben für Entscheidungen dienen, z. B., welche Berechtigungen einem Code erteilt werden können. Weitere Informationen finden Sie unter <xref:System.EnterpriseServices.Internal.Publish.GacRemove%2A> und unter <xref:System.Reflection.Assembly.Evidence%2A>.  
  
 **Wenn Sie die RegisterAssembly\-Methode oder die UnregisterAssembly\-Methode verwenden, stellen Sie sicher, dass der Assemblyname nicht länger als MAX\_PATH Zeichen ist.**  
 Der Assemblyname darf nicht länger als MAX\_PATH Zeichen sein. Weitere Informationen finden Sie unter <xref:System.EnterpriseServices.Internal.IComSoapPublisher.RegisterAssembly%2A> und <xref:System.EnterpriseServices.Internal.IComSoapPublisher.UnRegisterAssembly%2A>.  
  
 **Stellen Sie zum Laden einer Satellitenassembly sicher, dass die angegebene CultureInfo zur CultureInfo der Datei passt.**  
 Satellitenassemblys enthalten lokalisierte Ressourcen, die nicht lokalisierbaren ausführbaren Code sowie Ressourcen für eine bestimmte Kultur enthalten, die als Standardkultur bzw. neutrale Kultur dienen. Weitere Informationen finden Sie unter <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>.  
  
## Siehe auch  
 <xref:System.IO.FileLoadException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)