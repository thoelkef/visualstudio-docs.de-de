---
title: Neutrale Ressourcensprachen für die Lokalisierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85e0be0172f27732f8efeb882cbcde5b9c6aef3d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670392"
---
# <a name="neutral-resources-languages-for-localization"></a>Neutrale Ressourcensprachen für die Lokalisierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 <xref:System.Resources.ResourceManager> [Einführung in internationale Anwendungen basierend auf der .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [hierarchischen Organisation von Ressourcen für die Lokalisierung Lokalisierung von](../ide/hierarchical-organization-of-resources-for-localization.md) [Anwendungen](../ide/localizing-applications.md) [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
