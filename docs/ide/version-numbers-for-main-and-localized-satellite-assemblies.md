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
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: a41d725b9f58d0f434c3f5169d76988b675aa312
ms.lasthandoff: 02/22/2017

---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys
Die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse bietet Unterstützung bei der Versionsverwaltung für eine Hauptassembly, die lokalisierte Ressourcen mithilfe des Ressourcen-Managers verwendet. Das Anwenden der <xref:System.Resources.SatelliteContractVersionAttribute> auf die Hauptassembly einer Anwendung ermöglicht es Ihnen, die Assembly zu aktualisieren und erneut bereitzustellen, ohne die Satellitenassemblys upzudaten. Beispielsweise können Sie die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse mit einem Service Pack verwenden, das keine neuen Ressourcen einbringt, ohne die Satellitenassemblys neu zu erstellen und erneut bereitzustellen. Damit Ihre lokalisierten Ressourcen zur Verfügung stehen, muss die Satellitenvertragsversion der Hauptassembly mit der <xref:System.Reflection.AssemblyVersionAttribute>-Klasse der Satellitenassemblys übereinstimmen. Sie müssen in der <xref:System.Resources.SatelliteContractVersionAttribute> eine genaue Versionsnummer angeben; Platzhalterzeichen wie „*“ sind nicht zulässig. Weitere Informationen finden Sie unter [Abrufen von Ressourcen in Desktop-Apps](http://msdn.microsoft.com/Library/eca16922-1c46-4f68-aefe-e7a12283641f).  
  
## <a name="updating-assemblies"></a>Aktualisieren von Assemblys  
 Mit der <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse können Sie eine Hauptassembly aktualisieren, ohne die Satellitenassembly aktualisieren zu müssen oder umgekehrt. Wenn die Hauptassembly aktualisiert wird, wird die Versionsnummer der Assembly geändert. Wenn Sie weiterhin die vorhandenen Satellitenassemblys verwenden möchten, ändern Sie die Versionsnummer der Hauptassembly, aber lassen Sie die Versionsnummer des Satellitenvertrags unverändert. Beispielsweise kann die Hauptassemblyversion im ersten Release 1.0.0.0 sein. Die Satellitenvertragsversion und die Assemblyversion der Satellitenassembly werden ebenfalls 1.0.0.0 sein. Wenn Sie die Hauptassembly für ein Service Pack aktualisieren müssen, können Sie die Assemblyversion zu 1.0.0.1 ändern, während Sie für die Satellitenvertragsversion und die Satellitenassemblyversion 1.0.0.0 beibehalten.  
  
 Wenn Sie eine Satellitenassembly, jedoch nicht die Hauptassembly aktualisieren müssen, ändern Sie die <xref:System.Reflection.AssemblyVersionAttribute> der Satellitenassembly. Zusammen mit der Satellitenassembly müssen Sie eine Richtlinienassembly bereitstellen, die besagt, dass die neue Satellitenassembly mit der alten Satellitenassembly kompatibel ist. Weitere Informationen zu Richtlinien finden Sie unter [So sucht Common Language Runtime nach Assemblys](http://msdn.microsoft.com/Library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die Satellitenvertragsversion festgelegt wird. Der Code kann in ein Buildskript, die AssemblyInfo.vb-Datei oder die AssemblyInfo.cs-Datei eingefügt werden.  
  
```vb#  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```c#  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [So sucht Common Language Runtime nach Assemblys](http://msdn.microsoft.com/Library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)   
 [Festlegen von Assemblyattributen](http://msdn.microsoft.com/Library/36a98a81-b5b5-4c19-912a-11f91eff7f4e)   
 [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
