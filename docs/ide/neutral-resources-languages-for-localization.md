---
title: "Neutrale Ressourcensprachen für die Lokalisierung | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 755be1dac065f2a8cd9ee769557f0a48e72ce03f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="neutral-resources-languages-for-localization"></a>Neutrale Ressourcensprachen für die Lokalisierung
Die Klasse <xref:System.Resources.NeutralResourcesLanguageAttribute> gibt die Kultur der Ressourcen an, die in der Hauptassembly enthalten sind. Mit diesem Attribut wird die Leistung optimiert, sodass das <xref:System.Resources.ResourceManager>-Objekt nicht nach Ressourcen sucht, die in der Hauptassembly enthalten sind.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie neutrale Sprachressourcen festgelegt werden. Der Code kann in ein Buildskript, die AssemblyInfo.vb-Datei oder die AssemblyInfo.cs-Datei eingefügt werden.  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Resources.ResourceManager>   
 [Einführung in internationale Anwendungen basierend auf .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Hierarchische Organisation der Ressourcen für die Lokalisierung](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)