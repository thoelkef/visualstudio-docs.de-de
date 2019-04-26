---
title: Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb699c7b5ab2aec928bf83ada5dd8824f93f3006
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558384"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Versionsnummern für Hauptassemblys und lokalisierte Satellitenassemblys
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse bietet Unterstützung bei der Versionsverwaltung für eine Hauptassembly, die lokalisierte Ressourcen mithilfe des Ressourcen-Managers verwendet. Das Anwenden der <xref:System.Resources.SatelliteContractVersionAttribute> auf die Hauptassembly einer Anwendung ermöglicht es Ihnen, die Assembly zu aktualisieren und erneut bereitzustellen, ohne die Satellitenassemblys upzudaten. Beispielsweise können Sie die <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse mit einem Service Pack verwenden, das keine neuen Ressourcen einbringt, ohne die Satellitenassemblys neu zu erstellen und erneut bereitzustellen. Damit Ihre lokalisierten Ressourcen zur Verfügung stehen, muss die Satellitenvertragsversion der Hauptassembly mit der <xref:System.Reflection.AssemblyVersionAttribute>-Klasse der Satellitenassemblys übereinstimmen. Sie müssen eine genaue Versionsnummer in <xref:System.Resources.SatelliteContractVersionAttribute> angeben; Platzhalterzeichen wie „*“ sind ungültig. Weitere Informationen finden Sie unter [Abrufen von Ressourcen in Desktop-Apps](http://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f).  
  
## <a name="updating-assemblies"></a>Aktualisieren von Assemblys  
 Mit der <xref:System.Resources.SatelliteContractVersionAttribute>-Klasse können Sie eine Hauptassembly aktualisieren, ohne die Satellitenassembly aktualisieren zu müssen oder umgekehrt. Wenn die Hauptassembly aktualisiert wird, wird die Versionsnummer der Assembly geändert. Wenn Sie weiterhin die vorhandenen Satellitenassemblys verwenden möchten, ändern Sie die Versionsnummer der Hauptassembly, aber lassen Sie die Versionsnummer des Satellitenvertrags unverändert. Beispielsweise kann die Hauptassemblyversion im ersten Release 1.0.0.0 sein. Die Satellitenvertragsversion und die Assemblyversion der Satellitenassembly werden ebenfalls 1.0.0.0 sein. Wenn Sie die Hauptassembly für ein Service Pack aktualisieren müssen, können Sie die Assemblyversion zu 1.0.0.1 ändern, während Sie für die Satellitenvertragsversion und die Satellitenassemblyversion 1.0.0.0 beibehalten.  
  
 Wenn Sie eine Satellitenassembly, jedoch nicht die Hauptassembly aktualisieren müssen, ändern Sie die <xref:System.Reflection.AssemblyVersionAttribute> der Satellitenassembly. Zusammen mit der Satellitenassembly müssen Sie eine Richtlinienassembly bereitstellen, die besagt, dass die neue Satellitenassembly mit der alten Satellitenassembly kompatibel ist. Weitere Informationen zu Richtlinien finden Sie unter [So sucht Common Language Runtime nach Assemblys](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die Satellitenvertragsversion festgelegt wird. Der Code kann in ein Buildskript, die AssemblyInfo.vb-Datei oder die AssemblyInfo.cs-Datei eingefügt werden.  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [So sucht Common Language Runtime nach Assemblys](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)   
 [Festlegen von Assemblyattributen](http://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e)   
 [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
