---
title: "Versionsnummern f&#252;r Hauptassemblys und lokalisierte Satellitenassemblys | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assemblys [Visual Studio], Versionsnummern"
  - "Satellitenassemblys, Versionsnummern"
  - "SatelliteContractVersionAttribute"
  - "Versionsnummern, Assemblys"
  - "Versionskontrolle, Assemblys"
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Versionsnummern f&#252;r Hauptassemblys und lokalisierte Satellitenassemblys
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die <xref:System.Resources.SatelliteContractVersionAttribute>\-Klasse stellt Versionsunterstützung für eine Hauptassembly bereit, die mithilfe des Ressourcenmanagers lokalisierte Ressourcen verwendet.  Durch die Anwendung von <xref:System.Resources.SatelliteContractVersionAttribute> in der Hauptassembly einer Anwendung kann die Hauptassembly aktualisiert und erneut bereitgestellt werden, ohne ihre Satellitenassemblys aktualisieren zu müssen.  Sie können z. B. die <xref:System.Resources.SatelliteContractVersionAttribute>\-Klasse mit einem Service Pack verwenden, das keine neuen Ressourcen einbringt, ohne die Satellitenassemblys erneut erstellen und bereitstellen zu müssen.  Damit lokalisierte Ressourcen verfügbar sind, muss die Satellitenvertragsversion der Hauptassembly mit der <xref:System.Reflection.AssemblyVersionAttribute>\-Klasse der Satellitenassemblys übereinstimmen.  Sie müssen in <xref:System.Resources.SatelliteContractVersionAttribute> eine genaue Versionsnummer angeben. Platzhalterzeichen, z. B. "\*", sind nicht zulässig.  Weitere Informationen finden Sie unter [Abrufen von Ressourcen](../Topic/Retrieving%20Resources%20in%20Desktop%20Apps.md).  
  
## Aktualisieren von Assemblys  
 Mithilfe der <xref:System.Resources.SatelliteContractVersionAttribute>\-Klasse können Sie eine Hauptassembly aktualisieren, ohne die Satellitenassemblys ebenfalls aktualisieren zu müssen, und umgekehrt.  Nachdem die Hauptassembly aktualisiert wurde, wird ihre Assemblyversionsnummer geändert.  Wenn Sie die vorhandenen Satellitenassemblys weiterhin verwenden möchten, ändern Sie die Versionsnummer der Hauptassembly, behalten aber die Nummer der Satellitenvertragsversion bei.  Angenommen, bei der ersten Release ist die Hauptassemblyversion 1.0.0.0.  Die Satellitenvertragsversion und die Assemblyversion der Satellitenassembly sind dann ebenfalls 1.0.0.0.  Wenn Sie die Hauptassembly mit einem Service Pack aktualisieren müssen, können Sie die Assemblyversion in 1.0.0.1 ändern, während die Satellitenvertragsversion und die Version der Satellitenassembly weiterhin 1.0.0.0 bleiben.  
  
 Wenn Sie eine Satellitenassembly aktualisieren, ohne dass die Hauptversion aktualisiert werden muss, ändern Sie das <xref:System.Reflection.AssemblyVersionAttribute> der Satellitenassembly.  Zusammen mit der Satellitenassembly müssen Sie eine Richtlinienassembly ausliefern, die angibt, dass die neue Satellitenassembly mit der bisherigen Satellitenassembly kompatibel ist.  Weitere Informationen zu Richtlinien finden Sie unter [So sucht Common Language Runtime nach Assemblys](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
 Der folgende Code zeigt das Festlegen der Satellitenvertragsversion.  Der Code kann entweder in ein Buildscript, in die Datei **AssemblyInfo.vb** oder die Datei **AssemblyInfo.cs** eingefügt werden.  
  
```vb#  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```c#  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## Siehe auch  
 [So sucht Common Language Runtime nach Assemblys](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md)   
 [Festlegen von Assemblyattributen](../Topic/Setting%20Assembly%20Attributes.md)   
 [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)