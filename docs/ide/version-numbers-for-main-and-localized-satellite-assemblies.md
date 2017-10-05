---
title: "Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: ed8f4db41c9b73f4efa376409f652fb3f7ec1f12
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys
Die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse bietet Unterstützung bei der Versionsverwaltung für eine Hauptassembly, die lokalisierte Ressourcen mithilfe des Ressourcen-Managers verwendet. Das Anwenden der <xref:System.Resources.SatelliteContractVersionAttribute> auf die Hauptassembly einer Anwendung ermöglicht es Ihnen, die Assembly zu aktualisieren und erneut bereitzustellen, ohne die Satellitenassemblys upzudaten. Beispielsweise können Sie die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse mit einem Service Pack verwenden, das keine neuen Ressourcen einbringt, ohne die Satellitenassemblys neu zu erstellen und erneut bereitzustellen. Damit Ihre lokalisierten Ressourcen zur Verfügung stehen, muss die Satellitenvertragsversion der Hauptassembly mit der <xref:System.Reflection.AssemblyVersionAttribute>-Klasse der Satellitenassemblys übereinstimmen. Sie müssen eine genaue Versionsnummer in <xref:System.Resources.SatelliteContractVersionAttribute> angeben; Platzhalterzeichen wie „*“ sind ungültig. Weitere Informationen finden Sie unter [Abrufen von Ressourcen in Desktop-Apps](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).  
  
## <a name="updating-assemblies"></a>Aktualisieren von Assemblys  
 Mit der <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse können Sie eine Hauptassembly aktualisieren, ohne die Satellitenassembly aktualisieren zu müssen oder umgekehrt. Wenn die Hauptassembly aktualisiert wird, wird die Versionsnummer der Assembly geändert. Wenn Sie weiterhin die vorhandenen Satellitenassemblys verwenden möchten, ändern Sie die Versionsnummer der Hauptassembly, aber lassen Sie die Versionsnummer des Satellitenvertrags unverändert. Beispielsweise kann die Hauptassemblyversion im ersten Release 1.0.0.0 sein. Die Satellitenvertragsversion und die Assemblyversion der Satellitenassembly werden ebenfalls 1.0.0.0 sein. Wenn Sie die Hauptassembly für ein Service Pack aktualisieren müssen, können Sie die Assemblyversion zu 1.0.0.1 ändern, während Sie für die Satellitenvertragsversion und die Satellitenassemblyversion 1.0.0.0 beibehalten.  
  
 Wenn Sie eine Satellitenassembly, jedoch nicht die Hauptassembly aktualisieren müssen, ändern Sie die <xref:System.Reflection.AssemblyVersionAttribute> der Satellitenassembly. Zusammen mit der Satellitenassembly müssen Sie eine Richtlinienassembly bereitstellen, die besagt, dass die neue Satellitenassembly mit der alten Satellitenassembly kompatibel ist. Weitere Informationen zu Richtlinien finden Sie unter [So sucht Common Language Runtime nach Assemblys](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die Satellitenvertragsversion festgelegt wird. Der Code kann in ein Buildskript, die AssemblyInfo.vb-Datei oder die AssemblyInfo.cs-Datei eingefügt werden.  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [So sucht Common Language Runtime nach Assemblys](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)   
 [Festlegen von Assemblyattributen](/dotnet/framework/app-domains/set-assembly-attributes)   
 [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
